---
layout: post
title: "Here comes AWS security cop: Amazon Inspector"
date: 2015-10-26
author: Pradeep Aradhya
tags: aws inspector cloud iaas security paas
category: tutorial
excerpt: "This is an Amazon Inspector tutorial for beginners. Application assessment tool."
---


In AWS [re:Invent 2015][13], Amazon introduced a new service in security domain known as [Amazon Inspector][6].


##What is Amazon Inspector?

![Inspector][11]

The name Inspector for this service fits in. As in real life, Inspector is responsible for individuals to follow protocols, defined guidelines.
Same way in AWS, Inspector is responsible for security and compliance issues in your application. It analyze the behavior of the applications deployed on the AWS instances to identify potential security issues.
Amazon Inspector is a set of built-in rules, best practices against which the application will be tested. And Inspector generates a detailed report of the findings and loopholes in the application and also suggests steps for remediation.

Basiclly its a combination of [Security Monkey][7] and [Conformity Monkey][8].

##Why is Inspector required?

Inspector is automated, repeatable, and low cost(no licencing for property tools)
Its serverless, one less server to maintain ;-)
It is built on Amazon's 20 years of operation knowledge
No dedicated Security team required


##How does it work?

###1. Install agents on EC2 instances

This Inspector agent collects all the data from ec2 instances to the Inspector. Agent can be installed by downloading from
"`wget https://s3-us-west2.amazonaws.com/inspector.agent.us-west-2/latest/install" and "sudo bash install`".

Can start / stop the agent by
	"`sudo /etc/init.d/inspector start/stop`"

By default Amazon Linux ships with agents installed.

###2. Tag
Tag the instances with application specific information; a collection of AWS resources that counts for your application.

###3. Configure Amazon Inspector
- Create an assessment, give it a logical name
- Add Set-of-Rules required for assessment
- Define the duration of the assessment


> ![Assessment overview][9]
Image Source: AWS Website

###4. Start the assessment
Click on **Start** button

###5. Exercise the application
Manually testing the application, automation etc

As, the application being exercised, an Inspector agents running on each instances collects file system, process and network activities. Agents also collects the information about other AWS services used by the application like s3 endpoints, network traffic between ensctances. All these informations from agents provides Inspector a complete understanding of the application.
All the collected data is analyzed and compared against the set of built-in security rules selected in **Step:3**

###6: The Report
After the assessment, Inspector generates a detailed report of any vulnerability or compliance issue and prioritize steps for remediation.

The preview launch of the Inspector will have the following set of rules:

- Common Vulnerabilities and Exposures
- Network Security Best Practices
- Authentication Best Practices
- Operating System Security Best Practices
- Application Security Best Practices
- PCI DSS 3.0 Assessment

Get your hands dirty by [Sign up][10] for the Inspector preview  

I will revisit this section again to dive deeper into configuration, use-case, advantages once Amazon Inspector is full blown service in AWS offerings.

## The Remote Lab DevOps Offerings:
<iframe src="//www.slideshare.net/slideshow/embed_code/key/h9h9GNjX5Gncpi" width="595" height="485" frameborder="0" marginwidth="0" marginheight="0" scrolling="no" style="border:1px solid #CCC; border-width:1px; margin-bottom:5px; max-width: 100%;" allowfullscreen> </iframe> <div style="margin-bottom:5px"> <strong> <a href="//www.slideshare.net/bhalothia/the-remote-lab-devops-offerings" title="The Remote Lab DevOps Offerings" target="_blank">The Remote Lab DevOps Offerings</a> </strong> from <strong><a href="//www.slideshare.net/bhalothia" target="_blank">Virendra Bhalothia</a></strong> </div>

Please leave your comments below if you have any doubts or questions.


**Need DevOps help? - Get in touch with** [The Remote Lab][1]
[LinkedIn][2] [Facebook][3] [Github][4] [Twitter][5]

Credits: [Amazon Inspector][6], [Amazon Blog][12], [AWS re:Invent][13]


  [1]: http://theremotelab.com
  [2]: https://www.linkedin.com/company/the-remote-lab
  [3]: https://www.facebook.com/TheRemoteLab
  [4]: https://github.com/TheRemoteLab
  [5]: https://twitter.com/TheRemoteLab
  [6]: https://aws.amazon.com/inspector/
  [7]: http://techblog.netflix.com/2014/06/announcing-security-monkey-aws-security.html
  [8]: http://techblog.netflix.com/2013/05/conformity-monkey-keeping-your-cloud.html
  [9]: https://s3-ap-southeast-1.amazonaws.com/trl-blog/insp_How_3.png
  [10]: http://aws.amazon.com/inspector/preview/
  [11]: https://s3-ap-southeast-1.amazonaws.com/trl-blog/amazon_inspector.png
  [12]: https://aws.amazon.com/blogs/aws/
  [13]: https://reinvent.awsevents.com/
