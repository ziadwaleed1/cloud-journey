# Task 03 - IAM User Access to Launch and Terminate EC2 Instances

## Objective

The objective of this task is to create an IAM user with limited permissions that allow launching and terminating Amazon EC2 instances without granting full administrative access.

This demonstrates the principle of least privilege by assigning only the permissions required for specific EC2 operations.

---

## Architecture

### IAM Components

* IAM User: `EC2User`
* IAM Policy: `LaunchAndTerminateEC2`

### Allowed Actions

* `ec2:RunInstances`
* `ec2:TerminateInstances`

### AWS Service

* Amazon EC2

---

## Step 1: Create IAM Policy

Created a custom IAM policy named:

```text
LaunchAndTerminateEC2
```

The policy grants the following permissions:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "VisualEditor0",
      "Effect": "Allow",
      "Action": [
        "ec2:RunInstances",
        "ec2:TerminateInstances"
      ],
      "Resource": "*"
    }
  ]
}
```

### Screenshot

![Policy JSON](<img width="1492" height="463" alt="policy-json png" src="https://github.com/user-attachments/assets/5f189d57-64a3-4f65-adeb-0a6c8d8a4044" />
)

---

## Step 2: Create IAM User

Created an IAM user named:

```text
EC2User
```

The user was configured to access AWS services according to assigned permissions.

---

## Step 3: Attach Policy to User

Attached the custom policy:

```text
LaunchAndTerminateEC2
```

to:

```text
EC2User
```

### Screenshot

![Policy Assignment](<img width="1895" height="792" alt="iam-user-policy-assignment png" src="https://github.com/user-attachments/assets/16a9bb25-f87a-4f91-8fe2-ba780283b64b" />
)

---

## Step 4: Test EC2 Permissions

Logged in using the IAM user and verified the assigned permissions by launching Amazon EC2 instances.

Successfully launched EC2 instances using the granted permissions.

### Screenshot

![EC2 Launch Success](<img width="1861" height="380" alt="ec2user-launch-success png" src="https://github.com/user-attachments/assets/6540d054-0407-4da5-8ec2-23412c86f5ab" />
)

---

## Validation

Successfully verified:

* ✅ IAM User Creation
* ✅ Custom IAM Policy Creation
* ✅ Policy Assignment
* ✅ EC2 Launch Permission
* ✅ EC2 Instance Creation
* ✅ Least Privilege Access Control

---

## Technologies Used

* AWS IAM
* Amazon EC2
* IAM Policies
* JSON Policy Documents
* Access Management

---

## Outcome

Successfully implemented a restricted IAM user capable of launching and terminating Amazon EC2 instances through a custom IAM policy. The task demonstrates how AWS IAM can enforce least-privilege access while allowing users to perform specific operational responsibilities.
