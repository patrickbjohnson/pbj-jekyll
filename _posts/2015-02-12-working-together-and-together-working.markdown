---
layout: post
title:  "Working Together and Together Working"
date:   2015-01-31
img: "http://media1.giphy.com/media/MQQwcpjOLD64U/giphy.gif"
permalink: /writing/working-together.html
summary: I finally got around to making a new site!
---
I [read an article on Smashing Magazine](https://www.smashingmagazine.com/2016/08/developers-own-code-should-designers-own-experience/), which, on first read, infuriated me as a developer. After reading a second time it was clear to see the author, a user-experience designer, was also frustrated but saw the light at the end of the tunnel. And the light, in this case, was teamwork. The topic in question: the working relationship between designers and developers. 

Both sides of the table have different ideas on what should be standard and what the *other* side should do and expect. Funny thing: both sides want the other side to do more than they are currently doing. 

Before this happens, there is one idea to remind us of why this relationship between designers and developers is the most important piece of a successful work product:


> Design without development is a picture and development without design is a text file.

It’s worth discussing some of the points brought up in the Smashing Magazine article from a developer's perspective. Not to bash the author's intention or thoughts, but to bring light from the other side. 

#### “... if [developers] claim that the particular target experience isn’t ‘technically possible’, which is often shorthand for ‘really difficult’, ‘I can’t be bothered doing it that way’ or ‘I think there’s a better way of doing it so am going to pull the dev card.’”

There is no dev-card. There is no “I can’t be bothered doing it that way” and there is no “I think there’s a better way of doing it so am going to pull the dev card”. There are, however, differing ideas or expectations. There are communication issues and misalignments. There are ideas lost due to lack of context, different priorities for different teams and a constantly changing project scope and feature sets. 

When we think of teams we usually think of the design team, product team, development team, sales team, etc. We don’t consider teams made up of multidisciplinary groups. Teams aren’t created the “MadMen” way - pairing an art director and copywriter together to create the work. And because our teams are grouped differently they have different goals, structure, and reasons for doing things. 

A few scenarios to illustrate this idea.

<div class="scenario-group">
  <h4 class="scenario-group__title">Scenario One</h4>
  <p><strong>Design Perspective:</strong> A designer passes off design files to a developer for reference while building a responsive site. Once the developer is at a good stopping point she shares the work with the designer. The designer immediately notices a bunch of “bugs” with spacing and type.</p>

  <p><strong>Development Perspective:</strong> The design files were handed over in two formats: mobile and desktop. The mobile comps at 375px and desktop at 1200px. The design team chose 375px and 1200px based on client reviews and approvals. However, the developer must consider all devices and starts at 320px. Due to the 55px different the developer went ahead and adjusted some spacing and font-sizes to ensure it fit accordingly for the real-world user.</p>

  <p><strong>Solution:</strong> Prior to starting any work, the team comes together to determine deliverables. Deliverables can vary between projects but should include sizes of designed screens, breakpoints and what should happen in between them. The respective expertises come together to create the best experience for the client and project.</p>
</div>

<div class="scenario-group">
  <h4 class="scenario-group__title">Scenario Two</h4> 
  <p><strong>Design Perspective:</strong> A designer walks a developer through a feature and all is going great. A few weeks later, due to adjusted business requirements, the design team is tasked with updating the original feature to accommodate a few more things.</p>

  <p><strong>Development Perspective:</strong> The developer says “this changes a lot”. Their response to the update in this feature is such because the unforeseen implications the changes carry are larger than the team considered. Feature X wasn’t meant to hold a video in the background or Feature Y wasn’t intended to upload images. So the developer is required to rewrite the feature or write a new one from scratch.</p>

  <p><strong>Solution:</strong> Include frequent stand-up meeting to discuss status of the project. Set the standard to include all team appropriate team members when discussing changes and how they may impact the overall work product.</p>
</div>

<div class="scenario-group">
  <h4 class="scenario-group__title">Scenario Three</h4>
  <p><strong>Design Perspective:</strong> As the project moves from the “design phase” to “dev phase” (typically happens in a waterfall environment versus an agile). The design team hands over some awesome prototypes through InVision and a few video files to help all parties understand the feeling and visualize the interactions.</p>

  <p><strong>Development Perspective:</strong> While these assets are great for visual references, it does not help the developer recreate the animations and transitions in production code. There are no references to <a href="http://cubic-bezier.com">speed, timing, or easing</a> and the developer must eyeball all of it in hopes they get it right. <a href="http://alistapart.com/article/communicating-animation">Something that could’ve taken two hours with documentation ended up taking six</a>.</p>
   

  <p><strong>Solution:</strong> Similar to Scenario one, the overall team sets standards on what is to be expected for the project. In the case of prototypes and animations, the team sets standards together on what should be expected in handoff. It could be video, story-boards or even comparable sites to review similar animations in the wild.</p>
</div>

<div class="scenario-group">
  <h4 class="scenario-group__title">Scenario Four</h4>
  <p><strong>Design Perspective:</strong> The design team sets up a hand-off meeting with the development team to review the latest round of designs for Product X before development starts. Through this meeting the design team reviews concepts and prototypes, and explains expected functionality and features. Some items are mandatory and some are nice-to-haves.</p>

  <p><strong>Development Perspective:</strong> The features presented are met with questions and concerns by the development team. This review meeting is the first time they’ve seen these designs. They are worried the timeline isn’t adequate to build and some features aren’t even possible due to legacy code and infrastructure. But since it's already been “sold to the client” the development team is left find some way to pull it off.</p>
  
  <p><strong>Solution:</strong> Set the standard up front to ensure appropriate (and necessary) team members have seen (and signed off) on the work being presented to the client for approval. This ensures appropriate (and necessary) team members are on board with the proposed work. It’s even more helpful to inform all team members who the designated team lead is ahead of time.</p>
</div>

<div class="scenario-disclaimer">
  *These are just a few for scenarios from my work experience, colleagues and friends. 
</div>


Sometimes priorities are different between teams. Even more so, priorities, timelines and deadlines can shift, slide, change and get reworked all the time.

> The best thing we can do as teams is this: bring everyone together from day one. 

**Additional Suggestions**:

- Encourage smaller huddles - informal, quick meetings, generally done when the development or design process is about to begin as a moment for everyone to ensure they are on the same page.
- Include everyone in all meetings invites (setting appropriate folks as mandatory and others optional).
- Have weekly (or every couple days) check-ins with all parties.
- Setup project process, expectations, and internal deliverables up front before the project begins. 


#### “... it often feels as though there’s an asymmetric level of respect between disciplines due to a belief that design is easy and therefore something everybody can have an opinion on, while development is hard and only for the specially initiated.”

Design isn’t easy. Development isn’t easy. If they were easy, both professions wouldn’t be highly sought after and yield six-figure salaries in some areas of the US. If design were easy, the US Government wouldn’t need to create the [US Digital Service](https://www.usds.gov/) to coordinate those exact efforts. 

> Design and development aren’t easy, but they become easier when we work together.

We aren’t the only ones in the world who have to work together. Consider other professions building things, or taking care of humans. 

Building a house involves:

- Architect
- General Contractor
- Electrician
- Plumber
- Roofer
- Paver

Performing a surgical procedure involves: 

- Family Doctor (or specialist) for pre-surgery physical
- Anesthesiologist
- Nurses
- Surgeon
- Surgical Assistants
- Therapist for post surgery recovery (vocal therapist, physical therapist, etc.)

If anyone in either two examples were to mess up, half-ass or just not show up, we’d end up in terrible positions, losing a lot of money, and potentially in danger. 


#### “So while designers are encouraged (sometimes expected) to involve everybody in the design process, they often aren’t afforded the same luxury.”
Both design and development teams should be held accountable to involve team members in the project. If this doesn’t happen, it should be called out and corrected. However, it can be difficult to include everyone in the development process. It can be a barrier to show non-dev folks a technical issues or resolution if it isn't visual, which can result in less interest in a topic (EX: talking about splicing array indicies to a sales person). 

The best way to bring all parties into the development process is to create the lowest barrier to review the design in the intended environment. 

Tools like [Pattern Lab](http://patternlab.io/) and [CodePen](http://codepen.io/) help bridge the gap between a design file and the finished product. They allow non-technical team members to interact with the design quickly and discuss unresolved ideas or “scratchpad” prototypes. It gets everyone on the same page earlier and faster. 

#### “...I do know enough to tell when the developers are fudging things and it’s always fun to come back to them with a working prototype of something they said was impossible or take months to implement — but I digress.”

Prototypes come in many forms. Some prototypes are visual and meant as referential while others are coded. Both are great, they help resolve issues when something changes, moves and modifies when engaged. Few things to consider when providing prototypes. 

- A visual prototype is nice to *see* how it should work but can take a really long time to recreate identically. And often times falls short. A visual prototype should be delivered with [additional documentation](http://alistapart.com/article/communicating-animation).
- A coded prototype is a great way to meet a developer halfway. This allows an even lower barrier to ensure the prototype gets implemented as intended. Ensure the code meets the team's code standards and if it doesn’t work with a developer to bring them up it up to par. In this case, it’s both parties job to make sure it's production ready.

As mentioned earlier, it's best to set up expectations on deliverables to-and-from both parties in the beginning. This way, when a prototype is handed over, both parties know what to expect and how it should be integrated in the the project. 

#### “Design team owns the design (experience), development team owns the development.”
If design owns the design, and development owns the code, who owns the finished product? This question comes to mind often when sitting with a designer combing over a site to polish off odds and ends. The two have differing opinions on how something should look or feel and then it gets awkward. The tone turns from “we are building this” to “I designed it, therefore it's my decision”.

The ownership mentality becomes the enemy of collaboration when trying to work together.

> The discipline owns the medium, the team owns the result.
 
And a few (suggested) ideas to work by:

- Design and development own the design files. Both move through them, expect them to be clear, clean and navigable. If a design change comes up, the designer makes the appropriate changes to the design files.
- Design and development both own the coded results. Both own the displayed results of the code written. If the results are wrong or change, the developer updates the code to resolve the issue. 
- Design and development both own the language. Often times common terms come to surface and help discuss aspects of the work. If design and development communicate the same ideas differently it creates challenges.
- Teams own the outcome, individual's own tools. 

There are no perfect, absolutely, indisputable answers to any of these topics or questions at hand. And some teams may find some techniques work better than others. The primary idea to ensure a better working experience is setting the table for communication and expectations from everyone. The sooner we know the less surprises come up. The more consistently we communicate the more effectively we help resolve issues and more forward. The better we work together as a team, the better we get as individuals.

Thanks to [Reid](https://twitter.com/reidhitt), [Pavan](https://twitter.com/ptrikutam?lang=en), [Kate](https://twitter.com/CMYKaytoe) and [Jack](https://twitter.com/jackmakesthings) for their review, feedback and editing.
