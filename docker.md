---
title: Docker
layout: colpage
pager: true
---
Part 1 - Software Delivery using Docker
{.lead}

<div class="row" markdown="1">
<div class="col-md-6">

<h2>Container Virtualization</h2>

Software sourcecode is usually delivered as binary artefact to a test or production environment. If the production environment consists of physical machines than deploying to production usually means to deliver the compiled sources in some form to the production box, place it in the correct directory and restart some services.
With virtualization one can abstract from the physical box. You can spin up some virtual machines, install the needed middleware and afterwards install the application binary. Scaling out the number of machines takes some minutes (or hours) to create the VMs and provision the needed middleware before the application can be deployed.
Container virtualization goes even one step further. The application binary is packages with all the needed libraries into an image. Based on this image new containers can be created within seconds. This technology makes scaling very easy but requires some new approaches to the way the software is packaged and deployed.

</div>
<div class="col-md-6" markdown="1">

<h2>Docker</h2>

[Docker][dockerio] is build around the namespace functionality in the Linux kernel. It has become a major ecosystem with support from a large community. Docker simplifies the build process of images and the management of containers ([Docker documentation][docker_docs]).
Running docker containers in production requires some cloud infrastructure. Some people might want to use hosted solution on [AWS][aws] or [Google Cloud][gcp] for that purpose while others will favor private cloud solutions like self-hosted [Openstack][openstack], [Docker Swarm][docker_swarm] or [Kubernetes][kubernetes].

[Docker][dockerio]{: .btn .btn-xs .btn-default role=button }
[Docker Docs][docker_docs]{: .btn .btn-xs .btn-default role=button }
[AWS][aws]{: .btn .btn-xs .btn-default role=button }
[Google Cloud][gcp]{: .btn .btn-xs .btn-default role=button }
[Openstack][openstack]{: .btn .btn-xs .btn-default role=button }
[Docker Swarm][docker_swarm]{: .btn .btn-xs .btn-default role=button }
[Kubernetes][kubernetes]{: .btn .btn-xs .btn-default role=button }

</div>
</div>
