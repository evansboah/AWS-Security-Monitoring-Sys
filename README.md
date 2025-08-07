
# 🛡️ Legendary AWS Security Monitoring System  
**Author:** Evans Yeboah | Cloud Security Engineer (Aspiring)  
**Platform:** [NextWork.org](https://nextwork.org)  
**Duration:** ~2 hours  
**Focus:** Secrets Manager, CloudTrail, CloudWatch, SNS  

---

## 🚀 Project Overview  
This project demonstrates how to build a security monitoring system on AWS. It tracks secret access events and sends real-time alerts using CloudWatch and SNS.

### 🔍 Objectives  
- Secure sensitive credentials with AWS Secrets Manager  
- Record access events using AWS CloudTrail  
- Monitor activity with CloudWatch metrics and alarms  
- Send notifications via Amazon SNS  

---

## 🧰 Tools & Services  
| Service            | Purpose                                      |
|--------------------|----------------------------------------------|
| AWS Secrets Manager| Store and manage sensitive credentials       |
| AWS CloudTrail     | Log and audit API activity across AWS        |
| Amazon CloudWatch  | Create metrics, alarms, and visual dashboards|
| Amazon SNS         | Send email alerts when alarms are triggered  |

---

## 🔐 Step 1: Create a Secret  
Created a secret named `TopSecretInfo` in AWS Secrets Manager containing credentials for the monitoring system.

```json
{
  "The Secret is": "I love my Wife"
}
```

---

## 📜 Step 2: Enable CloudTrail  
Enabled CloudTrail to record all management and data events.  
Tracked secret access via:
- **Event Source:** `secretsmanager.amazonaws.com`  
- **Event Name:** `GetSecretValue`  
- **User Identity:** IAM credentials used  
- **Resource Type:** Secrets Manager  

Command used to retrieve the secret:
```bash
aws secretsmanager get-secret-value --secret-id "TopSecretInfo" --region us-east-1
```

---

## 📊 Step 3: Create CloudWatch Metric  
Set up a metric filter to count secret access events.  
- **Metric Name:** `SecretIsAccessed`  
- **Namespace:** `SecurityMetrics`  
- **Metric Value:** `1` when accessed  
- **Default Value:** `0` when not accessed  

This setup ensures visibility into both access and inactivity periods.

---

## ⏰ Step 4: Configure CloudWatch Alarm  
Created a CloudWatch alarm to monitor the `SecretIsAccessed` metric.  
- **Threshold:** ≥ 1 access event  
- **Period:** 300 seconds  
- **Statistic:** Sum  
- **State Change:** OK → ALARM  

---

## 📣 Step 5: Set Up SNS Notifications  
Created an SNS topic named `SecurityAlarms` to send email alerts when the alarm triggers.  
Confirmed subscription via email.  
Tested notifications using manual SNS publish and alarm simulation.

---

## 🛠️ Troubleshooting  
Initially, notifications failed due to incorrect threshold configuration.  
Resolved by switching from `count` to `sum` in CloudWatch alarm settings.  
Verified:
- Alarm history  
- SNS topic access policy  
- Encryption settings  
- Manual publish tests  

---

## ✅ Results  
Received real-time email alerts when the secret was accessed.  
CloudWatch alarm transitioned to ALARM state as expected.

---

## 🔁 Extension: CloudTrail SNS Notifications  
Enabled SNS notifications for CloudTrail logs to receive alerts for broader AWS activity.  
Inbox flooded with alerts—highlighting system responsiveness and visibility.

---

## 📌 Key Takeaways  
- Security monitoring is achievable with native AWS tools  
- CloudTrail + CloudWatch + SNS = powerful alerting pipeline  
- Real-time visibility into secret access strengthens governance  

---

## 📣 Connect with Me  
🔗 [LinkedIn]https://www.linkedin.com/in/evans-yeboah-33b81954?
📁 [More Projects](https://github.com
🧠 [NextWork Profile](https://nextwork.org)

---

> “Security is not just a feature—it’s a mindset.”  
```
