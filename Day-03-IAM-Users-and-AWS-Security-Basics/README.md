# Day 03 – IAM Users and AWS Security Best Practices

Today we focus on securing your AWS account by:
- Understanding IAM (Identity and Access Management)
- Creating individual IAM users
- Following security best practices

---

## 👤 What is IAM?

**IAM (Identity and Access Management)** is a service that allows you to:
- Manage users and groups
- Define roles and permissions
- Control access to AWS resources securely

### Key IAM Components:
| Component  | Description |
|------------|-------------|
| **User**   | Represents a person or application |
| **Group**  | Collection of users with common permissions |
| **Role**   | Used to delegate access to services or applications |
| **Policy** | A JSON document defining allowed/denied actions |

---

## 🛠️ How to Create an IAM User

1. Go to AWS Console → **IAM**
2. Click **Users → Add users**
3. Enter username (e.g., `dev-user`)
4. Select **Access type**:
   - ✅ Programmatic Access (for CLI/API)
   - ✅ AWS Management Console Access
5. Set a custom password or auto-generate
6. Click **Next: Permissions**
7. Choose:
   - **Add user to group** (e.g., `Developers`)
   - OR attach existing policies (e.g., `AmazonS3ReadOnlyAccess`)
8. **Tag** user (optional)
9. Review and **Create User**
10. Save credentials (.csv file) for CLI use

---

## 🔐 AWS Security Best Practices

✅ **Don’t use the Root Account**  
❗ Only use it to create your first IAM user, then lock it down

✅ **Enable MFA (Multi-Factor Authentication)**  
Adds a second layer of security to sign-ins

✅ **Use IAM Groups for Permissions Management**  
Attach policies to groups, not individual users

✅ **Use IAM Roles for EC2 and services**  
Avoid hardcoding credentials inside applications

✅ **Rotate access keys regularly**

✅ **Set up Billing Alerts and Budgets**

✅ **Monitor with AWS CloudTrail and Config**

---

📌 **Next Steps**:  
In Day-04, we will set up **AWS Free tier account**.

---
