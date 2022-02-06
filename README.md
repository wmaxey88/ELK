- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly redundant, in addition to restricting access to the network.
- Load balancers protect against DOS attacks, by directing network traffic.  The advantage of a jump box is it gives you a secure machine to connect to before connecting to another environment whether it is trusted or not.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system metrics.
- _Filebeat monitors logs and file locations that an admin specifies, and forwards the collected data to Logstash or Elasticsearch.  
- _Metricbeat records metrics and stats from your servers, and it forwards this data to Logstash or Elasticsearch, as well. 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function     | IP Address | Operating System |
|----------|--------------|------------|------------------|
| Jump Box | Gateway      | 10.0.0.1   | Linux            |
| Web-1    | DVWA Machine | 10.0.2.8   | Linux            |
| Web-2    | DVWA Machine | 10.0.2.9   | Linux            |
| P1-Elk   | DVWA Machine | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _My local IP Address 

Machines within the network can only be accessed by SSH via their NIC Private IP's.
- _My Ansible container within my jump box machine has access to the ELK VM.  IP is that of my jump box, 10.0.0.1.    

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | 24.158.107.56        |
| Web-1    | No                  | 10.0.0.1             |
| Web-2    | No                  | 10.0.0.1             |
| P1-Elk   | No                  | 10.0.0.1             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _It allows you to make slight edits to make your config files work for other files.  i.e., filebeat config file being editable to work for a metricbeat config file. 

The playbook implements the following tasks:
- _- Install Docker
- _- Install Python3-pip
- _- Install Docker Python module 
- _- Increase the memory 
- _- Download and the ELK container and launch the service upon boot 


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Images/Elk_Container_Screenshot.png]

### Target Machines & Beats
This ELK server is configured to monitor the following machines: Web-1 and Web-2
- _- IP's 10.0.2.8 and 10.0.2.9, repectively 

We have installed the following Beats on these machines:
- _filebeat and metricbeat 

These Beats allow us to collect the following information from each machine:
- _Filebeat colleccts log data from Web-1, Web-2, and P1-Elk machines.  Metricbeat collects metric data from Web-1 and Web-2 containers.  I would expect to see SSH login attempts/failed attempts within filebeat Syslog dashboard.  

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- _- Copy the install-elk.yml file to ansible directory.
- _- Update the install-elk.yml file to include all the necessary tasks.  
- _- Run the playbook, and navigate to the ELK server to check that the installation worked as expected.

- _Which file is the playbook? Where do you copy it? install-elk.yml and you copy it to the ansible folder. 
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? You have to update the hosts file to run a specific machine.  You have to ensure the correct group name is referenced.  
- _Which URL do you navigate to in order to check that the ELK server is running? <My VM Public IP>:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc. 
Run = ansible-playbook <name-of-playbook>.yml 
Download = local.host <creater of image/image> 
