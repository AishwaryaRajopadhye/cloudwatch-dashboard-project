# Step-by-Step Guide: AWS CloudWatch Dashboards for Comprehensive Monitoring

---

## Step 1: Prerequisites

Ensure:
- Active AWS Account
- IAM role/user with:
  - AmazonSSMFullAccess
  - AmazonSSMManagedInstanceCore
  - CloudWatchAgentServerPolicy
  - Custom: `PutParameterCloudWatchPolicy`

Also:
- Enable billing alerts in **Billing → Preferences**
- EC2 instance with Amazon Linux
- CloudWatch Agent installed

---

## Step 2: Enable Billing Metrics

- Go to Billing → Preferences
- Check ✅ “Receive Billing Alerts”
- CloudWatch will now access AWS/Billing metrics

---

## Step 3: Create IAM Role for EC2

- IAM → Roles → Create Role
- Choose AWS service → EC2
- Attach:
  - AmazonSSMFullAccess
  - AmazonSSMManagedInstanceCore
  - CloudWatchAgentServerPolicy
  - PutParameterCloudWatchPolicy (custom)
- Attach this role to the EC2 instance

---

## Step 4: Install CloudWatch Agent on EC2

```bash
sudo yum install amazon-cloudwatch-agent
sudo /opt/aws/amazon-cloudwatch-agent/bin/amazon-cloudwatch-agent-config-wizard
