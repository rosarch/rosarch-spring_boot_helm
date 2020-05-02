# Collection of useful commands and other handy info

## k8 related stuff

### kubectl get pods
`kgp` 



This repository provides the [terraform](https://www.terraform.io/) configurations for provisioning an [EKS cluster](https://aws.amazon.com/eks/) on AWS.

NOTE: For completeness and full code examples, this codebase does not make use of the [Terraform registry](https://registry.terraform.io/)

A number of common modules (EG. The AWS VPC) _could_ be replaced by re-usable ones from the registry. For example the VPC could be configured utilising the verified [AWS VPC module](https://registry.terraform.io/modules/terraform-aws-modules/vpc/aws/2.33.0)

## Pre-Requisites

The repository assumes that you have installed Terraform and configured it to allow access to your (or the target) AWS account.

## Directory Structure

```
├── LICENSE
├── README.md
├── environments
│   ├── dev.tfvars
│   └── prod.tfvars
├── main.tf
└── modules
    └── vpc
        ├── variables.tf
        └── vpc.tf
        ...
└── state
...
```

The **main.tf** file is where terraform will start its executing. 

The **modules** directory contains re-usable modules for each part of our infrastructure. Each module has configurable variables which are then configured according to each environment - for example **dev.tfvars**

The **state** directory contains the terraform configuration for initialising the remote state.

## Instructions

### Preparation

**Output your public key**

`cat ~/.ssh/id_rsa_eks_cluster.pub`

**Update code with your public key**

Locate the environments/dev/variables.tf file

Replace the `ssh-rsa REPLACE_ME` with your public key.

So 
