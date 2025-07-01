# Day 05 – IAM Roles (In-Depth)

Today, we’ll explore IAM Roles in depth. Roles are one of the most powerful and flexible components in AWS Identity and Access Management.

---

## 🎭 What is an IAM Role?

An **IAM Role** is an AWS identity with specific **permissions** that can be **assumed temporarily** by trusted entities (users, services, or AWS accounts).

Unlike IAM Users:
- Roles **don’t have long-term credentials**
- They are **assumed** and provide **temporary security credentials**

---

## 👥 Who Can Assume a Role?

- **IAM Users** in the same or another AWS account
- **AWS Services** (e.g., EC2, Lambda)
- **Federated users** (e.g., SSO, Active Directory)

---

## 🧱 Components of a Role

| Component           | Description                                        |
|---------------------|----------------------------------------------------|
| **Trust Policy**     | Specifies **who** can assume the role             |
| **Permissions Policy**| Specifies **what** the role can access            |
| **Session Duration** | Duration of temporary credentials (up to 12 hours)|
| **Role ARN**         | Amazon Resource Name used to reference the role   |

---

## 🚀 Common Use Cases

### 1. **Assigning Role to EC2**
- Use a role to allow an EC2 instance to access S3, CloudWatch, etc. without storing credentials.

### 2. **Lambda Functions**
- Assign roles to Lambda for calling other AWS services securely.

### 3. **Cross-Account Access**
- Allow Account A to assume a role in Account B using trust relationships.

---

## 🛠️ Creating a Role (EC2 Example)

1. Go to **IAM > Roles > Create Role**
2. Select **Trusted Entity** → AWS Service → **EC2**
3. Click **Next**
4. Attach a permission policy (e.g., `AmazonS3ReadOnlyAccess`)
5. Add tags (optional)
6. Review and **Create Role**
7. Assign role to EC2 during launch or attach to a running instance

---

## 🔐 Temporary Security Credentials

Roles issue **temporary credentials** when assumed:
- `Access Key ID`
- `Secret Access Key`
- `Session Token`

These are valid only for a limited time (e.g., 1–12 hours)

---

## 📌 Best Practices

✅ Use roles instead of hardcoded access keys  
✅ Grant **least privilege** – only required permissions  
✅ Use roles for **cross-account and federated access**  
✅ Rotate and limit duration of temporary credentials

---

📌 **Next Steps:**  
In Day-06, we’ll dive into **IAM Trust Relationships**, which define who can assume a role and how cross-account access works.

---
