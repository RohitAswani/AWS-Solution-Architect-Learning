# Day 07 – IAM Policies (In-Depth)

Today, we explore **IAM Policies** – the heart of AWS permissions. You'll learn how to write, attach, and evaluate policies to securely control access to AWS resources.

---

## 🧾 What is an IAM Policy?

An **IAM Policy** is a **JSON document** that defines:
- **What actions** are allowed or denied
- **Which resources** they apply to
- **Under what conditions**

> Policies are attached to IAM users, groups, or roles to grant permissions.

---

## 🧱 Policy Types

| Type              | Description                                                |
|-------------------|------------------------------------------------------------|
| **Managed Policy** | Reusable standalone policy. AWS or customer-managed.       |
| **Inline Policy**  | Embedded directly into a single user, group, or role.      |

✅ Prefer **managed policies** for reusability and consistency.

---

## 🔍 IAM Policy Structure

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:ListBucket",
      "Resource": "arn:aws:s3:::my-bucket"
    }
  ]
}
```

Key Elements:
| Element     | Description                                         |
| ----------- | --------------------------------------------------- |
| `Version`   | Policy language version (always use `"2012-10-17"`) |
| `Effect`    | `Allow` or `Deny`                                   |
| `Action`    | Specific AWS API actions (e.g., `s3:GetObject`)     |
| `Resource`  | The ARN of the AWS resource                         |
| `Condition` | (Optional) Conditions for when the policy applies   |



📌 Examples
✅ Allow Read-Only Access to S3

```json
{
  "Effect": "Allow",
  "Action": [
    "s3:GetObject",
    "s3:ListBucket"
  ],
  "Resource": [
    "arn:aws:s3:::my-bucket",
    "arn:aws:s3:::my-bucket/*"
  ]
}
```


### ❌ Explicitly Deny All S3 Delete Access

```json
{
  "Effect": "Deny",
  "Action": "s3:DeleteObject",
  "Resource": "*"
}
```

---

## 🛠️ How to Attach a Policy (Console)

1. Go to **IAM > Users / Roles**
2. Select a **user or role**
3. Click **Add permissions**
4. Choose:
   - **Attach existing policies** (e.g. `AmazonS3ReadOnlyAccess`)
   - OR **Create an inline policy**
5. **Review and apply**

---

## 🔎 IAM Policy Simulator

Use the **IAM Policy Simulator** to test your policies before applying:  
👉 [https://policysim.aws.amazon.com](https://policysim.aws.amazon.com)

---

## 🔐 Best Practices

✅ Follow **least privilege** – grant only what is necessary  
✅ Prefer **managed policies** over inline policies  
✅ Use **wildcards** cautiously (`*`)  
✅ Regularly **review and audit** permissions  
✅ Use the **policy simulator** for validation

---

## 🧠 Summary

| Term           | Meaning                                      |
|----------------|----------------------------------------------|
| **Managed Policy** | Reusable and attachable policy           |
| **Inline Policy**  | One-time, embedded policy                |
| **Effect**         | Allows or denies access                  |
| **Action**         | AWS API operation                        |
| **Resource**       | AWS resource ARN                         |
| **Condition**      | (Optional) Constraints like IP, MFA, tags, etc. |

---
