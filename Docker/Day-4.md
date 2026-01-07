The Nautilus DevOps team possesses confidential data on App Server 3 in the Stratos Datacenter. A container named ubuntu_latest is running on the same server.



Copy an encrypted file /tmp/nautilus.txt.gpg from the docker host to the ubuntu_latest container located at /usr/src/. Ensure the file is not modified during this operation.

Approach:
1. ssh into app server 3.
2. execute the below command
   ```
   docker cp /tmp/nautilus.txt.gpg ubuntu_latest:/usr/src
   ```
3. To check the file inside the container
   ```
   docker exec -it ubuntu_latest /bin/bash
   ```
