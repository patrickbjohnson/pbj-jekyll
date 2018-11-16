---
layout: post
title:  "Creating dynamic, reactive UIs for Shopify without React"
date:   2018-11-16
permalink: /writing/reactive-shopify-ui.html
crosspost_to_medium: true
---

There are a ton of sites on the internet which rely upon Shopify to power their e-commerce needs. Almost all of those websites have interactions which are responsible for a handful of UI-based updates. Managing those UI updates between various JavaScript files can sometimes get carried away, leading to unorganized or closely-coupled code. 

The most recent site I built, [Colugo](https://hicolugo.com), uses Shopify and I ran into this thought while planning the build. I knew I’d need to share component state(s) between components and the site overall. I considered adding React but then decided to use the publisher-subscriber pattern via an events library may be a simpler approach. And as most clickbait articles would say: <em>The results will shock you!</em>

## Using Events in Shopify
It came to my surprise when I found out Shopify has an events library pre-packaged within Slate. By way of Webpack, Shopify ships with an event module, “events.js”, which implements the [Node.js events module for browser environments](https://www.npmjs.com/package/events).

This approach can be achieved with any other events module as well. 

## Dynamic, Reactive User Interfaces
My goal while building the e-commerce site for Colugo was to reduce direct coupling between my components as much as possible. Using a publisher-subscriber pattern to manage events made decoupling a breeze and ended with a much more organized code base.

Knowing I’d use this pattern up front enabled me to map out a few components which would require dynamic UI components and what some states would look like:

-   When a user adds an item to the cart
    - If successful, display the minicart and/or confirmation message
    - If unsuccessful, display error messaging.
-   When a user clicks the mobile “cart” icon to display the menu
    - If the mobile menu is visible, close it and display the mini cart
    - If the mobile menu is not visible, open the mini cart. 
- When a user views the product detail page
    - If a user selects a product color, then scrolls:
        - Display current color selection
        - User may update selection
        - New selection reflected between shared components
    - If a user updates color selection:
        - Display current quantity
        - When a user scrolls back up, new quantity should correctly display between shared components

If we were using React, a lot of this UI interaction would be composed via Redux or a HOC passing props and event handlers to smaller components. Since we can’t easily use React with Shopify we needed another way to share small pieces “state” updates between components.

## Enter Event.js

### Using Namespaces For Organized Events
Because our events were being fired in more than one module, we created a small object which exposed the event “types”. It looks like this:

    export default eventTypes = {
        menuUpdate: 'colugo:menu-update',
        mobileMenuUpdate: 'colugo:mobile-nav-update',
        cartUpdate: 'colugo:cart-update',
        variantUpdate: 'colugo:variant-update',
        productNavUpdate: 'colugo:pn-udpate',
        miniCartUpdate: 'colugo:minicart-update',
        recircUpdate: 'colugo:recirc-update',
        recircCartUpdate: 'colugo:recirc-cart-add',
    };

This module isn’t special. It provides a consistent way to set up named event publications and subscriptions I know won’t collide within modules.

### Payloads
Within each event, we passed in a payload object which represents the data any and all subscribers could use to update their UI. In the case of Colugo, the payloads were usually:

- Product
    - Variant
        - ID
        - Title
        - Price
        - Inventory
        - Color
- Cart
    - Total Count
    - Items Array
    - Cart Update (Success or Failure)
- Display States
    - Mini Cart Toggling
    - Menu Toggling
    - Newsletter Modals

### Publishing Events
Now that we have our namespaces setup along with our payloads, we can publish an event:

    import events from 'events'
    import eventTypes from 'eventTypes'

    events.emit(eventTypes.variantUpdate, {
        ... payload object
    });


### Subscribing To Events
Our event bus now makes subscribing events super easy. Bringing together our namespace and payload, subscribing to events looks like this:

    import events from 'events'
    import eventTypes from 'eventTypes'

    events.on(eventTypes.variantUpdate, (payload) => {
        ... run whatever you want
    }));

This separates UI updates from the events themselves. For instance, within Colugo, when a user selects a different product color a few UI changes happen:

- New color is selected as active
- Product variant name is updated
- Product price is updated
- Product inventory may be updated
- Product gallery images may be updated.

In past projects, I may have written all the UI changes into one “products.js” file encapsulating all of those DOM elements which make up the UI which changes. While this worked, we also had to keep track of multiple UI components, track which one was changed, when it changed and then propagate changes to other components. In a nutshell, the old approach meant a lot of arrays and looping.

In the case of Colugo, if a user interacted with the color picker, we subscribe to the `variantUpdate` event and call the component methods to update the UI.

    import events from 'events'
    import eventTypes from 'eventTypes'

    events.on(eventTypes.variantUpdate, (product) => {
        // destructure object for props if necessary
        //
        colorPicker.setActiveColor(product.variant.color)
        productContent.udpateTitle(product.title)
        productContent.updatePrice(product.price)
        productContent.updateInveotyr(product.inventoryCount)
        productGallery.updateGallery(product.variant.images)
        ...
        ...
    });

    By leveraging the publisher-subscriber pattern and the built-in events library in Webpack we’re able to manage UI changes in a clean, consistent and organized manner. Our footprint is kept to a minimum and UI components (existing or newly made) can easily subscribe to events with very little overhead.

### Aside on “events”
Throughout this article we use the term “events”. It’s worth clarifying we are not referring to browser events like “click” or “onchange” event. With the publisher-subscriber pattern, there are no browser events being fired so it can be beneficial for performance as well.

Helpful reference for further reading:[https://stackoverflow.com/questions/27677692/performance-cost-of-pubsub-excessive-events-and-event-handlers-in-javascript](https://stackoverflow.com/questions/27677692/performance-cost-of-pubsub-excessive-events-and-event-handlers-in-javascript)

#### IRL Examples
Rather than just talking about the work, feel free to check out [Colugo's Product Detail Page](https://hicolugo.com/products/compact-stroller?variant=14529068662854) and poke around! You’ll see how pieces of UI interact with one another. Here are a few areas you can look at which take advantage of the publisher-subscriber method and events.js

- Select a color on a product page
    - This should change the image gallery and some content in the hero
- Scroll down and use the sticky color picker to update the color
    - This will sync up the content and gallery to the new current selection
- Add a product to the cart 
    -If successful, will open the cart and update the cart number count

#### Demos
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

<p>Pub/Sub - Counter Example</p>
<p data-height="265" data-theme-id="0" data-slug-hash="QZPJvR" data-default-tab="js,result" data-user="pbj" data-pen-title="Pub/Sub - Counter Example" class="codepen"><a href="https://codepen.io/pbj/pen/QZPJvR/"></a>.</p>

<p>Pub/Sub - Cart Notification<</p>
<p data-height="265" data-theme-id="0" data-slug-hash="LgvMga" data-default-tab="css,result" data-user="pbj" data-pen-title="Pub/Sub - Cart Notification" class="codepen"><a href="https://codepen.io/pbj/pen/LgvMga/">/a></p>

<p>Pub/Sub - Active Element</p>
<p data-height="265" data-theme-id="0" data-slug-hash="oQZKRz" data-default-tab="css,result" data-user="pbj" data-pen-title="Pub/Sub - Active Element" class="codepen"><a href="https://codepen.io/pbj/pen/oQZKRz/"></a></p>


<p>Big thanks to <a href="http://www.zeespencer.com/" target="_blank">Zee Spencer</a> for reviewing and editing this post before publishing.</p>