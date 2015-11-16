---
user: __user__
user_firstname: __user_firstname__
user_lastname: __user_lastname__
user_company: __user_company__
user_email: __user_email__
wsappl_name: __wsappl_name__
wsappl_doc_version: __wsappl_doc_version__

title: Infrastructure as Code
layout: colpage
pager: true
---
Part 2 - Infrastructure as Code
{.lead}

<div class="row" markdown="1">
<div class="col-md-6">

<h2>Introduction to Infrastructure Development</h2>

Infrastructure is the Runtime Environment of an (often distributed) Application. It consists of a set of interconnected machines, either physical or virtualized like KVM VMs or Docker Containers. The VM Creation Process from "Scratch" to "Deployed Application" can be seen as a three step process: Bootstrapping + Provisioning + App Deployment.
During Bootstrapping a set of empty VMs are being created and the basic network setup is done. Bootstrapping is finished when all the boxes have a distinct hostnames and are accessible via ssh or similar.
In the next phase this empty boxes will get provisioned with the "right" middleware to fulfill their role in the runtime environment for the later deployed app. Typical server roles are database host, a java based microservice container, a message queue instance etc.
There are a handful of mature provisioning frameworks on the market: Chef, Puppet, Ansible, Salt Stack, etc.
In this Workshop we focus on Chef and its tool ecosystem.  

</div>
<div class="col-md-6" markdown="1">

<h2>3 Phase VM Creation Process</h2>

<img src="img/img1.png" class="img-thumbnail" />

</div>
</div>
--
<div class="row">
<div class="col-md-6">

<h2>Server Provisioning with Chef</h2>

Chef aims to be a platform independent provisioning framework providing all tools needed for the vast majority of server provisioning and configuration tasks. The main building block in Chef is the "cookbook". A cookbook bundles all infrastructure code to setup, configure and manage a specific service on a given machine. The actual code is grouped into "recipes" (files) and consists of "resources" (dsl code blocks inside recipes) . Extended or customized cookbooks can be composed from existing cookbooks using a dependency management tool called "berkshelf". A large number of excellent community cookbooks can be found at the [Chef Supermarket][chef_supermarked].   

[Chef Documentation][chef_doc]{: .btn .btn-xs .btn-default role=button }
[Chef Supermarket][chef_supermarked]{: .btn .btn-xs .btn-default role=button }

</div>
<div class="col-md-6">

<h2>Heading</h2>

Text.

[Link][binary_repo]{: .btn .btn-xs .btn-default role=button }

</div>
</div>
