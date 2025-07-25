🚀 AWS CodeDeploy + CodePipeline EC2 Project

This is a hands-on DevOps project that demonstrates a **fully automated CI/CD pipeline** using:

- ✅ Amazon EC2 (Dev and Test instances)
- ✅ Amazon S3 (to store app revisions)
- ✅ AWS CodeDeploy (to automate deployment)
- ✅ AWS CodePipeline (to automate the full pipeline)
---
## 📁 Project Structure

```
aws-codedeploy-pipeline-project/
├── sampleapp/
│   └── scripts/
├── screenshots/               # Deployment result screenshots
├── PROJECT_NOTES.txt          # Blog-style journey (included below)
├── Step_by_Step_Guide.docx    # Full step-by-step guide
└── README.md                  # This file
```
---

## 🔧 Technologies Used

- Amazon EC2 (Amazon Linux)
- Apache HTTP Server
- AWS IAM Roles and Policies
- Amazon S3 (versioning enabled)
- AWS CodeDeploy Agent
- AWS CodePipeline
---

## 🚀 How It Works

1. Modify `index.html` (e.g., change to "Version 2")
2. Zip the `sampleapp/` folder:
   ```bash
   zip -r sampleapp.zip sampleapp/
   ```
3. Upload it to S3:
   ```bash
   aws s3 cp sampleapp.zip s3://<your-bucket-name>
   ```
4. CodePipeline triggers automatically and deploys via CodeDeploy
---

## 📘 Full Deployment Journey (PROJECT_NOTES.txt)

### 🛠️ Project Overview

I created a full-stack deployment pipeline using AWS services:
- EC2 (Dev and Test)
- S3 (for storing zipped app code)
- CodeDeploy (for deployment automation)
- CodePipeline (for CI/CD automation)

This blog documents my journey step-by-step, including setup, common errors, and how I fixed them.

### 🔧 Setup Summary

- Created EC2 instances for Dev and Test
- Created IAM role with permissions: `AmazonS3FullAccess`, `AWSCodeDeployRole`, `AmazonSSMManagedInstanceCore`
- Prepared app with: `index.html`, `appspec.yml`, and shell scripts
- Installed Apache and CodeDeploy agent
- Configured CodeDeploy application (`sampleapp`) and deployment group (`mygrp`)
- Tagged EC2 with `AppName=SampleApp`
- Created a CodePipeline to automate deployment from S3 to EC2

---

## 🐛 Issues I Faced and How I Solved Them

| Issue | Solution |
|-------|----------|
| `aws: command not found` | Installed AWS CLI |
| `Unable to locate credentials` | Attached IAM role with S3 permissions |
| `BucketAlreadyExists` | Used globally unique bucket name |
| `sampleapp.zip does not exist` | Checked and recreated zip file |
| `No instances found for deployment group` | Added proper EC2 tags |
| `CodeDeploy agent not installed` | Manually installed the agent |
| `Site can't be reached` | Checked security group to allow port 80 |
| CodePipeline not triggering | Enabled versioning on S3 bucket |

---

## ✅ Outcome

- Fully working CI/CD pipeline on AWS
- Automatic deployments using S3 → CodePipeline → CodeDeploy
- Real-time updates reflected on EC2 web server
---
## 🧠 Author

Created by **Sakthivel S.** as part of AWS DevOps practice and hands-on learning.  
