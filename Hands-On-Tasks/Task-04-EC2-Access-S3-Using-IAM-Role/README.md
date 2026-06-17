# Task 04 - Access Amazon S3 from EC2 Using IAM Role

## Objective

The objective of this task is to provide secure access from an Amazon EC2 instance to an Amazon S3 bucket using an IAM Role instead of Access Keys.

This approach follows AWS security best practices by granting temporary credentials to the EC2 instance through IAM Roles.

---

## Architecture

EC2 Instance
↓
IAM Role (EC2-S3-Role)
↓
Amazon S3 Bucket
↓
Upload and Retrieve Objects

---

## Services Used

- Amazon EC2
- Amazon S3
- AWS IAM
- IAM Roles
- AWS STS
- AWS CLI

---

## Step 1: Create Amazon S3 Bucket

Created an S3 bucket to store application files and test uploads from the EC2 instance.

### Screenshot

![Create Bucket](<Screenshot 2026-06-17 161230.png>)

---

## Step 2: Create EC2 Key Pair

Created a Key Pair for secure SSH access to the EC2 instance.

Configuration:

- Key Pair Type: RSA
- Private Key Format: PEM

### Screenshot

![Create Key Pair](<Screenshot 2026-06-17 163908.png>)

---

## Step 3: Create IAM Role

Created an IAM Role named:

```text
EC2-S3-Role
```

Trust Relationship:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "Service": "ec2.amazonaws.com"
      },
      "Action": "sts:AssumeRole"
    }
  ]
}
```

### Screenshot

![Create IAM Role](<Screenshot 2026-06-17 164526.png>)

---

## Step 4: Attach IAM Role to EC2 Instance

Attached the IAM Role to the running EC2 instance.

Role:

```text
EC2-S3-Role
```

### Screenshot

![Attach Role](<Screenshot 2026-06-17 164729.png>)

---

## Step 5: Initial Access Test

Attempted to upload a file before proper configuration.

Result:

```text
AccessDenied
```

This verified that permissions were not yet available.

### Screenshot

![Access Denied](<Screenshot 2026-06-17 165614.png>)

---

## Step 6: Configure S3 Permissions

Updated the IAM Role permissions to allow full S3 access.

Permissions granted:

- List Buckets
- Get Objects
- Put Objects
- Delete Objects

### Screenshot

![S3 Permissions](<Screenshot 2026-06-17 170503.png>)

---

## Step 7: Verify IAM Role from EC2

Verified that the EC2 instance successfully assumed the IAM Role.

Command:

```bash
aws sts get-caller-identity
```

Result:

```text
arn:aws:sts::ACCOUNT_ID:assumed-role/EC2-S3-Role/INSTANCE_ID
```

### Screenshot

![Verify Role](<Screenshot 2026-06-17 170629.png>)

---

## Step 8: Verify S3 Access

Verified access to S3 resources.

Commands:

```bash
aws s3 ls

aws s3api list-buckets
```

Successfully listed available buckets.

### Screenshot

![List Buckets](<Screenshot 2026-06-17 171032.png>)

---

## Step 9: Review Bucket Configuration

Reviewed bucket configuration and permissions.

### Screenshot

![Bucket Configuration](<Screenshot 2026-06-17 171200.png>)

---

## Step 10: Upload File from EC2 to S3

Created a test file:

```bash
echo "Hello from EC2" > test.txt
```

Uploaded the file:

```bash
aws s3 cp test.txt s3://my-app-storage-646731024374-us-east-1-an/
```

### Screenshot

![Upload File](<Screenshot 2026-06-17 171420.png>)

---

## Step 11: Validate Uploaded Object

Verified that the uploaded object exists inside the S3 bucket.

Command:

```bash
aws s3 ls s3://my-app-storage-646731024374-us-east-1-an/
```

Output:

```text
test.txt
```

### Screenshot

![Upload Success](<Screenshot 2026-06-17 171647.png>)

---

## Validation

Successfully verified:

✅ S3 Bucket Creation

✅ EC2 Instance Deployment

✅ Key Pair Creation

✅ IAM Role Creation

✅ IAM Role Attachment

✅ Temporary Credential Usage

✅ STS Identity Verification

✅ S3 Bucket Access

✅ File Upload to S3

✅ Object Validation

---

## Security Benefits

- No Access Keys stored on the EC2 instance.
- Temporary credentials are automatically managed by AWS.
- Follows AWS Security Best Practices.
- Reduces risk of credential leakage.
- Enables secure service-to-service authentication.

---

## Outcome

Successfully configured an Amazon EC2 instance to access Amazon S3 using an IAM Role. The EC2 instance authenticated through AWS Security Token Service (STS), obtained temporary credentials automatically, and uploaded files to Amazon S3 without using Access Keys.
