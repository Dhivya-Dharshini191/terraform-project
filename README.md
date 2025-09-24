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
   │
   ▼
┌───────────┐
│   ALB     │  (Application Load Balancer)
└─────┬─────┘
      │
 ┌────┴─────┐
 │          │
▼           ▼
EC2-1     EC2-2
(subnet1) (subnet2)


 ****Project Structure****
├── main.tf          # Infrastructure resources (VPC, Subnets, IGW, ALB, EC2, SG, etc.)
├── provider.tf      # Provider configuration (AWS region, provider version)
├── variables.tf     # Variables for reusability (CIDR, etc.)
├── userdata.sh      # User data script for WebServer 1 (Apache + HTML page)
├── userdata2.sh     # User data script for WebServer 2 (Apache + HTML page)
└── README.md        # Project documentation

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
