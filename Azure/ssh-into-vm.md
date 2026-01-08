The Nautilus DevOps team is working on setting up secure SSH access for their virtual machines in Azure. One of the requirements is to add the SSH public key of the root user from the Azure client host (landing host) to the devops-vm Azure VM's authorized_keys file. This ensures secure and password-less SSH access to the VM.

Task Details:
1) VM Details:

The VM is named devops-vm and is running in the West US region. The default SSH user is azureuser — use this user to connect to the VM.
You need to add the root user's SSH public key from the Azure client host to the authorized_keys file of the VM's root user.
The SSH public key of the root user on the Azure client host is located at /root/.ssh/id_rsa.pub.
2) Public Key Addition:

Copy the public key located at /root/.ssh/id_rsa.pub on the Azure client host to the authorized_keys file of the root user on devops-vm.
Ensure that the proper permissions for the .ssh folder and authorized_keys file are set on the VM.
3) Verification:

After adding the public key, make sure that you are able to SSH into the devops-vm VM as the root user from the Azure client host without needing a password.

Approach:
1. Copy the public key of azure client host.
   ```
   cat /root/.ssh/id_rsa.pub
   ```
2. ssh into vm and switch to root user
   ```
   ssh azureuser@ip
   sudo su
   ```
3. after entering the password, create a .ssh folder in root
   ```
   mkdir .ssh
   ```
4. create a file called authorized_keys and copy the public key
   ```
   cd .ssh
   vi authorized_keys
   ```
5. Set the permissions of the .ssh folder
   ```
   chmod 600 /.ssh/authorized_keys
   chown -R root:root /.ssh/
   ```
6. Now, you can able to switch to root without password from azure client.
   


