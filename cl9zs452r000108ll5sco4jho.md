# Chapter 01. Introducing Kubernetes - Kubernetes in Action

# 1.0.0 Introduction
Kubernetes is the trend of deployment platforms these days. More businesses are incorporating Kubernetes into their infrastructure. Why? Kubernetes saves them money and resources. Kubernetes maintains containerized application clusters that would otherwise have to be handled manually. Because of this fact, learning Kubernetes is inevitably essential.

In this series, you will start your learning journey by reading a celebrated book titled "Kubernetes in Action". This book covers the most important concepts in Kubernetes starting from beginner mode to advanced mode.

These articles will discuss the main points in each chapter providing additional hands-on experience. We will begin with an introduction to the author and the book. Then dive into the meat directly by talking about the introduction chapter.

Hope you have an effective learning time. I'll be open to contributions and comments.
## 1.0.1.  About the author
Marko Lukša is a software engineer with more than 20 years of professional experience developing everything from simple web applications to full ERP systems, frameworks, and middleware software.
If you would like to know more about Marko, please check this link: https://www.linkedin.com/in/marko-luk%C5%A1a-a71205
## 1.0.2.  About the book
Kubernetes in Action teaches you almost all of the fundamentals required to efficiently design and execute apps in a Kubernetes cluster. The book is primarily aimed at application developers, but it also includes an overview of application management from an operational standpoint.

The book is divided into three parts that cover 18 chapters.  Chapter 1 explains what Kubernetes is, how it came to be, and how it helps to solve today’s problems of managing applications at scale.

To know more about each chapter, check page xxvi in the first edition of the book.

# 1.1. Understanding the need for a system like Kubernetes
In order to develop any software, you need a process and strategy for development and for deployment. These strategies have changed a lot over years. For example, one of the old processes is the waterfall methodology. This methodology acts like a sequential step-by-step. The following figure shows what I mean.

![waterfall-model-software.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1665356539293/ZDLRTuC5U.png align="center")

Also, in old days deployments of packaged software (maybe binary files) were done manually on servers. You have to put different files in different places on the operating systems and you may need to adhere to a naming convention related to the operating system in use.

These days, models have changed dramatically. We started to find that Agile methodologies have more benefits in different use cases than the waterfall strategy. No to mention the thousands of servers in control to provide a stable workload for different users. Besides, the various types of software need a different type of control like machine learning models for example.

The following figure depicts the transition from monolithic apps to microservices.

![monolithic-vs-microservices.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1665357125246/WSxeLx8HB.png align="center")

Because they all operate as a single OS process, monolithic programs are made up of components that are closely tied together and must be designed, deployed, and managed as a single entity. Splitting complex monolithic applications into smaller independently deployable components called microservices. Each
microservice runs as an independent process and communicates with other microservices through APIs.

Deploying microservices introduces new problems. These problems may be a flaw in communication due to the failure of one of them. Also, scaling each service and load-balancing workload are other types of problems.

![microservices-scaling.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1665358107966/U61KS3SIk.png align="center")
The following figure shows another problem that is multiple applications running on the same host may have conflicting dependencies.

![libraries-dependence.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1665357564940/8LosmFOkU.png align="center")

To limit the number of issues that appear only in production, it would be great if programs could operate in the same environment between development and production, with the same operating system, libraries, system setup, networking environment, and everything else.

To wrap up, the following list comprises the need for Kubernetes:
- Moving from monolithic apps to microservices.
- Providing a consistent environment for applications.
- Moving to continuous delivery: DevOps and NoOps.

# 1.2. Introducing container technologies
In this section, the author will introduce the Kubernetes method in solving the problems presented in [section 1.1](#heading-11-understanding-the-need-for-a-system-like-kubernetes). Kubernetes solves these problems using Linux container concepts.

Containers are much lighter than VMs, allowing you to run more software components on the same hardware. This is because each VM must run its own set of system processes, which requires additional compute resources in addition to those consumed by the component's own process.

The mechanisms of making containers isolated are:
- Linux Namespaces: makes sure each process sees its own personal view of the system (files, processes, network interfaces, hostname, and so on).
- Linux Control Groups (cgroups): which limit the amount of resources the process can consume (CPU, memory, network bandwidth, and so on).

Docker is a platform for packaging, distributing, and running applications. it allows you to package your application together with its whole environment.

Three main concepts in Docker:
- Images: A Docker-based container image is something you package your application and its environment into.
- Registries: A Docker Registry is a repository that stores your Docker images and facilitates easy sharing of those images between different people and computers.
- Containers: A Docker-based container is a regular Linux container created from a Docker-based container image.

![Docker.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1667401607138/td5POQk8N.png align="center")
# 1.3. Introducing Kubernetes
Kubernetes is a software system that enables the deployment and management of containerized applications on top of it. It uses the features of Linux containers to run heterogeneous applications without knowing any internal details about these applications or manually deploying them on each host.

The following figure shows the components that form the Kubernetes cluster.

![k8s-components.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1667401822795/V-_hfl9_W.png align="center")

- At the hardware level, a Kubernetes cluster is composed of many nodes, which can be split into two types:
  - The master node, which hosts the Kubernetes Control Plane that controls and manages the whole Kubernetes system.
  - Worker nodes that run the actual applications you deploy.
- Control Plane components can run on a single node or distributed on multiple nodes to ensure high availability.
- Control Plane components are:
  - The Kubernetes API Server: facilitate communication between components.
  - The Scheduler: assigns a worker node to each deployable component of the application.
  - The Controller Manager: performs cluster-level functions, such as replicating components, keeping track of worker nodes, and handling node failures.
  - etcd: a reliable distributed data store that persistently stores the cluster configuration.
- The worker nodes components that are responsible of running, monitoring, and providing services are:
  - Docker, rkt, or another container runtime, which runs your containers.
  - The Kubelet, which talks to the API server and manages containers on its node.
  - The Kubernetes Service Proxy (kube-proxy), which load-balances network traffic between application components.
- The following are some benefits of using Kubernetes:
  - Simplifying application deployment
  - Achieving better hardware utilization
  - Health checking and self-healing
  - Automatic scaling
  - Simplifying application development

# 1.4. Summary
This introductory chapter shows the importance of using the Kubernetes platform. In the next chapters, we will dive into using Kubernetes with practical examples and projects.