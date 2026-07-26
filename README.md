 

Hero Vired Assignment 

Assignment : CI/CD Pipeline Implementation Using Jenkins 

Objective 

The objective of this assignment is to implement a Continuous Integration and Continuous Deployment (CI/CD) pipeline using Jenkins. The pipeline automates the process of building, testing, and deploying a Flask application whenever changes are pushed to the GitHub repository through GitHub Webhooks. 

 

Tools and Technologies Used 

Jenkins 

GitHub 

GitHub Webhooks 

Python 3 

Flask 

Pytest 

MongoDB 

Amazon EC2 (Amazon Linux) 

Git 

Pip 

 

Architecture Overview 

Developer 
    │ 
    ▼ 
GitHub Repository 
    │ 
    ▼ 
GitHub Webhook 
    │ 
    ▼ 
Jenkins Pipeline 
    │ 
    ├── Build Stage 
    │       │ 
    │       ▼ 
    │ Install Python Dependencies 
    │ 
    ├── Test Stage 
    │       │ 
    │       ▼ 
    │ Execute Unit Tests using Pytest 
    │ 
    └── Deploy Stage 
            │ 
            ▼ 
Deploy Application Files to Staging Environment (/opt/staging) 
 

 

Step 1: Fork the GitHub Repository 

The provided GitHub repository was forked into my personal GitHub account. The repository contains the Flask application along with the Jenkinsfile required for implementing the CI/CD pipeline. 

 
 
Repository Details: 

Property 

Value 

    Repository 

    HV_FLASK_PRACTICE 

    Source Control 

   GitHub 

    Branch 

   main 

 
 
Screenshot: 

 

 

 

Step 2: Install and Configure Jenkins 

Jenkins was installed on an Amazon Linux EC2 instance. 

Configuration included: 

Installing Java 

Installing Jenkins 

Installing Git 

Installing Python 3 and Pip 

Installing required Jenkins plugins 

Starting Jenkins service 

Unlocking Jenkins 

Installing suggested plugins 

Required Plugins 

Git 

GitHub 

GitHub Integration 

Pipeline 

Pipeline: Stage View 

Email Extension Plugin (for notifications) 

Step 3: Configure GitHub Webhook 

A GitHub Webhook was configured to automatically trigger Jenkins whenever code is pushed to the repository. 

Webhook Configuration: 

Property 

Value 

Payload URL 

http://:<Jenkins-Host>:<Jenkins-HostPort>/github-webhook/ 

Content Type 

application/json 

Events 

Just the push event 

Webhook delivery status showed successful execution after each commit. 

Screenshot: 

 

Step 4: Create Jenkins Pipeline 

A Pipeline job was created in Jenkins. 

Pipeline Configuration 

Property 

Value 

Pipeline Type 

Pipeline Script from SCM 

SCM 

Git 

Repository 

GitHub Repository 

Branch 

main 

Script Path 

Jenkinsfile 

The Jenkinsfile was stored in the GitHub repository. 

Screenshot: 

 

 

Step 5: Build Stage 

The Build stage installs all required Python dependencies using the project's requirements.txt file. 

Build Command 

pip3 install -r requirements.txt 
 

This ensures all required libraries are available before executing the application and test cases. 

Screenshot: 

 

 

Step 6: Test Stage 

The Test stage executes all unit test cases using Pytest. 

Test Command 

python3 -m pytest 
 

Pytest validates the functionality of the Flask application before deployment. 

Result 

All test cases executed successfully. 

4 Test Cases Passed. 

Screenshot: 

 

Step 7: Deploy Stage 

After successful execution of all test cases, the application is deployed to a staging environment. 

Deployment Steps 

Create staging directory 

mkdir -p /opt/staging 
 

Copy application files 

cp -rf * /opt/staging/ 
 

Deployment Location 

/opt/staging 
 

This simulates deployment into a staging environment before production deployment. 

Screenshot: 

 

Step 8: Email Notification 

Email notifications were configured using the Jenkins Email Extension Plugin. 

Notification Events 

Build Success 

Build Failure 

Notifications are executed in the Jenkins Post Actions section after pipeline execution. 

Screenshot: 

 

 

Step 9: Jenkins Pipeline Execution 

Whenever a developer pushes changes to the GitHub repository: 

GitHub Webhook triggers Jenkins. 

Jenkins checks out the latest code. 

Build stage installs dependencies. 

Test stage executes unit tests. 

Deploy stage copies the application to the staging environment. 

Email notification is triggered based on the build status. 

Pipeline Flow 

GitHub Push 
     │ 
     ▼ 
GitHub Webhook 
     │ 
     ▼ 
Jenkins 
     │ 
     ▼ 
Build 
     │ 
     ▼ 
Test 
     │ 
     ▼ 
Deploy 
     │ 
     ▼ 
Email Notification 
 

Screenshot: 

 

 

Project Outcome 

The CI/CD pipeline was successfully implemented using Jenkins. 

Achievements 

Successfully integrated GitHub with Jenkins. 

Automated pipeline execution using GitHub Webhooks. 

Automated dependency installation. 

Successfully executed unit tests using Pytest. 

Automated deployment to the staging environment. 

Configured Jenkins email notifications. 

Verified successful pipeline execution after every GitHub commit. 

 

 
