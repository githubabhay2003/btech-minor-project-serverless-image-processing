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
<img width="2816" height="1536" alt="Gemini_Generated_Image_xhxaq9xhxaq9xhxa" src="https://github.com/user-attachments/assets/e6b35358-cd7e-4961-bc9c-4088bcc9a64b" />

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
### 2. Configure AWS Credentials

Run the following command to set up your AWS CLI with the necessary access keys and region:

```bash
aws configure
```
### 3. Build and Push Lambda Docker Image

Navigate to the lambda directory, build the Docker image for the `linux/amd64` platform, and push it to Amazon ECR.

> **Note:** Replace `<AWS_ACCOUNT_ID>` with your actual AWS Account ID.

```bash
cd lambda
docker build --platform=linux/amd64 -t <AWS_ACCOUNT_ID>[.dkr.ecr.us-east-1.amazonaws.com/serverless-image-processing-lambda:lambda](https://.dkr.ecr.us-east-1.amazonaws.com/serverless-image-processing-lambda:lambda) .
docker push <AWS_ACCOUNT_ID>[.dkr.ecr.us-east-1.amazonaws.com/serverless-image-processing-lambda:lambda](https://.dkr.ecr.us-east-1.amazonaws.com/serverless-image-processing-lambda:lambda)
```
### 4. Deploy Infrastructure Using Terraform

Initialize and apply the Terraform configuration to provision the infrastructure.

```bash
cd terraform
terraform init
terraform apply
```
### 5. Update Frontend Configuration

Edit the `frontend/app.js` file and update the following values with the outputs from the Terraform deploy:

* **Cognito Identity Pool ID**
* **AWS Region**
* **Input Bucket Name**

--- 

## CI/CD Pipeline

**Not implemented.**

This project intentionally avoids CI/CD pipelines to keep the scope suitable for academic evaluation. All deployments are performed manually using Terraform and Docker.

--- 

## Verification Steps

1. Open `frontend/index.html` in a browser.
2. Select an image file.
3. Upload the image.
4. **Verify the following:**
    * Upload success message is displayed.
    * Lambda logs appear in CloudWatch.
    * Resized image appears in the output S3 bucket.
    * Thumbnail image appears in the output S3 bucket.
---
## Screenshots

### 1. Frontend Image Upload Interface (Initial State)
<img width="1919" height="966" alt="Screenshot 2026-01-03 162432" src="https://github.com/user-attachments/assets/35cacf2a-8020-4aa9-a52d-49b6d59cc946" />
This screenshot shows the web-based frontend of **The Invisible Image Processor** before selecting any image. The interface allows users to choose an image file and initiate the upload process.

### 2. Frontend Image Upload Interface (After Image Selection)
<img width="1919" height="968" alt="Screenshot 2026-01-03 211625" src="https://github.com/user-attachments/assets/76137e6a-477a-4653-af50-9de559d7d278" />
This screenshot displays the frontend after an image file has been selected by the user. The original image preview is shown along with options to upload the image for processing and shows the status message after a successful upload. It also provides links to the resized image and thumbnail image generated by the system.

### 3. Amazon S3 Bucket List
<img width="1919" height="916" alt="Screenshot 2026-01-03 211706" src="https://github.com/user-attachments/assets/ad91aab2-edba-4280-94be-aa40f7718ef4" />
This screenshot shows the list of Amazon S3 buckets created for the project, including:
* **Input storage bucket** for uploaded images
* **Output storage bucket** for processed images
* **Terraform state bucket** for infrastructure management

### 4. Input Storage Bucket with Uploaded Image
<img width="1919" height="955" alt="Screenshot 2026-01-03 211753" src="https://github.com/user-attachments/assets/33767e01-543b-4411-ae55-209b2cbb0aa2" />
This screenshot shows the input S3 bucket containing the original image uploaded by the user before processing.

### 5. Output Storage Bucket Structure
<img width="1919" height="954" alt="Screenshot 2026-01-03 211758" src="https://github.com/user-attachments/assets/ac3dfd11-dd4a-4092-b8d4-cf13475f3b1c" />
This screenshot displays the output S3 bucket structure with separate folders for resized images and thumbnail images.

### 6. CloudWatch Log Group for Image Processing Lambda Function
<img width="1919" height="959" alt="Screenshot 2026-01-03 211807" src="https://github.com/user-attachments/assets/6539bad7-a2fb-40f3-99a9-6f8230e39985" />
This screenshot shows the CloudWatch log group automatically created for the AWS Lambda image processing function, used for monitoring and debugging.

### 7. CloudWatch Log Streams Generated During Image Upload Events
<img width="1919" height="958" alt="Screenshot 2026-01-03 211850" src="https://github.com/user-attachments/assets/189c6f9e-d1b4-4143-9f34-8321c2be12bc" />
This screenshot displays multiple log streams created when image upload events trigger the Lambda function.

### 8. CloudWatch Log Events Showing Image Processing Details
<img width="1919" height="964" alt="Screenshot 2026-01-03 211855" src="https://github.com/user-attachments/assets/96c4f8d6-8bdf-43f8-a38f-cd93a52137e1" />
This screenshot shows detailed execution logs including decoded image key, image size, resizing steps, thumbnail generation, and processing time.

### 9. Terraform Apply Output – Infrastructure Provisioning
<img width="1919" height="988" alt="Screenshot 2026-01-03 211937" src="https://github.com/user-attachments/assets/6ae365b2-fe07-40a3-939e-9af384c05480" />
This screenshot shows the successful execution of the `terraform apply` command, confirming that cloud resources such as S3 buckets, Lambda function, permissions, and notifications were provisioned successfully.

--- 

## Challenges and Learnings

The table below summarizes the **major challenges faced during the project**, the **approach used to resolve them**, and the **key learnings**, written in an academic and viva-friendly manner.

| Phase | Challenge | Root Cause | Approach Used | Key Learning |
|------|---------|-----------|---------------|-------------|
| Lambda Packaging | Pillow library import error (`_imaging` missing) | Lambda runtime mismatch with locally built dependencies | Switched from ZIP-based Lambda to **Docker image–based Lambda** using AWS-provided base image | Container images ensure runtime consistency and reduce dependency issues |
| Docker + Lambda | `InvalidParameterValueException: image manifest not supported` | Docker Buildx produced OCI manifest not supported by Lambda | Disabled provenance and used correct platform (`linux/amd64`) | AWS Lambda supports only specific image formats and architectures |
| Terraform State | Lambda deployment failing due to missing image | Image tag mismatch between Terraform and ECR | Introduced `image_tag` variable and enforced tag consistency | Infrastructure and application artifacts must stay tightly aligned |
| S3 Event Handling | `NoSuchKey` error during image fetch | URL-encoded S3 object keys (`%28`, `%29`) | Decoded object key inside Lambda using URL decoding | S3 events provide encoded object keys by default |
| IAM Permissions | AccessDenied errors for S3 operations | Missing `s3:ListBucket` and scoped permissions | Refined IAM policy with least-privilege actions | IAM permissions must match API behavior, not assumptions |
| Frontend Upload | Browser upload failed with CORS error | S3 bucket lacked CORS configuration | Added CORS rules via Terraform | Browser-based cloud access requires explicit CORS rules |
| Public Access | Processed image URLs returned `AccessDenied` | Account-level Block Public Access prevented bucket policy | Temporarily disabled account-level block and applied bucket policy | AWS account-level settings override resource-level permissions |
| Observability | Difficult to debug silent failures | Insufficient logging in Lambda | Added structured CloudWatch logs | Logging is essential for debugging serverless systems |
| Event Reliability | Failed Lambda executions lost silently | No retry or failure handling | Conceptual DLQ design using SQS (academic-safe) | DLQs improve reliability and fault isolation |
| Terraform Debugging | Repeated apply failures with no changes | Terraform state drift confusion | Used `terraform plan` + logs before reapply | Terraform state awareness is critical for stable IaC |
| Frontend Integration | Upload succeeded but output not visible | Output bucket access misconfigured | Enabled public read for output bucket only | Separation of read/write access improves security |
| Architecture Design | Risk of overengineering | Academic project constraints | Chose minimal AWS services only | Simpler architectures are easier to explain in viva |
| Security Scope | Risk of unrestricted uploads | No file validation initially | Added file type and size checks in Lambda | Validation should be enforced server-side |
| Performance | Large images slowed processing | Single-size resize initially | Added thumbnail generation | Multiple output sizes improve usability |
| Academic Constraints | Balancing depth vs complexity | Overuse of DevOps tools not suitable | Limited tooling to Terraform + Docker | Tool choice should match project goals |

---

### Overall Takeaway

This project demonstrated that **serverless systems shift complexity from infrastructure management to integration, permissions, and observability**.  
The systematic debugging approach—logs → permissions → configuration → architecture—proved essential and is directly applicable to real-world cloud engineering.

This experience significantly strengthened understanding of **event-driven architectures**, **cloud-native debugging**, and **Infrastructure as Code discipline**, while remaining well within **academic evaluation standards**.

---

## Future Improvements

* [ ] Add CloudFront for faster image delivery.
* [ ] Add user-specific folders using Cognito identity IDs.
* [ ] Add optional API Gateway layer.
* [ ] Improve frontend UI.
* [ ] Add image format conversion.

---

## Repository Structure

```text
btech-minor-project-serverless-image-processing/
├── frontend/
│   ├── index.html
│   └── app.js
├── lambda/
│   ├── Dockerfile
│   └── image_processor.py
├── terraform/
│   ├── main.tf
│   ├── variables.tf
│   └── outputs.tf
├── README.md
```
---

## Contributing

This repository is intended for academic use.

Contributions are not expected, but suggestions are welcome via issues.

--- 

## License

This project is provided for **educational purposes only**.

> **Disclaimer:** No production guarantees are provided.

--- 

## Author

**Abhay Kumar Saini**
*B.Tech Student*
*Minor Project – Cloud Computing & DevOps*

* **GitHub:** [https://github.com/githubabhay2003](https://github.com/githubabhay2003)



