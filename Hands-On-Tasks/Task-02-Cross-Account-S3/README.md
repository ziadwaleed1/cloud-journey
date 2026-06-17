# Task 02 - Cross Account Access to Amazon S3

## Objective

The goal of this task is to allow an IAM User from one AWS Account to access an Amazon S3 Bucket located in another AWS Account using Cross-Account Access.

This demonstrates how AWS Identity and Access Management (IAM) and S3 Bucket Policies work together to securely share resources between different AWS accounts.

---

## Architecture

### Source Account

* IAM User: `CrossUser`
* IAM Policy: `S3-CrossUser`

⬇ Cross-Account Access

### Target Account

* Amazon S3 Bucket
* Bucket Policy configured to trust the IAM user from the source account

---

## AWS Services Used

* AWS IAM
* Amazon S3
* AWS CLI

---

## Step 1: Create IAM User

Created an IAM user named:

```text
CrossUser
```

The user was configured with:

* AWS Management Console Access
* Programmatic Access

### Screenshot

![Create CrossUser](screenshots/Create%20CrossUser.png)

---

## Step 2: Generate Access Keys

Generated an Access Key ID and Secret Access Key for the IAM user.

These credentials are required for AWS CLI authentication.

### Screenshot

![Create Access Key](screenshots/create-access-key.png)

---

## Step 3: Create IAM Policy

Created a custom IAM policy named:

```text
S3-CrossUser
```

The policy grants the following permissions:

* s3:ListBucket
* s3:GetObject
* s3:PutObject

Policy JSON:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:ListBucket",
        "s3:GetObject",
        "s3:PutObject"
      ],
      "Resource": "*"
    }
  ]
}
```

### Screenshot

![Create S3 Policy](screenshots/create-s3-policy.png)

---

## Step 4: Attach Policy to IAM User

Attached the custom policy:

```text
S3-CrossUser
```

to the IAM user:

```text
CrossUser
```

### Screenshot

![Attach Policy](screenshots/attach-policy-to-user.png)

---

## Step 5: Configure S3 Bucket Policy

A bucket policy was added to the target S3 bucket to allow the IAM user from the source account to access bucket resources.

Permissions granted:

* List Bucket
* Read Objects
* Upload Objects

### Screenshot

![Bucket Policy](screenshots/cross-account-bucket-policy.png)

---

## Step 6: Configure AWS CLI

Configured AWS CLI using:

```bash
aws configure
```

Provided:

```text
AWS Access Key ID
AWS Secret Access Key
Region: eu-north-1
Output Format: json
```

---

## Step 7: Verify Identity

Verified the authenticated IAM identity using:

```bash
aws sts get-caller-identity
```

This command confirmed that AWS CLI was authenticated using the CrossUser IAM account.

---

## Step 8: Test Cross-Account Access

Created a test file:

```bash
echo "Cross Account Test" > test.txt
```

Uploaded the file to the target S3 bucket:

```bash
aws s3 cp test.txt s3://cross-account-bucket-646731024374-eu-north-1-an/
```

Successful upload output:

```text
upload: .\test.txt to s3://cross-account-bucket-646731024374-eu-north-1-an/test.txt
```

### Screenshot

![Cross Account Success](screenshots/cross-account-access-success.png)

---

## Validation Results

The following tasks were successfully completed:

✅ IAM User Creation

✅ Access Key Generation

✅ IAM Policy Creation

✅ Policy Attachment

✅ S3 Bucket Policy Configuration

✅ AWS CLI Authentication

✅ Cross-Account Access Verification

✅ File Upload to Target S3 Bucket

---

## Security Concepts Demonstrated

* Identity-Based Policies (IAM Policies)
* Resource-Based Policies (S3 Bucket Policies)
* Cross-Account Resource Sharing
* Principle of Least Privilege
* AWS CLI Authentication
* Secure Access Management

---

## Outcome

Successfully implemented Cross-Account Access between two AWS accounts.

The IAM user from the source account was able to authenticate through AWS CLI and upload objects to an Amazon S3 bucket owned by another AWS account using a combination of IAM permissions and S3 Bucket Policies.
