---
title: "What is developer productivity and how to measure it?"
date: "2022-05-19"
tags: ["software development", "productivity"]
draft: false
summary: "Developer productivity, in general, refers to how productive a developer is during a specific period of time or based on any criteria. An organization would design objectives or metrics to track and set goals to attain or set a baseline of what is acceptable in order to be able to gauge developer productivity."
image: "/blog/static/images/blog/space-1.png"
layout: PostLayout
---


## How to define developer productivity?

Developer productivity, in general, refers to how productive a developer is during a specific time or based on any criteria. An organization would design objectives or metrics to track and set goals to attain or set a baseline of what is acceptable to be able to gauge developer productivity.

But evaluating developer productivity upon only specific metrics is hazardous. According to <a target="_blank" rel="noopener noreferrer nofollow" href="https://www.infoq.com/news/2021/03/space-developer-productivity/">Nicole Forsgren in an interview for InfoQ</a>, one of the researchers that created the SPACE framework (we'll talk about it more later on):

> One of the most common myths — and potentially most threatening to developer happiness — is the notion that productivity is all about developer activity, things like lines of code or number of commits. More activity can appear for various reasons: working longer hours may signal developers having to "brute-force" work to overcome bad systems or poor planning to meet a predefined release schedule.

Measuring developer outputs can be detrimental because there are not enough data points to understand if the unproductiveness was caused by the developer himself, or by his surroundings/company. So what are the best methods to measure developer productivity?

_If you prefer to go straight to the conclusion, you can find our engineering productivity cheatsheet inspired by the SPACE framework here!_

![space-framework](/static/images/blog/space-2.jpg)

## How to measure developer productivity?

Out there, there are two widespread methods to measure developer productivity: the SPACE and OKR frameworks.

### What is the SPACE framework?

For most developers, being in a state of hyper-productivity feels like being in a "flow". The SPACE framework tries to define several data points to quickly gauge developer productivity but also the surroundings of the developer. Is the organization structured in a way that enables productivity among the engineers? According to the <a target="_blank" rel="noopener noreferrer nofollow" href="https://queue.acm.org/detail.cfm?id=3454124">SPACE research paper</a>,

> developer productivity is necessary not just to improve engineering outcomes, but also to ensure the well-being and satisfaction of developers, as productivity and satisfaction are intricately connected.

SPACE was created, according to the authors, to capture various aspects of developer productivity and refute fallacies about it, such as the notion that productivity is measured by activity volume, tools, or individual performance.

They propose several distinct measures for each of them that apply at several levels, including individual, team or group, and system. SPACE, interestingly, does not recommend employing all the measurements at once, but rather a smaller collection of metrics that cover all three levels and represent different production dimensions.

So, what's SPACE again? Let's dive into each pillar.

#### Statisfaction and well-being among developers

Developer satisfaction refers to how satisfied they are with their work, team, tools, or culture; well-being refers to how happy and healthy they are, as well as how their work affects their health and happiness. Understanding and possibly even predicting productivity benefits from measuring satisfaction and well-being. 15 For example, because productivity and contentment are linked, it's feasible that satisfaction can operate as a leading indicator of productivity; a drop in satisfaction and engagement could foreshadow impending burnout and lower output.

Three main topics for satisfaction and well-being:

- Employee satisfaction. Are employees satisfied? Would they recommend their companies to others?
- Developer efficacy. Do employees have the resources and tools their need to complete any tasks?
- Burnout. Are they feeling exhausted by excessive workplace stress?

#### (Software developer) Performance

It's difficult to measure software developer performance since linking individual contributions to product outcomes isn't natural.

- It's possible that a developer who writes a lot of code isn't writing high-quality code.
- Customer value may not be delivered by high-quality code.
- Customers may not always respond positively to features that delight them.

Even though a developer's contribution can be linked to business outcomes, it is not always indicative of performance because the developer may have been allocated a less impacting assignment rather than having the freedom to choose more significant work. Furthermore, the software is frequently the total of several developers' contributions, making measuring the effectiveness of any given developer even more challenging.

Software is written by teams, not individuals, in most firms and organizations. As a result, performance is frequently measured in terms of outcomes rather than output. For example:

- Impact: Customer satisfaction, adoption and retention, feature usage, and cost reduction are all factors to consider.
- Quality: Reliability, the absence of bugs, and the overall health of the service.

#### Activity

If measured appropriately, developer activity can provide useful but restricted information about developer productivity, engineering systems, and team efficiency. Developers' activity is difficult to assess or quantify due to the varied and different activities they do. In truth, measuring and quantifying all aspects of developer activity across engineering systems and environments is nearly impossible.

A well-designed engineering system, on the other hand, will aid in the capture of activity metrics throughout the software development life cycle and the quantification of developer activity at scale. The following are some of the developer activities that are generally easy to measure and quantify:

- Design and coding: The number of design papers and specs, work items, pull requests, commits, and code reviews, as well as their volume or count.
- Operational activity: Count or distribute the number of incidents/issues based on severity, on-call involvement, and incident mitigation.
- Continuous integration and deployment: Build, test, deployment/release, and infrastructure utilization are all counted.

Because of their acknowledged limitations, these metrics can be used as a starting point for measuring some tractable developer tasks, but they should never be used in isolation to make choices regarding individual or team productivity. They should be adapted based on corporate demands and development environments, and they serve as starting points.

#### Communication and collaboration

High transparency and awareness of team member activities and task priorities are essential for effective teams that successfully contribute to and integrate each other's work. Furthermore, the availability and discoverability of documentation required for efficient alignment and integration of work are influenced by how information flows within and among teams. Teams with a diverse and inclusive membership perform better. More productive teams focus on the relevant challenges, are more likely to succeed in generating new ideas, and will select the best solution from a variety of options.

However, because of factors that are difficult to measure, such as invisible labor and articulation work for coordinating and organizing team tasks, understanding and quantifying team productivity and team member expectations are complicated. As an example of measures that can be used as proxies to quantify communication, collaboration, and coordination, consider the following:

- The speed with which work is assimilated.
- Network measurements that reveal who and how people are connected.
- Discoverability of documentation and expertise.
- Quality of reviews of work contributed by team members.
- Time spent onboarding new members and their prior experience.

#### Efficiency and flow

Finally, efficiency and flow refer to the ability to finish or progress work with minimal interruptions or delays, whether individually or as part of a system. This can include how well operations are coordinated inside and across teams, as well as if progress is being accomplished consistently.

Setting boundaries to get and stay productive—for example, shutting off time for a concentrated period—is critical for individual efficiency (flow). Individual productivity is frequently assessed in terms of uninterrupted concentrate time or time spent using value-creating apps (e.g., the time a developer spends in the integrated development environment is likely to be considered "productive" time).

The DORA (DevOps Research and Assessment) framework introduced some metrics to track team flow, such as deployment frequency, which measures how frequently an organization successfully releases to production, and lead time for changes, which measures how long it takes a commit to reach production. 

The following are some examples of efficiency and flow metrics:

- The total number of handoffs in a process; the total number of handoffs between teams in a procedure.
- Interruptions: the number, time, and spacing of interruptions, as well as their impact on development work and flow.
- The perceived capacity to stay in the zone and finish tasks.
- Time is measured using a system that includes total time, value-added time, and wait time.


### OKR to measure developer productivity

#### How to implement OKR for developers?

Measuring personal OKR is a great way to identify differences among developers. If one deploys twice as many commits as another one, you can start asking questions such as: is it caused by these developers themselves or by our management?

Each organization can set a wide range of metrics to follow every week, such as:

- Number of commits.
- Average commit size.
- Frequency of code reviews.
- Number of code reviews.
- Time to review.
- and so on...

But according to [Metabob](https://metabob.com/blog-articles/how-to-measure-developer-productivity.html) and as we previously said, following personal metrics will always show only a small fragment of the true work of a developer. A better way to manage OKR is to set the team or company-wide and follow frameworks such as the DORA frameworks. Accelerate is the result of years of research upon more than 23 000 different organizations.



#### OKR may have a negative influence

There are two main issues with an OKR implementation among engineers are:

##### OKR force engineers to focus on new tasks

If you do not allocate time for your engineering team to remediate technical debt, it won't ever stop. After the implementation of OKR, you'll need to create dedicated time for technical debt remediation.

##### OKR could be a source of stress

As we know, only considering engineering output is not a good solution. Sometimes, some problems need more time to be fixed, hence a developer won't be able to comply with his weekly OKR baseline. Instead of promoting creativity, a developer might think that they should repetitively push commits.

So now that you have different frameworks to measure developer productivity, start implementing them with feedback from your engineering teams. You will see along the way what works best for your team, there is no unique solution!
