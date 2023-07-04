# Creating AWS EC2 Instances Using Terraform (SSH with Putty)

# Create 
- an EC2 instance. Here I have created using RHL CentOS Linux Ami
- create key pair. Here I have created .ppk
- an IAM user in AWS then attach administrator policy then create a secret key, secret access key 
- find out ami ID from your AWS EC2 ami ID

# Putty
- install then open putty, add public ip with SSH
- connect putty with .ppk file stored in your local machine

# Commands
- ec2-user
- sudo yum update -y
- sudo yum install -y yum-utils
- sudo yum-config-manager --add-repo https://rpm.releases.hashicorp.com/RHEL/hashicorp.repo
- sudo yum -y install terraform
- terraform  (just to recheck terraform up or not!)
- mkdir terraform
- cd terraform
- vi terraform.tf

# Insert

- provider "aws" {
- region = "us-east-1"
- access_key = "AKIAjhhuhwj5623212"
- secret_key = "NTtkhfsjfbnknsmlsmlmlm1425"
- }

- resource "aws_instance" "us-east-1" {
  - ami           = "ami-026ebd4cfe2c043b2"
  - instance_type = "t2.micro"
  - key_name= "your_ppk"
- }


- resource "aws_security_group" "main" {
  - egress = [
    - {
      - cidr_blocks      = [ "0.0.0.0/0", ]
      - description      = ""
      - from_port        = 0
      - ipv6_cidr_blocks = []
      - prefix_list_ids  = []
      - protocol         = "-1"
      - security_groups  = []
      - self             = false
      - to_port          = 0
    - }
  - ]
 - ingress                = [
   - {
     - cidr_blocks      = [ "0.0.0.0/0", ]
     - description      = ""
     - from_port        = 22
     - ipv6_cidr_blocks = []
     - prefix_list_ids  = []
     - protocol         = "tcp"
     - security_groups  = []
     - self             = false
     - to_port          = 22
  - }
  - ]
- }


# Next Commands
- Press Esc, then :wq!
- terraform init
- terraform plan 
- terraform apply
- yes
# EC2 Instance Created !! Check your AWS console
# after finishing the lab, please do not forget to destroy the running ec2 instances
- pass destroy command: terraform destroy
- No running EC2 instance existed now!
# Please consider sharing it with your peers/team. Thank YOU
