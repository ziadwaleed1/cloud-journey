# Task 02 - Cross Account Access to Amazon S3

## Objective

The goal of this task is to allow an IAM User from one AWS Account to access an Amazon S3 Bucket located in another AWS Account using Cross-Account Access.

This demonstrates how AWS Identity and Access Management (IAM) and S3 Bucket Policies work together to securely share resources between different AWS accounts.

---

## Architecture

Account A (Source Account)
- IAM User: CrossUser
- IAM Policy: S3-CrossUser

⬇ Cross-Account Access

Account B (Target Account)
- Amazon S3 Bucket:
  cross-account-bucket-646731024374-eu-north-1-an

---

## Step 1: Create IAM User

Created an IAM user named:

```text
CrossUser
```

The user was configured with:
- AWS Management Console Access
- Programmatic Access (Access Key & Secret Key)

### Screenshot

![Create CrossUser](screenshots/01-create-crossuser.png)

---

## Step 2: Generate Access Keys

Created Access Key and Secret Access Key for the IAM user.

These credentials are used to authenticate through AWS CLI.

### Screenshot

![Create Access Key](screenshots/02-create-access-key.png)

---

## Step 3: Create IAM Policy

Created a custom policy named:

```text
S3-CrossUser
```

Policy Permissions:

- s3:ListBucket
- s3:GetObject
- s3:PutObject

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

![Create Policy](screenshots/03-create-s3-policy.png)

---

## Step 4: Attach Policy to IAM User

Attached the custom policy:

```text
S3-CrossUser
```

to:

```text
CrossUser
```

### Screenshot

![Attach Policy](screenshots/04-attach-policy-to-user.png)

---

## Step 5: Configure S3 Bucket Policy

In the target account, a Bucket Policy was added to allow the IAM user from the source account to access the bucket.

Permissions granted:

- List Bucket
- Upload Objects
- Read Objects

### Screenshot

![Bucket Policy](screenshots/05-cross-account-bucket-policy.png)

---

## Step 6: Configure AWS CLI

Configured AWS CLI using:

```bash
aws configure
```

Entered:

```text
Access Key ID
Secret Access Key
Region: eu-north-1
Output Format: json
```

---

## Step 7: Verify Identity

Verified the active AWS identity using:

```bash
aws sts get-caller-identity
```

Output confirmed:

```text
User: CrossUser
```

---

## Step 8: Upload File to Target S3 Bucket

Created a test file:

```bash
echo "Cross Account Test" > test.txt
```

Uploaded it to the bucket:

```bash
aws s3 cp test.txt s3://cross-account-bucket-646731024374-eu-north-1-an/
```

Result:

```text
upload: .\test.txt to s3://cross-account-bucket-646731024374-eu-north-1-an/test.txt
```

This confirms successful Cross-Account Access.

### Screenshot

![Cross Account Success](screenshots/06-cross-account-access-success.png)

---

## Validation

Successfully verified:

✅ IAM User Creation

✅ Access Key Generation

✅ IAM Policy Creation

✅ Policy Attachment

✅ S3 Bucket Policy Configuration

✅ AWS CLI Authentication

✅ Cross-Account Access

✅ File Upload to S3 Bucket

---

## Technologies Used

- AWS IAM
- Amazon S3
- AWS CLI
- JSON Policies
- Cross-Account Access

---

## Outcome

The IAM user `CrossUser` from one AWS account successfully accessed and uploaded objects to an Amazon S3 bucket located in another AWS account using AWS Cross-Account Access.
