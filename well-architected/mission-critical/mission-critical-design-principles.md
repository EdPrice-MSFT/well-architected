---
title: Design principles of a mission-critical workload
description: Key design principles that serve as a compass for subsequent design decisions across technical domains and the critical design areas.
author: calcof
ms.author: calcof
ms.date: 02/28/2022
ms.topic: conceptual
ms.service: architecture-center
ms.subservice: well-architected
categories: web
products: azure
ms.custom:
  - mission-critical
  - alwayson
---

# Design principles of a mission-critical workload

The mission-critical design methodology is underpinned by five key design principles which serve as a compass for subsequent design decisions across the critical design areas. We highly recommend that you familiarize yourselves with these principles to better understand their impact and the trade-offs associated with non-adherence.

> [!IMPORTANT]
> This article is part of the [Azure Well-Architected mission-critical workload](index.yml) series. If you aren't familiar with this series, we recommend you start with [What is a mission-critical workload?](mission-critical-overview.md#what-is-a-mission-critical-workload).
>
> ![GitHub logo](./../_images/github.svg) [Azure Mission-Critical open source project](http://github.com/azure/alwayson)
>
> The [reference implementations](mission-critical-overview.md#illustrative-examples) are part of an open source project available on GitHub. The provided code assets illustrate implementations associated with the design principles highlighted in this article.

![Mission critical design principles](./images/mission-critical-design-principles.png "Mission critical design principles")

These mission-critical design principles resonate and extend the quality pillars of the Azure Well-Architected Framework&mdash;[Reliability](/azure/architecture/framework/#reliability), [Performance Efficiency](/azure/architecture/framework/scalability/), [Operational Excellence](/azure/architecture/framework/devops/), [Security](/azure/architecture/framework/security/). 

## Reliability

**_Maximum reliability_** - Fundamental pursuit of the most reliable solution, ensuring trade-offs are properly understood.

|Design principle|Considerations|
|---|---|
|[**Design for failure**](/azure/architecture/framework/resiliency/principles#design-for-failure)| Failure is impossible to avoid in a highly distributed multi-tenant cloud environment like Azure. By anticipating failures and cascading or correlated impact, from individual components to entire Azure regions, a solution can be designed and developed in a resilient manner.|
|[**Observe application health**](/azure/architecture/framework/resiliency/principles#observe-application-health)|Before issues impacting application reliability can be mitigated, they must first be detected. By monitoring the operation of an application relative to a known healthy state it becomes possible to detect or even predict reliability issues, allowing for swift remedial action to be taken.|
|[**Drive automation**](/azure/architecture/framework/resiliency/principles#drive-automation)|One of the leading causes of application downtime is human error, whether that be due to the deployment of insufficiently tested software or misconfiguration. To minimize the possibility and impact of human errors, it is vital to strive for automation in all aspects of a cloud solution to improve reliability; automated testing, deployment, and management.|
|[**Design for self-healing**](/azure/architecture/framework/resiliency/principles#design-for-self-healing)|Self healing describes a system's ability to deal with failures automatically through pre-defined remediation protocols connected to failure modes within the solution. It is an advanced concept that requires a high level of system maturity with monitoring and automation, but should be an aspiration from inception to maximize reliability.|


## Performance Efficiency

**_Sustainable performance and scalability_** - Design for scalability across the end-to-end solution without performance bottlenecks.

|Design principle|Considerations|
|---|---|
|[**Design for scale-out**](/azure/architecture/framework/resiliency/principles#design-for-scale-out)|Scale-out is a concept that focuses on a system's ability to respond to demand through horizontal growth. This means that as traffic grows, more resource units are added in parallel instead of increasing the size of the existing resources. A systems ability to handle expected and unexpected traffic increases through scale-units is essential to overall performance and reliability by further reducing the impact of a single resource failure.|
|[**Model capacity**](/azure/architecture/framework/scalability/test-checklist)|The system's expected performance under various load profiles should be modeled through load and performance tests. This capacity model enables planning of resource scale levels for a given load profile, and additionally exposes how system components perform in relation to each other, therefore enabling system-wide capacity allocation planning.|
|[**Test and experiment often**](/azure/architecture/framework/scalability/performance-test)|Testing should be performed for each major change as well as on a regular basis. Such testing should be performed in testing and staging environments, but it can also be beneficial to run a subset of tests against the production environment. Ongoing testing validates existing thresholds, targets and assumptions and will help to quickly identify risks to resiliency and availability.|
|[**Baseline performance and identify bottlenecks**](/azure/architecture/framework/scalability/test-tools#identify-baselines-and-goals-for-performance)|Performance testing with detailed telemetry from every system component allows for the identification of bottlenecks within the system, including components which need to be scaled in relation to other components, and this information should be incorporated into the capacity model.|
|[**Reduce overhead with managed compute services**](/azure/architecture/guide/design-principles/managed-services)|Using managed compute services and containerized architectures significantly reduces the ongoing administrative and operational overhead of designing, operating, and scaling applications by shifting infrastructure deployment and maintenance to the managed service provider.|

## Operational Excellence

**_Operations by design_** - Engineered to last with robust and assertive operational management.

|Design principle|Considerations|
|---|---|
|[**Loosely coupled components**](/azure/architecture/framework/devops/principles#use-loosely-coupled-architecture)|Loose coupling enables independent and on-demand testing, deployments, and updates to components of the application while minimizing inter-team dependencies for support, services, resources, or approvals.|
|[**Optimize build and release process**](/azure/architecture/framework/devops/principles#optimize-build-and-release-processes)|Fully automated build and release processes reduce the friction and increase the velocity of deploying updates, bringing repeatability and consistency across environments. Automation shortens the feedback loop from developers pushing changes to getting automated near instantaneous insights on code quality, test coverage, security, and performance, which increases developer productivity and team velocity.|
|[**Understand operational health**](/azure/architecture/framework/devops/principles#understand-operational-health)|Full diagnostic instrumentation of all components and resources enables ongoing observability of logs, metrics and traces, and enables health modeling to quantify application health in the context to availability and performance requirements.|
|[**Rehearse recovery and practice failure**](/azure/architecture/framework/devops/principles#rehearse-recovery-and-practice-failure)|Business Continuity (BC) and Disaster Recovery (DR) planning and practice drills are essential and should be conducted periodically, since learnings from drills can iteratively improve plans and procedures to maximize resiliency in the event of unplanned downtime.|
|[**Embrace continuous operational improvement**](/azure/architecture/framework/devops/principles#embrace-continuous-operational-improvement)|Prioritize routine improvement of the system and user experience, leveraging a health model to understand and measure operational efficiency with feedback mechanisms to enable application teams to understand and address gaps in an iterative manner.|

## Security

**_Always secure_** - Design for end-to-end security to maintain application stability and ensure availability.

|Design principle|Considerations|
|---|---|
|[**Monitor the security of the entire solution and plan incident responses**](/azure/architecture/framework/security/security-principles#monitor-system-security-plan-incident-response)|Correlate security and audit events to model application health and identify active threats. Establish automated and manual procedures to respond to incidents leveraging Security Information and Event Management (SIEM) tooling for tracking.|
|[**Model and test against potential threats**](/azure/architecture/framework/devops/principles#optimize-build-and-release-processes)|Ensure appropriate resource hardening and establish procedures to identify and mitigate known threats, using penetration testing to verify threat mitigation, as well as static code analysis and code scanning.|
|[**Identify and protect endpoints**](/azure/architecture/framework/devops/principles#understand-operational-health)|Monitor and protect the network integrity of internal and external endpoints through security capabilities and appliances, such as firewalls or web application firewalls. Use industry standard approaches to protect against common attack vectors like Distributed Denial-Of-Service (DDoS) attacks, such as SlowLoris.|
|[**Protect against code level vulnerabilities**](/azure/architecture/framework/devops/principles#rehearse-recovery-and-practice-failure)|Identify and mitigate code-level vulnerabilities, such as cross-site scripting or SQL injection, and incorporate security patching into operational lifecycles for all parts of the codebase, including dependencies.|
|[**Automate and use least privilege**](/azure/architecture/framework/devops/principles#embrace-continuous-operational-improvement)|Drive automation to minimize the need for human interaction and implement least privilege across both the application and control plane to protect against data exfiltration and malicious actor scenarios.|
|[**Classify and encrypt data**](/azure/architecture/framework/security/security-principles#classify-and-encrypt-data)|Classify data according to risk and apply industry standard encryption at rest and in transit, ensuring keys and certificates are stored securely and managed properly.|

## Cloud native design

- [**Azure-native managed services**](/azure/architecture/guide/design-principles/managed-services) - Azure-native managed services are prioritized due to their lower administrative and operational overhead as well as tight integration with consistent configuration and instrumentation across the application stack.

- [**Roadmap alignment**](/azure/architecture/guide/design-principles/design-for-evolution) - Incorporate upcoming new and improved Azure service capabilities as they become Generally Available (GA) to stay close to the leading edge of Azure.

- **Embrace preview capabilities and mitigate known gaps** - While Generally Available (GA) services are prioritized for supportability, Azure service previews are actively explored for rapid incorporation, providing technical and actionable feedback to Azure product groups to address gaps.

- **Azure Landing Zone alignment** - Deployable within an [Azure Landing Zone](/azure/cloud-adoption-framework/ready/landing-zone) and aligned to the Azure Landing Zone design methodology, but also fully functional and deployable in a bare environment outside of a landing zone.

## Next step

Explore the eight design areas that provide critical considerations and recommendations for building a mission-critical workload.

> [!div class="nextstepaction"]
> [Design areas](./mission-critical-design-areas.md)
