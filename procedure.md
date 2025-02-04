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
