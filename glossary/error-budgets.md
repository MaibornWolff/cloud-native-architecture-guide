---
title: "Error Budgets"
category: "glossary"
---

# Error Budgets

Error budgets are a quantitative approach to service reliability that establishes an acceptable level of system unreliability. They represent the maximum amount of downtime, errors, or degraded service that a system can experience while still meeting its Service Level Objectives (SLOs). The core concept is simple: if a service is meeting its reliability targets with room to spare, teams have the freedom to take more risks and innovate faster. If the service is close to exhausting its error budget, teams should focus on reliability improvements rather than new features.

In the DevOps context, error budgets create a shared accountability model between development teams (who want to ship features quickly) and operations teams (who want to maintain system stability), helping to balance velocity and reliability. This approach transforms reliability from a subjective discussion into an objective, measurable framework that aligns with business goals. Error budgets are typically calculated as the inverse of the SLO target (Error Budget = 100% - SLO target). For example, if your SLO is 99.9% availability, your error budget is 0.1%, which translates to approximately 43.8 minutes of downtime per month.

> "Error budgets provide a common incentive that allows both product development and SRE to focus on finding the right balance between innovation and reliability." - [Google SRE Book](https://sre.google/sre-book/embracing-risk/)

## Implementation and Policy

Implementing error budgets requires several key components, including defined SLIs (Service Level Indicators) and SLOs, monitoring infrastructure to track reliability metrics, and cross-team alignment on how budgets will be used. Organizations typically start by categorizing services based on business impact, establishing appropriate SLOs for each service, and then calculating the corresponding error budgets. Many organizations adopt a tiered approach, with critical services having the highest reliability requirements and smallest error budgets, while non-critical services have larger error budgets to enable more experimentation.

A comprehensive error budget policy defines how budgets are calculated, measured, and reset (typically on a time-based cycle like monthly or quarterly). The policy also establishes clear actions that occur at different levels of budget consumption. For example, when 50% of the error budget is consumed, teams might review recent incidents and identify potential reliability risks. At 75%, additional deployment safeguards might be implemented. When 100% of the budget is exhausted, a feature freeze might be enacted until reliability improves and the budget is replenished. These policies create a structured approach to balancing innovation and reliability without requiring constant negotiation between teams.

Error budget policies also typically include exception processes for special circumstances like security vulnerabilities or legal requirements that might necessitate changes even when budgets are exhausted. The most effective policies are developed collaboratively across development, operations, and product teams to ensure buy-in and alignment with business objectives. Regular reviews of policy effectiveness help organizations refine their approach over time, adjusting SLOs and actions based on changing business needs and technical capabilities.

## Good Practices

Define clear, measurable SLIs that accurately reflect the user experience, focusing on metrics that matter to your customers rather than technical implementation details.

Implement automated, reliable monitoring systems to track error budget consumption in real-time, providing visibility to all stakeholders through dashboards and alerts.

Create a formal error budget policy document that clearly outlines the consequences of budget depletion, ensuring all teams understand and agree to the process before incidents occur.

Use error budgets as learning tools rather than punishment mechanisms, focusing on systemic improvements and blameless post-mortems when incidents consume the budget.

Balance reliability work with feature development based on error budget consumption, allowing teams to take calculated risks when budgets are healthy while focusing on stability when budgets are depleted.

## Further Reading

* [Google SRE Book - Chapter on Error Budgets](https://sre.google/sre-book/embracing-risk/) - The definitive explanation of error budgets from the team that pioneered the concept at Google

* [Implementing Service Level Objectives](https://www.oreilly.com/library/view/implementing-service-level/9781492076803/) by Alex Hidalgo - Comprehensive guide to implementing SLOs and error budgets in various organizational contexts

* [Site Reliability Engineering Workbook](https://sre.google/workbook/table-of-contents/) - Practical guidance on implementing SRE practices including error budgets

* [The Art of SLOs Workshop](https://github.com/google/the-art-of-slos) - Google's open-source workshop materials for implementing SLOs and error budgets

* [Seeking SRE: Conversations About Running Production Systems at Scale](https://www.oreilly.com/library/view/seeking-sre/9781491978856/) edited by David N. Blank-Edelman - Collection of essays from industry experts on SRE practices including error budgets
