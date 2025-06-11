---
title: "Infrastructure as Code"
category: "glossary"
---

# Infrastructure as Code

Infrastructure as Code (IaC) is a practice in which infrastructure resources are provisioned and managed using machine-readable definition files rather than through manual processes or interactive configuration tools. This approach treats infrastructure configuration as software code, applying software development practices such as version control, testing, and continuous integration to infrastructure management. With IaC, engineers define the desired state of their infrastructure—including networks, virtual machines, load balancers, and connection topologies—using declarative or imperative code, which is then executed by automation tools to create, modify, or delete resources as needed.

In the DevOps context, Infrastructure as Code serves as a foundational practice that enables the rapid, consistent, and repeatable deployment of infrastructure environments. By automating infrastructure provisioning, IaC eliminates the traditional bottlenecks and human errors associated with manual configuration, allowing development and operations teams to work together more efficiently. This automation aligns perfectly with DevOps principles of collaboration, automation, and continuous delivery, as it enables teams to treat infrastructure changes with the same rigor and processes as application code changes, including code reviews, testing, and versioning.

> "Infrastructure as Code is the approach to defining computing and network infrastructure through source code that can then be treated just like any software system. Such code can be kept in source control to allow auditability and ReproducibleBuilds, subject to testing practices, and follow a full deployment pipeline for phased build, test, and release." - [Martin Fowler](https://martinfowler.com/bliki/InfrastructureAsCode.html)

## Declarative vs. Imperative Approaches

Infrastructure as Code implementations typically follow one of two primary approaches: declarative or imperative. The **declarative approach** focuses on defining the desired end state of the infrastructure without specifying the step-by-step process to achieve it. Tools like Terraform, AWS CloudFormation, and Azure Resource Manager templates exemplify this approach, where engineers specify what resources should exist with what properties, and the tool determines how to create or modify the infrastructure to match that specification. This approach simplifies infrastructure management by abstracting away the implementation details and allowing the tool to handle the complexity of resource dependencies and creation order.

In contrast, the **imperative approach** involves writing scripts that specify the exact sequence of commands needed to achieve the desired infrastructure state. Configuration management tools like Ansible, Chef, and Puppet often use this approach, though many now support declarative models as well. While imperative IaC provides more control over the exact implementation process, it typically requires more detailed knowledge of the underlying systems and can be more complex to maintain as infrastructure scales. Many organizations use a combination of both approaches, leveraging declarative tools for resource provisioning and imperative tools for configuration management and application deployment.

The choice between declarative and imperative approaches depends on various factors including team expertise, existing tooling, infrastructure complexity, and specific use cases. Regardless of the approach, both methods enable the core benefits of Infrastructure as Code: consistency, repeatability, scalability, and the ability to manage infrastructure through version-controlled code that can be tested, reviewed, and automatically deployed through continuous integration and delivery pipelines.

## Good Practices

Store infrastructure code in version control systems alongside application code, enabling change tracking, collaboration, and the ability to roll back to previous configurations when needed.

Implement automated testing for infrastructure code, including syntax validation, policy compliance checks, and integration tests that verify the actual provisioned resources match the expected state.

Adopt a modular approach to infrastructure code by creating reusable components and modules that encapsulate specific functionality, improving maintainability and enabling consistent implementation of common patterns.

Implement a continuous integration and deployment pipeline for infrastructure changes, automating the testing and deployment process to ensure consistent and reliable infrastructure updates.

Incorporate security and compliance requirements directly into infrastructure code through policy-as-code tools, ensuring that all provisioned resources adhere to organizational standards and regulatory requirements.

## Further Reading

* [Infrastructure as Code: Managing Servers in the Cloud](https://www.oreilly.com/library/view/infrastructure-as-code/9781491924334/) by Kief Morris - Comprehensive guide to the principles and practices of infrastructure as code

* [Terraform: Up & Running](https://www.oreilly.com/library/view/terraform-up/9781492046899/) by Yevgeniy Brikman - Practical guide to implementing infrastructure as code using Terraform

* [Ansible for DevOps](https://www.ansiblefordevops.com/) by Jeff Geerling - Detailed exploration of using Ansible for configuration management and infrastructure automation

* [Infrastructure as Code: From the Iron Age to the Cloud Age](https://www.thoughtworks.com/insights/articles/infrastructure-code-iron-age-cloud-age) - ThoughtWorks article on the evolution and importance of infrastructure as code

* [AWS Cloud Development Kit (CDK) Developer Guide](https://docs.aws.amazon.com/cdk/latest/guide/home.html) - Documentation for AWS CDK, which allows defining cloud infrastructure using familiar programming languages
