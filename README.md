# Continuous Deployment Pipeline for Laravel Application on EC2 Instance

This repository contains the necessary configurations and instructions to set up a continuous deployment pipeline using GitHub Actions to deploy a Laravel application on an EC2 instance. This pipeline automates the deployment process, making it easier and more efficient to deploy updates to your application. ✨🚀

## Prerequisites 📋

Before setting up the deployment pipeline, make sure you have the following prerequisites:

- AWS Account: You need an AWS account to create an EC2 instance and an RDS instance to deploy the Laravel application. ☁️
- Laravel Application: Create a Laravel application on your local machine and ensure it is working correctly. 🌟
- GitHub Repository: Create a repository on GitHub to host your Laravel application and store the deployment pipeline configurations. 📦

## Steps 🚀

Follow these steps to set up the continuous deployment pipeline:

### 1. Create an AWS EC2 Instance 🖥️

- Launch an EC2 instance with the appropriate configuration, such as an Ubuntu machine image and a t2.micro instance type.
- Create a key pair and download the corresponding .pem file to access the EC2 instance later. 🔑

### 2. Create an AWS RDS Instance 💾

- Create a private subnet group in the AWS RDS console.
- Launch an RDS instance with the MySQL engine in a private subnet.
- Ensure that the security group associated with the RDS instance allows inbound connections from the EC2 instance. 🛡️

### 3. Connect EC2 Instance and RDS Instance 🤝

- Connect remotely to the EC2 instance using SSH and the downloaded .pem file.
- Use the RDS console's "Connect" function to establish a connection between the EC2 and RDS instances by configuring security groups and inbound/outbound rules.

### 4. Install Required Libraries and Applications on EC2 📚

- Connect to the EC2 instance using SSH and install the necessary dependencies: PHP, Composer, MySQL, and Apache2. These are required to deploy the Laravel application. 🛠️

### 5. Set Up GitHub Actions Pipeline ⚙️

- Inside your Laravel application directory, create a directory named `.github/workflows`.
- Create a YAML file named `main.yml` inside the `.github/workflows` directory. This file will define the deployment pipeline.
- Configure the `main.yml` file to trigger the pipeline when changes are pushed to the master branch of the GitHub repository.
- Define the steps in the pipeline, including checking out the repository code, installing Composer dependencies, syncing the code to the EC2 instance using rsync, and running any necessary deployment scripts or commands.
- Set up any required parameters and secret variables inside the GitHub repository's secrets and variables section. 🔧

### 6. Send Slack Webhook Messages 💬

- Create a Slack workspace and configure an incoming webhook integration.
- Obtain the webhook URL provided by Slack.
- Update the `slack.yml` file in the GitHub Actions pipeline to trigger a Slack message after the deployment process is completed. Set the webhook URL to the obtained Slack webhook URL.

## Troubleshooting ❗

If you encounter any issues during the deployment pipeline setup, refer to the following solutions for common problems:

1. **Deployment pipeline failure with PHP environment setup** 

   - Ensure that the PHP version in the EC2 instance matches the required PHP version for your Laravel application.
   - Update the PHP version in the `main.yml` file and the EC2 instance to a compatible version, such as 8.1.

2. **Unable to connect to the EC2 instance with rsync command** 

   - Convert the private key to the PEM format without a passphrase using the ssh-keygen command. This ensures that the key format is compatible with the rsync command.

## Conclusion 

By following the steps outlined in this readme, you can set up a continuous deployment pipeline using GitHub Actions to deploy your Laravel application on an EC2 instance. Enjoy seamless deployments and streamline your development workflow! 🚀✨
