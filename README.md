
# 🔐 Cloud Infrastructure Compliance Auditor & Auto-Remediator (CICAR)

CICAR is a real-world, cloud security automation project that audits AWS infrastructure for misconfigurations and optionally remediates them while sending alert notifications. It mimics real-world DevSecOps and Cloud Security workflows, showcasing your ability to implement proactive cloud compliance and security automation solutions.

---

## 📌 Key Features

- ✅ Audits AWS EC2, S3, and IAM configurations for common security issues
- ✅ Generates compliance reports in JSON and optional HTML
- ✅ Sends real-time alerts to Slack (or other services)
- ✅ Auto-remediates common misconfigurations like public S3 buckets
- ✅ Designed to simulate a real Security Operations or DevSecOps workflow

---

## 🎯 Use Case

CICAR is ideal for cloud engineers, DevSecOps teams, and security analysts who want to:
- Continuously monitor AWS for misconfigurations
- Enforce security best practices (like AWS Well-Architected, CIS Benchmarks)
- Respond automatically to insecure configurations

---

## 🧱 Architecture Overview

1. **Audit Scripts** (Python using Boto3) scan:
   - **EC2** for overly permissive ports
   - **S3** for public buckets
   - **IAM** for insecure settings (MFA, access keys)
2. **Report Generator** saves scan results to JSON
3. **Remediation Engine** optionally fixes issues using AWS APIs
4. **Alert System** notifies the team via Slack

---

## 🛠️ Tech Stack

| Category           | Tool/Service                  |
|--------------------|-------------------------------|
| Cloud              | AWS (EC2, S3, IAM)            |
| Language           | Python                        |
| SDK/API            | Boto3 (AWS SDK)               |
| Alerting           | Slack Webhooks                |
| Reporting          | JSON, Optional HTML           |

---

## 🗂️ Folder Structure

```
cloud-compliance-auditor/
├── scripts/
│   ├── audit_ec2.py          # Scan EC2 security groups
│   ├── audit_s3.py           # Scan S3 bucket permissions
│   ├── audit_iam.py          # Scan IAM security settings
│   ├── remediate.py          # Fix misconfigurations (optional)
│   └── send_alerts.py        # Send Slack or email alerts
├── reports/
│   └── audit_report.json     # Security findings
├── config/
│   └── settings.json         # Region & webhook configs
├── README.md
├── requirements.txt
```

---

## 🚀 How to Run the Project

### 1. Install Dependencies

```bash
pip install -r requirements.txt
```

### 2. Configure AWS Access

Set up your AWS CLI credentials using:

```bash
aws configure
```

Make sure your IAM user has permissions to describe EC2, S3, IAM.

### 3. Update Config

Edit `config/settings.json`:

```json
{
  "slack_webhook": "https://hooks.slack.com/services/your/webhook/url",
  "regions": ["us-west-2"]
}
```

### 4. Run Audit Scripts

```bash
python scripts/audit_ec2.py
python scripts/audit_s3.py
python scripts/audit_iam.py
```

### 5. (Optional) Run Remediation

```bash
python scripts/remediate.py
```

### 6. Send Alerts

```bash
python scripts/send_alerts.py
```

---

## 📸 Real Output Screenshots

### EC2 Audit Output
![EC2 Audit](./real_ec2_audit_output.png)

### S3 Public Access Alert
![S3 Alert](./real_s3_audit_output.png)

### Auto-Remediation + Slack Notification
![Remediation](./real_remediation_output.png)

---

## 📈Report Output (JSON)

```json
{
  "EC2": {
    "InsecureInstances": [
      {
        "InstanceId": "i-0a12345678",
        "OpenPorts": [22, 3389],
        "Severity": "HIGH"
      }
    ]
  },
  "S3": {
    "PublicBuckets": [
      {
        "BucketName": "my-public-bucket",
        "Permission": "READ",
        "Severity": "CRITICAL"
      }
    ]
  }
}
```

---

## 💡 Future Improvements

- Integrate with AWS Config or Security Hub
- Export to external dashboard (Streamlit or Grafana)
- Add risk scoring or compliance mapping (CIS/NIST)

---

---




