# Container Technology

## Docker介绍

[Docker Wikipedia](https://en.wiki2.org/wiki/Docker_(software))

Docker is an open-source project that automates the deployment of applications inside software containers, by providing an additional layer of abstraction and automation of operating-system-level virtualization on Linux. Docker uses resource isolation features of the Linux kernel such as cgroups and kernel namespaces to allow independent "containers" to run within a single Linux instance, avoiding the overhead of starting and maintaining virtual machines.

The Linux kernel's support for namespaces mostly isolates an application's view of the operating environment, including process trees, network, user IDs and mounted file systems, while the kernel's cgroups provide resource isolation, including the CPU, memory, block I/O and network. Since version 0.9, Docker includes the libcontainer library as its own way to directly use virtualization facilities provided by the Linux kernel, in addition to using abstracted virtualization interfaces via libvirt, LXC (Linux Containers) and systemd-nspawn.

According to industry analyst firm 451 Research, "Docker is a tool that can package an application and its dependencies in a virtual container that can run on any Linux server. This helps enable flexibility and portability on where the application can run, whether on premise [sic], public cloud, private cloud, bare metal, etc."

### How is this different from virtual machines?

Each virtual machine includes the application, the necessary binaries and libraries and an entire guest operating system - all of which may be tens of GBs in size.

Containers include the application and all of its dependencies, but share the kernel with other containers. They run as an isolated process in userspace on the host operating system. They’re also not tied to any specific infrastructure – Docker containers run on any computer, on any infrastructure and in any cloud.

![](./img/2015/07/container-vs-vm.jpg)

### Docker's Architecture

参考：[https://docs.docker.com/introduction/understanding-docker/](https://docs.docker.com/introduction/understanding-docker/)

Docker uses a client-server architecture. The Docker client talks to the Docker daemon, which does the heavy lifting of building, running, and distributing your Docker containers. Both the Docker client and the daemon can run on the same system, or you can connect a Docker client to a remote Docker daemon. The Docker client and daemon communicate via sockets or through a RESTful API.

![](./img/2015/07/architecture.svg)

## LXC, LXD, LXCFS and CGManager

[Linux Containers](https://linuxcontainers.org/)

linuxcontainers.org is the umbrella project behind LXC, LXD, LXCFS and CGManager.

The goal is to offer a distro and vendor neutral environment for the development of Linux container technologies.

## CoreOS rkt

[rkt](https://coreos.com/rkt/)

rkt is the next-generation container manager for Linux clusters. Designed for security, simplicity, and composability within modern cluster architectures, rkt discovers, verifies, fetches, and executes application containers with pluggable isolation. rkt can run the same container with varying degrees of protection, from lightweight, OS-level namespace and capabilities isolation to heavier, VM-level hardware virtualization.

rkt’s primary interface comprises a single executable, rather than a background daemon, and rkt leverages this design to easily integrate with existing init systems, like systemd, and with advanced cluster orchestration environments, like Kubernetes. rkt implements a modern, open, standard container format, the App Container (appc), but can also execute other container images, like those created with Docker.

# Docs & Books

- [Get Started with Docker for Linux](http://docs.docker.com/linux/started/)
- [Get Started with Docker for Mac OS X](http://docs.docker.com/mac/started/): 需要安装boot2docker，boot2docker会安装VirtualBox、Docker、Boot2Docker management tool
- [Get Started with Docker for Windows](http://docs.docker.com/windows/started/): 需要安装boot2docker，boot2docker会安装VirtualBox、Docker、Boot2Docker management tool
- [Docker Docs](https://docs.docker.com/)
- [The Docker Book](http://book.douban.com/subject/26285268/)
- [Docker Up and Running](http://www.amazon.com/Docker-Up-Running-Karl-Matthias/dp/1491917571/ref=sr_1_1?ie=UTF8&qid=1437978051&sr=8-1&keywords=docker)
- [shipyard中文文档](http://dockerpool.com/static/books/shipyard_doc/index.html)
- [Docker Cheat Sheet](https://github.com/wsargent/docker-cheat-sheet/)

# Resources

网站：

- [Docker Hub](https://hub.docker.com/)
- [DaoCloud技术Blog](http://blog.daocloud.io/)
- [灵雀云Blog](http://www.alauda.cn/blog/)
- [UnitedStack技术分享](https://www.ustack.com/skill-share/)

社区：

- [DockOne](http://dockone.io/)

容器类产品：

- [灵雀云](http://www.alauda.cn/)
- [DaoCloud](http://www.daocloud.io/)
- [希云cSphere](https://csphere.cn/): 企业级Docker管理平台

公有云类产品：

- [阿里云](http://www.aliyun.com/)
- [Window Azure CN](http://www.windowsazure.cn/)
- [UnitedStack](https://www.ustack.com/)
- [青云](https://www.qingcloud.com/)
- [时速云](https://www.tenxcloud.com/)

# Projects

## Container

- [Docker Engine](https://www.docker.com/): An open platform for distributed applications for developers and sysadmins
    - [docker kitematic](https://kitematic.com/): Kitematic is the fastest and easiest way to start using Docker on your laptop. A completely automated process installs and configures the Docker environment on your machine in just minutes. Build and run containers through a simple, yet powerful graphical user interface (GUI).
    - [docker registry](https://www.docker.com/docker-registry): [源代码](https://github.com/docker/distribution), Docker Registry is an open source application dedicated to the storage and distribution of your Docker images. Its seamless architecture allows both for fine grain integration with other systems and high-level scalability. Aggressively developed, its vibrant community includes industry leaders and users using it at the core of their images distribution solutions.
    - [docker machine](https://www.docker.com/docker-machine): To get started with Docker, first you need to setup a Docker Engine. Docker Machine automatically sets up Docker on your computer, on cloud providers, and inside your data center. Docker Machine provisions the hosts, installs Docker Engine on them, and then configures the Docker client to talk to the Docker Engines.
    - [docker compose](https://www.docker.com/docker-compose): Distributed applications consist of many small applications that work together. Docker transforms these applications into individual containers that are linked together. Instead of having to build, run and manage each individual container, Docker Compose allows you to define your multi-container application with all of its dependencies in a single file, then spin your application up in a single command. Your application’s structure and configuration are held in a single place, which makes spinning up applications simple and repeatable everywhere.
    - [docker swarm](https://www.docker.com/docker-swarm): The nature of distributed applications requires compute resources that are also distributed. Docker Swarm provides native clustering capabilities to turn a group of Docker engines into a single, virtual Docker Engine. With these pooled resources, you can scale out your application as if it were running on a single, huge computer.

## Docker Network

- [flannel](https://github.com/coreos/flannel): flannel is a virtual network that gives a subnet to each host for use with container runtimes. Platforms like Google's Kubernetes assume that each container (pod) has a unique, routable IP inside the cluster. The advantage of this model is that it reduces the complexity of doing port mapping.
- [Weave](https://github.com/weaveworks/weave): Weave creates a virtual network that connects Docker containers deployed across multiple hosts and enables their automatic discovery.
- [Pipework](https://github.com/jpetazzo/pipework): Software-Defined Networking for Linux Containers. Pipework lets you connect together containers in arbitrarily complex scenarios. Pipework uses cgroups and namespace and works with "plain" LXC containers (created with lxc-start), and with the awesome Docker.

## Configuration Management

- [Registrator](https://github.com/gliderlabs/registrator): Service registry bridge for Docker with pluggable adapters

## Docker Host OS

- [CoreOS](https://coreos.com/): CoreOS produces, maintains and utilizes open source software for Linux containers and distributed systems. Projects are designed to be composable and complement each other in order to run container-ready infrastructure.
- [boot2docker](http://boot2docker.io/): boot2docker is a lightweight Linux distribution based on Tiny Core Linux made specifically to run Docker containers. It runs completely from RAM, weighs ~27MB and boots in ~5s (YMMV).
- [Atomic](http://www.projectatomic.io/): Atomic是Red Hat公司发起的以应用为中心的操作系统，它可以更方便地部署和管理你的Docker容器。Atomic基于成熟的底层操作系统，保证容器运行环境的安全，并且集成了Kubernetes、Systemd等管理工具，提供容器应用部署的全套解决方案。与传统操作系统不同，Atomic经过裁剪后体积更小更容易维护，并且集成了SELinux安全技术，让Docker容器有更好的安全隔离，还有Gockpit等工具让容器的部署和管理更加方便。
- [Ubuntu Core](http://ubuntu.com.cn/cloud/tools/snappy): Ubuntu Core is a new rendition of Ubuntu for the cloud with transactional updates. Ubuntu Core is a minimal server image with the same libraries as today’s Ubuntu, but applications are provided through a simpler mechanism. The snappy approach is faster, more reliable, and lets us provide stronger security guarantees for apps and users — that’s why we call them “snappy” applications.

## Container Management

- [kubernetes](http://kubernetes.io/): Manage a cluster of Linux containers as a single system to accelerate Dev and simplify Ops.
    - [kube-ui](https://github.com/kubernetes/kube-ui): Container Cluster Manager from Google Web UI. 介绍见[这里](http://kubernetes.io/v1.0/docs/user-guide/ui.html).
    - [Kubernetes API client libraries](http://kubernetes.io/v1.0/docs/devel/client-libraries.html): 文档见[这里](https://godoc.org/github.com/kubernetes/kubernetes/pkg/client)

## Monitor

- [cAdvisor](https://github.com/google/cadvisor): Analyzes resource usage and performance characteristics of running containers.
- [heapster](https://github.com/kubernetes/heapster): Compute Resource Usage Analysis and Monitoring of Container Clusters

## Data Volume Management

- [ClusterHQ Flocker](https://github.com/ClusterHQ/flocker): Flocker is an open-source Container Data Volume Manager for your Dockerized applications.

## Image Build

- [dockramp](https://github.com/jlhawn/dockramp): Docker 1.8.0 will introduce a new API endpoint for copying files and directories into a container. With this addition, anyone can now implement their own build system using the Docker Remote API. Dockramp is the first proof of concept for an alternative to docker build.
- [packer](https://packer.io/): Packer is a tool for creating machine and container images for multiple platforms from a single source configuration.

## Continous Integration

- [Drone](https://github.com/drone/drone): Drone是一个使用Go语言编写的基于Docker的持续集成系统。Drone可以快速提供隔离的虚拟环境编译测试，而且根据需要保留结果，比使用VM更加简洁有效。如何使用 Drone和Docker搭建全功能的CI服务器可以参考此文。使用Drone搭建CI服务器后，代码可以不离开公司网络即可测试，这非常适合大公司的保密原则，另外，由于Drone基于Docker使用，所以部署到生产环境也非常容易。

## Continuous Delivery

- [wharf](https://github.com/containerops/wharf): ContainerOps is all about product workflow. Wharf builds and runs a container image you defined whenever new code is being pushed, along with corresponding dependence system. But it's not all, the image will also work with continuous integration, or continuous deployment with Rocket, LXC or Atomic, etc. Wharf is focusing on the continuous changes from version control system to production environment.

## Visualization

- [dockviz](https://github.com/justone/dockviz): Visualizing docker data

## Developer Tools

- [Vagrant](https://www.vagrantup.com/): Vagrant 是一个基于 Ruby 的工具，用于创建和部署虚拟化开发环境。它使用 Oracle 的开源 VirtualBox 虚拟化系统，使用 Chef 创建自动化虚拟环境。
- [Panamax](http://panamax.io/): Panamax是一个CenturyLink开源的Docker管理工具，用户可以把多个Docker容器组合为模板并分享到GitHub。Panamax中的应用是由基于Docker镜像的独立服务组合而成，这些Docker镜像来自Docker Hub或者其它的Docker registry。Web的用户界面允许每个服务可以连接到其他服务，并可以配置环境变量、端口绑定、卷。另外也可以添加自定义的Docker运行命令。当这些服务组合在一起成为一个具备完整功能的应用后就可以作为一个模板保存到GitHub。Panamax的最初版本运行在由Vagrant管理的VirtualBox上，由于Vagrant的限制，目前Panamax仅可运行在Mac和Linux的VirtualBox上，并不支持其他虚拟化平台。CenturyLink的云平台也将会支持Panamax。

## PaaS

- [Flynn](https://flynn.io/): Flynn是一个使用Go语言编写的开源PaaS平台，Flynn使用模块化的设计，任何一个模块都可以独立的进行修改、升级和替换。Flynn的目标是简化分布式环境中应用的部署和维护，通过使用git push命令，Flynn就可以将应用部署到Docker，从而省去了复杂的配置和操作。Flynn的架构大致分为两层，Layer 0是底层的资源层，提供分布式配置、任务调度、服务发现、主机隔离等基础功能；Layer 1基于Layer 0构建了一个用于集群中管理、部署、扩展服务的系统，主要包括管理API/客户端、Git接收器、数据存储、路由。Flynn目前仍在开发中，尚未发布稳定版，但已经获得了很多公司的资助，它被称为是下一代的开源PaaS平台。
- [Deis](http://deis.io/): Deis也是一个支持共有云和私有云的开源PaaS系统，Deis基于Docker和CentOS构建了一个类Heroku的PaaS系统。Deis主要设计用来和不同的云提供商进行交互，目前支持 Rackspace、EC2、 DigitalOcean、Google Compute Engine、Bare-Metal。Deis使用out-of-the-box的方式支持Ruby、Python、Node.js、Java、Clojure、Scala、Play、PHP、Perl、Dart和Go语言，同样支持git push部署。Flynn和Deis都是两个基于Docker的云计算微PaaS技术，关于它们的区别，可以参考这篇文章，作者从架构、实现方式等多方面对二者进行了比较，Deis目前也尚未发布1.0版本，但在GitHub上已经有2000+的star量。
- [Dokku](https://github.com/progrium/dokku): Dokku是一个迷你版的Heroku，基于Docker使用100行左右的Bash代码编写，简单的安装和配置后，即可使用Git命令将应用部署到本地的Dokku平台（当使用git push命令的时候，Dokku会使用buildpack检测应用，然后再部署）。Dokku实际上相当于一个单机版的Heroku，它包含4个组件，分别是Docker、Buildstep、pluginhook、sshcommand。Dokku目前支持Node.js、Ruby、Python。
- [OpenShift Origin](http://www.openshift.org/): OpenShift 3 is built around a core of application containers powered by Docker, with orchestration and management provided by Kubernetes, on a foundation of Atomic and Enterprise Linux. OpenShift Origin is the upstream community project that brings it all together along with extensions, to accelerate application development and deployment.

## IaaS

- [OpenStack](http://www.openstack.org/): Open source software for creating private and public clouds.
- [Apache CloudStack](http://cloudstack.apache.org/): Apache CloudStack is open source software designed to deploy and manage large networks of virtual machines, as a highly available, highly scalable Infrastructure as a Service (IaaS) cloud computing platform. CloudStack is used by a number of service providers to offer public cloud services, and by many companies to provide an on-premises (private) cloud offering, or as part of a hybrid cloud solution.
- [Zstack](http://zstack.org/cn/): ZStack是下一代开源的云计算IaaS（基础架构即服务）软件。它主要面向的是未来的智能数据中心， 通过提供全完善的APIs来管理包括计算、存储和网络在内的数据中心的各种资源。 用户可以基于ZStack构建自己的智能数据中心，也可以在稳定的ZStack之上搭建灵活的云应用场景， 例如VDI（虚拟桌面基础架构），PaaS（平台即服务），SaaS（软件即服务）等等。

## Virtual Machine OS

- [Clear Linux](https://clearlinux.org/): The Clear Linux* Project for Intel® Architecture is a project that is building a Linux OS distribution for various cloud use cases. The goal of Clear Linux OS is to showcase the best of Intel Architecture technology, from low-level kernel features to more complex items that span across the entire operating system stack.

## Virtual Machine Host

- [Xen](http://www.xenproject.org/): Xen 是一个开放源代码虚拟机监视器，由剑桥大学开发。它打算在单个计算机上运行多达100个满特征的操作系统。操作系统必须进行显式地修改（“移植”）以在Xen上运行（但是提供对用户应用的兼容性）。这使得Xen无需特殊硬件支持，就能达到高性能的虚拟化。
- [XenServer](http://xenserver.org/): XenServer is the leading open source virtualization platform, powered by the Xen Project hypervisor and the XAPI toolstack. It is used in the world's largest clouds and enterprises.
- [Kernel Virtual Machine](http://www.linux-kvm.org/page/Main_Page): KVM (for Kernel-based Virtual Machine) is a full virtualization solution for Linux on x86 hardware containing virtualization extensions (Intel VT or AMD-V). It consists of a loadable kernel module, kvm.ko, that provides the core virtualization infrastructure and a processor specific module, kvm-intel.ko or kvm-amd.ko.
- [Hyper](https://hyper.sh/): Hyper 是一种 App-Centric 的虚拟化技术，我们完全摒弃了传统虚机上必须和物理机一样，运行一个完整 OS 这种看似显然的假设，我们让Docker Image 直接运行在 Hypervisor 上。我们让一组容器直接启动在 hypervisor 上的时间达到 350 毫秒，并且还在进一步优化。而且所有这些，都是“开箱即得的”。当然有人会问，有了容器为什么还要虚机。诚然，虚机并不是所有人都需要的，但是，虚机天然具备更好的隔离性；虚拟机也仍然存在于很多企业应用的协议栈中，这样一个依赖更少、开箱即得，而且还带有 Pod、persist mode 等附加丰富特性的应用，是不少场景中都需要的。而我们最期待的，就是去引爆新的容器服务 —— CaaS。.传统虚拟机的问题其实在于过于刻意模仿物理机，刻意要承载完整操作系统，启动一台虚拟机要若干秒，甚至几分钟，Image 有若干GB，加载传播都很慢，但其实根本没有这个必要，Hyper希望兼取两者的强项
- [OpenVZ](http://openvz.org/Main_Page): OpenVZ is container-based virtualization for Linux. OpenVZ creates multiple secure, isolated Linux containers (otherwise known as VEs or VPSs) on a single physical server enabling better server utilization and ensuring that applications do not conflict. Each container performs and executes exactly like a stand-alone server; a container can be rebooted independently and have root access, users, IP addresses, memory, processes, files, applications, system libraries and configuration files.

## Network Virtualization

- [Open vSwitch](http://openvswitch.org/): Open vSwitch is a production quality, multilayer virtual switch licensed under the open source Apache 2.0 license.  It is designed to enable massive network automation through programmatic extension, while still supporting standard management interfaces and protocols (e.g. NetFlow, sFlow, IPFIX, RSPAN, CLI, LACP, 802.1ag).  In addition, it is designed to support distribution across multiple physical servers similar to VMware's vNetwork distributed vswitch or Cisco's Nexus 1000V.
- [Data Plane Development Kit](http://www.dpdk.org/): DPDK is a set of libraries and drivers for fast packet processing. It was designed to run on any processors. The first supported CPU was Intel x86 and it is now extended to IBM Power 8, EZchip TILE-Gx and ARM. It runs mostly in Linux userland. A FreeBSD port is available for a subset of DPDK features.
- [Open Networking Foundation](https://www.opennetworking.org/index.php): Foundation about SDN and Open Flow

## Docker on OSX

- [Dlite](https://github.com/nlf/dlite): The simplest way to use Docker on OSX.

# FAQ

## How to install and uninstall Docker in Ubuntu

```sh
# install docker
$ curl -fsSL https://get.docker.com/ | sh

# Uninstall docker and it's dependencies
$ sudo apt-get remove --auto-remove docker

# Purging docker, config/data and it's dependencies
$ sudo apt-get purge --auto-remove docker-engine

# restart to start docker server
$ sudo shutdown -r 0
```

## Use docker hub mirror to speed up download docker image

```sh
$ echo "DOCKER_OPTS=\"\$DOCKER_OPTS --registry-mirror=http://6de9fa0c.m.daocloud.io\"" | sudo tee -a /etc/default/docker
$ sudo service docker restart
```

Refer to:

- [DaoCloud 加速器和 Toolbox](http://docs.daocloud.io/faq/what-is-daocloud-accelerator)


## How to make docker daemon accept connections incoming from any network interface

参考[Docker client communicating with docker host](http://stackoverflow.com/questions/26481258/docker-client-communicating-with-docker-host)

Using the -H tcp://127.0.0.1:5555 docker daemon option on the UbuntuA machine will instruct docker to bind to the loopback network interface (127.0.0.1). As a result it will only accept connections originating from the UbuntuA machine.

If you want to accept connections incoming from any network interface use -H tcp://0.0.0.0:5555. Be aware that anyone that would be able to connect to your UbuntuA machine on port 5555 will be able to control your docker host. You need to protect it with firewall rules to allow only UbuntuB to connect to UbuntuA on port 5555.

## 在Mac OS X中，启动VirutalBox VM中的mongodb容器，挂载Mac OS X本地数据卷，启动mongod报“fsync: Invalid argument”的错误

参考：

- ["Fatal Assertion" with "fsync: Invalid Argument"](https://github.com/mvertes/docker-alpine-mongo/issues/1)
- [can not use external volume](https://github.com/docker-library/mongo/issues/30)
- [OFFICIAL REPOSITORY - mongo](https://hub.docker.com/_/mongo/)
- [How to set docker mongo data volume](http://stackoverflow.com/questions/35400740/how-to-set-docker-mongo-data-volume)

WARNING: because MongoDB uses memory mapped files it is not possible to use it through vboxsf to your host (vbox bug). VirtualBox shared folders are not supported by MongoDB (see docs.mongodb.org and related jira.mongodb.org bug). This means that it is not possible with the default setup using Docker Toolbox to run a MongoDB container with the data directory mapped to the host.
