The Nautilus DevOps team is strategically planning the migration of a portion of their infrastructure to the Azure cloud. Acknowledging the magnitude of this endeavor, they have chosen to tackle the migration incrementally rather than as a single, massive transition. Their approach involves creating Virtual Networks (VNets) as the initial step, as they will be provisioning various services under different VNets.

Create a Virtual Network (VNet) named xfusion-vnet in the East US region with 192.168.0.0/24 IPv4 CIDR.


Approach:
1. Go to portal.azure.com
2. Search for Virtual Network.
3. Name the vnet "xfusion-vnet" and set the location to "East US".
   <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/bf8bc69e-fd66-4b37-ba0c-8f6e160cb30c" />
4. Set the ip address range 192.168.0.0/24
   <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b464a064-6f7d-4c6c-8646-c639039488fd" />
5. leave rest as it is. Click on review + create
