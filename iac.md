---
title: Infrastructure as Code
layout: colpage
pager: true
---
Part 2 - Infrastructure as Code
{.lead}

<div class="row" markdown="1">
<div class="col-md-6">

<h2>Introduction to Infrastructure Development</h2>

Infrastructure is the Runtime Environment of an (often distributed) Application. It consists of a set of interconnected machines, either physical or virtualized like [KVM VMs][kvm_intro] or [Docker Containers][docker_intro]. The VM Creation Process from Scratch to Deployed Application can be seen as a three step process: Bootstrapping + Provisioning + App Deployment.
During Bootstrapping a set of empty VMs are being created and the basic network setup is done. Bootstrapping is finished when all the boxes have distinct hostnames and are accessible over the network via ssh or similar.
In the next phase these empty boxes will get provisioned with the middleware needed to fulfill their role in the app runtime environment. Typical server roles are for example database host, a java app server, message queue instance etc.
Typical Provisioning Tools are [Chef][chef_intro], [Puppet][puppet_intro], [Ansible][ansible_intro], [Saltstack][salt_intro], etc. In this workshop we focus on [Chef][chef_intro] and its tool ecosystem.  

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

[Chef][chef_intro] aims to be a platform independent provisioning framework providing all tools needed for the vast majority of server provisioning and configuration tasks. The main building block in Chef is the [cookbook][chef_cookbook]. A cookbook bundles all infrastructure code to setup, configure and manage a specific service on a given machine. The actual code is grouped into [recipes][chef_recipes] (files inside the subfolder recipes) and consists of [resources][chef_resources] ([dsl][dsl] code blocks inside recipes) . Extended or customized cookbooks can be composed from existing cookbooks using a dependency management tool called [berkshelf][berkshelf]. A large number of excellent community cookbooks can be found at the [Chef Supermarket][chef_supermarket].   

[Chef Documentation][chef_doc]{: .btn .btn-xs .btn-default role=button }
[Chef Supermarket][chef_supermarket]{: .btn .btn-xs .btn-default role=button }
[Berkshelf][berkshelf]{: .btn .btn-xs .btn-default role=button }

</div>
<div class="col-md-6">

<h2>TD Infrastructure Development</h2>
Red-Green-Refactor is the [TDD Cycle][tdd] in Software Engineering: First write a test that specifies the desired behavior, then develop the code that implements that behavior. With Infrastructure Testing Frameworks like [Serverspec][serverspec] or [Bats][bats] this process can be adapted to Infrastructure Code Development as well.
In this workshop we focus on [Serverspec][serverspec] Tests. [Serverspec][serverspec] provides a [DSL][dsl] with idioms for most of the typical server testing scenarios.
To try out the provisioning code and run all tests locally [testkitchen][testkitchen] is the tool of choice. With this commandline tool you can bootstrap an empty box (kitchen create), provision it with the cookbook you're just creating (kitchen converge) and run all your tests (kitchen verify) on the provisioning result with ease.
Later we will use exact the same kitchen tooling in a central build [pipeline for infrastructure code][envs].

[Testkitchen][testkitchen]{: .btn .btn-xs .btn-default role=button }
[Serverspec][serverspec]{: .btn .btn-xs .btn-default role=button }

</div>
</div>
