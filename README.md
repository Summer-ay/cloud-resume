 # ☁️ Cloud Resume Challenge (Lite) – Static Website on AWS

## 📌 Overview

This project hosts a **static resume website** on **Amazon S3**, configured with **public access, routing, and content delivery**. The entire deployment process is automated using a custom **Bash script** and version-controlled with **Git + GitHub**.
 
✅ Focuses on Git, AWS CLI, S3 buckets, IAM, Bash scripting, and CI basics

---

## 🔧 Tools & Technologies

- AWS S3 (static site hosting)
- AWS IAM (programmatic access via CLI)
- AWS CLI
- Bash (deployment automation)
- Git & GitHub
- Visual Studio Code (or terminal-based editing)

---

## 🧠 Key Concepts Practiced

| Concept            | What I Learned                                      |
|--------------------|-----------------------------------------------------|
| Linux & CLI        | Navigating with Bash, scripting, file permissions   |
| Version Control    | Git basics, GitHub remote workflows                 |
| AWS S3             | Bucket policies, static website hosting, ACLs       |
| IAM                | Users, policies, access keys for least-privilege    |
| Deployment Script  | Automating upload with `aws s3 sync`, ACL configs   |
| CI Intro           | Git-based automation + GitHub Actions preview       |

---

## 🛠 How It Works

1. Website content (HTML/CSS) is versioned in Git
2. AWS S3 bucket is configured for public static hosting
3. A Bash script (`deploy.sh`) uploads the site and sets correct permissions
4. Public access is tested via browser using the S3 website endpoint

---

## 🚀 Deploy Instructions

### 🧱 1. Prerequisites

- AWS account (Free Tier)
- IAM user with `AmazonS3FullAccess`
- AWS CLI installed and configured (`aws configure`)
- Git installed

---

### ⚙️ 2. Run the Deployment Script

```bash
./deploy.sh
```
    This will:
           Upload your resume.html (or other files) to the S3 bucket
           Set the bucket policy and public ACLs
           Confirm that the files are accessible via the S3 static site URL

### 🧪 Sample Bash Script: deploy.sh
```bash
#!/bin/bash
set -e

BUCKET="your-s3-bucket-name"

# Upload website files to S3
aws s3 sync . s3://$BUCKET \
  --exclude "deploy.sh" \
  --exclude "*.json" \
  --delete

# Print S3 website URL
echo "Website deployed at:"
aws s3 website s3://$BUCKET.s3.(region).amazonaws.com/resume.html
```
### 🌍 Hosting Architecture

    Local Machine
    │
    ├──> Git commit → GitHub
    │
    └──> ./deploy.sh
         └──> aws s3 sync → S3 static website bucket

🔗 Sample Output

Once deployed, visit:

    http://<your-bucket-name>.s3-website-<region>.amazonaws.com

You should see your resume or portfolio page live on the web!
