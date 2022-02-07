---
title: 'Google云原生微服务架构'
date: 2022-02-07
permalink: /posts/2022/02/Microservice/
tags:
  - 云原生
---



### 云原生？微服务？
云原生作为一种新型的云基础架构，云原生计算基金会（CNCF）致力于培养和维护开源生态系统，并推广云原生技术。

云原生技术有利于各组织在公有云、私有云和混合云等新型动态环境中，构建和运行可弹性扩展的应用。云原生的代表技术包括**容器、服务网格、微服务、不可变基础设施和声明式API**。
这些技术能够构建容错性好、易于管理和便于观察的松耦合系统。结合可靠的自动化手段，云原生技术使工程师能够轻松地对系统作出频繁和可预测的重大变更。

其中微服务将应用需要执行的各个任务分离成单独的服务，每项服务都可独立进行开发和管理，并且具有自己的API、发布、扩缩和配额管理。
微服务是**独立的、模块化的、动态的、短暂的**。它们可以分布在许多主机、集群甚至云端上。

![image-center]({{ '../images/posts/microservice/cloudnaive.jpeg' | absolute_url }}){: .align-center}

### 云原生安全

云原生安全则强调在云原生系统架构设计之初就提出了安全框架。Google云原生安全系统BeyondProd旨在提供更简单的管理、可扩展性功能。

传统的边界安全服务基于用户信任，根据上下文网络状态（IP、主机名）判断信任设备。随着公司网络权限的开放，越来越多的用户不在生产网络中使用服务，使得基于边界的安全服务不再可信。

因此云原生安全架构提出对服务的信任，通过对代码出处和服务身份的认证实现对服务的信任。
服务可以部署在公有云、私有云和第三方托管，用户也可以从不同的网络环境中使用服务。

使用微服务架构的容器化基础架构，能做到在开发和部署生命周期中尽早解决问题。
借助**服务网格**将安全功能和服务实现标准化和一致化。
进而保证开发者在开发过程中对安全的关注更少，花费时间更短，系统更安全。

BeyongdProd主要包括六个部分：
- 互相进行身份验证的服务端点
- 保证传输安全性
- 全局负载平衡控制
- 在边缘终止拒绝服务攻击
- 端到端的代码出处校验
- 运行时沙盒隔离

云原生安全提出了三个方面要求变化：
1. 网络层：从传统的边界安全（WAF）仅关注特定IP、服务认证转向零信任安全，所有服务间无信任，实现基于服务的认证，授信已知出处的代码。

2. 应用：应用使用独立的安全策略，应用更新需要整体更新转向跨服务强制一致安全，可以频繁更新个别微服务。

3. 硬件：从传统的部署在虚拟机或物理机转向通过隔离机制中封装工作负载，不同的应用服务可以共享操作系统。

### 云原生安全与零信任安全模型
   
对比零信任安全模型，云原生安全模型有不少相似性。
零信任安全模型针对用户身份验证，借助加密场景实现用户级的安全管理；云原生安全强调微服务级细分的边界安全，针对不同信任级别和控制措施。
云原生安全身份基于服务，不再基于IP地址和主机名。

云服务安全可实现一致性安全策略，将安全政策拆分成单独的微服务，可重用组件实现一致的安全策略，包括用户访问以及TLS加密等组件。

### 云原生产品

Google云原生安全架构实现包括6个方面的安全原则：
1. 在边缘保护网络。对应的产品：Google Front End（GFE）。
2. 服务之间没有固有的相互信任。对应的产品：Application Layer Transport Security（ALTS）。
3. 运行具有已知出处代码的机器。对应的产品：Binary Authorization for Borg（BAB）代码审计，Host Integrity（HINT）机器认证。
4. 用于跨服务强制执行一致政策的关卡。对应的产品：Service Access Policy，End User Context tickets（EUC）。
5. 简单、自动化、标准化的更新发布。对应的产品：Brog tooling。
6. 在共享操作系统的工作负载之间进行隔离。对应的产品：gVisor。

使用的安全产品主要说明：
> GFE：Terminates TLS (Transport Layer Security), edge proxy.

> ALTS: Remote Procedure Call (RPC), RPC authentication, integrity, encryption.

> Identities Features: seamless microservice replication, load balancing, rescheduling across hosts. Identities are in general bound to services, not hosts or server name.

> BAB: code review, binaries verifiably.

> HINT: secure boot process, verification of digital signatures(host system software) on BIOS, BMC, bootloader and OS kernel.

> Service Access Policy: authentication, authorization, auditing policies.

> EUC tickes: integrity protected, centrally-issued, forwardable credentials.

> Brog tooling for blue/green deployments: migrating running workloads when performing maintenance tasks.

> Live migration: changes affecting Google Cloud infrastructure VM workloads are not impacted.

> gVisor: workload isolation. Use user space kernel to intercept and handle syscalls, reducing the interaction with the host.