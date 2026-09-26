# 🚀 Abishek Baskaran — DevOps Portfolio

A personal portfolio website built with **HTML, CSS, Docker, and Nginx**, with a CI/CD pipeline using **Jenkins and GitHub**.

The project demonstrates how source code can be pushed to GitHub, automatically built into a Docker image by Jenkins, and deployed as a Docker container accessible through localhost.

---

## 🏗️ Architecture

```text
Developer
    │
    │ git push
    ▼
 GitHub Repository
    │
    │ Jenkins pulls code
    ▼
   Jenkins
    │
    │ docker build
    ▼
 Docker Image
    │
    │ docker run
    ▼
Docker Container
    │
    │ Port 8099 → 80
    ▼
http://localhost:8099
```

## 📁 Project Structure

```text
portfolio-project/
│
├── index.html
├── Dockerfile
├── Jenkinsfile
└── README.md

# 🎯 Project Objective

The main objective of this project is to demonstrate a simple DevOps workflow:

```
text
Code
 ↓
Git
 ↓
GitHub
 ↓
Jenkins
 ↓
Docker
 ↓
Nginx
 ↓
Application
```

📫 Connect With Me

**GitHub:**
https://github.com/Abis2001

**LinkedIn:**
*Add your LinkedIn profile here*

**Email:**
abishekbaskar23@gmail.com

---

## 📄 License

This project is created for personal portfolio and learning purposes.

---

**Built by Abishek Baskaran 🚀**
