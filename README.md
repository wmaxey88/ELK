# ELK
Phase I
Deployed ELK Stack during boot camp. 
Created new VNet within AZURE.
Peered my existing VNet to my new VNet.
Created new VM within the new VNet. 
Allowed SSH access via same public key as previous VM's. 
Built .yml playbook to download docker, container, and auto-start container on boot. 
Connected to my Kibana dashboard using my new VM's public IP through port 5061 that I opened up in my security group inbound rules.

Phase II 
Had to troubleshoot why my IP could not connect through port 5601. 
Discovered that the memory command in the playbook was not working correctly, ran a new play in the play book and connected. 
Downloaded the filebeat config file and edited per specifications. 
Edited filebeat playbook to download Web-1 and Web-2 VM log data to ELK VM.
Edited metricbeat playbook to download Web-1 and Web-2 container data to ELK VM. 
Project diagram overview can be found here: https://drive.google.com/file/d/1nwnS_CoD_z_cYAf9C1XA4joKzYAKbk0e/view?usp=sharing
