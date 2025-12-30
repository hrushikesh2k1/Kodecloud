There is a critical issue going on with the Nautilus application in Stratos DC. The production support team identified that the application is unable to connect to the database. After digging into the issue, the team found that mariadb service is down on the database server.



Look into the issue and fix the same.

Approach:
1. Switch to root user.
   ```
   sudo su
   ```
   
2. Get the mariadb service status.
   ```
   systemctl status mariadb
   ```
   you will be seeing status as Inactive (dead)
   
4. Run the below command to see the exact reason for mariadb down.
   ```
   journctl -xeu mariadb
   ```
   why journalctl?
   "journalctl" is used to view systemd logs to find why a service failed.
   When "systemctl status" shows a generic error, journalctl provides the exact reason (permissions, missing files, config issues), which is essential for troubleshooting.
   
   you can see the logs as "mariaDB database is not initialized, but the directory /var/lib/myaql is not empty, so initialization cannot be done"
   This means the database initialization is not done properly. MariaDB expects fresh and empty folder for its internal files.
   So, what we do is we create a mysql directory.
   
5. create the mysql directory
   ```
   mkdir mysql
   ```
   
6. Restart the mariadb service
   ```
   systemctl restart mariadb
   ```
   Still the error persists. Run the below command
   ```
   journalctl -xeu mariadb
   ```
   Now you can see "some permission issue with /var/lib/mysql/"
   
7. change the ownership of mysql directory to mysql
   ```
   chown mysql:mysql mysql
   ```
   why to change the ownership?
   MariaDB runs as the mysql system user, not as root.
   Its data directory (/var/lib/mysql) must be owned by the same user so the process can create, read, and modify database files.
   If the ownership is incorrect (for example, root:root), MariaDB is denied write access and fails to start.
   Setting ownership to mysql:mysql ensures the database can operate securely and correctly.
   
8. Now restart the mariabDB service
   ```
   systemctl restart mariadb
   ```
   
