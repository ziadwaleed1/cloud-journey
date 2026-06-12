# Task 01 - IAM User Creation and Billing Access

## Objective

Create an IAM user with administrative privileges and provide access to AWS Billing and Cost Management services.

## Steps

### Step 1: Create IAM User

Created a new IAM user named `test1` and enabled console access.

![Create User](https://github.com/user-attachments/assets/07c272a3-e404-49e1-bda3-b08e4387c264)

---

### Step 2: Grant Administrator Access

Attached the AWS managed policy:

* AdministratorAccess

![Administrator Access](https://github.com/user-attachments/assets/53492712-8b2f-4a28-95d1-abc6b152b18a)

---

### Step 3: Review AWS Documentation

Reviewed AWS official documentation to understand Billing access requirements for IAM users.

![AWS Billing Documentation](https://github.com/user-attachments/assets/0716bd6d-bc6d-4e91-80b5-dd342e2872d2)

---

### Step 4: Billing Access Denied

Attempted to access the Bills page using the IAM user and received an access denied message.

![Billing Access Denied](https://github.com/user-attachments/assets/448a9c41-18c1-418c-b225-3b46665798c9)

---

### Step 5: Payments Access Denied

Attempted to access the Payments page and confirmed that Billing permissions were still missing.

![Payments Access Denied](https://github.com/user-attachments/assets/448a9c41-18c1-418c-b225-3b46665798c9)

---

### Step 6: Enable IAM Billing Access

Activated IAM User and Role Access to Billing Information using the root account.

![IAM Billing Access Activated](https://github.com/user-attachments/assets/6db12698-3bf8-44d5-8095-7f405082fa75)

---

### Step 7: Attach Billing Policy

Attached the AWS managed policy:

* Billing

to the IAM user.

> Add the Billing policy attachment screenshot here.

```md
![Billing Policy](YOUR_BILLING_POLICY_IMAGE_LINK)
```

---

### Step 8: Verify Bills Access

Successfully accessed the Bills page.

![Bills Page](https://github.com/user-attachments/assets/662af8f4-9d6c-4ac6-b183-a2bc7b71e26a)

---

### Step 9: Verify Payments Access

Successfully accessed the Payments page.

![Payments Page](https://github.com/user-attachments/assets/bffb92fc-b334-4f03-883f-04d266ed220b)

---

### Step 10: Verify Cost Explorer Access

Successfully accessed Cost Explorer.

![Cost Explorer](https://github.com/user-attachments/assets/b286a48f-38dc-45ab-a8ea-05765165c621)

---

## Key Learnings

* IAM users cannot access Billing information by default.
* AdministratorAccess alone does not guarantee Billing access.
* Billing access must be enabled by the root user.
* The Billing policy must be attached to IAM users or roles.
* AWS documentation should be consulted when troubleshooting permission issues.

## Result

Successfully created an IAM user, configured Billing permissions, resolved access issues, and validated access to Bills, Payments, and Cost Explorer.
