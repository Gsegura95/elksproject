## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

<img width="1037" alt="Screen Shot 2021-07-12 at 10 25 56 PM" src="https://user-images.githubusercontent.com/87348052/128952468-92d2dd0c-e675-4fa4-a184-02f071530471.png">


These are the files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire pictured above. Alternatively, select portions of the ansible file may be used to install only certain pieces of it, such as Filebeat.

  -ELK-Stack-Project/Ansible/
  
This document contains the following details:
Description of the Topologu
Access Policies
ELK Configuration
Beats in Use
Machines Being Monitored
How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available for customers, in addition to restricting attacks to the network. If a server goes down, or needs to be updated, services will still continue.
-The advantage of using a jump box is that only the jump box can access the Virutal network via ssh. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
- Filebeat monitors the log files or locations specified, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
- Metricbeat is an extremely easy-to-use, efficient and reliable metric shipper for monitoring your system and the processes running on it. 
The configuration details of each machine may be found below.

| Name       | Function   | IP Address                              | Operating System |
|------------|------------|-----------------------------------------|------------------|
| JumpBoxPro   | Gateway    | Public: 40.86.73.173 Private: 10.0.0.8  | Linux            |
| Web1VM      | Server     | Public: N/A          Private: 10.0.0.9  | Linux            |
| Web2VM      | Server     | Public: N/A          Private: 10.0.0.10 | Linux            |
| ELK-Server | Monitoring | Public: 52.137.81.98 Private: 10.2.0.4  | Linux            |

### Access Policies

The machines on the internal network are not shown to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

5061 Kibana port

Machines within the network can only be accessed by the Jump-Box-Provisioner.

A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible  | Allowed IP Address |
|------------|----------------------|--------------------|
| Jump Box   | yes                  | 73.73.60.19        |
| Web-1      | no                   | 10.0.0.8           |
| Web-2      | no                   | 10.0.0.8           |
| ELK-Server | no                   | 10.0.0.8           |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it was easy to do and prevented any easily overloook vulnerablities. 

The playbook implements the following tasks:
- Install docker.io
- Install python3-pip
- Install docker via pip
- Increase vitual memory  
- Use more memory 
- Download and launch a docker elk container - starts docker and establishes the ports being used.  

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
<img width="819" alt="Screen Shot 2021-08-10 at 9 18 05 PM" src="https://user-images.githubusercontent.com/87348052/128955191-578e7de6-39b9-4418-a6e3-7a8be4094539.png">





### Target Machines & Beats
This ELK server is configured to monitor the following machines:
| Name  | IP Address  |
|-------|-------------|
| Web-1 | 10.0.0.9    |
| Web-2 | 10.0.0.10   |

I have installed the following Beats on these machines:
Filebeat
Metricbeat 

| Name       | IP Address   |
|------------|--------------|
| Web-1      | 10.0.0.9     |
| Web-2      | 10.0.0.10    |
| ELK-Server | 52.137.81.98 |

These Beats allow us to collect the following information from each machine:
-filebeat collects log data and shows them in the monitoring clusters. 
-metricbeat collects metrics and statistics and shows them in the output specified, for example Elasticsearch or Logstash. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
Copy the playbook (.yml) file to /etc/Ansible/ directory.
Update the host file to include webserver and ELK. 
Run the playbook, and navigate to Kibana to check that the installation worked as expected. 
   ( http://[your.VM.IP]:5601/app/kibana )

