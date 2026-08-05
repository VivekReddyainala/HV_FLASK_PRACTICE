 

Hero Vired Assignment 

Assignment 1 : CI/CD Pipeline Implementation Using Jenkins 

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

     Source  Control 

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
       
       
 

Screenshot: 

 

 

Project Outcome 

The CI/CD pipeline was successfully implemented using Jenkins. 

Achievements 

Successfully integrated GitHub with Jenkins. 

Automated pipeline execution using GitHub Webhooks. 

Automated dependency installation. 

Successfully executed unit tests using Pytest. 

Automated deployment to the staging environment. 

Verified successful pipeline execution after every GitHub commit. 

 

 

 

 

 

 

 

Assignment 2 : GitHub Actions CI/CD Pipeline Implementation for Flask Application 

Objective 

The objective of this assignment is to implement a Continuous Integration and Continuous Deployment (CI/CD) pipeline using GitHub Actions for a Python Flask application. 

The workflow automates the process of installing dependencies, running tests, building the application, and deploying the application to staging and production environments based on GitHub branch and release events. 

 

Tools and Technologies Used 

Tool / Technology 

Purpose 

GitHub 

Source code repository 

GitHub Actions 

CI/CD automation platform 

Python 3 

Application runtime 

Flask 

Web application framework 

Pytest 

Unit testing framework 

Pip 

Python dependency management 

Git 

Version control 

GitHub Secrets 

Secure storage of deployment credentials 

 

Architecture Overview 

Developer 
    │ 
    ▼ 
GitHub Repository 
    │ 
    ├─────────────── Push to main branch 
    │ 
    ▼ 
GitHub Actions Workflow 
    │ 
    ├── Install Dependencies 
    │       │ 
    │       ▼ 
    │   Install Python packages using pip 
    │ 
    ├── Test Stage 
    │       │ 
    │       ▼ 
    │   Execute Pytest test cases 
    │ 
    ├── Build Stage 
    │       │ 
    │       ▼ 
    │   Prepare application for deployment 
    │ 
    ├── Push to staging branch 
    │       │ 
    │       ▼ 
    │   Deploy to Staging Environment 
    │ 
    └── GitHub Release Published 
            │ 
            ▼ 
        Deploy to Production 
 

Step 1: Repository Setup 

A Flask Python application repository was used for implementing the CI/CD pipeline. 

The repository was configured with two branches: 

Property 

Value 

Repository 

Flask Application Repository 

Source Control 

GitHub 

Main Branch 

main 

Deployment Branch 

staging 

The staging branch was created from the main branch to support separate staging and production workflows. 

Commands Used: 

Create staging branch: 

git checkout -b staging 
 
Push staging branch: 

git push -u origin staging 
 
Screenshot: 

 

Step 2: Create GitHub Actions Workflow 

A workflow directory was created inside the repository: 

.github/workflows 
 

A YAML workflow file was created: 

.github/workflows/ci-cd.yml 
 

The workflow defines automated CI/CD jobs executed by GitHub Actions. 

Screenshot: 

 

Step 3: Configure CI Pipeline 

The workflow was configured to execute the following CI stages: 

Install Dependencies 

The required Python packages were installed using pip. 

Command: 

python -m pip install --upgrade pip 
pip install -r requirements.txt 
 

This ensures all application dependencies are available before testing. 

Screenshot: 

 

 

Step 4: Test Stage 

The application test cases were executed using Pytest. 

Command: 

python -m pytest 
 

Pytest validates the functionality of the Flask application before proceeding to deployment. 

Result: 

All test cases passed successfully 
 

Screenshot: 

 

 

Step 5: Build Stage 

After successful completion of tests, the build stage prepares the application for deployment. 

The build stage verifies that the application is ready for deployment. 

Build Step: 

echo "Preparing application for deployment..." 
 

Screenshot: 

 

 

Step 6: Deploy to Staging Environment 

The staging deployment was configured to trigger automatically when changes are pushed to the staging branch. 

Workflow trigger: 

push: 
  branches: 
    - staging 
 

Deployment process: 

Checkout application source code. 

Prepare staging deployment directory. 

Copy application files. 

Complete staging deployment process. 

Deployment location: 

/tmp/staging 
 

Screenshot: 

 

 

Step 7: Deploy to Production Environment 

Production deployment was configured using GitHub Releases. 

Workflow trigger: 

release: 
  types: 
    - published 
 

Deployment flow: 

Create a Git tag. 

Example: 

git tag v1.0 
 

Push the tag: 

git push origin v1.0 
 

Create and publish a GitHub Release. 

GitHub Actions automatically triggers the production deployment job. 

Screenshot: 

 

Step 8: Configure GitHub Secrets 

GitHub Secrets were configured to securely store application configuration values used during the workflow. 

The repository secret was created by navigating to: 

Repository 
→ Settings 
→ Secrets and variables 
→ Actions 
→ New repository secret 

The following secret was added: 

Secret Name 

Value 

MONGO_URI 

mongodb://localhost:27017/test_student_db 

The workflow was updated to use the secret instead of hardcoding the MongoDB connection string. 

env: 
  MONGO_URI: ${{ secrets.MONGO_URI }} 

Using GitHub Secrets helps keep configuration values separate from the workflow file and follows GitHub Actions best practices. 
Screenshot: 

 

 

Step 9: Update README Documentation 

The README.md file was updated with: 

CI/CD workflow explanation 

Branch strategy 

Workflow triggers 

GitHub Secrets configuration steps 

Deployment process 

 

Step 10: GitHub Actions Execution Results 

The workflow execution was verified through the GitHub Actions dashboard. 

Successful workflow runs included: 

Trigger 

Executed Jobs 

Push to main 

Install Dependencies → Test → Build 

Push to staging 

Install Dependencies → Test → Build → Deploy Staging 

Release Published 

Install Dependencies → Test → Build → Deploy Production 

Screenshots: 

 

 

Conclusion 

The GitHub Actions CI/CD pipeline was successfully implemented for the Flask application. 

The pipeline automates: 

Dependency installation 

Application testing 

Build preparation 

Staging deployment 

Production deployment through GitHub Releases 

The implementation demonstrates an automated CI/CD workflow using GitHub Actions following modern DevOps practices. 

 

This format will match your previous Jenkins assignment documentation style, so both submissions will look consistent. 

 

 

 
