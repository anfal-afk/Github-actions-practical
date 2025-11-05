# Github-actions-practical
Github-actions-practice


Prerequisites required - CI-CD_python.yml

✅ 1. GitHub Actions Setup

Repository: Your Python application code must be in a GitHub repository.
Workflow File: Place the YAML file under .github/workflows/ci-cd.yml.


✅ 2. Secrets Configuration
Add these secrets in your GitHub repository settings under Settings → Secrets → Actions:

WIN_SERVER → Windows Server hostname or IP.
WIN_USER → Username with deployment permissions.
WIN_PASS → Password for the user.
(Optional for CloudWatch):

AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
AWS_REGION




✅ 3. Windows Server Configuration

Enable WinRM:

Run Enable-PSRemoting -Force on the server.
Allow ports 5985 (HTTP) or 5986 (HTTPS) in firewall.


Permissions:

The user in WIN_USER must have rights to copy files and run Python.


Python Installed:

Ensure Python 3.11 or compatible version is installed on the server.


IIS or Service Setup (optional):

If hosting via IIS or as a Windows service, configure accordingly.




✅ 4. Python App Structure

requirements.txt → All dependencies listed.
tests/unit and tests/integration → For unit and integration tests.
app.py or entry point → The script to start your app.


✅ 5. Backup Strategy

Create C:\apps\python-app-backup folder on the server for rollback.
Ensure enough disk space for backups.


✅ 6. AWS CloudWatch (Optional Health Check)

Install AWS CLI on the runner (already in YAML).
Ensure your app is behind an Application Load Balancer (ALB) with a Target Group for health metrics.
Configure CloudWatch metrics for HealthyHostCount.


✅ 7. GitHub Runner

Using windows-latest hosted runner is fine for build/test.
If you want direct deployment without WinRM, set up a self-hosted runner on the Windows Server.


🔥 Do you want me to add the AWS CloudWatch health check step into your current YAML (with rollback if unhealthy) AND an HTTP endpoint check for extra safety?
Or should I prepare a version for self-hosted runner (no WinRM needed)?
Provide your feedback on BizChatAdd HTTP endpoint check stepPrepare version for self-hosted runnerExplain AWS metric query usedDrop your files hereMessage CopilotFilesFilesAI-generated content may be incor
