## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Images/Red-Team-Network.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

- (YML-Playbooks/DVWA-Playbook.yml) -used to install DVWA servers
- (YML-Playbooks/Elk-Playbook.yml) -used to install ELK Server
  - (YML-Playbooks/filebeat-playbook.yml) -used to install and configure Filebeat on ELK Server and DVWA Servers 
  - (YML-Playbooks/metricbeat-playbook.yml) -used to install and configure Metricbeat on ELK Server and DVWA Server.

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- What aspect of security do load balancers protect? 
  - The purpose of Load Balancing is to distribute network traffic. There they are protect availability. This can aid organizations against distributed denial-of-service (DDOS) attacks.  
- What is the advantage of a jump box?
  - A jump box is similar to a gateway router. It is placed between machines in a network that are not exposed to the public internet,  and the traffic trying to gain access from the internet. As oppose to monitoring all interactions with all system. Focus can be placed on the interactions between traffic from the internet  and the jump box.  

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
- What does Filebeat watch for?
Installed as an agent on your servers, Filebeat monitors the log files or locations that are specified, collects the log events, and forwards them either to Elasticsearch or Logstash for indexing.
- What does Metricbeat record?
It periodically collect metrics from the operating system and from services running on the server. The information collected is sent to the output that you specify, such as Elasticsearch or Logstash.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name       | Publicly Accessible    | Allowed IP Address                            |
|------------|------------------------|-----------------------------------------------|
| Jump-Box   | No                     | Personal IP Address                           |
| Web-1      | Yes Thru Load Balancer | 104.209.32.221 LB <br>10.0.0.4 - JumpBox      |
| Web-2      | Yes Thru Load Balancer | 104.209.32.221 LB<br>10.0.0.4 JumpBox         |
| ELK-Server | No                     | 10.0.0.4 - JumpBox  <br>Personal IP/Port 5601 |
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Personal IP Address

Machines within the network can only be accessed by SSH.
- The ELK-Server from the Jump Box
- The DVWA's from the Jumpbox 

A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible    | Allowed IP Address                            |
|------------|------------------------|-----------------------------------------------|
| Jump-Box   | No                     | Personal IP Address                           |
| Web-1      | Yes Thru Load Balancer | 104.209.32.221 LB <br>10.0.0.4 - JumpBox      |
| Web-2      | Yes Thru Load Balancer | 104.209.32.221 LB<br>10.0.0.4 JumpBox         |
| ELK-Server | No                     | 10.0.0.4 - JumpBox  <br>Personal IP/Port 5601 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- The main advantage of automating configuration with Ansible is easy deployment. It enables an individual to think twice and do once. Using the ansible and specifying the location of the devices. A playbook can be executed to install on all servers. This ensures that less time is spent on deployment and possible redeplyoment in the future. _

The playbook implements the following tasks:
- Install Docker.io
- Install Python pip3
- Increase Virtual Memory 
- Download and Launch ELK Docker Container
- Sets Published Ports 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

**Note**: The following image link needs to be updated. Replace `docker_ps_output.png` with the name of your screenshot image file.  


(Images/docker-ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 10.0.0.5
- Web-2 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat watches for log files/locations and collect log events. (Filebeat: Lightweight Log Analysis & Elasticsearch)
- Metricbeat records metrics and statistical data from the operating system and from services running on the server (Metricbeat: Lightweight Shipper for Metrics)


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

### References

Filebeat: Lightweight Log Analysis & Elasticsearch. (n.d.). Retrieved August 22, 2020, from https://www.elastic.co/beats/filebeat Metricbeat: Lightweight Shipper for Metrics. (n.d.). Retrieved August 22, 2020, from https://www.elastic.co/beats/metricbeat
