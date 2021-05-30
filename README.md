## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

!Topology_elk.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the install-elk.yml file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly distributed, in addition to restricting accesss to the network. A load balancer makes sure that each machine specified by the load balancer, receives a distributed amount of traffic. DDoS attacks are lessened and generally ensure that no single machine is overwhelmed with traffic. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the system and system logs.
Filebeat is used to monitor log files and collect log events, then forwards them to their elasticsearch or logstash for indexing. 
Your metricbeat takes the metrics and statistics that it collects and sends them to elasticsearch or logstash. This will help monitor servers by collecting metric from the services running on the server. 

| Jumpbox    | gateway    | 10.0.0.4  |   | Linux |
|------------|------------|-----------|---|-------|
| Web-1      | web server | 10.0.0.11 |   | Linux |
| Web-2      | web server | 10.0.0.12 |   | Linux |
| Web-3      | web server | 10.0.0.13 |   | Linux |
| Elk-Server | Log server | 10.1.0.4  |   | Linux |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the load balancer machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
Only my personal laptop

Machines within the network can only be accessed by SSH via
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_

A summary of the access policies in place can be found in the table below.

| Jumpbox    | gateway    | 10.0.0.4  |
|------------|------------|-----------|
| Web-1      | web server | 10.0.0.11 |
| Web-2      | web server | 10.0.0.12 |
| Web-3      | web server | 10.0.0.13 |
| Elk-Server | Log server | 10.1.0.4  | 

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because
the configuration can be automated and run in the yml file. By doing this you can use one machine, or multiple machines. The process can be done induvidually by logging in to each machine if they have ssh access. 

The playbook implements the following tasks:
- it installs docker, via the install-elk.yml file
- it increases the virtual memory allocation of the Elk-server
- it downloads and launches the docker container The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- The IP addresses of the machines you I am monitoring include; 10.0.0.11, 10.0.0.12, 10.0.0.13

We have installed the following Beats on these machines:
- I installed FileBeat and MetricBeat onto the Elk-server These Beats (services) allow us to collects information from each machine, including system usage, data usage, and system metrics such as uptime and connections.

These Beats allow us to collect the following information from each machine:
- FileBeat collects and forwards log data such as log files and log events, and forwards them to either Elasticsearch or Logstash for indexing.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to the /etc/ansible/ folder on the ansible container machine.
- Update the install-elk.yml file to include the machines that you want to have the playbook action - in this case, the machine is Elk-server.
- Run the playbook, and navigate to your Elk-server to check that the installation worked as expected.

- Copy the install-elk.yml playbook file to the /etc/ansible/ folder on your ansible container machine.\
- On the docker container VM, navigate to /etc/ansible/ and update the hosts file with specific IPs of each VM.
- To check that the Elk server is running, from the docker container, run the following: ssh azadmin@10.1.0.4 (to connect to the Elk-server)
