Here is the full content you can put into your `README.md` file for your internship task:

---

# 🖥️ AWS CloudWatch Monitoring Task – Internship Project

This project is done as part of the **CodTech Internship** under the task:

> **"Set Up Monitoring for a Cloud-Based Application using AWS CloudWatch, Google Cloud Monitoring, or Azure Monitor."**

---

##  Objective

To deploy a simple Node.js application on an EC2 instance and configure **AWS CloudWatch** for monitoring system metrics (CPU, Memory), collect logs, and set up alerts and a dashboard.

---

## 📦 Technologies Used

* **AWS EC2**
* **Amazon CloudWatch**
* **Amazon CloudWatch Agent**
* **Node.js**
* **Git**
* **Amazon Linux 2**

---

## 🧱 Steps Followed

### 1️⃣ Launched EC2 Instance

* Amazon Linux 2 AMI
* Enabled ports: **22 (SSH)** and **80 (HTTP)** in the Security Group.
* Created a key pair to securely SSH into the EC2 instance.

### 2️⃣ Connected to EC2 via SSH (Windows)

Used Git Bash with `.pem` key to connect:

![Screenshot 2025-05-31 112752](https://github.com/user-attachments/assets/b6c59117-43e9-4ed1-b7fe-72306a2600bd)
ssh -i "aws_key.ppk" ec2-user@184.73.57.245


### 3️⃣ Installed Dependencies


sudo yum update -y
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.3/install.sh | bash
source ~/.bashrc
nvm install 18
nvm use 18
sudo yum install git -y

### 4️⃣ Cloned GitHub Repo & Ran Node.js App


git clone https://github.com/SatyaDatta/aws_cloudwatch_task2.git
cd aws_cloudwatch_task2
npm install
node app.js


> The `app.js` logs a message every 5 seconds to simulate application activity.

### 5️⃣ Installed & Configured CloudWatch Agent


sudo yum install amazon-cloudwatch-agent -y


Created a CloudWatch Agent config file at:

```bash
/opt/aws/amazon-cloudwatch-agent/bin/config.json
```

**Config Includes:**

* CPU and Memory usage metrics
* Log collection from `/var/log/messages`

Started the agent:

```bash
sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-ctl \
-a fetch-config -m ec2 -c file:/opt/aws/amazon-cloudwatch-agent/bin/config.json -s
```

---

## 📈 Monitoring & Alerts
![Screenshot 2025-05-31 103823](https://github.com/user-attachments/assets/8f3acd27-dd1f-48ab-a6e9-6e427deb02c7)


### 🔹 CloudWatch Dashboard

* Created dashboard displaying:

  * CPU Utilization
  * Memory Usage
  * Custom Logs

### 🔹 CloudWatch Alarms

* Alarm set to monitor:

  * **CPU > 80%**
  * **Memory > 75%**
* Notification sent via **SNS** (email subscription).

---

## 📁 Repository Contents

aws_cloudwatch_task2/
├── app.js                # Node.js test app
├── package.json          # NPM project file
├── README.md             # This file
└── cloudwatch-config.json (optional)
```

## 📬 Conclusion

✅ The app is successfully deployed on AWS EC2.
✅ CloudWatch Agent is configured and running.
✅ Metrics and logs are visible on a custom dashboard.
✅ Alarms trigger email alerts for high

 CPU and memory usage.


