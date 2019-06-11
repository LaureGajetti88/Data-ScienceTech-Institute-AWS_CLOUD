# Summary of course on AWS 

[TOC]

## What we have done

1. Create an instance on AWS
2. Create a VPC (NAT)
   1. Public
   2. Private
3. Create security groupe : firewall 
   1. how to ping an address
4. Use script to create automatically configuration of instance 
   1. ex : install R studio, jupiter...
5. Elastic load balance (ELB)

We explore a Scenario on AWS : https://docs.aws.amazon.com/fr_fr/vpc/latest/userguide/VPC_Scenario2.html


**For the thirds points**, please refer to a tutorial repertory which explain this with more details.

The point 4 and 5 will be resume later.

## The most important to know for working on AWS

**All** on the cloud have a price. **Be carefull** of all what you do.

You have two types of architecture :

1. Multi-VPC
2. Multi-Account

In this document, as the course,  we work with the case 1 : Multi-VPC



## Keywords :

- Igw-id : Boxe to have acess on internet (custom route table) it's Public!
- NAT : Network Adress Translation (IP, router)
- ELB : Elastic Load Balancing
- VPC : Amazone Virtual Private Cloud



## Others Recommandations if you work with AWS :

1. Take a backup : Try to work we 2 different area
2. be careful with notion of public and private
3. Create security group
4. Be very careful with the key-access. If you lost your key she is really and totaly lost. You need to generate another key and change all dependences.
