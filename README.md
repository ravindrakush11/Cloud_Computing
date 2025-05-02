# Cloud_Computing

## 🛠️ Setup

The quickest setup to run example notebooks includes:

- An **AWS account**
- Proper **IAM User and Role** setup
- An **Amazon SageMaker Notebook Instance**
- An **S3 bucket**

# 🚀 Getting Started with Amazon SageMaker Studio

This guide helps beginners set up, use, and optionally delete resources in Amazon SageMaker Studio.

---

## 🛠️ Prerequisites

- ✅ An AWS account
- ✅ IAM permissions for SageMaker, S3, and IAM role creation

---

## 📦 Step 1: Set Up a SageMaker Studio Domain

1. Go to the SageMaker Console:  
   [https://console.aws.amazon.com/sagemaker](https://console.aws.amazon.com/sagemaker)

2. In the left sidebar, select:  
   `SageMaker Studio > Domains`

3. Click **"Create domain"**.

4. Choose **Quick setup** for beginners.

5. Set the following:
   - **Domain name** (e.g., `my-studio-domain`)
   - **User profile name** (e.g., `default-user`)
   - Select a **VPC and subnet**
   - Optionally configure or create an **execution role**

6. Attach or allow the wizard to create an S3 bucket.

7. Review and create the domain.

---

## 🧑‍💻 Step 2: Launch SageMaker Studio

1. Go to `SageMaker Studio > Domains`.
2. Click your domain name.
3. Select the user profile (e.g., `default-user`).
4. Click **"Open Studio"**.

---

## 📚 Step 3: Use Prebuilt ML Tools (Optional)

From the Studio interface, you can:
- Use **JumpStart** to try prebuilt ML models
- Open **Notebooks** to run Python/ML code
- Use **AutoML**, **Pipelines**, or **Data Wrangler**

You can also:
- Train and deploy models
- Use Hugging Face models like `distilbert-base-uncased`

---

## 🧹 Step 4: Cleanup (Optional but Recommended)

### 🔄 A. Stop Running Apps (to avoid charges)
1. Go to `SageMaker Studio > Domains`
2. Click on your domain
3. Select the **User Profile**
4. Stop all listed apps (e.g., JupyterServer, KernelGateway)

---

### 🗑️ B. Delete the User Profile
1. Still in the user profile page
2. Once all apps are stopped, click **“Delete”** on the top-right

---

### ❌ C. Delete the Domain
1. Go to `SageMaker Studio > Domains`
2. Check the box next to your domain
3. Click **“Delete”** (it appears only when all user profiles are removed)
4. Confirm by typing **delete**

---

### 🗑️ D. Optional Cleanup of Other Resources
- Go to **S3**, delete SageMaker buckets (e.g., `sagemaker-...`)
- Remove custom IAM roles created for SageMaker

---

## 📝 Notes

- SageMaker Studio is a **fully managed IDE** for ML. You only pay for what you use.
- Deleting apps or domains will **prevent unwanted charges**.
- Free tier users get limited usage hours for Studio.

---

## 📌 Recommended Next Steps

- Explore JumpStart models
- Learn Boto3 SDK to script SageMaker
- Try deploying your own ML model

---

## 📎 References

- [SageMaker Studio Docs](https://docs.aws.amazon.com/sagemaker/latest/dg/studio.html)
- [AWS Pricing](https://aws.amazon.com/sagemaker/pricing/)
