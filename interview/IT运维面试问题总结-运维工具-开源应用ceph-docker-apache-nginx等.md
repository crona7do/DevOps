## 运维工具

### 简述Ansible及其优势？

`Ansible`是一款极其简单的开源的自动化运维工具，基于Python开发，集合了众多运维工具(puppet, cfengine, chef, func, fabric)的优点。实现了批量系统配置，批量程序部署，批量运行命令等功能。
同时Ansible是基于模块工作，其实现批量部署的是ansible所运行的模块。

Ansible其他重要的优势：

- 跨平台支持：Ansible在物理、虚拟、云和容器环境中为Linux、Windows、UNIX和网络设备提供无代理支持。
- 人类可读的自动化：Ansible playbook以YAML文本文件的形式编写，易于阅读，有助于确保每个人都理解他们将要做的事情。
- 对应用程序的完美描述：Ansible playbook可以进行任何更改，并且可以描述和记录应用程序环境的每个细节。
- 易于管理的版本控制：Ansible剧本和项目是纯文本。它们可以像源代码一样处理，并放在现有的版本控制系统中。
- 支持动态库存：Ansible管理的机器列表可以从外部资源动态更新，以便随时捕获所有受管服务器的正确的当前列表，无论基础设施或位置如何。
- 易于与其他系统集成的编排：HP SA、Puppet、Jenkins、Red Hat Satellite，以及存在于环境中的其他系统，都可以被利用并集成到Ansible工作流中。

### 简述Ansible工作机制及其特性？

Ansible是一款自动化运维工具，基于Python开发，具有批量系统配置, 批量程序部署, 批量运行命令等功能。

其工作机制如下：

- 1、用户使用Ansible或Playbook，在服务器中断输入Ansible的Ad-Hoc命令集或Playbook；
- 2、Ansible遵循预先编排的规则将Playbooks逐条拆解为Play；
- 3、Play组织成Ansible可识别的任务（Task）；
- 4、Task会调用任务所涉及的所有模块（Module）和插件（Plugin）；
- 5、读取Inventroy中定义的主机列表；
- 6、通过SSH认证（默认）将任务集以临时文件或命令的形式传输到远程客户端执行并返回执行结果。
其特性如下：
- 7、no agents：不需要在被管控主机上安装任何客户端，只需SSH、Python即可，建议Python版本为2.6.6以上；
- 8、no server：无服务器端, 使用时直接运行命令即可；
- 9、modules in any languages：基于模块工作, 丰富的内置模块，可使用任意语言开发模块；
- 10、yaml, not code：使用yaml语言定制剧本playbook，易于管理，API简单明了；
- 11、ssh by default：基于SSH工作，整个过程简单、方便、安全，建议使用公钥方式认证；
- 12、strong multi-tier solution：可实现多级指挥。

### 简述Ansible中如何保存敏感数据？

在ansible内容中保留秘密数据并仍然公开共享，那么可以在playbooks中使用Vault。Ansible Vault，它包含在Ansible中，可以加密和解密Ansible使用的任何结构化数据文件。

### 简述Ansible适合的场景？

Ansible将编排与配置管理、供应和应用程序部署结合并统一在一个易于使用的平台上。Ansible的一些主要场景包括:

- 配置管理：集中配置文件管理和部署是Ansible的一个常见场景。
- 应用程序部署：当使用Ansible定义应用程序，并使用Ansible Tower管理部署时，团队可以有效地管理从开发到生产的整个应用程序生命周期。
- 部署：当在系统上部署或安装应用程序时，Ansible和Ansible Tower可以帮助简化供应系统的流程，无论是PXE启动的裸金属服务器或虚拟机，还是从模板创建虚拟机或云实例。
- 持续交付：创建CI/CD管道需要许多团队的协调和参与。如果没有一个简单的自动化平台，团队协作很难完成。而Ansible playbook在应用程序的整个生命周期中可以保持适当的部署(和管理)
- 安全性和审计：当安全策略在Ansible中定义时，可以将站点范围的安全策略的扫描和修复集成到其他自动化流程中。安全性是部署的所有内容中不可或缺的一部分。
- 编排：配置本身不能定义环境，需要定义多个配置如何交互，并确保可以将不同的部分作为一个整体来管理。

### 简述Ansible Inventory？

Ansible中受管主机列在主机清单（inventory）文本文件中，清单还将这些系统组织成group，以便更容易地进行批量管理。一个Inventory定义了Ansible将管理的主机集合。这些主机还可以分配至组，可以对组进行批量管理。组可以包含子组，主机可以是多个组的成员。Inventory根据类型可分为静态清单和动态清单：

- 静态主机Inventory可以由文本文件定义。
- 动态主机Inventory可以由脚本或其他程序根据需要使用外部信息提供者生成。

### 简述Ansible配置文件优先级？

Ansible 只使用最高优先级配置文件中的设置，其它配置文件中的设置将被忽略。即使存在其他优先级较低的文件，它们的设置也将被忽略，并且不会与所选配置文件中的设置相结合。

$ANSIBLE_CONFIG环境变量指定的任何文件都将覆盖所有其他配置文件。如果没有设置该变量，接下来将检查运行ansible命令的目录以查找ansible.cfg文件。如果该文件不存在，则检查用户的主目录以查找.ansible.cfg文件。如上配置文件都不存在时，才使用全局/etc/ansible/ansible.cfg文件。

### 简述Ansible ad-hoc命令？

Ad-Hoc命令是一种快速执行单个Ansible任务的方法，适合于不需要永久保存该任务，临时执行的场景。Ad-Hoc是简单的控制台操作，无需编写剧本就可以运行。它们对于快速测试和更改非常有用。

### 简述Ansible ad-hoc和playbook的区别？

- Ad-Hoc 命令可以作为一次性命令对一组目标主机运行单个、简单的任务。
- Ad-Hoc 不适合复杂配置管理或编配场景，Ad-Hoc 一次只能调用一个模块和一组参数。当需要多个操作时，必须使用多个 Ad-Hoc 来执行。
- playbook可以实现以一种简易重复的方式对一组目标主机运行多个复杂的任务。
- Playbook 是描述要在受管主机上实施的必要配置或程序性步骤的文件。
- Playbook 为配置管理和部署提供了强大而灵活的解决方案。
- Playbook 可以将冗长而复杂的管理任务转变为可轻松重复的历程，并且可预测成果然而。
- playbook 是一个文本文件，其中包含一个或多个按顺序运行的play的列表。
- playbook中，可以将playbook中的tasks保存为人类可读且可立即运行的形式。
- play 是一组有序的任务，应该对从目录中选择的主机运行。

### 简述Ansible变量？

Ansible 利用变量存储整个 Ansible 项目文件中可重复使用的值，从而可以简化项目的创建和维护，并减少错误的发生率。在定义Ansible变量时，通常有如下三种范围的变量：

- global范围：从命令行或Ansible配置中设置的变量；
- play范围：在 play 和相关结构中设置的变量；
- host范围：inventory、facts 或 register 的变量，在主机组和个别主机上设置的变量。

### 简述Ansible如何实现任务的循环？

简单循环：

- Ansible支持使用loop在一组item上迭代任务；
- loop可以使用列表中的每个项、列表中每个文件的内容、生成的数字序列或使用更复杂的结构来重复任务。
- 使用loop使管理员不必编写使用相同模块的多个任务。

复杂（嵌套）循环：

- with_nested键用于嵌套循环，循环在循环中运行。它需要一个包含两个或多个列表的列表。例如，将一个列表划分为两个列表，任务将迭代第一个列表中的每一项与第二个列表中的每一项。

### 简述Ansible hanlder？

Ansible模块被设计成幂等的，即在一个适当编写的剧本中，剧本及其任务可以在不更改受管主机的情况下多次运行，除非它们需要进行更改以使受管主机达到所需的状态。

然而，有时当一个任务对系统进行了更改后同时需要运行另一个任务。例如，对服务的配置文件的更改可能需要重新加载服务，以便更改后的配置生效。此时就需要使用hanlder程序。handler程序是响应由其他任务组成的通知的任务。每个handler程序都有一个全局惟一的名称，并在剧本中任务块的末尾触发。

如果没有任务通过名称调用handler程序，它将不会运行。

如果一个或多个任务都调用handler程序，它将在剧中的所有其他任务完成后仅运行一次。

因为handler程序是任务，所以可以在handler程序中使用与处理任何其他任务相同的模块。通常，handler程序用于重新启动主机和重新启动服务。

handler程序可以视为非活动任务，只有在使用notify语句显式调用时才会触发这些任务。

### 简述Ansible Block？
在 playbook 中， blocks 是囊括了任务的子句；

blocks 允许对任务进行逻辑分组，并可用于控制任务的执行方式，例如，管理员可以定义一组主要任务和一组附加任务，附加任务仅在第一组失败时执行。为此，可利用三个关键字在 playbook 中使用块：

- block：定义要运行的主要任务；
- rescue：定义将在 block 子句中定义的任务失败时运行的任务；
- always：定义始终都独立运行的任务，不论 block 和 rescue 子句中定义的任务是成功还是失败。

### 简述Ansible如何处理play错误的？

Ansible审查每个任务的返回代码，以确定任务是否成功或失败。默认情况下，当一个任务失败时，Ansible会立即中止该主机上的其他操作，并跳过所有后续任务。

实际生产中，若希望即使任务失败也能继续执行play，Ansible也包含了多种特性用于管理任务错误：

忽略任务失败：在任务中使用ignore_errors关键字忽略错误，即使任务失败，也继续在主机上执行playbook。

### 简述Ansible角色？

数据中心有各种不同类型的主机。如web服务器、数据库服务器，基于开发环境的服务器。随着时间的推移，具有处理所有这些情况的任务和人员的Ansible playbook将变得庞大而复杂。

- 角色允许将复杂的剧本组织成独立的、更小的剧本和文件。
- 角色提供了一种从外部文件加载任务、处理程序和变量的方法。
- 角色也可关联和引用静态的文件和模板。
- 角色可以编写成满足普通用途需求，并且能被重复利用。
- 定义角色的文件具有特定的名称，并以严格的目录结构进行组织。

### 简述Ansible Galaxy？

Ansible Galaxy是一个由各种Ansible管理员和用户编写的Ansible角色的公共库。它是一个包含数千个Ansible角色的归档文件，并且有一个可搜索的数据库，帮助Ansible用户识别可能帮助他们完成管理任务的角色。Ansible Galaxy包括指向新用户和角色开发人员的文档和视频的链接。

### 简述Ansible如何控制任务的并行执行？

通过在所有主机上并行运行任务，Ansible可以对剧本的执行进行更多的控制。默认情况下，Ansible默认最多并行5个，因此它将同时在5台不同的机器上运行一个特定的任务。Ansible可以通过配置forks来设置并行执行任务数量。

同时Ansible也可以通过serial来减少ork数量所指定的并行书，serial关键字主要用于控制滚动更新，避免一次性更新过多的节点。

### 简述Ansible故障后的排查思路？

- `日志判断`：默认情况下，Ansible没有配置为将其输出，记录到任何日志文件中。可通过ansible.cfg配置文件default部分中的log_path参数或$ANSIBLE_LOG环境变量进行配置。然后通过日志进行定位。
- `Debug模块`：调试模块是Ansible可用的模块之一，它可以更好地了解控制节点上正在进行的操作。这个模块可以在playbook执行时为某个变量提供值。
- `syntax-check`：通过ansible-playbook 命令的 --syntax-check命选项检查剧本的YAML语法。
- `diff`：Ansible还提供了--diff选项。此选项报告对受管主机上的模板文件所做的更改。如果与--check选项一起使用，这些更改将显示出来，而不是实际执行。从而判断Ansible整个过程需要做何种更改。

## 开源应用

### 简述Ceph的优势及其特点？

Ceph是一个分布式的数据对象存储，Ceph相对其他存储系统具有如下优势：

- CRUSH算法： ceph摒弃了传统的集中式存储元数据寻址的方案，而使用CRUSH算法完成数据的寻址操作。能够实现各类负载的副本放置规则，例如跨机房、机架感知等。Crush算法有相当强大的扩展性，理论上支持数千个存储节点，从而增强了Ceph弹性扩展和高可用性。
- 高可用：通过CRUSH算法指定副本的物理存储位置以分隔故障域，支持数据强一致性，ceph可以忍受多种故障场景并自动尝试并行修复。
- 高扩展性：Ceph本身并没有主控节点，扩展起来比较容易，并且理论上，它的性能会随着磁盘数量的增加而线性增长。
- 特性丰富：Ceph支持三种调用接口：对象存储，块存储，文件系统挂载。三种方式可以一同使用。
Ceph主要特点如下：
- 统一存储；
- 无任何单点故障；
- 数据多份冗余；
- 存储容量可扩展；
- 自动容错及故障自愈。

### 简述Ceph存储体系架构？

Ceph体系架构主要由RADOS和RADOS GW和RBD以及CephFS构成。

-  `RADOS`（Reliable, Autonomic Distributed Object Store）是Ceph的底层核心，RADOS本身也是分布式存储系统，CEPH所有的存储功能都是基于RADOS实现。RADOS由两个组件组成：OSD和Monitor。
    -  OSD主要提供存储资源，每一个disk、SSD、RAID group或者一个分区都可以成为一个OSD，而每个OSD还将负责向该对象的复杂节点分发和恢复；
    - Monitor维护Ceph集群并监控Ceph集群的全局状态，提供一致性的决策。
- `RADOS GW`和`RBD`：RADOS GateWay、RBD其作用是在librados库的基础上提供抽象层次更高、更便于应用或客户端使用的上层接口。其中，RADOS GW是一个提供与Amazon S3和Swift兼容的RESTful API的gateway，以供相应的对象存储应用开发使用。 RBD则提供了一个标准的块设备接口，常用于在虚拟化的场景下为虚拟机创建volume。
- `CEPHFS`：CEPHFS则提供了POSIX接口，用户可直接通过客户端挂载使用。

### 简述Ceph Pool有几种类型？

Ceph存储池Pool是Ceph存储集群用于存储对象的逻辑分区。池类型确定池用于确保数据持久性的保护机制，Ceph有两种Pool类型：

replication类型：在集群中分布每个对象的多个副本。

erasure coding类型：将每个对象分割成块，并将它们与其他擦除编码块一起分发，以使用自动纠错机制保护对象。

### 简述Ceph Pool、PG、ODDs的关系？

Ceph存储池Pool是Ceph存储集群用于存储对象的逻辑分区。

Pool中存在一定的数量的PG，PG将对象存储在一组由CRUSH算法确定的osd中。

Ceph使用CRUSH算法将对象分配给池中的一个PG，根据池的配置和CRUSH算法，PG自动映射到一组OSDs。

一个PG里包含一堆对象，一个对象只能属于一个PG。

### 简述Ceph节点的角色？

所有Ceph存储集群的部署都始于部署一个个Ceph节点、网络和Ceph存储集群。Ceph存储集群至少需要一个Ceph Monitor和两个OSD守护进程。而运行Ceph文件系统客户端时，则必须要有元数据服务器（Metadata Server）。

- Ceph OSDs：Ceph OSD守护进程（ Ceph OSD ）的功能是存储数据，处理数据的复制、恢复、回填、再均衡，并通过检查其他OSD守护进程的心跳来向Ceph Monitors提供一些监控信息。当Ceph存储集群设定为有2个副本时，至少需要2个OSD守护进程，集群才能达到active+clean状态（Ceph默认有3个副本）。
- Monitors：Ceph Monitor维护着展示集群状态的各种图表，包括监视器图、OSD图、归置组（PG）图、和CRUSH 图。
- MDSs：Ceph元数据服务器（MDS）为Ceph文件系统存储元数据（也就是说，Ceph块设备和Ceph 对象存储不使用MDS）。元数据服务器使得POSIX文件系统的客户端，可以在不对Ceph存储集群造成负担的前提下，执行诸如ls、find等基本命令。

### 简述Ceph的适应场景？

Ceph的应用场景主要由它的架构确定，Ceph提供对象存储、块存储和文件存储。

- LIBRADOS应用

Librados提供了应用程序对RADOS的直接访问，目前Librados已经提供了对C、C++、Java、Python、Ruby和PHP的支持。

- RADOSGW应用

此类场景基于Librados之上，增加了HTTP协议，提供RESTful接口并且兼容S3、Swfit接口。RADOSGW将Ceph集群作为分布式对象存储，对外提供服务。

- RBD应用

此类场景也是基于Librados之上的，细分为下面两种应用场景。

第一种应用场景为虚拟机提供块设备。通过Librbd可以创建一个块设备（Container），然后通过QEMU/KVM附加到VM上。通过Container和VM的解耦，使得块设备可以被绑定到不同的VM上。

第二种应用场景为主机提供块设备。这种场景是传统意义上的理解的块存储。

以上两种方式都是将一个虚拟的块设备分片存储在RADOS中，都会利用数据条带化提高数据并行传输，都支持块设备的快照、COW（Copy-On-Write）克隆。最重要的是RBD还支持Live migration。

- CephFS（Ceph文件系统）

此类应用是基于RADOS实现的PB级分布式文件系统，其中引入MDS（Meta Date Server），它主要为兼容POSIX文件系统提供元数据，比如文件目录和文件元数据。

### 简述Docker的特性？

Docker主要有如下特性：

- 标准化
    - 保证一致的运行环境
    - 弹性伸缩，快速扩容
    - 方便迁移
    - 持续集成、持续交付与持续部署
- 高性能
    - 不需要进行硬件虚拟以及运行完整的操作系统
- 轻量级
    - 快速启动
    - 隔离性
    - 进程隔离

### 简述Docker容器的几种状态？

Docker容器可以有四种状态：
- 运行
- 已暂停
- 重新启动
- 已退出

### 简述Dockerfile、Docker镜像和Docker容器的区别？

`Dockerfile` 是软件的`原材料`，`Docker镜像` 是`软件的交付品`，而 `Docker容器` 则可以认为是`软件的运行态`。从应用软件的角度来看，Dockerfile、Docker 镜像与 Docker 容器分别代表软件的三个不同阶段，Dockerfile 面向开发，Docker 镜像成为交付标准，Docker 容器则涉及部署与运维。

### 简述Docker与KVM（虚拟机）的区别？

- 容器部署简单，虚拟机部署相对复杂。

虚拟化技术依赖物理CPU和内存，是硬件级别的；

而docker构建在操作系统上，利用操作系统的containerization技术，所以docker甚至可以在虚拟机上运行。

- 容器秒级启动，虚拟机通常分钟级启动。

传统的虚拟化技术在构建系统的时候较为复杂，需要大量的人力；

而docker可以通过Dockfile来构建整个容器，重启和构建速度很快。

- 容器需要的资源（如磁盘、CPU、内存）相对更少。
- 容器比较轻便，虚拟机相对较重。

虚拟化系统一般都是指操作系统级概念，比较复杂，称为“系统”；

而docker开源而且轻量，称为“容器”，单个容器适合部署少量应用，比如部署一个redis、一个memcached。

### 简述Docker主要使用的技术？

容器主要使用如下技术：

- Cgroup：资源控制
- Namespace：访问隔离
- rootfs：文件系统隔离
- 容器引擎（用户态工具）：生命周期控制

### 简述Docker体系架构？

Docker体系相对简单，主要涉及如下5个组件：

- Docker客户端 – Docker

docker客户端则扮演着docker服务端的远程控制器，可以用来控制docker的服务端进程。

- Docker服务端 – Docker Daemon

docker服务端是一个服务进程，管理着所有的容器。

- Docker镜像 – Image

docker镜像，一个能够运行在docker容器上的一组程序文件，是一个只读的模板，不包含任何动态数据。

- Docker容器 – Docker Container

docker容器，就是运行程序的载体，容器是镜像运行时的实体。

- Docker镜像仓库 -- Registry

Docker仓库是集中存放镜像文件的场所，Docker仓库分为公开仓库（Public）和私有仓库（Private）两种形式。

### 简述Docker如何实现网络隔离？

Docker利用了网络的命名空间特性，实现了不同容器之间的网络隔离。命名空间可以支持网络协议栈的多个实例，独立的协议栈被隔离到不同的命名空间中。

因此处于不同命名空间中的网络栈是完全隔离的，彼此之间无法通信。每个独立的命名空间中可以有自己独立的路由表及独立的iptables设置来提供包转发、NAT及IP包过滤等功能。

### 简述Linux文件系统和Docker文件系统？

`Linux文件系统`：由bootfs和rootfs组成，bootfs主要包含bootloader和kernel，bootloader主要是引导加载kernel，当kernel被加载到内存之后bootfs就被卸载掉了。rootfs包含的就是典型linux系统中/dev,/proc,/bin,/etc等标准目录。

`Docker文件系统`：Docker容器是建立在Aufs分层文件系统基础上的，Aufs支持将不同的目录挂载到同一个虚拟文件系统下，并实现一种layer的概念。Aufs将挂载到同一虚拟文件系统下的多个目录分别设置成read-only，read-write以及whiteout-able权限。docker 镜像中每一层文件系统都是read-only。

### 简述Docker网络模式？

Docker使用Linux的Namespaces技术来进行资源隔离，其中Network Namespace实现隔离网络。

一个Network Namespace提供了一份独立隔离的网络环境，包括网卡、路由、Iptable规则等，Docker网络有如下四种模式：

- `host模式`：host模式下容器将不会获得独立的Network Namespace，该模式下与宿主机共用一个Network Namespace。容器将不会虚拟出自己的网卡，不会配置独有的IP等，而是使用宿主机的IP和端口。
- `container模式`：Container 网络模式是 Docker 中一种较为特别的网络的模式，处于container模式下的 Docker 容器会共享其他容器的网络环境，因此，两个或以上的容器之间不存在网络隔离，而配置container模式的容器又与宿主机以及除此之外其他的容器存在网络隔离。  
- `none模式`：none模式下，Docker容器拥有自己的Network Namespace，但是，并不为Docker容器进行任何网络配置和构造任何网络环境。Docker 容器采用了none 网络模式，那么容器内部就只能使用loopback网络设备，不会再有其他的网络资源。Docker Container的none网络模式意味着不给该容器创建任何网络环境，容器只能使用127.0.0.1的本机网络。
- `bridge模式`：bridge模式是Docker默认的网络设置，此模式会为每一个容器分配Network Namespace、设置IP等，并将该宿主机上的Docker容器连接到一个虚拟网桥上。

### 简述Docker跨主机通信的网络实现方式？

docker跨主机通信按原理可通过以下三种方式实现：

- 直接路由方式：直接在不同宿主机之间添加静态路由；
- 桥接方式（如pipework）：通过静态指定容器IP为宿主机IP同一个网络的形式，即可实现。
- Overlay隧道方式：使用overlay网络实现，Overlay网络指在现有网络层之上叠加的虚拟化技术，实现应用在网络上的承载，并能与其他网络业务分离，并且以基于IP的网络技术为主，如flannel、ovs+gre。

### 简述flannel网络模型实现原理？

Flannel为每个host分配一个subnet，容器从subnet中分配IP，这些IP可以在host间路由，容器间无需使用nat和端口映射即可实现跨主机通信。每个subnet都是从一个更大的IP池中划分的，flannel会在每个主机上运flanneld的agent，负责从池子中分配subnet。

Flannel使用etcd存放网络配置、已分配的subnet、host的IP等信息，Flannel数据包在主机间转发是由backend实现的，目前已经支持UDP、VxLAN、host-gw、AWS VPC和GCE路由等多种backend。

### 简述什么是Apache服务器？

Apache服务器是一个非常流行、功能强大并且开源的Web服务器，基于HTTP超文本传输协议运行，这一协议提供了服务器和客户端Web浏览器通信的标准。它支持SSL、CGI文件、虚拟主机等许多功能特性。

### 简述Apache虚拟主机？

Apache虚拟主机相当于一个在同一台服务器中却相互独立的站点，从而实现一台主机对外提供多个 web 服务，每个虚拟主机之间是独立的，互不影响的。Apache具有两种类型的虚拟主机：基于名称的虚拟主机和基于IP的虚拟主机。

### 简述Apache的Worker MPM和Prefork MPM之间的区别？

它们都是MPM，Worker和Prefork有它们各自在Apache上的运行机制，取决于哪种模式启动Apache。Worker MPM和Prefork MPM基本的区别在于它们产生子进程的处理过程。

- 1、Prefork MPM中，一个主httpd进行被启动，这个主进程会管理所有其它子进程为客户端请求提供服务。Worker MPM中一个httpd进程被激活，则会使用不同的线程来为客户端请求提供服务.
- 2、Prefork MPM使用多个子进程，每一个进程带有一个线程，Worker MPM使用多个子进程，每一个进程带有多个线程。
- 3、Prefork MPM中的连接处理，每一个进程一次处理一个连接而在Worker MPM中每一个线程一次处理一个连接。
- 4、内存占用Prefork MPM占用庞大的内存，而Worker MPM占用更小的内存。

### 简述Nginx是什么及其主要特点？

Nginx是一款自由的、开源的、高性能的HTTP服务器和反向代理服务器。可以作为一个HTTP服务器进行网站的发布处理，同时也可以作为反向代理进行负载均衡的实现。其主要特点有：

- 占有内存少，并发能力强。
- Nginx使用基于事件驱动架构，使得其可以支持数以百万级别的TCP连接。
- 高度的模块化和自由软件许可证使得第三方模块非常丰富。
- Nginx是一个跨平台服务器，可以运行在Linux，Windows，FreeBSD，Solaris，AIX，Mac OS等操作系统上。

### 简述Nginx和Apache的差异？

- Nginx是一个基于事件的Web服务器，Apache是一个基于流程的服务器；
- Nginx所有请求都由一个线程处理，Apache单个线程处理单个请求；
- Nginx避免子进程的概念，Apache是基于子进程的；
- Nginx在内存消耗和连接方面更好，Apache在内存消耗和连接方面一般；
- Nginx的性能和可伸缩性不依赖于硬件，Apache依赖于CPU和内存等硬件；
- Nginx支持热部署，Apache不支持热部署；
- Nginx对于静态文件处理具有更高效率，Apache相对一般；
- Nginx在反向代理场景具有明显优势，Apache相对一般。

### 简述Nginx主要应用的场景？

基于Nginx的特性，Nginx的应用场景主要有：

- http服务器：Nginx是一个http服务可以独立提供http服务，可以做网页静态服务器。
- 虚拟主机：可以实现在一台服务器虚拟出多个网站。
- 正反代理：负载均衡或加速，当网站的访问量达到一定程度后，单台服务器不能满足用户的请求时，需要用多台服务器集群可以使用Nginx做反向代理，并且多台服务器可以平均分担负载。

### 简述Nginx HTTP连接和请求的关系？

HTTP是建立在TCP上，一次HTTP请求需要先建立TCP三次握手（称为TCP连接），在连接的基础上再进行HTTP请求。

HTTP请求建立在一次TCP连接基础上，对于HTTP会话，一次TCP连接可以建立多次HTTP请求。

### 简述Nginx支持哪些访问控制方式？

- 连接限制：Nginx自带的limit_conn_module模块（TCP连接频率限制模块）和limit_req_mudule模块（HTTP请求频率限制模块）支持对连接频率以及请求频率、来源进行限制，通常可可以用来防止DDOS攻击。
- IP限制：Nginx使用http_access_module模块可实现基于IP的访问控制，但通过代理可以绕过限制。
- 账号限制：Nginx使用http_auth_basic_module模块可实现用户密码的登录限制。
- 流量限制：Nginx使用http_core_moduleblock模块可实现客户端传送响应的速率限制。

### 简述Nginx Master进程和Worker节点？

`master进程`主要用来管理worker进程，包含：接收来自外界的信号，向各worker进程发送信号，监控worker进程的运行状态，当worker进程退出后(异常情况下)，会自动重新启动新的worker进程。

`worker进程`则是处理基本的网络事件。多个worker进程之间是对等的，他们同等竞争来自客户端的请求，各进程互相之间是独立的。一个请求，只可能在一个worker进程中处理，一个worker进程，不可能处理其它进程的请求。

### 简述Nginx如何处理HTTP请求？

- 首先，Nginx 在启动时，会解析配置文件，获取需要监听的端口与 IP 地址，然后在 Nginx 的 Master 进程里面先初始化好这个监控的Socket（创建 Socket，设置 addr、绑定ip和端口，然后listen 监听)。
- 然后，再 fork 出多个子进程出来。
- 之后，子进程会竞争 accept 新的连接。此时，客户端就可以向 nginx 发起连接了。当客户端与nginx完成TCP三次握手，与 nginx 建立好一个连接后。此时，某一个子进程会 accept 成功，得到这个建立好的连接的 Socket ，然后创建 nginx 对连接的封装。
- 接着，设置读写事件处理函数，并添加读写事件来与客户端进行数据的交换。
- 最后，Nginx 或客户端来主动关掉连接，完成整个HTTP请求的处理。

### 简述Nginx对于HTTP请求采用哪两种机制进行处理？

Nginx 是一个高性能的 Web 服务器，能够同时处理大量的并发请求。它结合多进程机制和异步非阻塞机制 。

- 多进程机制：服务器每当收到一个客户端请求时，就有服务器主进程 （master process）生成一个子进程（worker process）和客户端建立连接进行交互，直到连接断开，该子进程就结束了。
    - 使用进程的好处是各个进程之间相互独立，不需要加锁，减少了使用锁对性能造成影响。
    - 其次，采用独立的进程，可以让进程互相之间不会影响 ，如果一个进程发生异常退出时，其它进程正常工作，master进程则很快启动新的worker进程，确保服务不会中断，从而将风险降到最低。
    - 缺点是操作系统生成一个子进程需要进行 内存复制等操作，在资源和时间上会产生一定的开销。当有大量请求时，会导致系统性能下降 。
- 异步非阻塞机制：每个工作进程使用异步非阻塞方式，可以处理多个客户端请求 。
    - 当某个工作进程接收到客户端请求以后，调用 IO 进行处理，如果不能立即得到结果，就去处理其他请求（即为非阻塞 ）。而客户端在此期间也无需等待响应，可以进行其他任务（即为 异步 ）。
    - 当IO返回时，就会通知此工作进程。该进程得到通知，暂时挂起当前处理的事务去响应客户端请求。

### 简述Nginx支持哪些类型的虚拟主机？

对于Nginx而言，每一个虚拟主机相当于一个在同一台服务器中却相互独立的站点，从而实现一台主机对外提供多个 web 服务，每个虚拟主机之间是独立的，互不影响的。通过 Nginx 可以实现虚拟主机的配置，Nginx 支持三种类型的虚拟主机配置：

- 基于 IP 的虚拟主机（较少使用）
- 基于域名的虚拟主机
- 基于端口的虚拟主机

### 简述Nginx缓存及其作用？

缓存对于Web至关重要，尤其对于大型高负载Web站点。Nginx缓存可作为性能优化的一个重要手段，可以极大减轻后端服务器的负载。通常对于静态资源，即较少经常更新的资源，如图片，css或js等进行缓存，从而在每次刷新浏览器的时候，不用重新请求，而是从缓存里面读取，这样就可以减轻服务器的压力。

### 简述Nginx作为代理缓存后，客户端访问的过程？

使用Nginx作为代理缓存后，可加快客户端的访问，其过程大致如下：

- 1、第一步：客户端第一次向Nginx请求数据A；
- 2、第二步：当Nginx发现缓存中没有数据A时，会向服务端请求数据A；
- 3、第三步：服务端接收到Nginx发来的请求，则返回数据A到Nginx，并且缓存在Nginx；
- 4、第四步：Nginx返回数据A给客户端应用；
- 5、第五步：客户端第二次向Nginx请求数据A；
- 6、第六步：当Nginx发现缓存中存在数据A时，则不会请求服务端；
- 7、第七步：Nginx把缓存中的数据A返回给客户端应用。

### 简述Nginx代理及其类型？

代理（forward）是一个位于客户端和原始服务器(origin server)之间的服务器，即代理服务器。为了从原始服务器取得内容，客户端向代理服务器发送一个请求并指定目标原始服务器，然后代理服务器向原始服务器转交请求并将获得的内容返回给客户端。
其通常有如下三种代理模式：

- 正向代理（forward proxy）：一个位于客户端和原始服务器(origin server)之间的服务器，为了从原始服务器取得内容，客户端向代理发送一个请求并指定目标(原始服务器)，然后代理向原始服务器转交请求并将获得的内容返回给客户端。
- 反向代理（reverse proxy）：指以代理服务器来接受 Internet上的连接请求，然后将请求，发给内部网络上的服务器并将从服务器上得到的结果返回给 Internet 上请求连接的客户端，此时代理服务器对外就表现为一个反向代理服务器。
- 透明代理

### 简述Nginx盗链及如何防护？

`盗链` 指的是在自己的界面展示非本服务器上的内容，通过技术手段获得其他服务器的资源。绕过他人资源展示页面，在自己页面向用户提供此内容，从而减轻自己服务器的负担，因为真实的空间和流量来自其他服务器。

因此，通常为了避免被盗链，通常Web服务器建议配置防盗链。Nginx防盗链其主要防盗链思路是能区别哪些请求是非正常用户请求，对于非正常用户的请求直接反馈403或重定向至其他页面。

### 简述Nginx负载均衡的意义？

负载均衡是将负载分摊到多个操作单元上执行，从而提高服务的可用性和响应速度，带给用户更好的体验。对于Web应用，通过负载均衡，可以将一台服务器的工作扩展到多台服务器中执行，提高整个网站的负载能力。其本质采用一个调度者，保证所有后端服务器都将性能充分发挥，从而保持服务器集群的整体性能最优，这就是负载均衡。

### 简述Nginx负载均衡的优势？

Nginx作为负载均衡器具有极大的优势，主要体现在：

- 高并发连接
- 内存消耗少
- 配置文件非常简单
- 成本低廉
- 支持Rewrite重写规则
- 内置的健康检查功能
- 节省带宽
- 稳定性高

### 简述Nginx负载均衡主要的均衡机制（策略）？

Nginx作为负载均衡器具有极大的优势，其负载均衡策略可以划分为两大类：内置策略和扩展策略，扩展策略为第三方提供。

- 内置策略
    - 轮询（默认）：Nginx根据请求次数，将每个请求均匀分配到每台服务器；
    - weight：加权轮询，加权轮询则是在第一种轮询的基础上对后台的每台服务赋予权重，服务器的权重比例越大，被分发到的概率也就越大。
    - least_conn：最少连接，将请求分配给连接数最少的服务器。Nginx会统计哪些服务器的连接数最少。
    - ip_hash：IP 哈希，绑定处理请求的服务器。第一次请求时，根据该客户端的IP算出一个HASH值，将请求分配到集群中的某一台服务器上。后面该客户端的所有请求，都将通过HASH算法，找到之前处理这台客户端请求的服务器，然后将请求交给它来处理。
- 扩展策略
    - fair：按后端服务器的响应时间来分配请求，响应时间短的优先分配。
    - url_hash：按访问url的hash结果来分配请求，使每个url定向到同一个后端服务器，后端服务器为缓存时比较有效。

### 简述Nginx负载均衡（反向代理）通过什么方式实现后端RS的健康检查？

nginx负载均衡（反向代理）包含内置的或第三方扩展来实现服务器健康检测的。如果后端某台服务器响应失败，nginx会标记该台服务器失效，在特定时间内，请求不分发到该台上。

- fail_timeout：该指令定义了多长时间服务器将被标记为失败。在fail_timeout后，服务器还是failed，nginx将检测该服务器是否存活，如果探测成功，将标记为活的。
- max_fails：该指令设置在fail_timeout期间内连续的失败尝试。默认情况下，max_fails为1。如果被设置为0，该服务器的健康检测将禁用。

### 简述Nginx动静分离？

为了提高网站的响应速度，减轻程序服务器（Tomcat，Jboss等）的负载，对于静态资源，如图片、js、css等文件，可以在反向代理服务器中进行缓存，这样浏览器在请求一个静态资源时，代理服务器就可以直接处理，而不用将请求转发给后端服务器。对于用户请求的动态文件，如servlet、jsp，则转发给Tomcat，Jboss服务器处理，这就是动静分离。即动态文件与静态文件的分离。

### 简述Nginx动静分离的原理？

动静分离可通过location对请求url进行匹配，将网站静态资源（HTML，JavaScript，CSS，img等文件）与后台应用分开部署，提高用户访问静态代码的速度，降低对后台应用访问。通常将静态资源放到nginx中，动态资源转发到tomcat服务器中。

### 简述Nginx同源策略？

同源策略是一个安全策略。同源，指的是协议，域名，端口相同。浏览器处于安全方面的考虑，只允许本域名下的接口交互，不同源的客户端脚本，在没有明确授权的情况下，不能读写对方的资源。

### 简述Nginx跨域及如何实现？

从一个域名的网页去请求另一个域名的资源，或任何协议、域名、端口有一处不同的请求，就被当作是跨域，即都被当成不同源。

通常基于安全考虑，Nginx启用了同源策略，即限制了从同一个源加载的文档或脚本如何与来自另一个源的资源进行交互。这是一个用于隔离潜在恶意文件的重要安全机制。

Nginx若要实现跨域访问，可通过JSONP和CORS进行实现。

### 简述Nginx重定向及其使用的场景？

重定向(Redirect)指通过各种方法将各种网络请求重新定个方向转到其它位置（如：网页重定向、域名的重定向、路由选择的变化也是对数据报文经由路径的一种重定向）。

URL重写是指通过配置conf文件，以让网站的URL中达到某种状态时则定向/跳转到某个规则，比如常见的伪静态、301重定向、浏览器定向等。当客户端浏览某个网址时，将其访问导向到另一个网址的技术。

其主要场景有如下两个：

- 将一串很长的网址，转成较短的网址，从而实现便于传播、易于记忆。
- 调整或更换Web服务器，网址（域名）又必须要变更（如访问目录、访问扩展名HTML变为PHP、访问域名），为了能使旧的访问依旧生效，从而实现自动重定向到新的网站。

### 简述Nginx地址重写、地址转发、反向代理？

- `地址重写`：为了实现地址的标准化，如地址栏中中输入 www.baidu.com. 也可以输入 www.baidu.cn。最后都会被重写到 www.baidu.com 上。浏览器的地址栏也会显示www.baidu.com。即nginx把收到客户端请求的内容所对应的服务器地址发给客户端，让客户端自己去获取，nginx同时返回302正确信息。
- `地址转发`：指在网络数据传输过程中数据分组到达路由器或桥接器后，该设备通过检查分组地址并将数据转发到最近的局域网的过程。
- `反向代理`：当浏览器访问网站时，nginx反向代理服务器会代替客户端向后端服务器查找所需的内容，然后nginx反向代理服务器会把查找的内容返回给客户端。

### 简述Nginx地址重写和地址转发的差异？

地址重写和地址转发有以下不同点：

- 地址重写会改变浏览器中的地址，使之变成重写成浏览器最新的地址。而地址转发不会改变浏览器的地址的。
- 地址重写会产生两次请求，而地址转发只会有一次请求。
- 地址转发一般发生在同一站点项目内部，而地址重写且不受限制。
- 地址转发的速度比地址重定向快。

### 简述Nginx 301和302重定向及其区别？

301和302状态码都表示重定向，表示浏览器在拿到服务器返回的这个状态码后会自动跳转到一个新的URL地址，这个地址可以从响应的Location首部中获取（客户端输入的地址A瞬间变成了另一个地址B）。其主要差异为：

- 301：代表永久性转移(Permanently Moved)：旧地址A的资源已经被永久地移除了（这个资源不可访问了），搜索引擎在抓取新内容的同时也将旧的网址交换为重定向之后的网址；
- 302：代表暂时性转移(Temporarily Moved)：旧地址A的资源还在（仍然可以访问），这个重定向只是临时地从旧地址A跳转到地址B，搜索引擎会抓取新的内容而保存旧的网址。

### 简述Nginx高可用的常见方案？

Keepalived + Nginx 实现Nginx的高可用：通过Keepalived来实现同一个虚拟IP映射到多台Nginx代理服务器，从而实现Nginx的高可用性。

Heartbeat + Nginx 实现Nginx的高可用：通过Heartbeat的心跳检测和资源接管、集群中服务的监测、失效切换等功能，结合Nginx来实现高可用性。

### 简述SSL和HTTPS？

`SSL`（Secure Socket Layer）安全套接字层是一种数字证书，它使用ssl协议在浏览器和web server之间建立一条安全通道，数据信息在client与server之间的安全传输。

`HTTPS`（Hypertext Transfer Protocol Secure）是超文本传输协议和SSL/TLS的组合，用以提供加密通讯及对网络服务器身份的鉴定。

HTTPS也可以理解为HTTP over SSL，即HTTP连接建立在SSL安全连接之上。

> - 作者：木二
> - 链接：https://www.yuque.com/docs/share/d3dd1e8e-6828-4da7-9e30-6a4f45c6fa8e