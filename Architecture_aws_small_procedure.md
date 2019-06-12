# Summary of course on AWS 

[TOC]

## What we have done

1. Create an instance on AWS
2. Create a VPC (NAT)
   1. Public
   2. Private
3. Create security group: firewall 
   1. how to ping an address
4. Use script to configure instance automatically
   1. ex : install R studio, jupyter...
5. Elastic load balance (ELB)

We explore a Scenario on AWS : https://docs.aws.amazon.com/fr_fr/vpc/latest/userguide/VPC_Scenario2.html


**For the third point**, please refer to a tutorial repertory which explains this with more details.

The point 4 and 5 will be completed later.

## The most important thing to know when working on AWS

**Everything** on the cloud has a price. **Be carefull** of anything you do. 

You have two types of architecture :

1. Multi-VPC
2. Multi-Account

In this document, as the course,  we work with the case 1 : Multi-VPC

## Keywords :

- Igw-id : Box to have acess on internet (custom route table) it's Public. Internet gateway. 
- NAT : Network Address Translation (IP, router)
- ELB : Elastic Load Balancing
- VPC : Amazon Virtual Private Cloud



## Others Recommandations if you work with AWS :

1. Make a backup: Try to work with 2 different areas
2. Be careful with notion of public and private
3. Create security groups
4. Be very careful with the key-access. If you lost your key that's it. You need to generate another key and change all dependencies.
