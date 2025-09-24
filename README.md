****Terraform AWS Project – VPC, EC2, and ALB****
****Project Overview****

This project provisions a highly available web application setup on AWS using Terraform.
It includes:

Custom VPC with 2 public subnets in different Availability Zones.

Internet Gateway + Route Table for external connectivity.

EC2 Instances running Apache web servers.

Application Load Balancer (ALB) distributing traffic between servers.

Security Groups for HTTP and SSH access.

S3 bucket (for storing static files/images).

****Architecture****
 

 Internet
  ↳  Application Load Balancer (ALB)
    - Routes traffic across two servers
    - Performs health checks
    - Ensures high availability
       ↳  EC2 Instance 1 (Apache Web Server)
       ↳  EC2 Instance 2 (Apache Web Server


 ****Project Structure****
    main.tf → Defines AWS resources (VPC, Subnets, ALB, EC2, SG, etc.)

    provider.tf → AWS provider and region settings

    variables.tf → Stores reusable values like CIDR block

    userdata.sh → Bootstrap script for Web Server 1

    userdata2.sh → Bootstrap script for Web Server 2

    README.md → Project documentation

***Steps to Deploy****

Clone the Repository

git clone https://github.com/Dhivya-Dharshini191/terraform-project.git
cd <your-repo>


1.Initialize Terraform

  terraform init

2.Preview the Infrastructure

  terraform plan

3.Deploy the Infrastructure

  terraform apply -auto-approve


Access the Application

Copy the ALB DNS name from Terraform output

Paste it in your browser → You’ll see your hosted web pages

****Sample Output (Web Page)****

Each EC2 instance serves a different HTML page:

Server 1: Shows instance ID + welcome message (Abhishek Veeramalla’s channel).

Server 2: Shows instance ID + welcome message (CloudChamp’s channel).

 ****Clean Up****

4.To avoid extra AWS charges, destroy resources after testing:

  terraform destroy -auto-approve

****Skills Learned****

Infrastructure as Code (IaC) using Terraform

AWS Networking (VPC, Subnets, Route Tables)

High Availability with Load Balancer

Automating server setup using User Data scripts

Managing security groups and traffic flow

  This project demonstrates how to automate cloud infrastructure using Terraform and host a scalable web application on AWS.
