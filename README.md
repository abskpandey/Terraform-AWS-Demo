# Terraform AWS Infrastructure Setup

Welcome to the Terraform AWS Infrastructure setup repository. This repository contains Terraform code to automate the creation and configuration of essential AWS infrastructure components. Below is a detailed guide on what the code does and how to use it.

## Table of Contents

- [Prerequisites](#prerequisites)
- [Directory Structure](#directory-structure)
- [Usage](#usage)
  - [Initialization](#initialization)
  - [Execution](#execution)
- [Resources Created](#resources-created)
- [Configuration](#configuration)
- [Notes](#notes)
- [License](#license)

## Prerequisites

Before using this Terraform configuration, ensure you have the following:

1. **Terraform:** Download and install Terraform from [Terraform's official website](https://www.terraform.io/downloads.html).
2. **AWS CLI:** Configure your AWS CLI with appropriate access credentials. You can install it from [AWS CLI installation page](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html).
3. **An AWS Account:** Ensure you have access to an AWS account with appropriate permissions to create the resources defined in this configuration.

## Directory Structure

The repository contains the following main files:

- `main.tf`: Contains the Terraform code for creating the VPC, Internet Gateway, Route Table, Subnet, Security Group, Network Interface, and the Ubuntu server.
- `variables.tf`: Defines the variables used in the `main.tf` file.
- `outputs.tf`: Defines the output values to retrieve information about the created resources.

## Usage

### Initialization

1. Clone the repository:

   ```bash
   git clone https://github.com/your-repo/terraform-aws-infrastructure.git
   cd terraform-aws-infrastructure
   ```

2. Initialize Terraform:

   ```bash
   terraform init
   ```

   This command will download the necessary Terraform providers and set up the working directory.

### Execution

1. Review the configuration:

   ```bash
   terraform plan
   ```

   This command will show you the resources that will be created or modified.

2. Apply the configuration:

   ```bash
   terraform apply
   ```

   Confirm the prompt to proceed with the creation of resources.

3. To destroy the created resources:

   ```bash
   terraform destroy
   ```

   Confirm the prompt to delete the resources.

## Resources Created

The Terraform code in this repository performs the following tasks:

1. **Create a VPC:** A Virtual Private Cloud (VPC) is created to isolate resources.
2. **Create an Internet Gateway:** An Internet Gateway is attached to the VPC to allow external internet access.
3. **Create a Custom Route Table:** A route table is created to manage routing for the VPC.
4. **Create a Subnet:** A subnet is created within the VPC for resource placement.
5. **Associate Subnet with Route Table:** The created subnet is associated with the custom route table.
6. **Create a Security Group:** A security group is created to allow inbound traffic on ports 22 (SSH), 80 (HTTP), and 443 (HTTPS).
7. **Create a Network Interface:** A network interface is created with an IP address in the created subnet.
8. **Assign an Elastic IP:** An Elastic IP is associated with the network interface for stable IP addressing.
9. **Create an Ubuntu Server:** An Ubuntu server is provisioned with Apache2 installed and enabled.

## Configuration

The following variables can be configured in `variables.tf`:

- `region`: The AWS region where resources will be created.
- `vpc_cidr`: The CIDR block for the VPC.
- `subnet_cidr`: The CIDR block for the subnet.
- `instance_type`: The type of EC2 instance for the Ubuntu server.
- `ami_id`: The AMI ID for the Ubuntu server.

Modify these variables as needed to fit your requirements.

## Notes

- Ensure that your AWS user has sufficient permissions to create and manage the specified resources.
- Be cautious with resource limits and quotas in your AWS account to avoid hitting limits during resource creation.
- Review the Terraform state files to track the state of your infrastructure.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

Feel free to reach out if you have any questions or need further assistance. Happy Terraforming!
