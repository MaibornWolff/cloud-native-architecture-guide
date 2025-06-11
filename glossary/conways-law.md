---
title: "Conway's Law"
category: "glossary"
---

# Conway's Law

Conway's Law is an observation that organizations design systems that mirror their own communication structure. Named after computer programmer Melvin Conway who introduced the concept in 1967, this principle states that the architecture of a system will inevitably reflect the social boundaries of the organization that created it. The interfaces between software components tend to mirror the social and communication boundaries between the teams responsible for those components, resulting in a direct relationship between organizational design and system architecture.

In DevOps environments, Conway's Law has profound implications for how teams are structured and how systems are designed. Organizations seeking to implement microservices architectures, for example, often find they must first reorganize into small, cross-functional teams to be successful. Similarly, companies attempting to move from monolithic to distributed systems may struggle if their organizational structure remains siloed and hierarchical. Recognizing and working with Conway's Law, rather than against it, has become a fundamental strategy in modern software development and organizational design.

> "Any organization that designs a system (defined broadly) will produce a design whose structure is a copy of the organization's communication structure." - [Melvin Conway](http://www.melconway.com/Home/Committees_Paper.html)

## The Inverse Conway Maneuver

The **Inverse Conway Maneuver** is a strategic approach that leverages Conway's Law as a tool for driving architectural change through organizational restructuring. Rather than allowing the existing organizational structure to dictate system architecture, this approach deliberately restructures teams to match the desired target architecture. By aligning team boundaries with the desired component boundaries, organizations can use the natural effects of Conway's Law to drive architectural evolution in the intended direction.

Implementing the Inverse Conway Maneuver typically begins with identifying the target architecture based on business goals and technical requirements. Once this architecture is defined, the organization is restructured to mirror it, with teams aligned to specific components or services. Communication patterns between teams are then established to reflect the desired interaction patterns between components. Over time, as teams work within these new boundaries, the system architecture naturally evolves to match the organizational structure, often with less resistance than would be encountered through purely technical mandates.

The effectiveness of this approach has been validated in numerous digital transformation efforts, particularly in organizations moving from monolithic to microservices architectures. Companies like Amazon, Netflix, and Spotify have all employed variations of this strategy, reorganizing into small, autonomous teams that own specific services or products. The resulting architectures tend to be more modular, loosely coupled, and independently deployable, reflecting the autonomous nature of the teams that built them.

## Good Practices

Structure teams around business capabilities rather than technical functions to create system boundaries that align with business domains and reduce cross-team dependencies.

Visualize both organizational structure and system architecture to identify misalignments and potential areas where Conway's Law may be creating unintended architectural constraints.

Implement clear API contracts and team interaction models that define how teams (and consequently their systems) should communicate and integrate with each other.

Use the Inverse Conway Maneuver proactively when planning significant architectural changes, restructuring teams to match the target architecture rather than expecting architecture to change while organizational structure remains static.

Foster a culture of collaboration and transparency across team boundaries to prevent the formation of isolated "information silos" that can lead to duplicated functionality and integration challenges.

## Further Reading

* [Team Topologies](https://teamtopologies.com/) by Matthew Skelton and Manuel Pais - Comprehensive guide to organizing business and technology teams for fast flow

* [Building Microservices](https://www.oreilly.com/library/view/building-microservices-2nd/9781492034018/) by Sam Newman - Explores the relationship between team structures and microservices architecture

* [Accelerate](https://itrevolution.com/book/accelerate/) by Nicole Forsgren, Jez Humble, and Gene Kim - Research-based book that discusses Conway's Law in high-performing organizations

* [How Do Committees Invent?](http://www.melconway.com/Home/Committees_Paper.html) by Melvin Conway - The original 1968 paper that introduced Conway's Law

* [The DevOps Handbook](https://itrevolution.com/book/the-devops-handbook/) by Gene Kim, Jez Humble, Patrick Debois, and John Willis - Explores organizational design principles for effective DevOps implementation
