---
layout: post
title: "Here comes AWS security cop: Amazon Inspector"
date: 2015-10-26
author: Pradeep Aradhya
tags: aws inspector cloud iaas security paas
category: tutorial
excerpt: "This is an Amazon Inspector tutorial for beginners. Application assessment tool."
---


Amazon has introduced a new service in security domain known as [Amazon Inspector][6]. 


##What is Amazon Inspector?

![Inspector][11]

The name Inspector for this service fits in. As in real life, Inspector is respnsible for individuals to follow protocals, defined gidelines. 
Same way in AWS, Inspector is responcible for security and complaince issues in your application. It analyze the behavior of the applications deployed on the AWS instances to identify potential security issues. 
Amazon Inspector is a set of built-in rules, best practices against which the application will be tested. And Inspector genrates a detailed report of the findings and loopholes in the application and also suggests steps for remidiation.

Basiclly its a combination of [Security Monkey][7] and [Conformity Monkey][8].

##Why is Inspector required?

Inspector is automated, repetable, and low cost(no licencing for properoty tools)
Its serverless, one less server to maintain ;-)
It is built on Amazon's 20 years of operation knowledge 
No dedicated Security team required 


##How does it work?

**1. Install agents on EC2 instances**
	This Inspector agent collects all the data from ec2 instances to the Inspector. Agent can be installed as in;
	Download "`wget https://s3-us-west-2.amazonaws.com/inspector.agent.us-west-2/latest/install" and "sudo bash install`". 
	Can start / stop the agent by "`sudo /etc/init.d/inspector start/stop`"

**2. Tag **
	Tag the instances with application specific information; a clooection of AWS resources that counts for your application.

**3. Configure Amazon Inspector**
	Create an assessment, give it a logical name
	Add Set-of-Rules required for assessment 
	Define the deuration of the assessment

![Assessment overview][9]

Image Source: AWS Website

**4. Start the assessment**
**5. Exercise the application**
	Manually testing the application, automation etc

As, the application being exercised, an Inspector agents running on each instances collects file system, process and network activities. Agents also collects the information about other AWS services used by the application like s3 endpoints, network traffic between ensctances. All these informations from agents provides Inspector a complete understanding of the application. 
All the collected data is analyzed and compared against the set of built-in security rules selected in Step:3

**6: The Report**
	After the assessment, Inspector genrates a detailed report of any vulnerability or complaince issue and priortize steps for remideations. 



The preview launch of the Inspector will have the following set of rules:

- Common Vulnerabilities and Exposures
- Network Security Best Practices
- Authentication Best Practices
- Operating System Security Best Practices
- Application Security Best Practices
- PCI DSS 3.0 Assessment

Ge your hands dirty by [Signup][10] for the Inspector preview  

I will revisit this section again to dive deeper into configuration, usecase, advantages once Amazon Inspector is full blown service in AWS offerings.


  [1]: http://theremotelab.io
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
