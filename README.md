# WORK IN PROGRESS
Just trying to update the versions and make it Fedora friendly.

The WIP in the section name below indicates which section is currently being worked on.

# Kubernetes The Hard Way on Azure

This tutorial is designed for [Microsoft Azure](https://azure.microsoft.com) and [Azure CLI 2.0](https://github.com/azure/azure-cli).
It is a fork of the great [Kubernetes The Hard Way](https://github.com/kelseyhightower/kubernetes-the-hard-way) from [Kelsey Hightower](https://twitter.com/kelseyhightower) that describes same steps using [Google Cloud Platform](https://cloud.google.com).

Azure part is based on the superb translation done by [Jonathan Carter - @lostintangent](https://twitter.com/LostInTangent) in this [fork](https://github.com/lostintangent/kubernetes-the-hard-way). He is the one who is really behind the Azure "translation".

This tutorial walks you through setting up Kubernetes the hard way. This guide is not for people looking for a fully automated command to bring up a Kubernetes cluster. If that's you then check out [Azure Container Services](https://azure.microsoft.com/en-us/services/container-service), or the [Getting Started Guides](http://kubernetes.io/docs/getting-started-guides).

Kubernetes The Hard Way is optimized for learning, which means taking the long route to ensure you understand each task required to bootstrap a Kubernetes cluster.

Kubernetes Dashboard configuration has been added at the end of the tutorial, to let you play with the cluster through a UI.

> The results of this tutorial should not be viewed as production ready, and may receive limited support from the community, but don't let that stop you from learning!

## Target Audience

The target audience for this tutorial is someone planning to support a production Kubernetes cluster and wants to understand how everything fits together.

## Cluster Details

Kubernetes The Hard Way guides you through bootstrapping a highly available Kubernetes cluster with end-to-end encryption between components and RBAC authentication.

* [Kubernetes](https://github.com/kubernetes/kubernetes) 1.22.2
* [containerd Container Runtime](https://github.com/containerd/containerd) 1.5.7
* [coredns](https://github.com/coredns/coredns) v1.8.6
* [CNI Container Networking](https://github.com/containernetworking/cni) 1.0.1
* [etcd](https://github.com/coreos/etcd) v3.3.26


## Labs

This tutorial assumes you have access to the [Microsoft Azure](https://azure.microsoft.com). While Azure is used for basic infrastructure requirements the lessons learned in this tutorial can be applied to other platforms.

* [Prerequisites](docs/01-prerequisites.md)
* [Installing the Client Tools(WIP)](docs/02-client-tools.md)
* [Provisioning Compute Resources](docs/03-compute-resources.md)
* [Provisioning the CA and Generating TLS Certificates](docs/04-certificate-authority.md)
* [Generating Kubernetes Configuration Files for Authentication](docs/05-kubernetes-configuration-files.md)
* [Generating the Data Encryption Config and Key](docs/06-data-encryption-keys.md)
* [Bootstrapping the etcd Cluster](docs/07-bootstrapping-etcd.md)
* [Bootstrapping the Kubernetes Control Plane](docs/08-bootstrapping-kubernetes-controllers.md)
* [Bootstrapping the Kubernetes Worker Nodes](docs/09-bootstrapping-kubernetes-workers.md)
* [Configuring kubectl for Remote Access](docs/10-configuring-kubectl.md)
* [Provisioning Pod Network Routes](docs/11-pod-network-routes.md)
* [Deploying the DNS Cluster Add-on](docs/12-dns-addon.md)
* [Smoke Test](docs/13-smoke-test.md)
* [Dashboard](docs/14-dashboard.md)
* [Cleaning Up](docs/15-cleanup.md)
