Terraform Module to provision an EC2 Instance that is running Apache.

Not intended for production use. Just showcasing how to create a public module on Terraform Registry.

```hcl
terraform {

}

provider "aws" {
  # Configuration options
  region = "us-east-1"
}

module "apache" {
    source = "./terraform_aws_apache_example"
    vpc_id = "0000000"
    my_ip_with_cidr = "My_IP_addres/32"
    public_key = "ssh-rsa AAAAB3………………P"
    instance_type = "t2.micro"
    server_name = "Apache Example Server"
}

output "public_ip" {
  value = module.apache.public_ip
}

```