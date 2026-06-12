# Task 01 - IAM User Creation and Billing Access

## Objective

Create an IAM user with administrative privileges and provide access to AWS Billing and Cost Management services.

---

## Step 1: Create IAM User

Created a new IAM user named `test1` and enabled console access.

![Create User](screenshots/01-create-user.png)

---

## Step 2: Grant Administrator Access

Attached the AWS managed policy:

* AdministratorAccess

![Administrator Access](screenshots/02-administrator-access.png)

---

## Step 3: Review AWS Documentation

Reviewed AWS official documentation to understand Billing access requirements for IAM users.

![AWS Billing Documentation](screenshots/03-aws-billing-documentation.png)

---

## Step 4: Billing Access Denied

Attempted to access Billing services using the IAM user and received an access denied message.

![Billing Access Denied](screenshots/04-billing-access-denied.png)

---

## Step 5: Enable IAM Billing Access

Logged in using the AWS root account and enabled IAM User and Role Access to Billing Information.

![IAM Billing Access Activated](screenshots/05-iam-billing-access-activated.png)

---

## Step 6: Attach Billing Policy

Attached the AWS managed `Billing` policy to the IAM user.

![Billing Policy Attached](screenshots/06-billing-policy-attached.png)

---

## Step 7: Verify Bills Access

Successfully accessed the Bills page.

![Bills Page](screenshots/07-bills-page.png)

---

## Step 8: Verify Payments Access

Successfully accessed the Payments page.

![Payments Page](screenshots/08-payments-page.png)

---

## Step 9: Verify Cost Explorer Access

Successfully accessed Cost Explorer.

![Cost Explorer Page](screenshots/09-cost-explorer-page.png)

---

## Issue Encountered

After attaching the `AdministratorAccess` policy, the IAM user was still unable to access AWS Billing services.

### Observed Error

* Access denied when opening Billing pages.
* Access denied when accessing payment information.

### Root Cause

IAM users cannot access Billing information by default. Billing access must be enabled at the AWS account level by the root user.

### Resolution

* Reviewed AWS Billing documentation.
* Enabled IAM User and Role Access to Billing Information.
* Attached the Billing managed policy.
* Retested Billing services access.

---

## Key Learnings

* IAM users do not have Billing access by default.
* AdministratorAccess alone does not guarantee access to Billing information.
* Billing permissions are managed separately from administrative permissions.
* Root user access is required to configure account-level Billing settings.
* AWS documentation is essential when troubleshooting permission-related issues.

---

## Result

Successfully created an IAM user, granted administrative permissions, enabled Billing access, resolved permission issues, and verified access to Bills, Payments, and Cost Explorer.

---


09-cost-explorer-page.png
```
