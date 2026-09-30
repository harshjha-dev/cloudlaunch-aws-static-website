# ☁️ CloudLaunch — AWS Static Website Deployment

CloudLaunch is a simple static website deployed on **Amazon Web Services (AWS)** using an **EC2 instance**, **Amazon Linux**, and **Nginx**.

The project demonstrates the basic workflow of taking a website from local development, storing the code on GitHub, deploying it to an AWS EC2 server, and serving it publicly through Nginx.

## 🏗️ Architecture

```text
HTML / CSS
    │
    ▼
 GitHub
    │
    ▼
 AWS EC2
    │
    ▼
 Amazon Linux
    │
    ▼
  Nginx
    │
    ▼
 Internet 🌐
```

## 🛠️ Technologies Used

* **HTML5 / CSS3** — Website
* **Git** — Version control
* **GitHub** — Source-code repository
* **AWS EC2** — Cloud server
* **Amazon Linux 2023** — Server operating system
* **Nginx** — Web server
* **SSH** — Remote server administration

## 🚀 Deployment Process

### 1. Create the website

The website was developed locally using HTML and CSS.

### 2. Initialize Git

The project was initialized as a Git repository and the website files were committed.

```bash
git init
git add website/
git commit -m "Initial CloudLaunch website"
```

### 3. Push to GitHub

The project source code was pushed to the GitHub repository.

```text
https://github.com/harshjha-dev/cloudlaunch-aws-static-website
```

### 4. Launch AWS EC2

An EC2 instance was created using:

* Amazon Linux 2023
* t3.micro
* SSH key authentication
* Public IPv4 address

The security group allowed:

* SSH — TCP 22 — My IP
* HTTP — TCP 80 — Anywhere IPv4

### 5. Configure the EC2 server

The server packages were updated and Nginx was installed.

```bash
sudo dnf update -y
sudo dnf install nginx -y
```

Nginx was started and enabled to start automatically after server boot.

```bash
sudo systemctl start nginx
sudo systemctl enable nginx
```

### 6. Clone the GitHub repository

The project was downloaded directly onto the EC2 server:

```bash
git clone https://github.com/harshjha-dev/cloudlaunch-aws-static-website.git
```

### 7. Deploy the website with Nginx

The website files were copied into Nginx's document root:

```bash
sudo cp -r cloudlaunch-aws-static-website/website/* /usr/share/nginx/html/
```

Nginx then served the website publicly through the EC2 instance's public IP address.

## 🔍 Verification

Nginx was verified using:

```bash
sudo systemctl status nginx
```

Expected status:

```text
Active: active (running)
```

The website was also tested through the EC2 public IP using HTTP.

A restart test was performed to verify that Nginx continued running correctly:

```bash
sudo systemctl restart nginx
```

## 📚 What I Learned

* Basic Git and GitHub workflow
* Creating and configuring an AWS EC2 instance
* Connecting to an EC2 instance using SSH
* Basic Amazon Linux administration
* Installing and managing software with `dnf`
* Installing and configuring Nginx
* Deploying a website to a Linux server
* Configuring HTTP and SSH access through an AWS security group
* Understanding the basic flow from source code to cloud deployment

## 📁 Project Structure

```text
cloudlaunch-aws-static-website/
│
└── website/
    └── index.html
```

## 🎯 Project Goal

The goal of CloudLaunch was to gain practical experience with **Linux servers, Git/GitHub, AWS EC2, SSH, and Nginx** by deploying a real website to the public internet.

## 👨‍💻 Author

**Harsh Jha**

GitHub:
https://github.com/harshjha-dev
