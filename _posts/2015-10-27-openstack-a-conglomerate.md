---
layout: post
title: "OpenStack a Conglomerate"
date: 2015-10-15
author: Thyagaraju
tags: OpenStack, Cloud, Public Cloud, Private Cloud
category: Use Cases
excerpt: "Lets discuss about the various components of OpenStack"
---

Before we begin, lets take a few minutes to know what is [OpenStack][6]. 

`OpenStack` is a set of software tools for building and managing cloud computing platforms for public and private clouds. Backed by some of the biggest companies in software development and hosting, as well as thousands of individual community members, many think that `OpenStack` is the future of `Cloud Computing`.

`OpenStack` is managed by [OpenStack Foundation][7], a non-profit organization, which oversees both development and community-building around the project.

This post is more about undertanding the various components of `OpenStack` and understanding how these different pieces combine together and give us the `OpenStack Platform`, a `Conglomerate`.

![OpenStack][8]

Lets get started with understanding of [OpenStack][6]

`OpenStack` as mentioned earlier, is a `Conglomerate` of different components and these components are referred to as individual projects with a `core designation`.

These `core` projects can use the [OpenStack][6] trademark and must pass all `must-pass` tests, as defined by the `OpenStack Foundation`. When someone is working on an OpenStack Deployment, these `core components` or these `individual projects` are what almost everyone will use.

Going forward, let me refer to these `core components` as `projects` as that would make our understanding better. Each of these `projects` would have a `Code Name` associated with them and it is equally important for us to get familiar with these `Code Names` as well.

Some of the Various `Projects` of OpenStack and their `Code Names` are below:

- Dashboard             --> Horizon
- Compute               --> Nova
- Networking            --> Neutron
- Identity Service      --> Keystone
- Object Storage        --> Swift
- Block Storage         --> Cinder
- Image Service         --> Glance
- Telemetry Service     --> Ceilometer
- Orchestration Service --> Heat
- Load Balancing        --> LBAAS

Now lets look at these `Projects` in detail and understand the role these individual projects play in `OpenStack Conglomerate` 

## Horizon

`Horizon` is `OpenStack’s Dashboard Project`, which provides a web based user interface to other `OpenStack Projects` such as `Nova`, `Swift`, `Keystone` and others which we would discuss later.

It is a Django-based project aimed at providing a complete OpenStack Dashboard along with an extensible framework for building new dashboards from reusable components.

## Nova

`Nova` which is also known as `OpenStack Compute` is the software that controls our Infrastructure as as Service (IaaS) cloud computing platform. Nova does not include any virtualization software, rather it defines drivers that interact with underlying virtualization mechanisms that run on our host operating system, and exposes functionality over a web API.


## Neutron

`Neutron` is an OpenStack project which was earlier called as `Quantum` and it is used to provide `networking as a service` between interface devices managed by other `Openstack` projects, especially `Nova`

It is a Pluggable, Scalable and API-driven system for managing networks and IP addresses. Neutron is an SDN (Software-defined Network) component and can be configured for network topologies, such as per-tenant private networks and others.

The core `Neutron` API includes support for Layer 2 networking and IP address management (IPAM) and also an extension for a Layer 3 router construct that enables routing between Layer 2 networks and gateways to external networks. 

`Neutron` includes a growing list of plugins that enable interoperability with various commercial and open source network technologies, including routers, switches, virtual switches and software-defined networking (SDN) controllers.

On a high level, a `Neutron` architecture can be depicted as below:

![Neutron Architecture][9]


## KeyStone

`KeyStone` is the `OpenStack` Project which provides Identity and Access Services for the all the projects within the `OpenStack Conglomerate`

KeyStone mainly has two major functions:

- `user management` --> User Access and User Level Permissions
- `service catalog` --> Database of Services which are available and also references to their API End Points

`KeyStone` acts as a `common Authentication System` across various other projects of `OpenStack` and can also integrate well with existing backend directory services such as LDAP or OpenLDAP.

On a high level, a `KeyStone` architecture can be depicted as below:

![KeyStone Architecture][10]


## Swift

`Swift` is the `OpenStack` project, which mainly focusses on `Storage Services`.  It is a Cost Effective, Scale-Out, Redundant, Scalable and Fully-Distributed API-accessible storage platform that can be integrated directly into applications or used for backup, archiving and data retention.

`Swift` nodes are of two types:

- `proxy node` : Proxy Nodes are the Front End Nodes, used for operations like Uploading, Managing and Modifying the MetaData. We can have `N`number of these proxy nodes and we can then load balance using any load balancers and the end points of the nodes
- `storage node` --> Storage Nodes are the actual nodes which stores data and these nodes need to be private

Depending the magnitude of our deployment setup, we can have both the Proxy and Storage Nodes on the same machines or they can be run on different machines.

On a high level, a `Swift` architecture can be depicted as below:

![Swift Architecture][11]

## Cinder

`Cinder` was originally part of the `Nova` Project and was called as `Nova Volume`. Later on, it came out of `Nova` and was renamed as `Cinder` which is now a standalone project. 

`Cinder` is the the OpenStack Block Storage Service, which provides persistent block storage to guest virtual machines for expanded storage, better performance and integration with enterprise storage platforms. It provides the platform to create and manage a service that provisions storage in the form of block devices known as Cinder volumes.

`Cinder` comes with the following components:

- `cinder-api`, which accepts the API requests and routes them to cinder-volume for action.
- `cinder-volume`, which responds to requests received through `cinder-api` by interacting with cinder-scheduler through message queue.
- `cinder-scheduler` which is responsible for choosing the right block storage node on which to create the volume.
- `messaging-queue`, which is is basically used to route the information across all the components.

On a high level, a `Cinder` architecture can be depicted as below:

![Cinder Architecture][12]

## Glance

`Glance` is the `OpenStack` project which has a RESTful API and provides services for discovering, registering, and retrieving virtual machine images.

It has the ability to copy (or snapshot) a server image and store. These stored images can then be used as templates to get new servers up and running quickly.

Glance has the following components:

- `glance-api`, which accepts API calls for image discovery, retrieval and storage.
- `glance-registry`, which stores, processes, and retrieves metadata information for images. 
- `database`, which stores image metadata
- `storage repository`, which integrates with various outside `OpenStack' components such as regular file systems, Amazon S3 and HTTP for image storages.

On a high level, a `Glance` architecture can be depicted as below:

![Glance Architecture][13]

## Ceilometer

`Ceilometer` is the Metering/Monitoring Service of `OpenStack` deployments, which is basically used for billing, benchmarking, scalability, and statistics gathering. 

This comes in handy when we need to retrieve usage data to help us optimize the utilization of our resources.

Following are the Basic Components of `Ceilometer'

- `compute agent`, which runs on each compute node and polls for resource utilisation stats
- `central agent`, which runs on central management server to poll for resource utilisation stats for resources not tied to instances or compute nodes
- `collector`, which runs on one or more central management servers to monitor the message queues. These notification messages are then processed and turned in to metering messages and sent back to the message bus using the appropriate topics crerated. Normally, these metering messages are written to the data store without modification.
- `datastore`, which are the databases which can handle concurrent writes from one or more collector instances and also can read from the API server.
- `API server`, which runs on one or more central management servers to provide the required access to the data from the data store. 

It is to be noted that only the `collector` and `API servers` have access to the `datastore`.

On a high level, a `Ceilometer` architecture can be depicted as below:

![Ceilometer Architecture][14]

## Heat

`Heat` is the main project in the `OpenStack Orchestration Program` and it implements an orchestration engine to launch multiple composite cloud applications based on the templates.

A `Heat` template describes the infrastructure for a cloud application in a text file which can also be version controlled. 

Resouces that can be described within `Heat` templates include, servers, floating ips, volumes, security groups, users, etc. `Heat` also provides an autoscaling service that integrates with `Ceilometer`.

`Heat` manages the whole lifecycle of the application and when we need any changesm, we simply can modify the template and use it to update our existing stack. `Heat` will fugure out means to facilitate changes wherever required.

`Heat` mainly manages infrastructure, however, `Heat` templates integrate well with other software configuration management tools such as `Puppet` and `Chef`. 

`Heat` is mainly a `Python` Project and consists of the following components:

- `heat-tool`, which is a CLI which communicates with the heat-api to execute AWS CloudFormation APIs if required.
- `heat-api`, which provides OpenStack-native ReST API that processes API requests by sending them to the heat-engine over RPC.
- `heat-api-cfn`, whichprovides an AWS-style Query API which is compatible with AWS CloudFormation and processes API requests by sending them to the heat-engine over RPC.
- `heat-engine`, which is the heart of `Heat` and which takes cares of `Orchestration` through templates and it also provides the information back to API.

`Heat` as mentioned earlier, is the very important project of `OpenStack` and its vision can be depicted from the below diagram.

![Heat Vision][15]

## LBaaS

`LBaaS` which stands for Load Balancer as a Service is actually a service provided by the `Neutron` component. 

`LBaaS` lets us to configure a load balancer which runs outside of our instances and directs traffic to our internal instances. We normally use `LBAAS` when we want to use multiple instances to reach our performance needs.

`LBaaS` management is performed via REST API and consists of the following components.

- `LBaaS Quantum Extension`, which is responsible for handling REST API calls
- `LBaaS Quantum AdvSvc Plugin`, which is responsible for request validation and scheduling of services
- `LBaaS Agent`, which manages the modules that transforms LBaaS object model into vendor-specific model. These modules can also be can also be addressed as drivers.

`LBaaS` architecture can be summed up like in the figure below.

![LBaaS Architcture][16]

As evident by now, an OpenStack Architecture involves integration with a lot of other components and relies heavily on the API calls between components.

Below diagram, hopefully would give us an idea about how the various components together form `OpenStack` and form a `Conglomerate`

![OpenStack Architecture][17]

 **Hope this was informative and please keep reading...**


#####Need DevOps help? - Get in touch with [The Remote Lab][1] 
[LinkedIn][2] [Facebook][3] [Github][4] [Twitter][5]


  [1]: http://theremotelab.io
  [2]: https://www.linkedin.com/company/the-remote-lab
  [3]: https://www.facebook.com/TheRemoteLab
  [4]: https://github.com/TheRemoteLab
  [5]: https://twitter.com/TheRemoteLab
  [6]: https://www.openstack.org/
  [7]: http://www.openstack.org/foundation/
  [8]: https://upload.wikimedia.org/wikipedia/commons/thumb/8/80/The_OpenStack_logo.svg/2000px-The_OpenStack_logo.svg.png
  [9]: http://s3.51cto.com/wyfs02/M01/23/81/wKioL1M47gfC2jpnAAJ3kGMk9TQ971.jpg
  [10]: http://docs.openstack.org/icehouse/training-guides/content/figures/8/a/figures/image19.png
  [11]: http://image.slidesharecdn.com/febopenstackmeetup-150217215138-conversion-gate01/95/openstack-swift-10-638.jpg?cb=1427719318
  [12]: https://varchitectthoughts.files.wordpress.com/2013/11/screen-shot-2013-11-18-at-11-00-24-am.png
  [13]: https://www.safaribooksonline.com/library/view/deploying-openstack/9781449311223/httpatomoreillycomsourceoreillyimages875415.png
  [14]: http://docs.openstack.org/developer/stevedore/_images/ceilometer-design.jpg
  [15]: https://wiki.openstack.org/w/images/2/25/Heat-Vision.png
  [16]: https://wiki.openstack.org/w/images/a/a7/Lbaas_architecture_new.png
  [17]: http://docs.openstack.org/icehouse/training-guides/content/figures/5/a/figures/openstack-arch-havana-logical-v1.jpg