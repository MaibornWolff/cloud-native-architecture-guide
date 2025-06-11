---
title: "Value Stream Mapping"
category: "glossary"
---

# Value Stream Mapping

Value Stream Mapping (VSM) is a lean management technique used to analyze, visualize, and optimize the flow of materials, information, and activities required to deliver a product or service to customers. Originally developed by Toyota as part of the Toyota Production System, this visual tool documents all the steps, both value-adding and non-value-adding, in a process from request to delivery. VSM reveals the current state of a process by capturing metrics such as cycle time, lead time, and wait time at each step, providing a comprehensive view of how value flows through an organization. The primary goal of VSM is to identify and eliminate waste (activities that consume resources without adding value), reduce lead times, and improve process efficiency.

In the DevOps context, Value Stream Mapping helps teams visualize the entire software delivery lifecycle from idea to production, revealing delays, handoffs, and inefficiencies that impede flow and value delivery. Traditional software development often suffers from significant waste in the form of waiting, handoffs between specialized teams, rework due to quality issues, and partially completed work. By mapping the value stream, organizations can identify bottlenecks such as manual approvals, excessive wait times, large batch sizes, and unnecessary process steps that slow down delivery. VSM provides a shared understanding of the current state and helps identify concrete steps toward an improved future state with faster flow, higher quality, and better alignment with business objectives. This makes VSM a powerful tool for organizations embarking on a DevOps transformation, as it highlights organizational and process impediments that must be addressed alongside technical practices.

> "Value stream mapping is a lean-management method for analyzing the current state and designing a future state for the series of events that take a product or service from the beginning of the specific process until it reaches the customer." - [Wikipedia](https://en.wikipedia.org/wiki/Value-stream_mapping)

## Core Concepts

### The Value Stream

A value stream encompasses all activities—both value-adding and non-value-adding—required to bring a product or service from concept to customer. In software development, this typically includes:

* Initial concept and requirements gathering
* Design and planning
* Development
* Testing and quality assurance
* Deployment and release
* Operations and monitoring
* Feedback and improvement

### Value-Adding vs. Non-Value-Adding Activities

Activities in a value stream can be categorized as:

* **Value-Adding (VA)**: Activities that directly contribute to what customers value and are willing to pay for
* **Necessary Non-Value-Adding (NNVA)**: Activities that don't directly add value but are currently necessary (e.g., compliance checks)
* **Non-Value-Adding (NVA)**: Pure waste that should be eliminated (e.g., unnecessary handoffs, waiting)

### Lead Time vs. Process Time

* **Lead Time**: The total elapsed time from when a request is made until it is fulfilled
* **Process Time**: The time spent actually working on the request (value-adding time)
* **Efficiency**: Process Time / Lead Time (typically expressed as a percentage)

In many software organizations, efficiency is surprisingly low—often less than 5%, meaning 95% of the time is spent waiting or in other non-value-adding activities.

## Value Stream Mapping Process

### 1. Preparation

* **Define Scope**: Determine the start and end points of the value stream
* **Identify Stakeholders**: Include representatives from all parts of the value stream
* **Set Objectives**: Clarify what you hope to achieve through the mapping exercise
* **Gather Materials**: Prepare visual tools (whiteboard, sticky notes, etc.)

### 2. Current State Mapping

#### Map the Process Flow
* Document each step in the process from left to right
* Include all teams, tools, and systems involved
* Show information flow as well as work flow

#### Collect Data for Each Step
* Process time (actual working time)
* Lead time (elapsed calendar time)
* Wait time between steps
* Batch sizes
* Quality metrics (defect rates, rework)
* Handoffs between teams

#### Identify Pain Points
* Bottlenecks where work accumulates
* Long wait times
* Frequent rework loops
* Manual processes that could be automated
* Handoffs that cause delays or information loss

### 3. Analysis

* Calculate the total lead time and process time
* Determine process efficiency (process time / lead time)
* Identify the biggest sources of delay and waste
* Analyze root causes of bottlenecks and constraints
* Quantify the impact of delays on business outcomes

### 4. Future State Mapping

* Design an improved process that addresses identified issues
* Focus on reducing handoffs, wait times, and batch sizes
* Identify automation opportunities
* Establish pull systems where appropriate
* Set target metrics for the improved process

### 5. Implementation Planning

* Prioritize improvement initiatives
* Create action plans with clear ownership
* Establish timeline and milestones
* Define how progress will be measured
* Plan for regular reassessment

## Value Stream Mapping in DevOps

### DevOps-Specific Considerations

* **Invisible Work**: Much of software development work is knowledge work that's not easily observable
* **Variability**: Software tasks have high variability in size and complexity
* **Multiple Value Streams**: Organizations often have multiple overlapping value streams
* **Toolchain Integration**: The flow through various tools and systems is critical
* **Feedback Loops**: Incorporate feedback mechanisms at various stages

### Common DevOps Value Stream Steps

1. **Ideation**: Feature requests, user stories, requirements
2. **Planning**: Prioritization, estimation, sprint planning
3. **Development**: Coding, unit testing, code review
4. **Integration**: Merging, integration testing
5. **Testing**: Automated testing, manual testing, security testing
6. **Deployment**: Release preparation, deployment to environments
7. **Operations**: Monitoring, incident management, support
8. **Feedback**: User feedback, metrics analysis, improvement

### Common Metrics to Collect

* **Cycle Time**: Time from work start to completion
* **Lead Time**: Time from request to delivery
* **Wait Time**: Time spent waiting between active work
* **Batch Size**: Number of stories, features, or lines of code in a release
* **WIP (Work in Progress)**: Number of items being worked on simultaneously
* **Deployment Frequency**: How often code is deployed to production
* **Change Failure Rate**: Percentage of changes that result in incidents
* **MTTR (Mean Time to Recovery)**: Average time to recover from failures

## Value Stream Mapping Techniques for DevOps

### Traditional VSM Adaptations

Traditional manufacturing VSM uses specific symbols and notations. For DevOps, these are often simplified to:

* **Process Boxes**: Represent activities or steps
* **Inventory Triangles**: Represent queues or backlogs
* **Arrows**: Show flow of information or work
* **Data Boxes**: Contain metrics for each step
* **Timeline**: Shows process time and wait time

### Digital Tools for VSM

While physical mapping with sticky notes is valuable for team engagement, digital tools offer advantages for complex or distributed teams:

* **Flowchart Software**: Lucidchart, Draw.io, Visio
* **Specialized VSM Tools**: Flomotion, Plutora, ConnectALL
* **Collaboration Platforms**: Miro, Mural, JIRA with plugins
* **Process Mining Tools**: Celonis, UiPath Process Mining

### Lightweight Approaches

For teams new to VSM or with limited time:

* **Value Stream Sketch**: Quick, high-level mapping in a single session
* **Walking the Process**: Physically follow a request through the system
* **Staple Yourself to a Story**: Track a single user story through the entire process
* **Metrics-First VSM**: Start with data collection, then visualize

## Common Patterns and Anti-Patterns

### Common Waste Patterns in Software Delivery

#### 1. Handoff Waste
* Multiple handoffs between specialized teams
* Knowledge loss during transfers
* Waiting for approvals or reviews

#### 2. Batch Processing Waste
* Large, infrequent releases
* Accumulating changes before testing
* Big bang integrations

#### 3. Partially Done Work Waste
* Incomplete features waiting for completion
* Code not integrated or deployed
* Untested or undocumented features

#### 4. Extra Processes Waste
* Excessive documentation
* Unnecessary approvals
* Redundant testing

#### 5. Task Switching Waste
* Developers working on multiple projects
* Frequent interruptions
* Context switching between tasks

### Anti-Patterns in VSM Implementation

* **Analysis Paralysis**: Spending too much time mapping without taking action
* **Tool Obsession**: Focusing on perfect diagrams rather than insights
* **Excluding Key Stakeholders**: Not involving all parts of the value stream
* **Ignoring Cultural Aspects**: Focusing only on process while ignoring people and culture
* **One-and-Done Approach**: Treating VSM as a one-time exercise rather than ongoing improvement

## Implementing Improvements

### Common Improvement Strategies

#### Eliminate Waste
* Remove unnecessary approvals or handoffs
* Eliminate duplicate work or redundant testing
* Reduce documentation to what's actually needed

#### Reduce Batch Sizes
* Implement smaller, more frequent releases
* Break large features into smaller increments
* Limit work in progress (WIP)

#### Establish Flow
* Create cross-functional teams to reduce handoffs
* Implement continuous integration and delivery
* Automate manual processes

#### Implement Pull Systems
* Use Kanban to visualize and manage flow
* Establish WIP limits
* Create clear "definition of ready" criteria

#### Continuous Improvement
* Regular retrospectives focused on value stream
* Metrics-driven improvement goals
* Experimentation with process changes

### Measuring Success

* **Lead Time Reduction**: Decreased time from request to delivery
* **Process Efficiency Improvement**: Higher ratio of value-adding time
* **Deployment Frequency Increase**: More frequent, smaller deployments
* **Quality Improvement**: Reduced defects and rework
* **Team Satisfaction**: Improved developer experience and reduced frustration

## Case Studies

### Financial Services Company

* **Initial State**: 6-month release cycles with 3 weeks of stabilization
* **Key Issues**: Siloed teams, manual testing, heavyweight change management
* **Improvements**: Cross-functional teams, automated testing, streamlined approvals
* **Results**: Reduced lead time from 6 months to 2 weeks, improved quality

### E-commerce Retailer

* **Initial State**: Bi-weekly releases with frequent rollbacks
* **Key Issues**: Large batch sizes, insufficient testing, deployment bottlenecks
* **Improvements**: Feature flags, CI/CD pipeline, automated testing
* **Results**: Daily deployments, 80% reduction in production incidents

### Healthcare Provider

* **Initial State**: Quarterly releases with extensive manual validation
* **Key Issues**: Regulatory compliance overhead, manual processes, specialized knowledge silos
* **Improvements**: Automated compliance checks, cross-training, documentation improvements
* **Results**: Monthly releases while maintaining compliance, improved knowledge sharing

## Value Stream Mapping in Different Contexts

### Enterprise vs. Startup

* **Enterprises**: Focus on reducing organizational handoffs and approval processes
* **Startups**: Focus on establishing repeatable processes and reducing technical debt
* **Both**: Benefit from visualizing the end-to-end flow and identifying bottlenecks

### Regulated Industries

* Additional compliance steps must be included
* Focus on automating compliance checks
* Balance between compliance requirements and flow
* Document risk mitigation strategies

### Product vs. Project Organizations

* **Product Teams**: Ongoing value streams with continuous improvement
* **Project Teams**: Temporary value streams with defined endpoints
* **Hybrid Models**: Mapping interactions between project and product teams

## Advanced Value Stream Concepts

### Value Stream Networks

Modern organizations often have complex networks of interconnected value streams:

* **Platform Value Streams**: Delivering capabilities used by other value streams
* **Product Value Streams**: Delivering end-user value
* **Support Value Streams**: Enabling other value streams to function

### Value Stream Architecture

The concept of designing systems around value streams rather than traditional architectural boundaries:

* Aligning system boundaries with value delivery
* Creating independent, deployable components
* Reducing cross-team dependencies
* Enabling autonomous teams

### Value Stream Management (VSM)

An emerging discipline that combines:

* Value stream mapping and analysis
* Flow metrics and visualization
* DevOps toolchain integration
* Continuous improvement frameworks
* Business value alignment

## Tools and Resources

### Books and Publications

* **Value Stream Mapping** by Karen Martin and Mike Osterling
* **DevOps Handbook** by Gene Kim, Jez Humble, Patrick Debois, and John Willis
* **Making Work Visible** by Dominica DeGrandis
* **Project to Product** by Mik Kersten

### Training and Certification

* **Value Stream Management Foundation** certification
* **Lean IT Foundation** certification
* **DevOps Institute Value Stream Management** training
* **Lean Kanban University** courses

### Communities and Events

* **DevOps Enterprise Summit**
* **Value Stream Management Consortium**
* **Lean IT Association**
* **DevOps Institute**

## Further Resources

* [Value Stream Mapping for Software Delivery](https://leankit.com/learn/kanban/value-stream-mapping/)
* [The Flow Framework](https://flowframework.org/)
* [Value Stream Management Consortium](https://www.vsmconsortium.org/)
* [DevOps Institute Value Stream Management Resources](https://www.devopsinstitute.com/value-stream-management/)
