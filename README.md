**EC2 Start/Stop Automation with EventBridge & GitHub Actions**

This project automates AWS EC2 start and stop operations to reduce cloud costs, while still allowing manual control via CI/CD when needed.

**🚀 Overview**

Idle EC2 instances can significantly increase AWS costs.
This solution uses:
```
AWS EventBridge (cron rules) for automatic scheduling

GitHub Actions for manual, controlled start/stop

Tag-based filtering for scalability and safety
```

**🕒 Automated Scheduling (Cost Optimization)**

Two EventBridge rules are configured:
```
⏰ Start EC2 instances at 7:30 AM

⏰ Stop EC2 instances at 6:30 PM
```
Only instances with the required tags are affected — no hardcoded instance IDs.

**✅ Benefits**
```
Eliminates idle EC2 costs outside business hours

Fully automated

Zero manual intervention required
```

**🔧 Manual Override via CI/CD**

Sometimes developers need EC2 instances outside business hours.
To handle this, a GitHub Actions workflow was added.

What the CI/CD pipeline does:
```
Allows manual start/stop of EC2 instances

Uses workflow_dispatch

Filters instances using tags

Uses GitHub Secrets for AWS credentials

No AWS Console access required

This keeps the environment:

Secure

Auditable

Easy to use
```

**🏷️ Tag-Based Control**

EC2 instances are managed using tags such as:
```
AutoManage = true

This ensures:

Only intended instances are affected

Easy onboarding of new instances

No risk of stopping critical systems
```

**🔐 Security**
```
AWS credentials stored securely in GitHub Secrets

IAM permissions follow least privilege

No credentials committed to the repository
```

**🧩 Technologies Used**
```
AWS EC2

AWS EventBridge

GitHub Actions

AWS CLI

IAM

Bash scripting
```

**📈 Outcome**
```
Reduced AWS EC2 costs

Automated day-to-day operations

Flexible manual override for developers

Improved operational efficiency
```

**📌 Future Improvements**
``
Slack / Teams notifications

Multi-environment support (dev / test / prod)

Instance group selection by environment tags
``
**📎 Notes**
```
This project demonstrates a real-world FinOps + DevOps use case, combining automation with practical operational flexibility.
```

**▶️ How to Run the CI/CD Pipeline (Manual EC2 Control)**

The GitHub Actions workflow allows you to manually start or stop EC2 instances when needed (for example, outside business hours).

Steps to run the pipeline:
```
Go to the GitHub repository

Click on the Actions tab

Select the workflow EC2 Start/Stop

Click Run workflow

Fill in the required inputs:

action → set to:

start to start EC2 instances

stop to stop EC2 instances

tag_key → the EC2 tag key (e.g. AutoManage)

tag_value → the EC2 tag value (e.g. true)

Click Run workflow
```

**✅ How it works**
```
The pipeline finds EC2 instances using the provided tags

Based on the action value, EC2 instances will:

Start if start is selected

Stop if stop is selected

No code changes are required — simply edit the start/stop value to control EC2 behavior
```
