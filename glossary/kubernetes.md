---
title: "Kubernetes"
category: "glossary"
---

# Kubernetes

Kubernetes (often abbreviated as K8s) is an open-source container orchestration platform that automates the deployment, scaling, and management of containerized applications. Originally developed by Google based on their internal system called Borg, Kubernetes was donated to the Cloud Native Computing Foundation (CNCF) in 2014 and has since become the de facto standard for container orchestration. The platform provides a framework to run distributed systems resiliently by handling scaling, failover, deployment patterns, and service discovery, while abstracting away the underlying infrastructure complexity.

In the DevOps context, Kubernetes bridges the gap between development and operations by providing a consistent platform for deploying and managing applications across environments. It enables teams to implement infrastructure as code, automate deployment workflows, and establish self-healing systems that reduce manual intervention. By standardizing the deployment platform, Kubernetes helps organizations achieve higher deployment frequency, lower change failure rates, and faster recovery times—key metrics for DevOps success. This standardization also facilitates the implementation of GitOps practices, where infrastructure and application configurations are managed through version control systems.

> "Kubernetes is an open-source system for automating deployment, scaling, and management of containerized applications. It groups containers that make up an application into logical units for easy management and discovery." - [Kubernetes.io](https://kubernetes.io/)

## Core Architecture Components

The Kubernetes architecture follows a client-server model with a clear separation between the control plane (master components) and the data plane (worker nodes). The **control plane** manages the overall state of the cluster and makes global decisions about scheduling, scaling, and responding to cluster events. It consists of several key components: the API Server, which exposes the Kubernetes API and serves as the front-end for the control plane; etcd, a consistent and highly-available key-value store that stores all cluster data; the Scheduler, which assigns workloads to nodes based on resource requirements and constraints; and various Controller Managers that regulate the state of the cluster.

The **worker nodes** are the machines that run containerized applications and are managed by the control plane. Each node runs several essential components: the kubelet, an agent that ensures containers are running in a Pod according to the specifications provided by the control plane; kube-proxy, which maintains network rules on nodes to enable communication to Pods from inside and outside the cluster; and the container runtime (such as Docker, containerd, or CRI-O), which is responsible for pulling container images and running the containers. This architecture provides a clear separation of concerns, with the control plane handling cluster-wide management decisions and worker nodes executing the actual workloads.

Kubernetes organizes applications using several abstraction layers that provide flexibility and control over how workloads are deployed and managed. The basic unit of deployment is the **Pod**, which represents one or more containers that share network and storage resources and are always scheduled together. Higher-level abstractions build on Pods to provide additional capabilities: **Deployments** manage stateless applications with declarative updates and rollback capabilities; **StatefulSets** handle stateful applications that require stable identities and persistent storage; **DaemonSets** ensure specific Pods run on all or selected nodes; and **Jobs** manage batch processing workloads. These abstractions, combined with services for networking and configuration management, create a comprehensive platform for orchestrating complex applications at scale.

## Good Practices

Implement resource requests and limits for all containers to ensure efficient resource allocation, prevent resource starvation, and maintain cluster stability during peak loads.

Use namespaces to create logical partitions within a cluster, enabling better resource management, access control, and organization of applications in multi-team or multi-environment deployments.

Leverage Kubernetes' declarative configuration approach with infrastructure as code practices, storing all manifests in version control and implementing GitOps workflows for automated, auditable deployments.

Design applications for high availability by using appropriate Pod disruption budgets, implementing proper health checks with liveness and readiness probes, and configuring horizontal pod autoscaling based on relevant metrics.

Implement a comprehensive security strategy including network policies for micro-segmentation, role-based access control (RBAC) for fine-grained permissions, Pod security standards for container isolation, and regular security scanning of container images.

## Further Reading

* [Kubernetes: Up and Running](https://www.oreilly.com/library/view/kubernetes-up-and/9781492046523/) by Brendan Burns, Joe Beda, and Kelsey Hightower - Comprehensive guide to Kubernetes fundamentals and practical deployment patterns

* [Kubernetes Patterns](https://www.oreilly.com/library/view/kubernetes-patterns/9781492050278/) by Bilgin Ibryam and Roland Huß - Collection of reusable patterns and principles for designing cloud-native applications on Kubernetes

* [Kubernetes in Action](https://www.manning.com/books/kubernetes-in-action-second-edition) by Marko Lukša - Detailed, hands-on guide to Kubernetes with practical examples and in-depth explanations

* [Kubernetes the Hard Way](https://github.com/kelseyhightower/kubernetes-the-hard-way) by Kelsey Hightower - Step-by-step guide to understanding each component of Kubernetes by installing it manually

* [Cloud Native DevOps with Kubernetes](https://www.oreilly.com/library/view/cloud-native-devops/9781492040750/) by John Arundel and Justin Domingus - Guide to implementing DevOps practices using Kubernetes as the platform
