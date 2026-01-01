The DevOps team established a new Git repository last week, which remains unused at present. However, the Nautilus application development team now requires a copy of this repository on the Storage Server in the Stratos DC. Follow the provided details to clone the repository:



The repository to be cloned is located at /opt/demo.git


Clone this Git repository to the /usr/src/kodekloudrepos directory. Perform this task using the natasha user, and ensure that no modifications are made to the repository or existing directories, such as changing permissions or making unauthorized alterations.


Approach:
1. ssh into storage server
2. Go to the kodecloudrepos directory.
   ```
   cd /usr/src/kodecloudrepos
   ```
3. Clone the repo
   ```
   git clone /opt/demo.git
   ```
   Since it(/opt/demo.git) was an absolute path, Git could locate the bare repository regardless of my working directory
