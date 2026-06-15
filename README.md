# 🚀 AWS DevOps CI/CD Pipeline Project

## 📌 Project Overview

This project demonstrates a complete CI/CD (Continuous Integration and Continuous Deployment) workflow using GitHub, Jenkins, Docker, Amazon ECR, and Amazon EC2.

Whenever new code is pushed to the GitHub repository, Jenkins automatically builds a Docker image, pushes it to Amazon ECR, and deploys the latest version to an EC2 instance without manual intervention.

The goal of this project is to understand how modern DevOps practices automate application deployment, improve consistency, and reduce manual effort.

---

## 🏗️ Architecture

```text
Developer
    │
    ▼
GitHub Repository
    │
    ▼
Jenkins Pipeline
    │
    ├── Checkout Source Code
    ├── Build Docker Image
    ├── Tag Docker Image
    ├── Login to Amazon ECR
    ├── Push Image to ECR
    └── Deploy to EC2
                │
                ▼
           Docker Container
                │
                ▼
          Live Website
```

---

## 🛠️ Technologies Used

### ☁️ Cloud Services

* AWS EC2
* AWS ECR

### 🔄 CI/CD

* Jenkins

### 📦 Containerization

* Docker
* Nginx

### 🔧 Version Control

* Git
* GitHub

### 🌐 Frontend

* HTML
* CSS

### 🐧 Operating System

* Linux (Ubuntu)

---

## 🚀 Project Workflow

### 1️⃣ Code Push

The developer pushes code changes to the GitHub repository.

```bash
git add .
git commit -m "Updated website"
git push origin main
```

---

### 2️⃣ Jenkins Pipeline Trigger

Jenkins pulls the latest source code from GitHub.

```groovy
git branch: 'main',
url: 'https://github.com/trupalgorasiya/website-docker-demo.git'
```

---

### 3️⃣ Docker Image Build

Jenkins builds a Docker image using the Dockerfile.

```bash
docker build -t website-docker-demo .
```

---

### 4️⃣ Docker Image Tagging

The image is tagged using:

* Build Number
* Latest Tag

Example:

```text
website-docker-demo1:15
website-docker-demo1:latest
```

This helps maintain image versions and supports rollback strategies.

---

### 5️⃣ Push Image to Amazon ECR

Jenkins authenticates with Amazon ECR and pushes the image.

```bash
docker push image:15
docker push image:latest
```

Amazon ECR acts as a private Docker registry.

---

### 6️⃣ Deploy to EC2

Jenkins connects to the EC2 server using SSH.

```bash
ssh ubuntu@EC2_PUBLIC_IP
```

Deployment process:

1. Login to Amazon ECR
2. Pull latest Docker image
3. Stop existing container
4. Remove old container
5. Start new container

```bash
docker pull latest
docker stop website-demo
docker rm website-demo
docker run -d -p 80:80 website-demo
```

---

### 7️⃣ Website Available

The latest version of the application becomes available through the EC2 Public IP.

```text
http://EC2-PUBLIC-IP
```

---

## 🐳 Dockerfile Explanation

```dockerfile
FROM nginx:alpine

COPY index.html /usr/share/nginx/html/index.html
COPY style.css /usr/share/nginx/html/style.css

EXPOSE 80
```

### 📖 What Happens?

* Pulls lightweight Nginx image
* Copies website files into Nginx web root directory
* Exposes port 80
* Serves static website through Nginx

---

## ⚙️ Jenkins Pipeline Stages

### 📥 Checkout

Fetches latest source code from GitHub.

### 🔨 Build Docker Image

Creates a Docker image from source code.

### 🏷️ Tag Docker Image

Creates versioned image tags.

### 🔐 Login to ECR

Authenticates Docker with Amazon ECR.

### 📤 Push Image to ECR

Uploads Docker image to ECR.

### 🚀 Deploy to EC2

Deploys the latest container on EC2.

---

## 🎯 Key DevOps Concepts Demonstrated

### 🔄 Continuous Integration (CI)

Every code change is automatically built and prepared for deployment.

### 🚀 Continuous Deployment (CD)

New versions are automatically deployed to the target server.

### 📦 Containerization

Application runs inside Docker containers ensuring consistency across environments.

### 🏷️ Image Versioning

Every build receives a unique tag.

```text
Build 1 → image:1
Build 2 → image:2
Build 3 → image:3
```

### 🤖 Automation

No manual deployment steps are required after pushing code.

---

## 🌟 Project Benefits

* ✅ Automated Deployments
* ✅ Faster Release Cycles
* ✅ Reduced Manual Errors
* ✅ Consistent Environments
* ✅ Version-Controlled Deployments
* ✅ Scalable Deployment Workflow

---

## 📚 Learning Outcomes

Through this project, I gained hands-on experience with:

* Jenkins Pipeline Development
* Docker Containerization
* Amazon Elastic Container Registry (ECR)
* Amazon EC2 Deployment
* GitHub Integration
* SSH-Based Remote Deployment
* CI/CD Best Practices
* Linux Server Management

---

## 🔮 Future Improvements

* 🌍 Terraform Infrastructure Provisioning
* 🔗 GitHub Webhook Integration
* ☸️ Kubernetes Deployment
* 🐳 Docker Compose
* 🔀 Nginx Reverse Proxy
* 🔒 SSL using Let's Encrypt
* 📊 Monitoring with Prometheus & Grafana
* 🔵🟢 Blue-Green Deployment Strategy

---

## 🎉 Conclusion

This project demonstrates an end-to-end CI/CD pipeline where application deployment is fully automated using Jenkins, Docker, Amazon ECR, and EC2.

It showcases essential DevOps practices including:

* Continuous Integration (CI)
* Continuous Deployment (CD)
* Docker Containerization
* Image Versioning
* AWS Cloud Deployment
* Deployment Automation

This project helped strengthen my understanding of modern DevOps workflows and cloud-native deployment practices.

---

## 👨‍💻 Author

### Trupal Gorasiya

🚀 DevOps & Cloud Enthusiast
