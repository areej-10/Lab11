
# Lab11

Lab 11: GH CLI Codespaces + AWS + Terraform
Student Name: Areej Fatima

Roll Number: bse-2023-010

Date: January 1, 2026

📖 Project Overview
This lab demonstrates the integration of GitHub CLI, Codespaces, and Terraform to provision AWS infrastructure. Key focus areas include Terraform variable precedence, complex data collections (maps, objects, sets), and the automated deployment of a VPC environment with an Nginx-enabled EC2 instance.

🛠 Task 0: Lab Setup
Initialized the environment using GitHub CLI to create a dedicated repository and Codespace.

Repository: CC_<Name>_<Roll>/Lab11

Environment: GitHub Codespace (Linux)

🏗 Task 1 - 6: Terraform Variables & Collections
In these tasks, I explored the mechanics of Terraform variables, including:

Variable Precedence: Tested the order of operations from default → TF_VAR → terraform.tfvars → -var.

Validation: Implemented Regex patterns to validate CIDR blocks and API tokens.

Sensitivity: Used sensitive = true and ephemeral = true to protect data in logs and state files.

Collections: Compared list, tuple, and set behaviors, specifically how sets handle duplicates.

🌐 Task 8: Networking Infrastructure
Provisioned the core AWS networking components.

Resources Created:
VPC: 10.0.0.0/16

Subnet: 10.0.10.0/24 in me-central-1a.

Internet Gateway: Attached to the VPC for external access.

Default Route Table: Modified to route 0.0.0.0/0 traffic through the IGW.

🖥 Task 9: EC2 & Automation
Deployed an EC2 instance with automated software installation.

Configuration:
Security Group: Restricted SSH (Port 22) to my public IP and opened HTTP (Port 80) to the world.

Key Pair: Generated an Ed25519 key pair via ssh-keygen and registered it with AWS.

User Data: Automated Nginx installation using an external script (entry-script.sh).

Bash

# entry-script.sh
#!/bin/bash
yum update -y
yum install -y nginx
systemctl start nginx
systemctl enable nginx
🧹 Cleanup & Verification
To avoid unnecessary AWS costs, all resources were destroyed.

Command: terraform destroy -auto-approve

State Verification: Confirmed terraform.tfstate reflects the removal of resources
0,taskA_codespace_create_and_list.png,[ ]
1,task1_var_override_with_dash_var.png,[ ]
2,task2_check_terraform_state_api_token.png,[ ]
4,task4_server_config_output.png,[ ]
8,task8_default_route_table_apply.png,[ ]
9,task9_nginx_browser_page.png,[ ]
Clean,cleanup_destroy.png,[ ]
