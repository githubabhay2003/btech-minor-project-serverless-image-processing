# Serverless Image Processing System (B.Tech Minor Project)

![AWS](https://img.shields.io/badge/AWS-Cloud-orange)
![Terraform](https://img.shields.io/badge/Terraform-IaC-blueviolet)
![Serverless](https://img.shields.io/badge/Architecture-Serverless-green)
![Status](https://img.shields.io/badge/Project-Academic_Minor_Project-blue)

An academic serverless image processing system built on AWS that automatically resizes images when uploaded through a secure web interface.

---

## Table of Contents

- [Overview](#overview)
- [Skills Demonstrated](#skills-demonstrated)
- [Architecture](#architecture)
- [Tech Stack](#tech-stack)
- [Prerequisites](#prerequisites)
- [Setup and Deployment](#setup-and-deployment)
- [CI/CD Pipeline](#cicd-pipeline)
- [Verification Steps](#verification-steps)
- [Screenshots](#screenshots)
- [Challenges and Learnings](#challenges-and-learnings)
- [Future Improvements](#future-improvements)
- [Repository Structure](#repository-structure)
- [Contributing](#contributing)
- [License](#license)
- [Author](#author)

---

## Overview

This project implements an **AWS-based Serverless Image Processing System** designed as a **B.Tech minor project**.  
Users upload images via a browser-based frontend. The system automatically resizes the images using AWS Lambda and stores the processed outputs in a separate S3 bucket.

The project focuses on:
- Serverless architecture concepts
- Infrastructure as Code using Terraform
- Secure frontend uploads using Amazon Cognito
- Event-driven cloud workflows

This system is intentionally kept **simple, academic-friendly, and viva-ready**.

---

## Skills Demonstrated

- AWS Serverless Architecture
- Amazon S3 event-based workflows
- AWS Lambda (Python + Pillow)
- IAM least-privilege access design
- Amazon Cognito Identity Pools
- Terraform Infrastructure as Code
- Basic frontend-cloud integration
- Cloud debugging using CloudWatch Logs

---

## Architecture

**Architecture Diagram (Placeholder)**  
`[ Add architecture diagram here for report / viva ]`

### Flow Explanation

- User uploads an image from the browser
- Image is stored in **S3 Input Bucket**
- S3 event triggers **Lambda Function**
- Lambda resizes the image and creates a thumbnail
- Processed images are stored in **S3 Output Bucket**
- User accesses processed images via public S3 URLs

---

## Tech Stack

| Category            | Tool / Service |
|---------------------|---------------|
| Cloud Provider      | AWS |
| Storage             | Amazon S3 |
| Compute             | AWS Lambda |
| Authentication      | Amazon Cognito Identity Pool |
| IaC                 | Terraform |
| Language            | Python |
| Image Library       | Pillow |
| Frontend            | HTML, JavaScript |
| Logging             | Amazon CloudWatch |

---

## Prerequisites

- AWS Account  
  https://aws.amazon.com/

- AWS CLI  
  https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html

- Terraform  
  https://developer.hashicorp.com/terraform/downloads

- Docker Desktop  
  https://www.docker.com/products/docker-desktop/

- Git  
  https://git-scm.com/

---

## Setup and Deployment

### 1. Clone the Repository

```bash
git clone https://github.com/githubabhay2003/btech-minor-project-serverless-image-processing.git
cd btech-minor-project-serverless-image-processing
```
