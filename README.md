# DevOps CI/CD Pipeline Project

## Project Overview

This project demonstrates a complete CI/CD (Continuous Integration and Continuous Deployment) pipeline using Jenkins, Docker, GitHub, AWS EC2, and VS Code.

The application is containerized using Docker and automatically deployed through Jenkins whenever code changes are pushed to GitHub.

---

## Technologies Used

- AWS EC2 (Ubuntu Server)
- Jenkins
- Docker
- Git
- GitHub
- VS Code
- Nginx

---

## Project Architecture

Developer (VS Code)
        ↓
Git Push
        ↓
GitHub Repository
        ↓
Jenkins Pipeline
(Build + Deploy)
        ↓
Docker Build
        ↓
Docker Container
        ↓
AWS EC2 Deployment

---

## Project Files

```
project-folder/

├── index.html
├── Dockerfile
├── Jenkinsfile
└── README.md
```

---

## Docker Configuration

Docker image is built automatically using:

```dockerfile
FROM nginx:latest

COPY index.html /usr/share/nginx/html/index.html

EXPOSE 80
```

---

## Jenkins Pipeline

Pipeline stages:

1. Build Docker Image
2. Stop Existing Container
3. Remove Existing Container
4. Deploy New Docker Container

Example pipeline:

```groovy
pipeline {

 agent any

 stages {

  stage('Build') {

   steps {

    sh 'docker build -t devops-app .'

   }

  }

  stage('Deploy') {

   steps {

    sh '''
    docker stop app || true
    docker rm app || true
    docker run -d --name app -p 8081:80 devops-app
    '''

   }

  }

 }

}
```

---

## Deployment Steps

1. Launch AWS EC2 Ubuntu instance
2. Install Docker
3. Install Jenkins
4. Configure GitHub repository
5. Create Dockerfile
6. Create Jenkinsfile
7. Push code to GitHub
8. Configure Jenkins Pipeline
9. Build Jenkins Job
10. Deploy application automatically

---

## Verification

Open browser:

```
http://EC2_PUBLIC_IP:8081
```

Expected Output:

```
Continuous Deployment Successful

Jenkins + Docker + AWS
```

---

## Learning Outcomes

- CI/CD Pipeline Creation
- Jenkins Automation
- Docker Container Deployment
- GitHub Integration
- AWS EC2 Management
- Infrastructure Automation

---

## Author

Madhulatha

DevOps CI/CD Project
