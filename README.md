# 🚀 EC2–S3 Integration using IAM Role (No Access Keys)

## 📌 Overview

This project demonstrates secure integration between an Amazon EC2 instance and an S3 bucket using IAM Roles.
The goal is to enable EC2 to access S3 **without storing access keys**, following AWS security best practices.

---

## 🧠 Key Concepts

* IAM Roles
* Least Privilege Principle
* AWS CLI
* Secure Service-to-Service Communication

---

## 🏗️ Architecture

EC2 Instance → IAM Role → S3 Bucket

* EC2 instance assumes an IAM Role
* IAM Role provides temporary credentials
* EC2 interacts with S3 securely via AWS CLI

---

## 🛠️ Services Used

* Amazon EC2
* Amazon S3
* AWS IAM
* AWS CLI

---

## ⚙️ Implementation Steps

### 1️⃣ Create S3 Bucket

* Created an S3 bucket to store files
* Bucket name: `my-ec2-s3-project-aman`

---

### 2️⃣ Create IAM Role

* Trusted Entity: EC2
* Attached custom policy with limited permissions

---

### 3️⃣ Attach IAM Role to EC2

* Launched EC2 instance
* Attached IAM role during instance creation

---

### 4️⃣ Install AWS CLI

```bash
sudo yum update -y
sudo yum install aws-cli -y
```

---

### 5️⃣ Verify Access

```bash
aws s3 ls
```

---

### 6️⃣ Upload File to S3

```bash
echo "Hello AWS" > test.txt
aws s3 cp test.txt s3://my-ec2-s3-project-aman/
```

---

### 7️⃣ Download File from S3

```bash
aws s3 cp s3://my-ec2-s3-project-aman/test.txt .
```

---

## 🔐 IAM Policy (Least Privilege)

```json
{
"Version": "2012-10-17",
"Statement": [
{
"Effect": "Allow",
"Action": ["s3:PutObject", "s3:GetObject", "s3:ListBucket"],
"Resource": [
"arn:aws:s3:::my-ec2-s3-project-aman",
"arn:aws:s3:::my-ec2-s3-project-aman/*"
]
}
]
}
```

---

* EC2 instance configuration
* IAM role attachment
* S3 bucket
* AWS CLI output

---

## ✅ Results

* Successfully connected EC2 to S3
* Uploaded and downloaded files securely
* No access keys were used

---

## 🚫 Security Best Practices Followed

* No hardcoded credentials
* Used IAM Role instead of access keys
* Applied least privilege policy

---

## 💡 What I Learned

* How IAM roles provide temporary credentials
* Secure interaction between AWS services
* Real-world DevOps practices

---

## 🔗 Future Improvements

* Automate file uploads using cron jobs
* Integrate with CloudWatch for monitoring
* Add CI/CD pipeline

---

## 👨‍💻 Author

Aman Singh

---
