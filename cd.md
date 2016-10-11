---
title: Continuous Delivery
layout: colpage
pager: true
---
Part 2 - Docker based Continuous Delivery
{.lead}

<div class="row" markdown="1">
<div class="col-md-6">

<h2>Example Application</h2>

The Example Application is a simple but multitiered Phonebook Web Application [frontend][example_sourcecode_frontend], [backend][example_sourcecode_backend] written in Ruby. We use simple scripts to [build and test][example_script_buildtest] the application.

[App Sourcecode Frontend][example_sourcecode_frontend]{: .btn .btn-xs .btn-default role=button }
[App Sourcecode Frontend][example_sourcecode_backend]{: .btn .btn-xs .btn-default role=button }
[Build Scripts][example_sourcecode_buildscripts]{: .btn .btn-xs .btn-default role=button }
[Build & Test Script][example_script_buildtest]{: .btn .btn-xs .btn-default role=button }

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

The [1st Stage][commit_stage] aka [Commitstage][commit_stage] checks out the Sourcecode, [builds][example_script_buildtest] the software and runs Unittests and Static Code Analysis. The result is a debian binary package for frontend and backend which can then be build into a [docker image][dockerfile]. This will be pushed to a central [Docker registry][docker_registry] (Principle: only build your binaries once). If and only if the commit stage has been successfull, it triggers the start of the acceptance test stage at the end (Principle: if any part of the pipeline fails, stop the line).

[Commitstage][commit_stage]{: .btn .btn-xs .btn-default role=button }
[Dockerfile][dockerfile]{: .btn .btn-xs .btn-default role=button }
[Docker registry][docker_registry]{: .btn .btn-xs .btn-default role=button }

</div>
<div class="col-md-6">

<h2>Binary Repository</h2>

All Build Artifacts are collected [here][docker_registry]. This is a private Docker registry run in kubernetes and created with kubectrl based on this [project][kubernetes_registry].

[Docker registry][docker_registry]{: .btn .btn-xs .btn-default role=button }
[Kubernetes Registry][kubernetes_registry]{: .btn .btn-xs .btn-default role=button }

</div>
</div>

<div class="row" markdown="1">
<div class="col-md-6">

<h2>Acceptance Test Stage</h2>

All docker images are tested in depth during subsequent stages of the pipeline. In our example we have a [2nd Stage][acceptance_test_stage] aka [Acceptance Test Stage][acceptance_test_stage] running some Integration Tests on a deployed instance of the just-build application. Two things are important: Reuse the docker image you've built in the [Commitstage][commit_stage] (Principle: only build your binaries once) and - second - use universal [Deployment Tooling][deployment_script] to deploy the image to the cluster environment. (Principle: deploy the same way to every environment).  

[Acceptance Test Stage][acceptance_test_stage]{: .btn .btn-xs .btn-default role=button }
[Deployment Script][deployment_script]{: .btn .btn-xs .btn-default role=button }

</div>
<div class="col-md-6" markdown="1">

<h2>Dashboard and parallelizing builds</h2>

Every commit triggers a pipeline run. That means a lot of feedback data gets produced (imagine 3 teams, 7 developers each, committing 2 times per hour -> 50 builds/h). A Dashboard helps spotting potential test failures and the corresponding pipeline jobs. It can also be used to implement a simple 'one button push' deployment to test environments.
To optimize the whole pipeline for throughput it is necessary to parallelize builds in all pipeline stages. The Jenkins [Pipeline Plugin][jenkins_pipeline] can be used for that purpose. For visualization the new [blue ocean ui][jenkins_blueocean] can be used.

[Pipeline Plugin][jenkins_pipeline]{: .btn .btn-xs .btn-default role=button }
[Blueocean UI][jenkins_blueocean]{: .btn .btn-xs .btn-default role=button }

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
