# End-to-End Cloud Infrastructure Automation and Deployment

## Problem Statement

Modern organizations require a fully automated, reliable, and scalable approach to provision infrastructure, configure systems, containerize applications, and deploy them efficiently.  
Manual infrastructure setup and application deployment often result in configuration drift, inconsistent environments, increased operational overhead, and delayed releases.

The objective of this project is to design and implement an **end-to-end cloud automation solution** using **Terraform, Ansible, Docker, and Kubernetes**, ensuring repeatability, idempotency, scalability, and minimal manual intervention.

---

## Project Objective

To build a complete automation workflow that:
- Provisions cloud infrastructure using Infrastructure as Code
- Configures servers automatically
- Packages applications into Docker containers
- Deploys and exposes applications on a Kubernetes cluster

---

## Architecture Overview

Terraform → Ansible → Docker → Kubernetes

- **Terraform** provisions AWS infrastructure
- **Ansible** configures the provisioned servers
- **Docker** containerizes a Python Flask application
- **Kubernetes (KOPS)** orchestrates and exposes the containerized application

---

## Tools & Technologies

- Terraform – Infrastructure as Code  
- Ansible – Configuration Management  
- Docker – Containerization  
- Kubernetes (KOPS) – Container Orchestration  
- AWS EC2 & S3  

---

## Implementation Details

### 1. Infrastructure Provisioning with Terraform

**Goal:**  
Automate the creation of cloud infrastructure to eliminate manual provisioning.

**Implementation:**
- Provisioned an Ubuntu EC2 instance (t2.micro) on AWS
- Generated and managed SSH key pairs using Terraform
- Created security groups to allow SSH access
- The EC2 instance acts as an **Ansible Workstation**

**Outcome:**
- Fully automated and reproducible infrastructure
- Secure and consistent server provisioning

---

### 2. Configuration Management with Ansible

**Goal:**  
Ensure consistent server configuration without manual setup.

**Implementation:**
- Installed Ansible on the provisioned EC2 instance
- Configured localhost as the managed node
- Created an Ansible playbook to:
  - Install Apache (httpd)
  - Start and enable the web service

**Outcome:**
- Idempotent configuration
- Zero manual intervention
- Web server accessible on port 80

---

### 3. Application Containerization with Docker

**Goal:**  
Package the application for portability and consistency across environments.

**Implementation:**
- Developed a Python Flask REST API
- Created a Dockerfile to:
  - Install dependencies
  - Copy application code
  - Expose application on port 5000
- Built and pushed Docker image to Docker Hub

**Outcome:**
- Portable and reusable Docker image
- Simplified application deployment

---

### 4. Container Orchestration with Kubernetes

**Goal:**  
Deploy and manage containers in a scalable and highly available environment.

**Implementation:**
- Created a Kubernetes cluster on AWS using KOPS
- Used S3 for Kubernetes state storage
- Deployed the Flask application as:
  - A Kubernetes Pod
  - A NodePort Service for external access
- Accessed the application using worker node public IP and NodePort

**Outcome:**
- Scalable container orchestration
- External access to application APIs
- Kubernetes-managed lifecycle and networking

---

## Application Endpoints

- `/` – Welcome message  
- `/v1/books/` – List all books  
- `/v1/books/{author}` – Get books by author  

---

## Final Outcome

- End-to-end automation from infrastructure provisioning to application deployment
- Reproducible and version-controlled infrastructure
- Consistent server configuration
- Containerized and portable application
- Scalable Kubernetes-based deployment
- Reduced operational risk and faster delivery

---

## Conclusion

This project demonstrates a real-world DevOps automation workflow by integrating **Terraform, Ansible, Docker, and Kubernetes** to deliver a fully automated cloud-native application deployment pipeline.
