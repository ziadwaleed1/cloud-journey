# Task 04 - EC2 Instance Access to Amazon S3 Using IAM Role

## Objective

The objective of this task is to allow an Amazon EC2 instance to securely access Amazon S3 using an IAM Role instead of Access Keys.

This demonstrates AWS best practices by using temporary credentials provided automatically through IAM Roles attached to EC2 instances.

---

## Architecture

EC2 Instance
│
├── IAM Role: EC2-S3-Role
│
└── Amazon S3 Bucket
    └── my-app-storage-646731024374-us-east-1-an

---

## Step 1: Create Amazon S3 Bucket

Created an S3 bucket to store files uploaded from the EC2 instance.

### Screenshot

![Create S3 Bucket](Screenshot 2026-06-17 161230.png)

---

## Step 2: Create Key Pair

Created a Key Pair for secure SSH access to the EC2 instance.

### Screenshot

![Create Key Pair](Screenshot 2026-06-17 163908.png)

---

## Step 3: Create IAM Role

Created an IAM Role named:

```text
EC2-S3-Role
