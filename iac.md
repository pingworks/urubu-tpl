---
user: __user__
user_firstname: __user_firstname__
user_lastname: __user_lastname__
user_company: __user_company__
user_email: __user_email__
wsappl_name: __wsappl_name__
wsappl_doc_version: __wsappl_doc_version__

title: IaC
layout: colpage
pager: false
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

[Chef Documentation][chef_doc]{: .btn .btn-xs .btn-default role=button }

</div>
<div class="col-md-6" markdown="1">

<h2>3 Phase VM Creation Process</h2>

<img src="img/img1.png" class="img-thumbnail" />

</div>
</div>
--
<div class="row">
<div class="col-md-6">

<h2>Commitstage</h2>

The [1st Stage][commit_stage] aka [Commitstage][commit_stage] checks out the Sourcecode, [builds][example_script_build] the software and runs [Unittests][example_script_unittest] and Static Code Analysis. The result is a (set of) binary package(s) which will be deployed into a central [Binary Repository][binary_repo] (Principle: only build your binaries once). If and only if the commit stage has been successfull, it triggers the start of the acceptance test stage at the end (Principle: if any part of the pipeline fails, stop the line).

[Commitstage][commit_stage]{: .btn .btn-xs .btn-default role=button }
[Binary Repository][binary_repo]{: .btn .btn-xs .btn-default role=button }

</div>
<div class="col-md-6">

<h2>Binary Repository</h2>

All Build Artifacts are collected [here][binary_repo]. We have chosen a very simple Binary Artifact Repo Solution: A [folder structure][binary_repo] on a ssh-accessible Server Instance with an Apache Web Server as [Frontend][binary_repo]. We created a set of Scripts to handle CRUD Operations on this [Binary Repo][binary_repo].

[Binary Repository][binary_repo]{: .btn .btn-xs .btn-default role=button }
[Create New Folderstructure Script][binary_repo_create]{: .btn .btn-xs .btn-default role=button }
[Upload Artifacts Script][binary_repo_upload]{: .btn .btn-xs .btn-default role=button }

</div>
</div>

<div class="row" markdown="1">
<div class="col-md-6">

<h2>Acceptance Test Stage</h2>

All binaries are tested in depth during subsequent stages of the pipeline. In our example we have a [2nd Stage][acceptance_test_stage] aka [Acceptance Test Stage][acceptance_test_stage] running some Integration Tests on a deployed instance of the just-build application. Two things are important: Reuse the binaries you've built in the [Commitstage][commit_stage] (Principle: only build your binaries once) and - second - use universal Deployment Tooling to [download][download_scipt] and [install][example_script_install] the binaries on the [Test Environment][test_env] (Principle: deploy the same way to every environment).  

[Acceptance Test Stage][acceptance_test_stage]{: .btn .btn-xs .btn-default role=button }
[Download Script][download_scipt]{: .btn .btn-xs .btn-default role=button }
[Installer Script][example_script_install]{: .btn .btn-xs .btn-default role=button }
[Test Environment][test_env]{: .btn .btn-xs .btn-default role=button }

</div>
</div>
