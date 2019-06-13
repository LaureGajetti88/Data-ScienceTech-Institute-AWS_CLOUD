# How to install RStudio at creation of instance (use script)



## 1. Reminder of the steps to create an instance

An EC2 instance is a virtual server hosted in Elastic Compute Cloud (EC2) to run applications on the Amazon Web Services (AWS) infrastructure.

source : https://docs.aws.amazon.com/fr_fr/vpc/latest/userguide/VPC_NAT_Instance.html

See the following diagram in the repertory.

Explain steps:

1. Sign in on rosettahub :
   1. Verify the region you're in, if it corresponds to your needs, we choose EU(Ireland) for this tutorial
   2. Click on the big yellow button on the left : "GO TO AWS Console". It will connect to AWS Management Console
2. Write on tool search : EC2 or select it on services AWS
3. Then click on big blue button "Launch an instance"

In the course we work with **Amazon Linux 2 AMI (HVM), SSD Volume Type** - ami-030dbca661d402413 (64 bits x86) / ami-08c5dd5d585629c8f (64 bits Arm) but you can choose another "AMI".

An AMI is a template that contains the software configuration (eg, an operating system, an application server, and applications).

1. Then, to do a free test choose : t2.micro (free in green) and click on "check and throw"

### Stop : At this step we have some modifications to do! 

In the other document , we saw that could "Verify and launch" directly the instance. Now, to install a specific  configuration of serveur we need to do some changements :

1. Click on "Next : configure instance details" :
   1. You can change the network and subnet with your own configuration, but for this tutorial we leave the default settings.
   2. Go on the end of page and enter in "advanced setting"
      1. You can add some script with installation of configuration you want. Our script for install R studio is : 

```
#!/bin/bash
#Update the package manager
#Yum in this case as it is ran on Amazon Linux
sudo yum update -y

#Install R
sudo yum install -y R

#Install RStudio-Server
#https://www.rstudio.com/products/rstudio/download-server/
wget https://download2.rstudio.org/rstudio-server-rhel-1.1.383-x86_64.rpm
sudo yum install -y --nogpgcheck rstudio-server-rhel-1.1.383-x86_64.rpm
sudo rm rstudio-server-rhel-1.1.383-x86_64.rpm

#Install shiny and shiny-server
sudo R -e "install.packages('shiny', repos='http://cran.rstudio.com/')"
wget https://download3.rstudio.org/centos5.9/x86_64/shiny-server-1.5.5.872-rh5-x86_64.rpm
sudo yum install -y --nogpgcheck shiny-server-1.5.5.872-rh5-x86_64.rpm
sudo rm shiny-server-1.5.5.872-rh5-x86_64.rpm

#add user(s)
sudo useradd username
echo username:password | sudo chpasswd
```

Copy and past in the boxe, but before change the last sentence : echo username:password | chpasswd 

Replace username by your proper login you want and your own password.

Then, click next step until step 6 of amazon: Configure the security group.

Here you have to add rule because we need to connect on the serveur that we create to login on Rsutio serveur. (Remark : you can do this step after if you forget to do it at this step). So :

Be careful to configure the Security Group. Hint, RServer uses the port 8787 and Shiny Server the port 3838.
1. Click on "add rules" : choose "custom TCP" for type and add 8787 for port range
2. Click on "add rules" : choose "custom TCP" for type and add 3838 for port range


Remark, before step 6 AWS you can add a Tag for more clarity like "R studio serveur" for your instance.

Then click on "verify and launch", and choose to create a new key or give your own key if you have.

Be patient, the launch of the instance is long.

Then, stop the instance (click right and stop), wait, restart it (why: it seems that when creating Rstudio the server is logging and if you do not stop the instance you can not connect because this script allows one connection at a time).



Then it's ok! go on your instance, keep the ipv4, then go on google and past this ipv4 plus the port of serveur Rstudio like this :

```
http://YOU_IPv4:3838/
```

It's open the interface of Rstudio and you can login with the variable that we have insert in the script configuration.



That's all thanks. Good luck :)
