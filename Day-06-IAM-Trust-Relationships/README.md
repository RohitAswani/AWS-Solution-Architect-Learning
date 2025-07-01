# Day 06 – IAM Trust Relationships (In-Depth)

Today, we’ll explore **Trust Relationships** in IAM – a critical part of roles that defines **who is allowed to assume** them.

---

## 🤝 What is a Trust Relationship?

A **Trust Relationship** is part of a role’s **trust policy**, which specifies the **trusted entities** (users, services, accounts) that can assume the role.

> Think of it as: "Who do I trust to use this role?"

---

## 🧾 Trust Policy – Structure

Trust relationships are defined using a JSON document called a **trust policy**.

### 🔍 Example: Trust policy allowing EC2 to assume a role

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

Principal – who can assume the role (EC2 in this case)

Action – must always be sts:AssumeRole

🤝 Trusting Other AWS Accounts
Trust relationships also enable cross-account access.

🔍 Example: Allowing Account B (ID: 123456789012) to assume a role in Account A


```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "AWS": "arn:aws:iam::123456789012:root"
      },
      "Action": "sts:AssumeRole"
    }
  ]
}
```

---

## 🔄 Flow of Role Assumption (Cross-Account)

1. **Account A** creates a role with a **trust policy** allowing **Account B**
2. **Account B** assumes the role using `sts:AssumeRole`
3. **Account B** receives temporary security credentials
4. These credentials are used to **access AWS resources** in Account A

---

## 🛠️ How to Modify a Role's Trust Relationship in Console

1. Go to **IAM → Roles**
2. Select the desired role
3. Click on the **"Trust relationships"** tab
4. Click **Edit trust policy**
5. Add or modify the trust policy JSON document

---

## 🧠 Summary

| Term           | Meaning                                                  |
|----------------|----------------------------------------------------------|
| **Trust Policy**   | Who is allowed to assume the role                      |
| **AssumeRole**     | STS API used to assume a role                          |
| **Principal**      | Trusted entity (account, user, service)               |
| **Cross-account**  | Allowing external AWS accounts to assume a role       |

---

## ✅ Best Practices

- Always define **specific principals**, not wildcards (`"Principal": "*"` is risky)
- Monitor **CloudTrail logs** for any role assumptions
- Combine **trust policies** and **permissions policies** to secure access
- Limit permissions using **least privilege principle**

---

📌 **Next Steps:**  
In **Day-07**, we’ll go deep into **IAM Policies** – how to write and evaluate them, and understand the difference between **inline** and **managed** policies.

---
