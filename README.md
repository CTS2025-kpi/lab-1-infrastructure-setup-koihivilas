[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/O_-fUwED)

# Lab1 Infrastructure setup

## 1. Set-up account

I created a Free Tier AWS Account with $180 of free credits.
![](assets/set_up_root_account.png)

## 2b. Create an IAM IC account and Organization

Created an IAM Identity Center account with full admin access.
![](assets/iam_identity_center_full_admin_user_1.png)
![](assets/iam_identity_center_full_admin_user_2.png)

And also created an Organization.
![](assets/aws_organization.png)

## 3-4. Create view-only user (IAM - for instances) with assumed role
![](assets/view_only_role_1.png) 
![](assets/view_only_role_2.png) 
![](assets/view_only_role_3.png) 
![](assets/view_only_role_4.png)

## 5. Create Cloudformation template for IAM policy and role
I auto-generated Cloudformation template for IAM policy and role [iam-role-policy-template-1763864000957.yaml](iam-role-policy-template-1763864000957.yaml).
![](assets/role-policy-template.png)

## 6. VPC
Created VPC according to the task
![](assets/vpc_1.png)

## 7. IaC stack with network resources
Auto-generated Cloudformation template for network resources [lab1-vpc-template-1763857369908.yaml](lab1-vpc-template-1763857369908.yaml).
![](assets/vpc_iac_canvac.png)

## 8. Monthly budget
As I understand two shards will need 2 computing units + coordinator unit. 
I would probably use 3 t3.micro with on-demand plan with 100% utilization which AWS pricing calculator
calculated as the following:
* 3 instances x 0.012 USD On Demand hourly cost x 730 hours in a month = 26.280000 USD
* On-Demand instances (monthly): 26.280000 USD
---
Plus using 3 instances of EBS with 8 GB each would cost:
* 2,190 total EC2 hours / 730 hours in a month = 3.00 instance months
* 8 GB x 3.00 instance months x 0.0952 USD = 2.28 USD (EBS Storage Cost)
* Amazon Elastic Block Store (EBS) total cost (monthly): 2.28 USD
---
So total would be **28.56 USD**
