---
layout: post
title: "Playing with rkt and appc"
date: 2016-09-07
author: Ramit Surana
tags: rkt aci docker
category: coreos rkt containers
excerpt: "Exploring the rkt container ecosystem"
---

Evolution is an ongoing process.In the containers spectrum it has been a regular custom to experiment with new stuff and make it better with time.Saying so one of the coolest evolving projects is the [rkt][8] project by Coreos guys.It is a substitute of the famous [docker][6] container project.It uses different methodology than the [docker][6] project.So I began exploring this awesome project and found out that its a really interesting approach on building containers.In this post I have shared some of my findings below:


##  About rkt:

[rkt][8] is an awesome project which started way back with a minor conflict of opinions on containers between the [Docker][6] guys and CoreOS guys.It is designed for security, simplicity, and composability within modern cluster architectures.[rkt][8] implements a modern, open, standard container format, the [App Container (appc)][9], but can also execute other container images, like those created with [docker][6].The most fundamental atomic unit in [rkt][8] is the pod, which is a group of related containers that share resources.One of the amazing things about [rkt][8] is that it is a single binary that integrates with init systems, scripts, and complex devops pipelines. Containers take their correct place in the PID heirachy and can be managed with standard utilities.

![rkt-1 0-banner](https://cloud.githubusercontent.com/assets/8342133/16660420/ce24e2e0-448b-11e6-97b5-b56079d0f631.png)


## About ACI's


[ACI][] full form is Application Container Image.You can think of it as a similar to [docker][6] Images.Except it's not !
It is a simple unix utility for constructing ACI manifests and container filesystems.Acbuild presents options for mapping ports, mounting filesystems, and specifying the base containers from which higher-level images are built — a dependency, in acbuild parlance.

Some of the features of ACI include:

* Composable
* Security
* Decentralization
* Open Souce

[appc][9] also defines several independent but composable aspects involved in running application containers, including an image format, runtime environment, and discovery mechanism for application containers.

![app-container-rkt-14-638](https://cloud.githubusercontent.com/assets/8342133/16660112/b66d8dc4-448a-11e6-916b-ff109cf64fe7.jpg)


# Building ACI Images:

Building aci images is easy to use with an awesome [acbuild][https://github.com/appc/acbuild] project.Using this project you can easily create your own aci images.Its under heavy development process and might change its workflow in the future.


Before starting to use the acibuild you need to follow the steps:
Download [acbuild][https://github.com/appc/acbuild/releases] package.
and

Here's how you can build ACI Images:

````
# Starting ACI build
acbuild begin

# 
acbuild set-name example.com/hello

# Following Command
acbuild copy hello /bin/hello

# Commands
acbuild set-exec /bin/hello

# Naming the aci
acbuild write hello-latest-linux-amd64.aci

#Ending the process
acbuild end

````
<script src="https://gist.github.com/ramitsurana/06f08da66dc9ec1c3a6299773bdaf4f0.js"></script>

## How it works ?

[rkt][8] works in multiple ways.Some of the most common ways include by using:
* Url of aci image,
* Using [Docker][6] registry
* Using quay.io
 

But all of these include one common thing that is to use the aci images while building up the rkt containers.
So I am going to discuss one of the most commonly used methods to build up rkt containers.In this method I am going to fetch a simple docker container from the docker registry and use it to build up a rkt container.

````
rkt run --interactive docker://alpine --insecure-options=image

```` 

In the above command, we use `--interactive` flag for using the STDIN and STDOUT devices from your kernel.The `--insecure-options=image` is used because some of the docker images don't have image signature verification.This flag skips the trouble of verifying image.Behind the scenes here's a depiction of what happens:

![rkt-work](https://cloud.githubusercontent.com/assets/8342133/16678420/85a9368a-44fc-11e6-9271-770ce896056c.png)


Basically what rkt does is simply pull the docker image from the registry.In every case you have to specify the registry using which you are pulling down the image.As per usage there are two popular options namely, docker registry and quay.io.After it fetches the image.A utility called as [docker2aci][] is used to convert these images to aci images.Then using this image the rkt container automatically brings up the rkt container.

## Building rkt containers

- Here are the steps to follow:

<script src="https://gist.github.com/ramitsurana/0a1c8e9f4af1b01e35c035c9b519564c.js"></script>

## Garbage Collection

This is one of the features that I love the most about [rkt][8] containers.In this feature,[rkt][8] can easily clear out containers that have exited and are not in use.Truly saying I feel that this feature is of very high importance.The reason is that when you deploy a huge lot of containers in real time scenario,it becomes really hard to manage containers which have exited and which are running.This creates a true messy condition for the user.Using the [rkt][8] gc command,it can automatically reap exited pods and container images from the local store after a configurable grace period.

<script src="https://gist.github.com/ramitsurana/e22d35562383600e5b68d645cd7a2c52.js"></script>

## Switching from Docker to rkt:

As a regular [Docker][6] user myself I find it hard to understand and use all the best of commands in [rkt][8].So
I have tried to summarise some of the commands that can be used while switching from [docker][6] to [rkt][8] :



Docker | rkt
------------ | -------------
pull | fetch
ps | list
image list | images
--interactive | -i -t 


Hope you enjoyed this post,please tell us your opinions in the comments section below.

## The Remote Lab DevOps Offerings:
<iframe src="//www.slideshare.net/slideshow/embed_code/key/h9h9GNjX5Gncpi" width="595" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/bhalothia/the-remote-lab-devops-offerings" title="The Remote Lab DevOps Offerings" target="_blank">The Remote Lab DevOps Offerings</a> </strong> from <strong><a href="//www.slideshare.net/bhalothia" target="_blank">Virendra Bhalothia</a></strong> </div>


**Hope you Enjoyed! Keep exploring.Keep learning.**

**Need DevOps help? - Get in touch with** [The Remote Lab][1]
[LinkedIn][2] [Facebook][3] [Github][4] [Twitter][5]


  [1]: http://theremotelab.com
  [2]: https://www.linkedin.com/company/the-remote-lab
  [3]: https://www.facebook.com/TheRemoteLab
  [4]: https://github.com/TheRemoteLab
  [5]: https://twitter.com/TheRemoteLab
  [6]: http://docker.com
  [7]: https://cloud.githubusercontent.com/assets/8342133/12071970/ed85ee72-b0ed-11e5-9a99-d4b0d8d8a36a.png
  [8]: http://coreos.com/rkt
  [9]: http://github.com/appc/spec
