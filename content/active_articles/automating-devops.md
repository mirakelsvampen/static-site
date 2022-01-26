title: Automating DevOps - Adding Azure Active Directory group through REST API
slug: automating-devops-rest-api-001
date: 2022-01-19
summary: 

Background
====

Lately I have been working on a project where I needed to bootstrap devops projects for a customer. This basically means that several tasks should be created from a standard procedure. I wanted this to be a fully automated workflow that could be started with a simple HTTP trigger (webhook).

This implies all included tasks must be performed programmatically. Tasks such as creating:

* A new Azure DevOps project
* New users that should be invited to the project
* Creates a security and licensing groups at the project scope

This can all be accomblished by using the offical [DevOps REST API](https://docs.microsoft.com/en-us/rest/api/azure/devops/?view=azure-devops-rest-7.1&viewFallbackFrom=azure-devops-rest-6.1)

This article will walk through the steps of adding Azure Active Directory groups to devops project.

For authentication we will be using basic auth with username & password. Where the password actually is a PAT token with the following permissions:

* dawd
* dwad

Requirements
====
This acticle does assume that an existing DevOps organization has been created and is linked to an active Azure tenant.


Understanding the API
====

Reading the documentation could be quite daunting because it does not really provide any information on relations between endpoints and in which order requests should be made etc.

The first step is to find out which endpoints I need to communicate with and what methods, payloads and responses I need to expect.

Using my browser's developer settings I can see what DevOps does under the hood when manually adding a Azure Directory group to a project.


Writing a simple function
====

I am using a azure function with a HttpTrigger because it allows me to start the project bootstrapping process through a webhook. So lets write a simple python function that allows us to implement the aforementioned logic.

Conclusion
====

