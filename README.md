
---

```markdown
# 📦 Terraform Project: Static Website Hosting on AWS S3

This project provisions a **static website** on AWS using Terraform. It uses **Amazon S3** to host an HTML/CSS frontend with public access and website configuration.

---

## 📁 Project Structure

```

proj-static-website-terraform/
├── index.html
├── style.css
├── main.tf
├── variables.tf
├── output.tf
├── terraform.tfstate (local state file)
└── .gitignore

````

---

## 🌐 Features

- Creates a versioned S3 bucket with a unique name
- Uploads `index.html` and `style.css` to the bucket
- Configures the S3 bucket for static website hosting
- Makes content publicly readable
- Outputs the public website URL

---

## 🔧 Prerequisites

- AWS CLI configured (`aws configure`)
- Terraform v1.3+ installed
- `index.html` and `style.css` in the same directory

---

## 🚀 How to Deploy

### 1. Initialize Terraform

```bash
terraform init
````

### 2. Apply the Infrastructure

```bash
terraform apply
```

> Confirm with `yes` when prompted. Terraform will generate a random suffix for the bucket name to ensure uniqueness.

### 3. Access the Website

Once applied, Terraform will output the website URL like this:

```
Outputs:

name = "mywebapp-bucket-<random-id>.s3-website.ap-south-1.amazonaws.com"
```

Open that URL in your browser to see your website.

---

## 🔄 Update Website Content

To update `index.html` or `style.css`:

1. Edit the files locally
2. Run:

```bash
terraform apply -refresh-only
```

*OR*, manually re-upload using:

```bash
aws s3 cp index.html s3://<bucket-name>/
aws s3 cp style.css s3://<bucket-name>/
```

---

## 🧹 Teardown

To delete all resources:

```bash
terraform destroy
```

---

## 🔐 Notes

* `block_public_acls` and related flags are disabled to allow public access
* Bucket name is randomized using `random_id` to avoid conflicts
* Ensure `content_type` is correct for both HTML and CSS uploads

---

## 👨‍💻 Author

**Vignesh Sadanki**
GitHub: [@Sadanki](https://github.com/Sadanki)

```
