The system admin team at xFusionCorp Industries has streamlined access management by implementing group-based access control. Here's what you need to do:



a. Create a group named nautilus_sftp_users across all App servers within the Stratos Datacenter.


b. Add the user jarod into the nautilus_sftp_users group on all App servers. If the user doesn't exist, create it as well.


Approach:
1. ssh into app server 1
2. create group
   ```
   sudo groupadd nautilus_sftp_users
   ```
3. check if user jarod exists
   ```
   id jarod
   ```
4. create user jarod
   ```
   sudo useradd jarod
   ```
5. add jarod user to group
   ```
   sudo usermod -aG nautilus_sftp_users jarod
   ```
   
