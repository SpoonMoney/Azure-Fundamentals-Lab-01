-- Azure Fundamentals (AZ-900) Lab 01: 3-Tier Web Infrastructure --

Project Overview:
  This project serves as a practical application of Azure Compute, Networking, and Governance concepts. The goal was to deploy a functional Linux web server within a private Virtual Network, configure security boundaries, and verify public accessibility.

Architecture:
  Provider: Microsoft Azure
  
  Resource Group: RG-Lab-Fundamentals (Logical container for lifecycle management)
  
  Virtual Network (VNet): 10.0.0.0/16 address space
  
  Subnet: WebSubnet (10.0.1.0/24)
  
  Compute: Ubuntu Server 22.04 LTS (D2_v3)
  
  Security: Network Security Group (NSG) permitting inbound traffic on Port 80 (HTTP) and Port 22 (SSH).

Implementation Steps:
  1. Provisioning & Networking
  I initialized the environment by creating a Resource Group to ensure easy cleanup and cost tracking. I then deployed a Virtual Network and a dedicated Subnet to simulate a real-world enterprise environment where resources are isolated.
  
  2. VM Deployment & Security
  I deployed a Linux VM using SSH Public Key Authentication rather than passwords, adhering to industry security best practices. To allow web traffic, I manually configured a Network Security Group (NSG) rule to open Port 80.
  
  3. Web Server Configuration
  Once the VM was provisioned, I accessed the instance via Azure Cloud Shell and performed the following:
    
  - Updated the package manager (apt-get update)
  
  - Installed the Nginx web server
  
  - Verified the service status using systemctl
  
  4. Customization & Verification
  To verify the "plumbing" of the network was working, I injected a custom HTML index file into the web directory:

```bash
echo '<h1>Hello from Reeses Azure Lab!</h1>' | sudo tee /var/www/html/index.html

Verification: The server successfully resolved the custom message via the VM’s Public IP address.

Key AZ-900 Lessons Learned:
  IaaS vs. PaaS: Managing the OS and Nginx installation manually highlighted the responsibilities inherent in Infrastructure as a Service (IaaS).
  
  Network Security Groups: Learned that NSGs act as a distributed firewall at the subnet/NIC level, and that "Least Privilege" is vital for cloud security.
  
  Cost Management (FinOps): Practiced the "Delete Resource Group" procedure to ensure no lingering costs from managed disks or public IP addresses.

Proof of Work: 
<img width="2556" height="1379" alt="AZ-900_Lab01_Screenshot" src="https://github.com/user-attachments/assets/30e22ce1-bcf9-4163-b505-14303598562f" />

