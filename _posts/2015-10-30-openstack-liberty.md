---
layout: post
title: "An overview of OpenStack Liberty"
date: 2015-12-28
author: Thyagaraju
tags: OpenStack, Cloud, Public Cloud, Private Cloud
category: Information
excerpt: "Lets discuss about OpenStack Liberty"
---

![openstack-liberty](https://cloud.githubusercontent.com/assets/8342133/12033099/68e58a38-ae45-11e5-98da-b4e990c32815.png)


## OpenStack Release Names


`Liberty` is the 12th major release of OpenStack and below are the list of all the releases so far.

- `Austin:` The first design summit took place in Austin, TX
- `Bexar:` San Antonio is located in Bexar county
- `Cactus:` Cactus is a city in Texas
- `Diablo:` Diablo is a city in the bay area near Santa Clara
- `Essex:` Essex is a city near Boston
- `Folsom:` Folsom is a city near San Francisco
- `Grizzly:` Grizzly is an element of the state flag of California
- `Havana:` Havana is an unincorporated community in Oregon
- `Icehouse:` Ice House is a street in Hong Kong
- `Juno:` Juno is a locality in Georgia
- `Kilo:` Paris (Sèvres, actually, but that's close enough) is home to the Kilogram
- `Liberty:` Liberty is a village in the Canadian province of Saskatchewan

PS: Next release will be called as `Mitaka`. It’s named after the town located in the Tokyo metro area known for Inokashira park and the Ghibli museum

## Lets welcome `OpenStack Liberty`

`OpenStack Liberty` is the 12th release of `OpenStack` and was released on October 15 2015.

Lets have a closer look at the major focus areas of `Liberty` before we dwell into individual projects

## Enhanced Manageability

 `Liberty` includes common library adoption and better configuration management, as well as `RBAC - Role Based Access Control` for the Heat orchestration and Neutron networking projects, enabling operators to more finely tune security settings.

## Simplified Scalability

There has been Performance and stability improvements in `OpenStack` in general, and the Horizon dashboard, Neutron networking, Cinder block storage, and Nova compute services in particular.

Nova Cells v2, which will eventually enable much larger multi-location compute deployments also makes its debut in Liberty and let me discuss this is detail later,

## Extensibility

While `OpenStack` has reduced the `Core` components that must be supported, starting from Liberty, it is also moving in the direction of enabling the support of multiple other technologies under the Big Tent structure.

## Lets look at some of the Major Changes in the some of the Individual Project (Compoents) of `OpenStack Liberty`

- Horizon: <br>
	-	New Launch Instance Dialog <br>
	-	Network Topology Visibility <br>
	-	IDP-specific WebSSO (Hybrid Cloud Management) <br>

- Nova: <br>
	-	NFV (Near Functions Virtualization)
	-	Cells Management

- Neutron: <br>
	-	Better control over security and bandwidth
	-	Neutron now does IPv6 prefix delegation, enabling automatic assignment of CIDRs to submits and making setting up 	 a network much easier.
	-	Administrators can now control bandwidth by assigning quotas not just to projects, but to individual VMs as well.
	- 	RBAC (Role Based Access Control)
	- 	The LBaaS reference implementation is now based on an operator-grade load balancer platform (Octavia)
	-	Pluggable IP address management (PIAM) is now available, enabling third-party IPAM.

- KeyStone: <br>
	-	Greater control over Identity Providers (IDP) through control WebSSO for individual IDP backends.
	- 	Different Clouds, Same Platform

- Swift: <br>
	-	Better performance when there are slow drives, as well as removing latency spikes and limiting data movement 		during cluster management.
	-	Operators can now use ring-builder-analyzer to test out different ring operations quickly.
	- 	Users can now set “per object” metadata for exploding archives.
- Cinder: <br>
	-	Quota enforcement in hierarchical projects
	-	Commonly used images can now be cached, improving performance
- Glance: <br>
	-	Glance now enables users to sign an image using their private key so that its integrity can be verified to be 		sure no malicious code has been inserted.
	-	 Glance can now be used from multiple networks with an S3 backend over an HTTP proxy.
- Ceilometer: <br>
	-	We can now trigger an alarm based on incoming events in real time.
	-	Most meters can now be created with a yaml file rather than python code.
	-	Asynchronous handling of new measures in Gnocchi.
	-	Ceilometer can now send metrics to the Gnocchi time series data storage system, which can also be used to 			visualize performance with Grafana.
- HEAT: <br>
	-	 Heat can now control Keystone endpoints.


 **Hope this was informative and please keep reading...**

## The Remote Lab DevOps Offerings:

 <iframe src="//www.slideshare.net/slideshow/embed_code/key/h9h9GNjX5Gncpi" width="595" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/bhalothia/the-remote-lab-devops-offerings" title="The Remote Lab DevOps Offerings" target="_blank">The Remote Lab DevOps Offerings</a> </strong> from <strong><a href="//www.slideshare.net/bhalothia" target="_blank">Virendra Bhalothia</a></strong> </div>

 Please leave your comments below if you have any doubts or questions.

**Need DevOps help? - Get in touch with** [The Remote Lab][1]
[LinkedIn][2] [Facebook][3] [Github][4] [Twitter][5]


  [1]: http://theremotelab.com
  [2]: https://www.linkedin.com/company/the-remote-lab
  [3]: https://www.facebook.com/TheRemoteLab
  [4]: https://github.com/TheRemoteLab
  [5]: https://twitter.com/TheRemoteLab
