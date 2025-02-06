# E-Commerce Platform Deployment with Git, Linux and AWS

## SCENARIO
You have been assigned to develop one e-commerce website for a new online marketplace named "MarketPeak." This pltform will feature product listings, a shopping cart and user authentication. Your objective is to utilize Git for version control, develop the platform in a linux environment and deploy it on an AWS EC2 instance. You can find a suitable website template at tooplate.com to kickstart your development.

## First and foremost configure your git username and email if not already set
### **git config --global user.name "olamidey-io"**
### **git config --global user.email "ibrahimolamide999@gmail.com"**

## Initialize Git Repository
Create the directories and do git init

## Obtain and prepare the E-commerce website template
Instead of developing the website from scratch, i can use a pre-existing template from "tooplate.com". This allows me focus moe on the deployment and operational aspect rather than web development.
* Download a project template from **tooplate.com**
* Extracted the downloaded template into my project directory
* Add all files to the staging area - **Run git add .**
* Commit the changes - **git commit -m "Initial commit: Added eCommerce website template"**
* I added my remote repository - **git remote add origin https://github.com/olamidey-io/My_PBL_Ecommerce.git**
* Push the code to Github - **git branch -M main**
* **git push -u origin main**

## AWS DEPLOYMENT
* Launch an EC2 instance: search ec2 - click launch instance - Name the instance (Ecommerce-sever) - select Amazon linux as AMI OS - instance type (t3 micro free tier) - create new key pair and download - setup security group - launch instance 
* Connect to the EC2 instance through ssh: Once my instance started running, I connected to it from my local machine using. first move the downloaded key pair into the project directory. copy the path to the key pair and you also have to know your public ip address. then run the command - **ssh -i "C:\Users\user\Documents\MY_PBL\My-PBL-MarketPeak-Ecommerce\Ecommerce-key.pem" ec2-user@13.60.199.183.** This connects you straight to the EC2 instance through ssh.
* Cloning the repository on the linux server: Before deploying my ecommerce platform, i need to clone the github repository to my AWS EC2 instance . This is me authenticating with github and chosing between ssh or http for the cloning.
* Since its the first time, you need to first install git
* I will revisit cloning with ssh method since its more secured.

## Installing Apache webserver on EC2:
**Apache HTTP server (htppd)** is a widely used web server that serves HTML files and content over the internet. Note that httpd is the software name for apache on systems using yum package manager. Installing it on Linux EC2 server allows you to host **MarketPeak Ecommerce** site. Then run the commands below
* sudo yum update -y
* sudo yum install httpd -y
* sudo systemctl start httpd
* sudo systemctl enable httpd

This first updates the linux server and then installs htppd (Apache), starts the web server and ensures it automatically starts on server boot.

### Configure httpd for website
* To serve the website from the ec2 instance, i need to configure httpd to point to the directory on the linux server where the website code files are stored, usually in /var/www/html
* So prepare the web directory by clearing the default httpd web directory and copy MarketPeak Ecommerce files into it.
* sudo rm -rf /var/www/html/*
* sudo cp -r ~/My_PBL_Ecommerce/* /var/www/html

The directory /var/www/html/ is a standard directory structure on linux systems that host web content, particularly for the Apache HTTP server. When you install Apache on linux system, the installation process automatically creates this directory.
* Apply these changes by reloading httpd service - **sudo systemctl reload httpd**

## Access website from browser
Make sure the index.html files are in the correct location, else the site will not load when you enter the public ip. You will only see "it work!". 
To confirm, run **ls -l /var/www/html**, you should see the website files listed (HTML, PHP etc)

