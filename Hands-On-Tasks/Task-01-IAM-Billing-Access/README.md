# Task 01 - IAM User Creation and Billing Access

## Objective

Create an IAM user with administrative privileges and provide access to AWS Billing and Cost Management services.

## Steps

### Step 1: Create IAM User

Created a new IAM user named `test1` and enabled console access.

![Create User](<img width="1907" height="928" alt="Screenshot 2026-06-12 185851" src="https://github.com/user-attachments/assets/67674ccb-a9b9-46fc-8f45-f93d65c8dee6" />
)

---

### Step 2: Grant Administrator Access

Attached the AWS managed policy:

* AdministratorAccess

![Administrator Access](<img width="1346" height="594" alt="Screenshot 2026-06-12 185927" src="https://github.com/user-attachments/assets/093e6986-ca74-4a98-9574-752a4d542367" />
)

---

### Step 3: Enable Billing Access

Verified that IAM User and Role Access to Billing Information is activated in the AWS account.

![Billing Access](<img width="1917" height="882" alt="Screenshot 2026-06-12 192423" src="https://github.com/user-attachments/assets/53cfc95c-c370-4841-b365-f2cdf99641b1" />
)

---

### Step 4: Attach Billing Policy

Attached the AWS managed policy:

* Billing

to the IAM user.

![Billing Policy](<img width="1650" height="252" alt="Screenshot 2026-06-12 194834" src="https://github.com/user-attachments/assets/857cd902-c9a5-4df6-ab4e-5ada86535b8e" />
)

### Step 5: Test Billing Access

Logged in using the IAM user and verified access to AWS Billing and Cost Management services.

#### Bills

Verified that the user can access the Bills page.

![Bills](<img width="1901" height="857" alt="Screenshot 2026-06-12 195434" src="https://github.com/user-attachments/assets/22ef2b9f-7f8b-4dd6-91f5-2bd798059728" />
)

---

#### Payments

Verified that the user can access the Payments page.

![Payments](<img width="1917" height="710" alt="Screenshot 2026-06-12 195449" src="https://github.com/user-attachments/assets/339d6305-1a45-4070-bc1b-ae429199bf27" />
)

---

#### Cost Explorer

Verified that the user can access Cost Explorer and view cost analysis data.

![Cost Explorer](<img width="1907" height="787" alt="Screenshot 2026-06-12 195505" src="https://github.com/user-attachments/assets/682eefd0-6dfa-4390-bc40-be841970124c" />
)

---

### Validation

Confirmed that the IAM user can successfully access:

* Bills
* Payments
* Cost Explorer

without permission errors.


## Key Learnings

* IAM users do not have access to Billing information by default.
* Billing access must be enabled at the account level.
* Billing permissions can be managed separately from administrative permissions.
* Root user access is required to manage account-level Billing settings.

## Result

Successfully created an IAM user, granted administrative permissions, configured Billing access, and validated Billing-related permissions.
****
