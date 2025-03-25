# 🚀 Flask App Deployment on AWS & CI/CD Demo

This repository contains a **Flask web application**, deployed on **AWS EC2**, with **CI/CD automation** using GitHub Actions.

---

## 📌 Steps to Set Up & Run

### **1️⃣ Prerequisites**
- ✅ AWS Account & EC2 instance (Ubuntu)
- ✅ Python3 installed
- ✅ Git & SSH configured
- ✅ Flask & dependencies installed

### **2️⃣ Clone This Repository**
```sh
git clone https://github.com/your-username/DevOps-CICD-Demo.git
cd DevOps-CICD-Demo
```

### **3️⃣ Set Up a Virtual Environment & Install Dependencies**
```sh
sudo apt update
sudo apt install python3-venv -y
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

### **4️⃣ Running the Flask Application Locally**
```sh
python3 app.py --host=0.0.0.0
```

📌 **Access the app in your browser:**  
`http://<your-public-ip>:5000/`

---

## 📌 Deployment on AWS EC2

### **1️⃣ Launch an AWS EC2 Instance**
- Choose **Ubuntu (t2.micro - Free Tier)**
- Configure **Security Groups**:
  - **Allow port 22** (SSH)
  - **Allow port 5000** (Flask)

### **2️⃣ Connect to EC2 via SSH**
```sh
ssh -i your-key.pem ubuntu@<your-public-ip>
```

### **3️⃣ Run the Flask App on AWS**
```sh
nohup python3 app.py --host=0.0.0.0 &
```

📌 **Now access the app:** `http://<your-public-ip>:5000/`

---

## 📌 CI/CD Workflow with GitHub Actions

Inside `.github/workflows/ci.yml`, we set up **CI/CD automation** to:
✅ Install dependencies  
✅ Run tests  
✅ Deploy automatically (if configured)  

📌 Example CI/CD Workflow (`.github/workflows/ci.yml`):
```yaml
name: CI/CD Pipeline

on:
  push:
    branches:
      - main

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repository
        uses: actions/checkout@v2
      
      - name: Set up Python
        uses: actions/setup-python@v2
        with:
          python-version: '3.9'

      - name: Install Dependencies
        run: |
          python -m pip install --upgrade pip
          pip install -r requirements.txt

      - name: Run Tests
        run: python -m unittest discover -s tests
```

---

## 📌 Troubleshooting Common Issues

🔴 **SSH Permission Denied?**  
✅ Fix with:
```sh
chmod 400 your-key.pem
```

🔴 **Flask App Stopped After Logout?**  
✅ Run in background:
```sh
nohup python3 app.py --host=0.0.0.0 &
```

🔴 **Port 5000 Not Accessible?**  
✅ Update AWS Security Group to allow **incoming traffic on port 5000**.

---

## 🚀 Next Steps
🔹 **Containerizing with Docker** 🐳  
🔹 **Automating deployment with CI/CD** 🔄  
🔹 **Exploring Kubernetes** ☸️  

📌 **Now, commit and push these updates to your repo:**
```sh
git add .
git commit -m "Updated README and project structure"
git push origin main
```

---

### ✅ Final Notes
With this updated **GitHub repository**, you now have a **clear reference** for the future! 🚀 This ensures that **whenever you revisit this project, everything is well-documented and easy to set up again!** 🔥

