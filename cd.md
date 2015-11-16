---
user: __user__
user_firstname: __user_firstname__
user_lastname: __user_lastname__
user_company: __user_company__
user_email: __user_email__
wsappl_name: __wsappl_name__
wsappl_doc_version: __wsappl_doc_version__

title: Continuous Delivery
layout: colpage
pager: true
---
Part 1 - Continuous Delivery
{.lead}

<div class="row" markdown="1">
<div class="col-md-6">

<h2>Example Application</h2>

The Example Application is a simple but multitiered [Phonebook Web Application ][example_deployed] written in Ruby. We use simple scripts to [build][example_script_build], [unittest][example_script_unittest] and [install][example_script_install] the application.

[App UI][example_deployed]{: .btn .btn-xs .btn-default role=button }
[App Sourcecode][example_sourcecode]{: .btn .btn-xs .btn-default role=button }
[Build Script][example_script_build]{: .btn .btn-xs .btn-default role=button }
[Unittest Script][example_script_unittest]{: .btn .btn-xs .btn-default role=button }
[Installer Script][example_script_install]{: .btn .btn-xs .btn-default role=button }

</div>
<div class="col-md-6" markdown="1">

<h2>Sourcecode Repository</h2>

Continuous Delivery Pipelines are triggered by code changes pushed to a central [Sourcecode Repository][central_scm]. In our case we'll use a central Git Repository.
A [Git-Hook-Script][central_scm_hookscript] triggers a pipeline run after each push (Principle: every change triggers the pipeline immediately).

[Central Sourcecode Repo][central_scm]{: .btn .btn-xs .btn-default role=button }
[Git-Hook-Script][central_scm_hookscript]{: .btn .btn-xs .btn-default role=button }
[Git-Hook-Documentation][git_hook_docu]{: .btn .btn-xs .btn-default role=button }

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
<div class="col-md-6" markdown="1">

<h2>Dashboard and parallelizing builds</h2>

Every commit triggers a pipeline run. That means a lot of feedback data gets produced (imagine 3 teams, 7 developers each, committing 2 times per hour -> 50 builds/h). A Dashboard helps spotting potential test failures and the corresponding pipeline jobs. It can also be used to implement a simple 'one button push' deployment to test environments.
To optimize the whole pipeline for throughput it is necessary to parallelize builds in all pipeline stages. Jenkins Plugins like: [Build Flow][jenkins_build_flow], [Workflow][jenkins_workflow] or [Parameterized Trigger][jenkins_trigger] and [Join][jenkins_join] (not recommended) can be used for that purpose.

[Dashboard][dash]{: .btn .btn-xs .btn-default role=button }
[Build Flow Plugin][jenkins_build_flow]{: .btn .btn-xs .btn-default role=button }
[Workflow Plugin][jenkins_workflow]{: .btn .btn-xs .btn-default role=button }
[Parameterized Trigger Plugin][jenkins_trigger]{: .btn .btn-xs .btn-default role=button }
[Join Plugin][jenkins_join]{: .btn .btn-xs .btn-default role=button }

</div>
</div>

<div class="row" markdown="1">
<div class="col-md-6">

<h2>Heise Developer Series</h2>

The authors have published a series of four articles about continuous delivery on [Heise Developer][heise_developer]. The [first article][heise_article1] will cover the [basics][heise_article1] of continuous delivery while the [second][heise_article2] one will elaborate on building up a [commit stage][heise_article2]. The [third articles][heise_article3] deals with setting up a basic [acceptance test stage][heise_article3] and the [fourth article][heise_article4] covers the basics of [Infrastructure as Code][heise_article4].

[Heise: CD Principles][heise_article1]{: .btn .btn-xs .btn-default role=button }
[Heise: Commit Stage][heise_article2]{: .btn .btn-xs .btn-default role=button }
[Heise: Acceptance Test Stage][heise_article3]{: .btn .btn-xs .btn-default role=button }
[Heise: Infrastructure as Code][heise_article4]{: .btn .btn-xs .btn-default role=button }

</div>
</div>
