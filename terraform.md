# Terraform

## terraform installation

```bash

# for mac
> brew tap hashicorp/tap
> brew install hashicorp/tap/terraform

# for ubuntu

# download the key
> wget -O - https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg

# update the apt source
> echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list

# update the apt cache
> sudo apt update

# install terraform
> sudo apt install terraform

```

## AWS CLI installation

```bash

# download cli
> curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"

# unzip the cli zip file
> unzip awscliv2.zip

# install the aws cli
> sudo ./aws/install

# verify if aws is installed
> aws --version

```

## configure the aws cli

```bash

# open management console: https://aws.amazon.com
# open IAM (Identity and Access Management)
# create a new user
# - user name: aws-admin
# - permissions option: attach policy directly
# - check the AdministratorAccess

# create access token for the new user
# - select the newly created user
# - select "security credentials" tab
# - create access key
# - use case: Command Line Interface (CLI)
# - download the csv file containing access key and secret key


# configure the aws cli
> aws configure

# check the aws cli configuration
> aws s3 ls

```

## VS extension

```bash

> https://marketplace.visualstudio.com/items?itemName=4ops.terraform
> https://marketplace.visualstudio.com/items?itemName=HashiCorp.terraform

```

## commands

```bash

# verify the terraform version
> terraform version

# download the required providers
> terraform init

# format the tf file(s)
> terraform fmt

# check the plan
> terraform plan

# apply the plan and create resources
> terraform apply

# tear down the resources
> terraform destroy


```
