Containerization with Docker
==


Introduction
--

### What is Containerization?

>A standardized unit of software which Package Software into Standardized Units for Development, Shipment and Deployment (ref:[docker][ref.5])

A container is a standard unit of software that packages up code and all its dependencies, so the application runs quickly and reliably from one computing environment to another. A Docker container image is a lightweight, standalone, executable package of software that includes everything needed to run an application: code, runtime, system tools, system libraries and settings.


### What is Docker?

>Docker is a container management service with the concept of develop, ship and run anywhere. The whole idea of Docker is for developers to easily develop applications, ship them into containers that can then be deployed anywhere.

![docker containerization][img.11]

Docker has a concept of docker images that become containers at runtime and in the case of Docker containers - images become containers when they run on Docker Engine. Available for both Linux and Windows-based applications, containerized software will always run the same, regardless of the infrastructure. Containers isolate software from its environment and ensure that it works uniformly despite differences for instance between development and staging.

Docker containers that run on Docker Engine:

- **Standard:** Docker created the industry standard for containers, so they could be portable anywhere
- **Lightweight:** Containers share the machine’s OS system kernel and therefore do not require an OS per application, driving higher server efficiencies and reducing server and licensing costs
- **Secure:** Applications are safer in containers and Docker provides the strongest default isolation capabilities in the industry

Docker is not the only available containerization tool in the market. Let's take at other tools and the evolvement of containerization technology.

History of containerization
--
Below is a summary of container history extracted from Wikipedia and other sources:

Back in 1960 Computers were very rare. At that time computers were typically assigned to a dedicated task which might take a very long time. Then multiple terminals connected to a single server. The Advantage over here was if terminals got a breakdown, the user simply goes to another terminal and can do the work and get access to the same filesystem. But what if the main central server goes down. This was the root cause which gave an idea that not only computers but also system processes should be separated individually.


### 1979 \- chroot
  
It all started with the release of Unix V7 where they introduced the concept of chroot jail. With chroot command, it was possible to change the apparent root directory for the running process, along with all the children and visible only to the running process. The idea here is to provide an isolation feature for each process. Later in 1982 BSD adopted this feature.

In the 1990s Bill Cheswick, a computer security and networking researcher was on some security research project for crackers and the result of this gave birth to the Linux jail command.

![chroot][img.1]

### 2000 \- FreeBSD Jails
After two decay's later, FreeBSD included the jail command intended to add more security on chroot command which was just giving isolation features. It also added process sandboxing features for isolating the filesystem, users, networking, etc. This means you can assign individual  IP to each jail, custom configuration, software installation, etc.

<!-- ![freebsd][img.2] -->

### 2001 \- Linux VServer  
OS level virtualization feature added with the release of Linux VServer which used both chroot with security contexts and  os level virtualization and advanced enough to run multiple Linux distros on single distribution.
jail is used to partition resources on a computer system (file system, CPU time, network addresses and memory) which is known as a security context, and the virtualized system within is a virtual private server.

![linuxvserver][img.3]

### 2004 \- Solaris Containers
In 2004, Sun (later acquired by Oracle) released Solaris Containers which combined system resource controls and the boundary separation provided by zones. Zones act as completely isolated virtual servers within a single OS instance.

<!-- ![solaris][img.4] -->

### 2005 \- OpenVZ (Open Virtuzzo)
OpenVZ is similar to Solaris Containers and uses a patched Linux kernel for virtualization, isolation, resource management, and checkpointing. In OS-level virtualization, containers share the same architecture and kernel version so situations, where guests require different kernel versions than that of the host, are limitations. Linux-VServer and OpenVZ require patching the kernel to add some control mechanisms. OpenVZ patches were not integrated into the Kernel.

<!-- ![OpenVZ][img.5] -->

<!-- <center>
![OpenVZ][img.5]
</center>

<div style="text-align: center" markdown="1">
![OpenVZ][img.5]
</div> -->

### 2006 \- Process Containers
In the year 2006, Google announced the implementation of Process Containers for limiting, accounting, and isolating resource usage for processes collection. 

### 2007 \- Control Groups
Process Containers was renamed to Control Groups to avoid the confusion multiple meanings of the term “container” in the Linux kernel context and merged to the Linux kernel 2.6.24. 

### 2008 \- LXC (Linux Container)
LXC was the first, most complete implementation of Linux container manager. It was implemented using cgroups and Linux namespaces, and it works on a single Linux kernel without requiring any patches. 

![LXC][img.6]
<!-- LXC was delivered in liblxc library and provided language bindings for the API in Python3, Python2, Lua, Go, Ruby, and Haskell. Contrast to other container technologies LXC works on vanila Linux kernel without requiring any patches. Today LXC project is sponsored by Canonical Ltd. and hosted here. -->

### 2011 \- Warden
CloudFoundry implemented warden in 2011, using LXC at the initial stage and later replacing it with its own implementation. Unlike LXC, Warden is not tightly coupled to Linux. In other words, it can isolate environments on any OS that can provide ways of isolating environments, running as a daemon and provides an API for container management. It developed a client-server model to manage a collection of containers across multiple hosts, and Warden includes a service to manage cgroups, namespaces and the process life cycle.

<!-- ![Warden][img.7] -->


### 2013 \- LMCTFY (Let Me Contain That For You)  
It is the open-source version of Google’s container stack, which provides Linux application containers. Here apps can be made "container aware" by creating and managing their own sub-containers. In the year 2015 Google started to contribute core lmctfy concepts and abstractions to libcontainer. As a result, now no active development is done in LMCTFY.

The libcontainer project was initially started by Docker and now it has been moved to Open Container Foundation.

### 2013 \- Docker
It was developed as an internal project at a PaaS company called dotCloud and later renamed to Docker. In its initial stages, Docker used LXC and later replaced that container manager with its own library, libcontainer. It offers an entire ecosystem for container management which make it unique. Docker initializes container cluster management solution called Docker Swarm.

<!-- ![Docker][img.8] -->


### 2014 \- Rocket  
It's similar initiative to Docker started by CoreOS to fix some of the drawbacks of Docker. It is implemented on App Container specifications to be a more open standard. In addition to Rocket, CoreOS also develops several other container related products used by Docker and Kubernetes: CoreOS Operating System, etcd, and flannel.

![Rocket][img.9]

### 2016 \- Windows Containers
Microsoft also jumped into this to add container support to the Microsoft Windows Server OS in 2015 for Windows-based applications, called Windows Containers. With this Docker would be able to run Docker containers on Windows natively without having to run a virtual machine to run Docker (earlier Docker ran on Windows using a Linux VM).


The Future of Containers
--
As of today, there is a significant trend in the industry to move towards containers from VMs for deploying software applications. The main reasons for this are the flexibility and low cost that containers provide compared to VMs. 

[More than 2 billion containers][ref.12] are running on Google infrastructure every week. Microsoft has also implemented native support for containers on Windows Server means os level virtualization.

If the host fails, all the containers that run on that host will also fail. To avoid this, a container host cluster needs to be used. Google developed an open-source container cluster management system called Kubernetes. Docker has a docker swarm. We will briefly discuss these in the future post.

<!-- One of the first most open source container cluster management platforms to solve this problem was Apache Mesos. It was initially developed at University of California, Berkeley as a research project and later moved to Apache in around year 2012. Google took a similar step to implement a cutting edge, open source container cluster management system called Kubernetes in year 2014 with the experience they got from Borg. Docker also started a solution called Docker Swarm in year 2015. Today these solutions are at their very early stages and it may take several months and may be another year to complete their full feature set, become stable and widely used in the industry in production environments. -->

From the SOA level, Microservices are another technology that uses containers for their deployment. It's nothing new but a lightweight implementation of a web service that can start extremely fast compared to a standard web service.

By considering the above facts we can predict that in the next few years, containers may take over virtual machines, and sometimes might replace them completely.

Summary
--
As we discussed above, containerization is a technology, which allows us to create a separate standardized unit of software that can be packaged to use for development, shipment and deployment. This type of environment supports microservice architecture if we can properly orchestrate it. Currently, docker is the equivalent word for containerization. But as we saw docker is not the only tool for that and we also saw the history of the evolvement of this technology and future. 

In the future article, we will take a deep look at the types of containerization techniques and how it's different from virtualizations.







<!-- reference links -->

<!-- [1]: https://dzone.com/articles/evolution-of-linux-containers-future -->

<!-- [2]: https://medium.com/faun/the-missing-introduction-to-containerization-de1fbb73efc5 -->

<!-- [3]: https://blog.aquasec.com/a-brief-history-of-containers-from-1970s-chroot-to-docker-2016 -->

<!-- [4]: https://linuxacademy.com/blog/containers/history-of-container-technology/ -->

[ref.5]: https://www.docker.com/resources/what-container

[ref.12]: https://speakerdeck.com/jbeda/containers-at-scale

<!-- reference images -->

[img.1]: https://drive.google.com/uc?export=view&id=11hPcQyAYwx368hAz4QVDSgksqZBGzpJj "Chroot Jail"

<!-- [img.2]: https://blog.aquasec.com/hs-fs/hubfs/BSD.jpg?width=150&name=BSD.jpg "FreeBSD" -->

[img.3]: https://drive.google.com/uc?export=view&id=1r3lSyd8urPJQxy4p7fqxBJcmWWtyRRyO "Linux VServer"

<!-- [img.4]: https://miro.medium.com/max/880/0*hB4RZW-bDUp8Y5vn "Solaris Containers" -->

<!-- [img.5]: https://miro.medium.com/max/312/0*uOQ2Hw4g57cCffs_.png "OpenVZ" -->

[img.6]: https://drive.google.com/uc?export=view&id=1a6-OZKTT0zBLl2EeT9AstykdUH6P8Dzh "LXC"

<!-- [img.7]: https://blog.aquasec.com/hs-fs/hubfs/CF2.jpg?width=150&name=CF2.jpg "Warden" -->

<!-- [img.8]: https://blog.aquasec.com/hs-fs/hubfs/Blog/history%20of%20containers/docker.png?width=150&name=docker.png "Docker" -->

[img.9]: https://drive.google.com/uc?export=view&id=1Ppz0UqJ49QrgD8Whwsaz4eovJZwSiITb "Rocket (rkt)"


[img.11]: https://www.docker.com/sites/default/files/d8/styles/large/public/2018-11/container-what-is-container.png?itok=vle7kjDj "container architechture"
