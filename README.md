Automating CI/CD Deployment Using Jenkins Pipeline
DevOps Internship – Task 2 & 5



This repository contains the implementation of Task 2, where I built and automated a complete CI/CD pipeline using Jenkins, integrated with Docker, GitHub, and DockerHub.
The pipeline automatically builds, tests, dockerizes, and pushes the application image to DockerHub whenever new changes are committed.

# Task 5 — Kubernetes Deployment (Minikube)

This task deploys a Node.js application to a local Kubernetes cluster using Minikube.
Files included:
- deployment.yaml
- service.yaml
- screenshots of cluster, pods, services, scaling, describe output

Steps:
1. Started Minikube with Docker driver
2. Applied deployment.yaml and service.yaml
3. Verified pods and services
4. Accessed app using NodePort
5. Scaled deployment to multiple replicas
6. Described pod for logs/debugging

This completes Task 5.




📌 Objective

To set up a complete CI/CD pipeline using Jenkins for a Node.js web application.
The pipeline performs:

✔ Code checkout
✔ Build & test
✔ Docker image creation
✔ DockerHub authentication
✔ Pushing container images automatically
✔ Post-build cleanup

This aligns with all requirements provided in the Task 2 PDF.

🛠️ Tech Stack & Tools Used
Tool	Purpose
Jenkins	CI/CD automation server
Jenkins Pipeline (Declarative)	Stage-based build pipeline
GitHub	Source code version control
Docker	Containerization of the Node.js app
DockerHub	Hosting & storing container images
Node.js / Express	Sample web application
📁 Repository Structure
.
├── server.js            # Sample Node.js application
├── package.json
├── Dockerfile           # To build Docker image
├── Jenkinsfile          # Jenkins CI/CD pipeline stages
└── README.md            # Documentation

🔧 Setup & Configuration (Step-by-Step)

Below is the exact workflow implemented as part of Task 2.

1️⃣ Install & Configure Jenkins

Installed Jenkins locally using Docker:

docker run --name jenkins -d \
  -p 8080:8080 -p 50000:50000 \
  -v jenkins_home:/var/jenkins_home \
  -v /var/run/docker.sock:/var/run/docker.sock \
  jenkins/jenkins:lts


Unlocked Jenkins using the initial admin password

Installed suggested plugins

Created an admin user

2️⃣ Add DockerHub Credentials in Jenkins

Jenkins → Manage Jenkins → Credentials → System → Global Credentials

ID	Username	Password
dockerhub-creds	DockerHub username	DockerHub access token
3️⃣ Create a Jenkins Pipeline Job

In Jenkins:

New Item → Pipeline

Name: task2-nodejs-pipeline

SCM: Git

Repo URL:

https://github.com/<your-username>/<this-repo>


Script Path:

Jenkinsfile

4️⃣ Pipeline Stages Included (As per Task Requirements)
✔ Stage 1: Checkout

Fetches the code from GitHub.

✔ Stage 2: Install & Build

Installs Node packages and prepares build.

✔ Stage 3: Test

Runs tests (if available).

✔ Stage 4: Docker Build

Builds app image:

docker build -t username/nodejs-demo-app:latest .

✔ Stage 5: Docker Login

Secure login using Jenkins credentials.

✔ Stage 6: Push Image

Pushes Docker image to DockerHub.

✔ Stage 7: Cleanup

Workspace cleaning to maintain build hygiene.

🐳 Docker Image Output

The Jenkins pipeline pushes the image here:

docker pull <your-dockerhub-username>/nodejs-demo-app:latest

📊 Pipeline Execution Screenshot (Add Yours Here)

(Add screenshots of your Jenkins pipeline success here)

Example placeholders:

/screenshots/jenkins-success.png
/screenshots/dockerhub-image.png

🎯 What This Task Demonstrates

✔ Understanding of CI/CD workflow
✔ Ability to create Jenkins pipelines
✔ Secure credential management
✔ Docker image automation
✔ End-to-end deployment workflow
✔ Integration of GitHub → Jenkins → DockerHub

📥 Submission

This repository link is submitted as part of DEVOPS Internship – Task 2, fulfilling all deliverables from the PDF.

🎉 Conclusion

This task showcases a complete, practical DevOps CI/CD pipeline using Jenkins and Docker. It automates every step from code commit → build → test → dockerize → deploy, ensuring fast, consistent, and reliable application delivery.
