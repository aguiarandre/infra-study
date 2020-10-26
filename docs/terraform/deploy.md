# Deploying a configuration

- **Provisioning Resources** 
- Planning Updates
- Using Source Control
- Reusing templates

## The scenario

- IT Ops admin @ Globalmants (global risk assessment company)
- Provision a development environment 
- Web, frontend, database; a DNS server to be deployed at AWS.

## Terraform components

- Terraform executable (written in Go)
- Terraform files [.tf]
- Terraform <u>plugins</u> to interact with providers (AWS, Google)
- Terraform state (current state of your environment)

### What is inside those terraform files

- variables 

```
variable "aws_access_key" {}
variable "aws_secret_key" {}

variable "aws_region" {
    default = "us-east-1"
}
```

- provider 

```
provider "aws" {
    access_key = "var.access_key"
    secret_key = "var.secret_key"
    region = "var.aws_region"
}
```

- data

```
data "aws_ami" "alx" {
    most_recent = true
    owners = ["amazon"]
    filters {}
}
```

- resource
```
resource "aws_instance" "ex" {
    ami = "data.aws_ami.alx.id"
    instance_type = "t2.micro"
}
```

- output
```
output "aws_public_ip" { 
    value = "aws_instance.ex.public_dns"
}
```