The Nautilus system admins team has prepared scripts to automate several day-to-day tasks. They want them to be deployed on all app servers in Stratos DC on a set schedule. Before that they need to test similar functionality with a sample cron job. Therefore, perform the steps below:



a. Install cronie package on all Nautilus app servers and start crond service.


b. Add a cron */5 * * * * echo hello > /tmp/cron_text for root user.


Approach:
The Nautilus system admins wanted to test scheduled task automation on all app servers before deploying real scripts.

cronie is the cron job scheduler on Linux systems (RHEL/CentOS based).
Cron allows you to:
1. Run commands automatically
2. At fixed times or intervals
3. Without human intervention

```
yum install -y cronie
```

crond is the background daemon (service) that:
1. Reads cron schedules
2. Executes jobs at the correct time
```
systemctl start crond
systemctl enable crond
```
start → makes cron work now
enable → makes cron start automatically after reboot

```
*/5 * * * * echo hello > /tmp/cron_text
```
Runs every 5min. Every 5 minutes: The file /tmp/cron_text is created or overwritten

```
sudo crontab -e
echo hello > /tmp/cron_text
```
This job runs at root, so to avoid any permission issues.

Repeat the above steps on all app servers.
