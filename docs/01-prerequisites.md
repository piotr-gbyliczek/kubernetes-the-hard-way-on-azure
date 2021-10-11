# Prerequisites

## Microsoft Azure

This tutorial leverages the [Microsoft Azure](https://azure.microsoft.com) to streamline provisioning of the compute infrastructure required to bootstrap a Kubernetes cluster from the ground up. [Sign up](https://azure.microsoft.com/free/) for $200 in free credits. In Azure Free Trial there is a limit of 4 Cores available, therefore tutorial instructions must be changed to create 4 nodes instead of 6 (2 controllers and 2 workers).

[Estimated cost](https://azure.microsoft.com/pricing/calculator/) to run this tutorial: $0.4 per hour ($10 per day).

> The compute resources required for this tutorial will not exceed the Microsoft Azure free tier.

## Microsoft Azure Cloud Platform SDK

### Install the Microsoft Azure CLI 2.0

Follow the Microsoft Azure CLI 2.0 [documentation](https://github.com/azure/azure-cli#installation) to install and configure the `az` command line utility.

Verify the Microsoft Azure CLI 2.0 version is 2.1.0 or higher:

```shell
az --version
```

In case you have access to more than one subscription, you can set default subscription with: 
```shell
az account set --subscription <subscription-id>
```

### Create a default Resource Group in a location

The guide assumes you've installed the [Azure CLI 2.0](https://github.com/azure/azure-cli#installation), and will be creating resources in the `uksouth` location, within a resource group named `kubernetes`. To create this resource group, simply run the following command:

```shell
az group create -n kubernetes -l uksouth
```

> Use the `az account list-locations` command to view additional locations.

You can use the following command to set default location:
```shell
az config set defaults.default-location=<location>
```

## Running Commands in Parallel with tmux

[tmux](https://github.com/tmux/tmux/wiki) can be used to run commands on multiple compute instances at the same time. Labs in this tutorial may require running the same commands across multiple compute instances, in those cases consider using tmux and splitting a window into multiple panes with `synchronize-panes` enabled to speed up the provisioning process.

> The use of tmux is optional and not required to complete this tutorial.

![tmux screenshot](images/tmux-screenshot.png)

> Enable `synchronize-panes`: `ctrl+b` then `shift :`. Then type `set synchronize-panes on` at the prompt. To disable synchronization: `set synchronize-panes off`.

Next: [Installing the Client Tools](02-client-tools.md)
