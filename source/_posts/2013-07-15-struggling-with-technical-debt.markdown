---
layout: post
title: "Struggling with Technical Debt"
date: 2013-07-15 22:13
comments: true
categories: [personal, software]
---

Every company I've ever worked at has struggled with the concept of Technical
Debt. If you're not familiar with the term

> Technical debt (also known as design debt or code debt) is a neologistic
> metaphor referring to the eventual consequences of poor or evolving software
> architecture and software development within a codebase.

Source: [Wikipedia - Technical Debt](http://en.wikipedia.org/wiki/Technical_debt)

A "move fast and break things"-esque culture, can make it hard to take a step
back and make sure the frankenhack you've created even qualifies as an MVP. When
the pressure is on and product expected delivery yesterday, I think we all have
a tendency to shutout that little voice in our head telling us to do it the
Right Way (tm). But at some point crunch time will end, and you're left
maintaining something that's hardly passable as a product, much less a paramount
of engineering prowess.

### Process to the... rescue?

In my experience, processes like Scrum and XP serve to exacerbate rather than
alleviate the problem if not managed carefully. Here's how it usually goes:

1. Start working on a [poorly scoped/written/sized/etc] story
2. Discover something ugly that needs to be re-worked, but isn't in the scope of
   your current story
3. Write a fixit chore in your [project tracker](https://www.pivotaltracker.com/)
   with a pithy title and high priority label
4. Watch as that ticket is immediately prioritized under the "real" work by the
   product team

This pattern carries on ad infinitum until the aforementioned frankenhack
buckles under its own complexity. Usually at this point someone utters the word
"re-write", much to the horror of everyone else in the company. Yes, we're
pushing out code at a break-neck pace, but at what cost?  Would this level of
flippancy about our craft be tolerated in any other engineering profession?

### Dash of plot-thickening agent

Almost without fail, when the topic of technical debt comes up with product or
businessy people around, someone presents this golden insight

> Why don't you just fix it as you see it?

There are at least two obvious reasons why this is deeply misguided at best, and
positively destructive at worst. First, refactoring tends to be a recursive
process with no clear base case. You might innocently start by ripping out a
function or cleaning up the logic of some helper class, but then you have to
track down all the tests for that bit of code. Oh, and while you're at it, track
down all the clients of that code which are hopefully well-factored already
(unlikely) and tested in a way that doesn't depend directly on the
implementation of that thing you just rewrote (also unlikely). This process
continues recursively until that one class or function you were refactoring
turns into a multi-hundred line commit across tens of files.

The second problem is far more insidious at a process level. Ask yourself this
question: do the above refactorings _really_ fall under the scope of the current
story? If the answer is no, then your 1 point story can easily turn into a 3 or
5 pointer in no time. (I'm using sizing jargon here loosely; translate the
points to whatever unit of work your organization uses.) This high degree of
churn can be absolutely demoralizing to a team that's used to shipping on a
regular basis. The high level of busy work without forward progress can create
stress and burnout throughout the product and engineering teams.

### Lights flicker in the distance

Many of these problems seem to compound and intensify as the engineering team
grows. There are no silver bullets, and process alone isn't going to get you
very far (it might even drag you backwards along the path). This is a problem I
reckon most engineering organizations struggle with and it is our duty as
working professionals to come up with a viable long-term solution. 

For the record, I don't really know what that solution looks like, but here are
some strategies I've used as both a manager and developer over the years with
varying degrees of success:

* **Stop compromising so much!** It's your job to ship features, yes. It is also
  your job to give other stakeholders (product, bizdev, marketing, etc.) the
  appropriate feedback and transparency so they can properly scale their
  expectations. There is of course an implicit requirement here that those
  stakeholders actually care what you have to say. Without that, many
  organizations are doomed to failure before they have a chance at success.

* **Be noisy about debt.** Don't let those fixit stories sink into the backlog
  abyss. Product-focused processes like Scrum drive the development of
  user-facing features often at the cost of engineering discipline. Engineering
  should strive to push their priorities through with the same level of
  commitment and force as the other stakeholders.

* **Perfectionism != Debt-reducing.** In my younger days, I was absolutely
  obsessed with perfection. Not to say everything I wrote was perfect (far from
  it), just that I spent an exorbitant amount of time thinking about the Right
  Way (tm) to do something. In the end, especially when working in a group of
  more than 1 or 2 people, the outcome will be the same (or worse). You've spent
  so much time building a perfect house of cards, you can't remember exactly how
  it all fits together. This is a classic example of optimizing for the wrong
  thing.

* **Set time aside on the roadmap.** If all else fails, create "cleanup
  sprints".  These are usually 1 or 2 week sprints where the engineering team
  doesn't build any new features and instead focuses on rebuilding existing code
  to meet higher quality standards. These sprints need to be carefully managed
  as they can easily turn into partial rewrites (often generating even more
  spaghetti code).

Especially in the start-up world, I think the problem of Technical Debt can
easily reach crisis levels. In an environment when you're already strapped for
time and money, how can you possibly slow down to fix the things you've broken?
There isn't an easy solution, but we owe it to ourselves and our organizations
to start the discussion today.
