# Terraform_AWS_Jenkins_Integration

This repository contains a set of Terraform scripts and configurations to provision an **AWS infrastructure** and set up a **Jenkins server** for **Continuous Integration (CI)** and **Continuous Deployment (CD)**. The project aims to automate the infrastructure provisioning and Jenkins setup for managing and deploying applications on AWS.

## Table of Contents

- [Project Overview](#project-overview)
- [Features](#features)
- [Prerequisites](#prerequisites)
- [Setup and Installation](#setup-and-installation)
- [Usage](#usage)
- [Terraform Commands](#terraform-commands)
- [Jenkins Setup](#jenkins-setup)
- [Technologies Used](#technologies-used)

## Project Overview

The **Terraform AWS Jenkins** project automates the setup of AWS resources required for running Jenkins. The Terraform scripts help in provisioning the following:

1. **AWS EC2 Instance**: A virtual machine to run Jenkins.
2. **AWS Security Groups**: To control network access and firewall rules.
3. **IAM Roles and Policies**: For securely managing AWS services used by Jenkins.
4. **AWS S3 Bucket**: For storing Jenkins build artifacts, logs, etc.
5. **Terraform AWS Provider**: Manages the AWS infrastructure.

This project aims to automate the entire setup process of Jenkins in a cloud environment, making it easy to implement a fully working Jenkins CI/CD pipeline with AWS.

## Features

- **Automated AWS Infrastructure Setup**: Use Terraform to provision all the necessary resources on AWS, such as EC2, Security Groups, S3 Buckets, and IAM roles.
- **Jenkins Installation**: Automated setup of a Jenkins server on an EC2 instance, pre-configured for CI/CD.
- **Customizable**: Easily adjust the configuration to suit different AWS regions, instance types, or any custom requirements.
- **Infrastructure as Code**: Fully managed and reproducible infrastructure setup with Terraform.
- **Cost Optimization**: Control the resources to provision and adjust them to match your budget.

## Prerequisites

To use this project, ensure you have the following tools installed on your local machine:

- **Terraform**: Infrastructure provisioning tool.
  - Install Terraform from [here](https://www.terraform.io/downloads).
- **AWS CLI**: Command Line Interface for AWS.
  - Install AWS CLI from [here](https://aws.amazon.com/cli/).
  - Configure AWS CLI by running `aws configure`.
- **AWS Account**: You need an active AWS account with appropriate permissions to create resources like EC2 instances, IAM roles, and S3 buckets.

## Setup and Installation

Follow these steps to set up and provision the infrastructure using Terraform:

### 1. Clone the Repository

Clone this repository to your local machine:

```bash
git clone https://github.com/KarinyCCTB/TerraformAWS-Jenkins.git
cd TerraformAWS-Jenkins
```

### 2. Configure AWS CLI

Before using Terraform, configure AWS CLI with your AWS credentials:

```bash
aws configure
```

Enter your `AWS Access Key`, `Secret Key`, `Region`, and `Output Format`.

### 3. Initialize Terraform

In the root directory of this repository, initialize Terraform. This will download the necessary providers and modules:

```bash
terraform init
```

### 4. Review Terraform Plan

Before applying changes to your AWS account, review what Terraform will create by running:

```bash
terraform plan
```

### 5. Apply the Terraform Configuration

Once you are satisfied with the plan, apply the configuration to create the infrastructure:

```bash
terraform apply
```

Terraform will prompt you to confirm. Type `yes` and press Enter. Terraform will now create the necessary resources on AWS, including EC2, Security Groups, and IAM roles.

### 6. Access Jenkins

Once the resources are provisioned, Terraform will output the **public IP** address of the EC2 instance running Jenkins. Access Jenkins by navigating to:

```
http://<public-ip>:8080
```

Use the `admin` user and the `initialAdminPassword` to log in. You can find the `initialAdminPassword` in the EC2 instance by checking the Jenkins logs or retrieving the password directly from the instance.

## Usage

Once Jenkins is up and running, you can:

- Configure Jenkins pipelines for your CI/CD workflows.
- Integrate with AWS services like S3, EC2, RDS, etc.
- Set up automated testing and deployment.

### Jenkins Setup

To fully configure Jenkins, you may need to install the following plugins based on your use case:

- **AWS SDK for Jenkins**
- **GitHub Plugin** (if you're using GitHub repositories)
- **Pipeline Plugin** for pipeline-based automation
- **Docker Plugin** (if you're using Docker containers in Jenkins)

### Jenkins Setup for AWS Access

For Jenkins to interact with AWS resources, configure AWS credentials in Jenkins:

1. Go to **Manage Jenkins > Manage Credentials**.
2. Add a new **AWS Credentials** entry with your AWS `Access Key ID` and `Secret Access Key`.
3. Ensure Jenkins is configured to use these credentials when accessing AWS resources.

## Terraform Commands

Here are some useful Terraform commands to manage your infrastructure:

- **Initialize the Terraform working directory**:

    ```bash
    terraform init
    ```

- **Create or update infrastructure**:

    ```bash
    terraform apply
    ```

- **Destroy infrastructure** (e.g., to clean up the resources):

    ```bash
    terraform destroy
    ```

- **Check the execution plan** (dry run):

    ```bash
    terraform plan
    ```

## Technologies Used

- **Terraform**: Infrastructure as Code tool used for provisioning and managing AWS resources.
- **AWS EC2**: Virtual machines used to host Jenkins.
- **AWS IAM**: Manages access and permissions for AWS services.
- **AWS S3**: Used for storing Jenkins build artifacts and logs.
- **Jenkins**: Automation server for continuous integration and delivery.
- **AWS Security Groups**: Used to control network traffic to and from EC2 instances.
