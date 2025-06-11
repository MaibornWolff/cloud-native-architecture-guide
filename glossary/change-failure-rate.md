---
title: "Change Failure Rate"
category: "glossary"
---
# Change Failure Rate

Change Failure Rate (CFR) is one of the four key metrics identified by the DevOps Research and Assessment (DORA) team to measure software delivery performance. It represents the percentage of changes to production that result in degraded service or require remediation such as hotfixes, rollbacks, or patch releases. This metric provides critical insight into the stability and reliability of an organization's software delivery process.

The formula for calculating Change Failure Rate is straightforward: divide the number of failed changes by the total number of changes, then multiply by 100 to get a percentage. For example, if a team deploys 20 changes to production in a month, and 5 of those changes result in incidents or require remediation, the Change Failure Rate would be 25%. According to DORA research, elite performing organizations maintain a Change Failure Rate between 0-15%, while low performers often experience rates of 46% or higher.

> "Change failure rate measures the percentage of deployments causing a failure in production. By 'failure,' we mean a deployment that either results in degraded service or subsequently requires remediation." - [Google Cloud Architecture Center](https://cloud.google.com/architecture/devops/devops-measurement#change_failure_rate)

## Factors Affecting Change Failure Rate

Multiple factors influence an organization's Change Failure Rate, spanning technical, process, and cultural dimensions. **Technical factors** include test coverage, code complexity, and architectural decisions. Inadequate test coverage often leads to undetected issues reaching production, while highly complex code with significant technical debt increases the risk of failures. The deployment architecture also plays a crucial role—monolithic applications typically experience higher failure rates than well-designed microservices due to their interconnected nature and broader blast radius.

**Process factors** significantly impact Change Failure Rate through the effectiveness of quality gates and deployment practices. Thorough code review processes can catch potential issues before they reach production, while comprehensive testing practices across unit, integration, and end-to-end tests reduce the likelihood of failures. The size and frequency of changes also matter—smaller, more frequent changes tend to have lower failure rates than large, infrequent releases because they're easier to test thoroughly and have more limited scope for introducing errors.

**Cultural factors** may be less visible but are equally important in determining Change Failure Rate. Organizations with a blame culture often experience higher failure rates as team members become reluctant to report or address issues openly. Conversely, teams with high psychological safety can discuss problems candidly and implement improvements. Similarly, clear service ownership ensures that specific teams take responsibility for reliability, while cross-functional collaboration between development and operations teams leads to more stable releases through shared understanding and goals.

## Good Practices

Implement automated testing at multiple levels (unit, integration, end-to-end) with high coverage to catch issues before they reach production and make testing a non-negotiable part of the development process.

Adopt progressive deployment strategies such as feature flags, canary releases, and blue-green deployments to limit the impact of changes and enable quick rollbacks when issues are detected.

Break large changes into smaller, more manageable increments that can be tested thoroughly and deployed independently, reducing the scope and complexity of each individual change.

Conduct blameless postmortems after failures to identify root causes and systemic issues without assigning individual blame, focusing instead on process improvements and learning opportunities.

Enhance monitoring and observability to quickly detect issues in production, including comprehensive logging, metrics collection, and alerting systems that provide early warning of potential problems.

## Further Reading

* [Accelerate: The Science of Lean Software and DevOps](https://itrevolution.com/book/accelerate/) - Definitive book on DORA metrics and their impact on organizational performance
* [DORA State of DevOps Reports](https://www.devops-research.com/research.html) - Annual research reports on DevOps practices and performance metrics
* [Google's Site Reliability Engineering Book](https://sre.google/sre-book/table-of-contents/) - Comprehensive guide to reliability practices that affect change failure rates
* [The Phoenix Project](https://itrevolution.com/book/the-phoenix-project/) - Novel illustrating DevOps principles and their impact on delivery performance
* [Continuous Delivery: Reliable Software Releases](https://www.pearson.com/en-us/subject-catalog/p/continuous-delivery-reliable-software-releases-through-build-test-and-deployment-automation/P200000009415) - Book on practices that reduce change failure rate through improved delivery processes
