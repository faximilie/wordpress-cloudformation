# Wordpress Cloudformation deployment

This was created as a technical evaluation for a DevOps position.

## Components

This cloudformation template will spin up various resources, and the amount and properties of each resource will change based on if it's production or development.

The main components are:
 - A new VPC
  - 2 new private subnets
    - NAT gateway
  - 2 New public subnets
    - Internet gateway
  - A VPC default security Group
 - An Application Load balancer
 - An EC2 launch config that will install wordpress and set it up for the database
 - An EC2 Security group
 - A database instance
   - A database subnet group
   - A database security group

## Dev VS Prod

You can deploy between dev and prod by changing the `pIsProd` parameter to true or false.

There are some key differences between Dev and Prod, mainly in the size and number of resources.

### Dev

 - 2 EC2 instances at `t2.small`
 - 1 `db.t2.small` database with no Multi-AZ ability

### Prod

 - 6 EC2 instances at `t2.large`
 - 1 `db.m3.large` database with Multi-AZ ability
