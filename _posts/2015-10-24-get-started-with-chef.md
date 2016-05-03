---
layout: post
title: "Chef is all about speed and awesomeness"
date: 2015-10-24
author: Ramit Surana
tags: script chef automation devops
category: Automation Tool
excerpt: "If you are looking to transform your complex infrastructure into code, chef is your answer"
---

If you are looking to transform your complex infrastructure into code, [chef][6] is your answer. It becomes your single source of truth for all infrastructure needs and fastens your development rate.

## What is 'Chef' ?

Chef is an automation provisioning tool. It is a cloud infrastructure automation framework that makes it easy
to deploy servers and applications to any physical, virtual, or cloud location, no matter the size of the infrastructure.

## 'Architecture':

![chef-fig2][7]

## Cookbook:

It is the fundamental unit of configuration and policy distribution. A cookbook defines a scenario and contains everything that is required to support that scenario. Recipes that specify the resources to use and the order in which they are to be applied

- Attribute values
- File distributions
- Templates
- Extensions to Chef, such as libraries, definitions, and custom resources

## Recipe:

It is the most fundamental configuration element within the organization. A recipe is authored using Ruby, which is a programming language designed to read and behave in a predictable manner. It is mostly a collection of resources, defined using patterns (resource names, attribute-value pairs, and actions)
helper code is added around this using Ruby, when needed it must define everything that is
required to configure part of a system. It must be:

- Must be stored in a cookbook​
- May be included in a recipe​
- May use the results of a search query and read the contents of a data bag (including an encrypted data bag)​
- May have a dependency on one (or more) recipes​
- May tag a node to facilitate the creation of arbitrary groupings​
- Must be added to a run-list before it can be used by the chef-client​
- Is always executed in the same order as listed in a run-list.

## Knife:

![xknife-solo png pagespeed ic n88w0gtft_][8]

It is a Chef's command-line tool called to interact with the Chef Server.
It is used for uploading cookbooks and managing other aspects of Chef.
It provides an interface between a local chef-repo and the Chef server.
Knife helps users to manage:​

- Nodes
- Cookbooks and recipes
- Roles
- Stores of JSON data (data bags), including encrypted data
- Environments
- Cloud resources, including provisioning
- The installation of the chef-client on management workstations
- Searching of indexed data on the Chef server

## Chef-Server:

The Chef server stores cookbooks, the policies that are applied to nodes, and metadata that describes each registered node that is being managed by the chef-client.
The nodes are used the chef-client to ask the Chef server for configuration details, such as recipes, templates, and file distributions.
The chef-client then does as much of the configuration work as possible on the nodes themselves.

![chef_graph 1][9]


## Chef-Client:

It is a provisioning which works on server.​It is an agent that runs locally on every node that is under management by Chef.
When a chef-client is run, it will perform all of the steps that are required to bring the node into the expected state, including:​

- Registering and authenticating the node with the Chef server​
- Building the node object​
- Synchronizing cookbooks​
- Compiling the resource collection by loading each of the required cookbooks, including recipes, attributes, and all other dependencies​
- Taking the appropriate and required actions to configure the node​
- Looking for exceptions and notifications, handling each as required​

## Using Foodcritic:

![foodcritic][10]

It tries to identify possible issues with the logic and style of your cookbooks.
It comes with rules concerning various areas: style, correctness, attributes, strings,
portability, search,services, files, metadata, and so on.

## RSpec Framework:

It is composed of multiple libraries, which are designed to work together, or
can be used independently with other testing tools like Cucumber or Minitest.
The parts of RSpec are:​

- *rspec-core:*
The spec runner, providing a rich command line program, flexible and customizable reporting,
and an API to organize your code examples.

- *rspec-expectations:*
Provides a readable API to express expected outcomes of a code example.  ​

- *rspec-mocks:*
Test double framework, providing multiple types of fake objects to allow you
to tightly control the environment in which your specs run.   

- *rspec-rails:*
Supports using RSpec to test Ruby on Rails applications in place of Rails' built-in test framework.

## Chef Test Kitchen:

It is a test harness tool to execute your configured code on one or more platforms in isolation.
A driver plugin architecture is used which lets you run your code on various cloud providers and virtualization
technologies such as Amazon EC2, Blue Box, CloudStack, Digital Ocean,Rackspace, OpenStack, Vagrant, Docker, LXC containers, and more.
Many testing frameworks are already supported out of the box including Bats, shUnit2, RSpec, Serverspec, with others being created weekly.​

## Chef DSL(Domain Specific Language):

Recipe DSL helps ensure that recipes interact with nodes (and node properties) in the desired manner.
Ruby is a dynamic, open source programming language with a focus on simplicity and productivity.
It has an elegant syntax that is natural to read and easy to write.

## Chef Analytics:

It is a Feature of Chef that provides real-time visibility into what is happening on the Chef server,what’s changing, who made those changes, and when they occurred.
It is the relationships between the various elements of Chef Analytics, including how information is routed from various nodes to the Chef Analytics server (through the Chef server) nodes,
where reports about chef-client run outcomes may be viewed, where rules are processed, and where Chef Analytics data may be viewed.​

## Data Bags:

![lncf_1301][11]

A data bag is a global variable that is stored as JSON data and is accessible from a Chef server.
A data bag is indexed for searching and can be loaded by a recipe or accessed during a search.
It can be created in two ways: using knife or manually.

My Slides on slide share can be found [here][12].

**Hope this helps! Keep forking.**

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
  [6]: https://www.chef.io/
  [7]: https://cloud.githubusercontent.com/assets/8342133/10710473/a9b2b360-7a79-11e5-9f6e-e1d5b34a2e3a.png
  [8]: https://cloud.githubusercontent.com/assets/8342133/10710510/978ac66c-7a7b-11e5-9f28-f63a94abbc68.png
  [9]: https://cloud.githubusercontent.com/assets/8342133/10710541/430d5cfc-7a7c-11e5-9472-b7c0abbe836b.png
  [10]: https://cloud.githubusercontent.com/assets/8342133/10710537/12185e44-7a7c-11e5-8395-3b0a268dd610.png
  [11]: https://cloud.githubusercontent.com/assets/8342133/10710517/cfd7f774-7a7b-11e5-99a7-4a8ef9fc45b1.png
  [12]: http://www.slideshare.net/ramitsurana/introducing-chef-an-it-automation-for-speed-and-awesomeness
