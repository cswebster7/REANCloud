# REAN Cloud DevOps Assignment 1 README

This will launch an AWS EC2 instance and install WordPress on the server. CloudFormation will also create a VPC, a 10.0.0.0/24 subnet, an Internet Gateway with necessary public routes, and a security group that allows http and ssh access.

## Preliminary Steps

First, you must set the AWS credentials in order to connect to the AWS account:

    $ export AWS_ACCESS_KEY_ID="[ACCESS KEY]"
    $ export AWS_SECRET_ACCESS_KEY="[SECRET ACCESS KEY]"

Also, an AWS Key Pair must be generated. This assumes that a Key Pair has been created named "key_name".

## How To Run

Begin by running the Ansible playbook, start.yml:

    $ ansible-playbook start.yml

This will prompt you for three inputs, necessary to setup WordPress. Specify a database username, a database password, and a database root password.

The playbook will then call role ansible/main.yml and launch the AWS CloudFormation stack through the template CloudFormation.yaml, which will create all the resources, start the EC2 instance, and install WordPress.

When the stack has completed creation, the URL of the newly created WordPress webserver will be displayed as below:

    $ "msg": "The WordPress server is online at http://ec2-34-205-172-39.compute-1.amazonaws.com/wordpress"
