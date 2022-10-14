# Create AWS EKS cluster with Terraform
Edit by Mateus Paulo - Based on the HashiCorp tutorial
https://learn.hashicorp.com/terraform/kubernetes/provision-eks-cluster#optional-configure-terraform-kubernetes-provider


Prerequisites
The tutorial assumes some basic familiarity with Kubernetes and kubectl but does not assume any pre-existing deployment.

For this tutorial, you will need:

an AWS account
the AWS CLI, installed and configured
AWS IAM Authenticator
the Kubernetes CLI, also known as kubectl
»Set up and initialize your Terraform workspace
In your terminal, clone the following repository. It contains the example configuration used in this tutorial.

```
$ git clone https://github.com/hashicorp/learn-terraform-provision-eks-cluster
```

Change into the repository directory.

```
$ cd aws-eks-terraform
```

This example repository contains configuration to provision a VPC, security groups, and an EKS cluster. The diagram below shows the architecture this configuration defines:

![alt text](https://mktg-content-api-hashicorp.vercel.app/api/assets?product=tutorials&version=main&asset=public%2Fimg%2Fterraform%2Feks%2Foverview.png)

The configuration is organized across multiple files:

__versions.tf__: sets the Terraform version to at least 1.3. It also sets versions for the providers used by the configuration.

__variables.tf__: contains a region variable that controls where to create the EKS cluster

__vpc.tf__: provisions a VPC, subnets, and availability zones using the AWS VPC Module. The module creates a new VPC for this tutorial so it doesn't impact your existing cloud environment and resources.

__security-groups.tf__: provisions the security groups the EKS cluster will use

__eks-cluster.tf__: uses the AWS EKS Module to provision an EKS Cluster and other required resources, including Auto Scaling Groups, Security Groups, IAM Roles, and IAM Policies.

## Initialize Terraform workspace

Initialize your configuration.

```
terraform init
```

## Provision the EKS cluster
Run ```terraform apply``` to create your cluster and other necessary resources. Confirm the operation with a yes.

This process should take approximately 10 minutes. Upon completion, Terraform will print your configuration's outputs.


## Clean up your workspace
Destroy any resources you create when you are done with this tutorial. Run ```terraform destroy``` and confirm with yes in your terminal.

Enjoy!
