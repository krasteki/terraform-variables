# This Repo contains Terraform configuration which is deploying a web application on AWS.

The supporting infrastructure includes a VPC, Public and Private subnets, load balancer, and EC2 instances

Overview of the infrastructure 

<img width="865" alt="image" src="https://user-images.githubusercontent.com/51786552/154634342-122e1e57-b9db-48e4-a641-e536b55146be.png">

The configuration using the following official modules(Modules are small, reusable Terraform configurations that let you manage a group of related resources as if they were a single resource.)

- [VPC](https://registry.terraform.io/modules/terraform-aws-modules/vpc/aws/latest)
- [app_security_group](https://registry.terraform.io/modules/terraform-aws-modules/security-group/aws/latest)
- [lb_security_group](https://registry.terraform.io/modules/terraform-aws-modules/security-group/aws/latest)
- [elb_http](https://registry.terraform.io/modules/terraform-aws-modules/elb/aws/latest)
- [ec2_instances](https://github.com/krasteki/terraform-variables/tree/main/modules/aws-instance) - local in directory modules/aws-instance

### Prerequisites

Some AWS knowledge (what is VPC, public and private subnets, ec2, security groups, load balancer, NAT gateway)

- The [Terraform CLI](https://learn.hashicorp.com/tutorials/terraform/install-cli)
- AWS Credentials [configured for use with Terraform](https://registry.terraform.io/providers/hashicorp/aws/latest/docs#authentication)
- The [git CLI](https://git-scm.com/downloads)

**Note**:Some of the infrastructure in this configuration may not qualify for the AWS free tier. Destroy the infrastructure at the end of the guide to avoid unnecessary charges.

### Before deploy the Infrastucture

- The configuration is parameterized with variables declarations in file called `variables.tf`
- You can change the values of the variables by your needs
- Current inputs will deploy - VPC with 2 public subnets for the loadbalancer, 2 private subnets with 2 ec2 instances in them, tags for the resources and the used region(eu-west-2)

### Create infrastructure

1. Clone the [Terraform variables](https://github.com/krasteki/terraform-variables) GitHub repository for this tutorial.

```
git clone https://github.com/krasteki/terraform-variables.git
```

2. Change to the repository directory.

```
cd terraform-resources
```

3. The configuration in main.tf defines a web application, including a VPC, load balancer, and EC2 instances. Initialize this configuration.

```
terraform init
```

4. Now apply the configuration

```
terraform apply
```
Respond to the confirmation prompt with a yes to create the example infrastructure.

5. Destroy the infrastructure to avoid unnecessary charges.

```
terraform destroy
```
Respond to the confirmation prompt with a yes to create the example infrastructure.
