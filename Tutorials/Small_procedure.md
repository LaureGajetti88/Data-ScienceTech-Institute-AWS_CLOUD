# Overview of procedure

**Contest :**

This document is being created. Thank you for your understanding

## Prerequisites

1. Create an account for AWS : https://signin.aws.amazon.com/
2. Create a rosettabuh account : https://www.rosettahub.com/console/Logon.aspx#FederatedDashboard



For this tutorial, we use free option on aws services. But maybe you need to credit your account to create another instance.

## How to create an instance

An EC2 instance is a virtual server hosted in Elastic Compute Cloud (EC2) to run applications on the Amazon Web Services (AWS) infrastructure.

source : <https://docs.aws.amazon.com/fr_fr/vpc/latest/userguide/VPC_NAT_Instance.html>

See the following diagram in the repertory.

Explain steps : 

1. Sign in on rosettabuh :
   1. Verify the area where you are, if it correspond at your needs, we choose EU(Ireland) for this tutorial
   2. And click on the big yellow button on the left : "GO TO AWS Console". It will connect to AWS Management Console
2. Write on tool search : EC2 or select it on services AWS 
3. Then click on big blu button "Launch an instance"

In the course we work with **Amazon Linux 2 AMI (HVM), SSD Volume Type** - ami-030dbca661d402413 (64 bits x86) / ami-08c5dd5d585629c8f (64 bits Arm) but you can choose another "AMI".

An AMI is a template that contains the software configuration (eg, an operating system, an application server, and applications).

4. Then, to do a free test choose : t2.micro (free in green) and click on "check and throw"
   1. Click always next, just verify you are on default parameter
   2. for the final step :
      1. Create a new pair of keys
      2. Or choose your keys if you have already key
5.  "Launch and throw" : Felicitation, we created our first instance!

## How to create a VPC

A virtual private cloud (VPC) is a virtual network dedicated to your AWS account. It is logically isolated from other virtual networks in the AWS cloud. You can launch your AWS resources, such as Amazon EC2 instances, in your VPC.
When you create a VPC, you must specify an IPv4 address range for the VPC in the form of a Classless Inter-Domain Routing (CIDR) address block, for example, 10.0.0.0/16. This is the primary CIDR block for your VPC. 

source : https://docs.aws.amazon.com/fr_fr/vpc/latest/userguide/VPC_Subnets.html

See the following diagram in the repertory.

Explain steps : 

1. Sign in on rosettabuh :
   1. Verify the area where you are, if it correspond at your needs, we choose EU(Ireland) for this tutorial
   2. And click on the big yellow button on the left : "GO TO AWS Console". It will connect to AWS Management Console
2. Write on tool search : VPC or in Networking and Content Delivery choose VPC
3. Verify your chosse area. Specific VPC are not all available, you need to take care in function what you want to do.

By defaut, you have 2 VPC existants by AWS and rosettaHub

4. We can create our VPC, click on "create VPC" blu button in the header.



#### TO DO



## How to create an security group

A security group acts as a virtual firewall for your instance to control incoming and outgoing traffic. When you launch an instance in a VPC, you can assign up to five security groups to the instance. Security groups act at the instance level, not at the subnet level. Therefore, each instance in a subnet of your VPC could be assigned to a different set of security groups. If you do not specify a particular group at launch, the instance is automatically assigned to the default security group for the VPC.
For each security group, you add rules that control incoming traffic to instances and a separate set of rules that control outgoing traffic. This section describes the basics you need to know about security groups for your mail order and its rules.
You can define network ACLs using rules similar to your security groups to add an additional layer of security to your VPC. For more information about the differences between security groups and network ACLs, see the section

source : <https://docs.aws.amazon.com/fr_fr/vpc/latest/userguide/VPC_SecurityGroups.html>

#### TO DO