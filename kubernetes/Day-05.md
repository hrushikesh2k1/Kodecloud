An application currently running on the Kubernetes cluster employs the nginx web server. The Nautilus application development team has introduced some recent changes that need deployment. They've crafted an image nginx:1.19 with the latest updates.


Execute a rolling update for this application, integrating the nginx:1.19 image. The deployment is named nginx-deployment.

Ensure all pods are operational post-update.

Approch:
1. Edit the nginx-deployment file, change the image to nginx:1.19
   ```
   kubectl edit deployment nginx-deployment
   ```
   <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0359352a-1667-441e-9325-ffc559193df5" />
2. You can see the rolling updates live
   ```
   kubectl get pods -w
   ```
   <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b4f4933f-5154-4113-be85-71d9f8a02718" />

   
