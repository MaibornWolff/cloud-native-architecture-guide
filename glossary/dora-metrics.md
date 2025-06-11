---
title: "DORA Metrics"
category: "glossary"
---

# DORA Metrics

DORA Metrics are a set of four key measurements identified by the DevOps Research and Assessment (DORA) team through rigorous research across thousands of organizations. These metrics have been proven to correlate with software delivery performance and organizational success, providing a data-driven framework for measuring and improving DevOps capabilities. The four metrics—Deployment Frequency, Lead Time for Changes, Time to Restore Service, and Change Failure Rate—balance both speed and stability dimensions, demonstrating that high-performing teams excel at both simultaneously rather than trading one for the other.

In the DevOps context, these metrics serve as objective indicators of an organization's software delivery performance and help teams identify areas for improvement. Deployment Frequency measures how often code is deployed to production, while Lead Time for Changes captures the time from code commit to production deployment. Time to Restore Service (also called Mean Time to Recovery or MTTR) measures how quickly service can be restored after an incident, and Change Failure Rate represents the percentage of changes that result in degraded service or require remediation. Together, these metrics provide a holistic view of delivery performance that transcends specific technologies, methodologies, or industry contexts.

> "Our research shows that none of these measures is important in isolation, but that they must be balanced against each other. For example, it doesn't matter if you can deploy quickly if the changes you're deploying are breaking the system." - [DORA State of DevOps Report](https://cloud.google.com/devops/state-of-devops/)

## Performance Benchmarks and Implementation

The DORA research categorizes organizations into four performance levels—Elite, High, Medium, and Low—based on their metrics performance. Elite performers deploy multiple times per day with lead times of less than one hour, restore service in less than one hour, and maintain a change failure rate below 15%. This benchmarking allows organizations to assess their current state and set improvement targets based on industry standards rather than arbitrary goals. The performance tiers demonstrate that there is no fundamental tradeoff between speed and stability; in fact, the research shows that elite performers excel at both dimensions simultaneously.

Implementing DORA metrics requires both technical and cultural considerations. From a technical perspective, organizations need systems to collect and analyze the data, which often involves integrating with CI/CD pipelines, version control systems, and incident management tools. Automated collection provides more accurate and timely data than manual processes, though many organizations start with manual collection as they build their measurement capabilities. Common implementation challenges include ensuring data accuracy, integrating disparate tools, establishing consistent definitions across teams, and avoiding behaviors that improve metrics without improving outcomes.

The cultural aspects of implementation are equally important. DORA metrics should be used for learning and improvement rather than punishment or individual performance evaluation. Teams should focus on trends rather than absolute values, especially when first establishing their measurement practices. Creating visibility through dashboards and regular reviews helps teams understand their performance and identify improvement opportunities. Most importantly, organizations should recognize that the metrics are means to an end—improving software delivery performance to better serve customers and achieve business outcomes—rather than ends in themselves.

## Good Practices

Start with establishing clear definitions for each metric that are consistently applied across teams, ensuring everyone understands what constitutes a deployment, a change, a failure, and service restoration in your specific context.

Implement automated data collection wherever possible by integrating with your existing toolchain, including CI/CD pipelines, version control systems, and incident management platforms, to ensure accuracy and reduce manual effort.

Focus on trends rather than absolute values, especially when beginning your measurement journey, as improvement over time is more important than comparing to industry benchmarks initially.

Use metrics as learning tools rather than performance evaluations, creating a culture where teams feel safe discussing challenges and experimenting with improvements without fear of punishment for not meeting targets.

Balance all four metrics rather than optimizing for just one or two, recognizing that true high performance requires excellence in both speed and stability dimensions.

## Further Reading

* [Accelerate: The Science of Lean Software and DevOps](https://itrevolution.com/book/accelerate/) by Nicole Forsgren, Jez Humble, and Gene Kim - The definitive book on DORA research that established the four key metrics and their correlation with organizational performance

* [Google's DevOps Research and Assessment (DORA)](https://www.devops-research.com/research.html) - The official site for ongoing DORA research, including annual State of DevOps reports that update findings and benchmarks

* [The DevOps Handbook](https://itrevolution.com/book/the-devops-handbook/) by Gene Kim, Jez Humble, Patrick Debois, and John Willis - Comprehensive guide to DevOps practices that enable improvement in DORA metrics

* [Four Keys Project](https://github.com/GoogleCloudPlatform/fourkeys) - Google's open-source project for measuring DORA metrics, including reference implementations for data collection and visualization

* [DORA's DevOps Quick Check](https://www.devops-research.com/quickcheck.html) - A free assessment tool to evaluate your organization's current performance level according to DORA research
