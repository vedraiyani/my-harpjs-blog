Containerization with Docker : Part 2
==

In the previous article, we briefly discussed what containerization and docker are and also discussed how it's evolved with time. In this article, we will mainly discuss the relation between containerization and virtualization, its type and why containers are powerful over virtual machines.  


## [**Virtualization and Containerization**][ref.5]


>Virtualization is the process of running a virtual instance of a computer system in a layer abstracted from the actual hardware. Most commonly, it refers to running multiple operating systems on a computer system simultaneously. ... There are many reasons why people utilize virtualization in computing. ref: [opensource][ref.13]

In virtualization, guest os runs on the top of the hypervisor which is on host os while in containerization, it shares the kernel of the host os itself using container engine and it doesn't have dedicated os so it doesn't take much time to be loaded. Containerization is also a type of virtualization let's discuss this briefly with the types of virtualization below.

#### [Types of virtualizations:](#typevirt)
1. **Full Virtualization**  
   Full virtualization is a virtualization technique used to provide a VME that completely simulates the underlying hardware. In this type of environment, any software capable of execution on the physical hardware can be run in the VM, and any OS supported by the underlying hardware can be run in each VM individually.  
   ref\: [sciencedirect][ref.6], [geeksforgeeks][ref.7]

   ![vm][img.12]
  
2. **Para Virtualization**  
   In computing, para-virtualization is a virtualization technique that presents a software interface to the virtual machines which are similar, yet not identical to the underlying hardware\-software interface.  
   ref\: [wiki][ref.8], [sciencedirect][ref.9]

3. [**OS Level Virtualization**](#osvirt)
   The OS Level virtualization is also called containerization. It's a server virtualization technology that involves altering an operating system making it possible to run different applications that can be operated by different users working on a single computer at one time. Technologies like Linux-VServer and OpenVZ can run multiple operating systems while sharing the same architecture and kernel version.  
   ref\: [wiki][ref.10], [geeksforgeeks][ref.11]

![Virtualization][img.10] 

<!-- "source: https://fntlnz.wtf/post/why-containers" -->

System containers (e.g LXC) offer an environment as close as possible as the one you’d get from a VM but without the overhead that comes with running a separate kernel and simulating all the hardware. 



## [Types of Containers](#typecont)

We have two types of containers here:
1. **OS Containers**   
   In this type of containers, OS with the whole application stack is packaged. It runs multiple services in the same container and uses the native resource isolation.
2. **Applications Containers**   
   It usually runs a single process per container and built on top of OS container.
  
For [example](#example) if we take an example if we deploy LEMP on OS it will be deployed as a whole app stack with os. In the case of App Containers, we would create individual containers for each of the services as given below:
1. PHP server.
2. Webserver (Nginx).
3. Mysql.

![os container][img.13] ![app container][img.14]


[Why Containers?][ref.14] [](#diffvmcont)
--

[As we saw above containers virtualize at the OS level](#osvirt), with multiple containers running on top of the OS kernel directly. which makes containers lightweight(shares OS kernel, start faster, and use less memory compared to booting an OS.)

It gives developers the ability to create predictable and consistent environments(which includes software dependencies, libraries, and version of the software) that are isolated from other applications. That means if developer develops an app with some dependency or version of library or any of the software dependency, it will be consistent throughout the end to end cycle which saves the times to test these dependencies or any other environmental consistency on the deployment platform, you just have to deploy your container which is guaranteed to be consistent no matter where the application is ultimately deployed.

Containers can be run anywhere, also in the cloud, which makes ease of deployment of the application. Docker image helps to achieve portability.

Containers virtualize resources at the OS-level, which provides a [sandboxed view](#sandbox) of the OS logically isolated from other applications to the developer. Containers isolate applications from each other unless you explicitly connect them which ensures of divesting from conflicting dependencies. We can consider it as an additional security layer since it isn't running directly on the host os.

<!-- It helps developers to Containers can also include software dependencies needed by the application, such as specific versions of programming language runtimes and other software libraries. From the developer’s perspective, all this is guaranteed to be consistent no matter where the application is ultimately deployed. All this translates to productivity: developers and IT Ops teams spend less time debugging and diagnosing differences in environments, and more time shipping new functionality for users. And it means fewer bugs since developers can now make assumptions in dev and test environments they can be sure will hold true in production. -->


you can pack your application with dependencies into manifest that can be version controlled.

<!-- Just as how software libraries package bits of code together, allowing developers to abstract away logic like user authentication and session management, containers allow your application as a whole to be packaged, abstracting away the operating system, the machine, and even the code itself. Combined with a service-based architecture, the entire unit that developers are asked to reason about becomes much smaller, leading to greater agility and productivity. All this eases development, testing, deployment, and overall management of your applications. -->

### **Benefits of Containers vs Virtual Machines**
| 	|CONTAINER BENEFITS	| VIRTUAL MACHINE BENEFITS |
|   --- |   --- |   ---|
| Consistent Runtime Environment | &#9745; | &#9745; |
|   Application Sandboxing  | &#9745; | &#9745; |
|   Small Size on Disk  | &#9745;  | &#9744; |
|   Low Overhead  | &#9745;   | &#9744; |
|	|	![container][img.11]	|	![container][img.12]	|



## [Monolithic to Service Oriented Architecture (Microservice Architecture)][ref.16] [](#microservice)

Containers work best for service-based architectures as compare to monolithic architectures, where every piece of the application is intertwined but microservice-based architectures separate these into separate components. [We can compare this using the above example.](#example) which allows your services to continue running even if others are failing, which increases reliability.


you can health check each container, limit each service to specific resources and maintain, start or stop them independently.

We can treat containers separated services as black boxes, which helps the developer thinks abstractly. When developers work on services that depend on another, they can use that service container without wasting time for setting up the environment and troubleshooting.


Summary
--
Now we know about the basic [difference](#diffvmcont) between virtualization and containerization. We also discussed the [types of virtualization](#typevirt) and [containerization](#typecont). We also discussed a basic [example](#example) of that. We can consider container as a [sandbox](#sandbox) that is useful from the architectural points of view for [microservice-based architecture](#microservice) and the advantages of microservice architecture over monolithic architecture. Orchestration of these services is again a big topic to discuss, we will discuss it in the future post which will include the Kubernetes, Docker Swarm and other orchestration tools also.

We know enough about history, architectural points of view and the usefulness of containers. Now we are ready to jump into the implementation part so in the future post we will start with hands-on exercise part of containerization.





<!-- reference links -->

<!-- [1]: https://dzone.com/articles/evolution-of-linux-containers-future

[2]: https://medium.com/faun/the-missing-introduction-to-containerization-de1fbb73efc5

[3]: https://blog.aquasec.com/a-brief-history-of-containers-from-1970s-chroot-to-docker-2016

[4]: https://linuxacademy.com/blog/containers/history-of-container-technology/
-->

<!-- https://dzone.com/articles/microservices-1-introduction-monolithic-vs-microse -->

<!-- https://articles.microservices.com/monolithic-vs-microservices-architecture-5c4848858f59 -->

[ref.5]: https://www.docker.com/resources/what-container

[ref.6]: https://www.sciencedirect.com/topics/computer-science/full-virtualization

[ref.7]: https://www.geeksforgeeks.org/virtualization-vmware-full-virtualization/

[ref.8]: https://en.wikipedia.org/wiki/Paravirtualization

[ref.9]: https://www.sciencedirect.com/topics/computer-science/paravirtualization

[ref.10]: https://en.wikipedia.org/wiki/OS-level_virtualization

[ref.11]: https://www.geeksforgeeks.org/operating-system-based-virtualization/

<!-- [ref.12]: https://speakerdeck.com/jbeda/containers-at-scale -->

[ref.13]: https://opensource.com/resources/

[ref.14]: https://cloud.google.com/containers/



[ref.16]: https://dzone.com/articles/microservices-1-introduction-monolithic-vs-microse

[img.10]: https://drive.google.com/uc?export=view&id=15si2-OveTPiWqq7Ol2--QaDGKwnhxMNc "virtualization"

[img.11]: https://drive.google.com/uc?export=view&id=1PvnhdqwUH4JrMFKZ4ils_dsrW7fdQkui "container"

[img.12]: https://drive.google.com/uc?export=view&id=1nrJoq5u5mwfss3UMaML9blQqvtifyrHI "vm"

[img.13]: https://drive.google.com/uc?export=view&id=1TY99RPSpHjaiPZir4sUPW7PVEn_WiMYq "OS Container"

[img.14]: https://drive.google.com/uc?export=view&id=14NQe6e9Dn8LujpxCarSnbcnfpCqE3pLH "App Container"