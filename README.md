# Elastic-SIEM
<!--"" -->
<!--<h1>Elastic-SIEM<br/></h1>-->


## Overview
Welcome to my home lab setup! "Dashershomelab" I've created this environment to learn and understand various aspects of networking, monitoring, prevention, administration, and hardening techniques. It's been an incredible learning experience, and I'm excited to share my setup with you.
This Lab is a simple Elastic SIEM lab to monitor security events and provide alerts. <br>

## Goal

- Setup and configure elastic stack SIEM.

- Configure Elastic agents for log collections.

- Configure Elastic agents for forwarding data to the SIEM

- Monitoring security events and threat detection.

- Create alert rules for detecting specific events.

<img align="center" src="assets/images/dashboard1.png" /><br/>

## Prerequisites

- Virtual Box.

- Kali Linux VM.

- Elastic Account.

- Elastic agents and forwarders.<br>

## Tasks

1.	### Setup VirtualBox.
2.	### Install Kali Linux VM in VirtualBox.
3.	### Setup an account with Elastic cloud.
4.	### Configure the Elastic Agent on Kali Linux VM to forward the logs to the SIEM.
5.	### Generate security events in Kali Linux.
6.	### Create a Dashboard to visualise the security events.
7.	### Create Rules/Alerts for security events.<br>

## Task 1

### Install Kali Linux Vm on Virtual Box

- 	Download and install Virtual Box. https://www.virtualbox.org/wiki/Downloads.<br>

<img align="center" src="assets/images/vbox1.png" /><br/>

## Task 2

- 	Download and install Kali Linux Vm on VirtualBox. https://www.kali.org/get-kali/#kali-platforms

- 	Make sure you have internet access<br>

<img align="center" src="assets/images/kali1.png" /><br/>

## Task3

### Setup an account with Elastic cloud.

- 	Sign up for a free Elastic cloud account. It’s a 14-day trial.

- 	Create account and then log into it. Start you free trial by clicking on start your trial.

- 	Click on Create Deployment.

- 	You will enter the Homepage of Elastic cloud. Click on the hamburger menu to access integrations. 

- 	Once the configuration is completed. Click continue and you can find the deployment listed.<br>

<img align="center" src="assets/images/deploy.png.png" /><br/>
<img align="center" src="assets/images/elastic_home.png" /><br/>

## Task 4

### Configuring the Elastic Agent

- 	On the Elastic SIEM Instance click on the Hamburger meu and scroll down.<br>

- 	Click on the Add Integrations button.<br>

- 	Select Elastic Defend.<br>

- 	Select a name, description and pretty much use the default settings.<br>

- 	Click on save and then click the button Install Elastic Agent Button.<br>

- 	Once done a message to add agent to Host pops up. Click on the Button.<br>

- 	Follow the instructions and depending on the OS choose the add method, in this case I choose Linux, so I copy and paste the curl command in Kali terminal and execute it.<br>

- 	Once installation completes we can test using ”sudo systemctl status elastc-agent.service”.<br>

<img align="center" src="assets/images/add_integration.png" /><br>

<img align="center" src="assets/images/elastic_defend.png" /><br>

<img align="center" src="assets/images/elastic_defend_conf.png" /><br>

<img align="center" src="assets/images/add_agent_host.png" /><br>

<img align="center" src="assets/images/script_add.png" /><br>

<img align="center" src="assets/images/kali_term_install.png" /><br>

<img align="center" src="assets/images/kali_term_finish.png" /><br>

<img align="center" src="assets/images/kali_term_status.png" /><br>



## Task5

### Generate security events in Kali.
- 	We can use nmap commands to generate security events.

- 	Using nmap -P localhost will scan kali itself.

- 	Once some events are generated we can go to the SIEM and view the logs.

- 	To view logs click on the hamburger menu, select observability and then click on logs.

<img align="center" src="assets/images/kali_nmap.png" /><br/>

### To query a result in Elastic Instance

- 	To query a search in the logs we can filter them using preset keywords with required string.

- 	For example to query all logs related to Nmap scans , we can use Query: event. Action: “Nmap scan”

- 	Or for sudo events we can use: process.args: “sudo”

- 	Then click on search and it should present the filtered results.<br>


<img align="center" src="assets/images/query1.png" /><br/>

[Details of an event]([https://github.com/rajeevlraman/Elastic-SIEM/assets\images\detail1.png](https://github.com/rajeevlraman/Elastic-SIEM/blob/main/assets/images/detail1.png))


## Task 6

### Creating a Dashboard to visualize the results
-	In the Elastic Instance click on the Hambuger menu.

-	Select Analytics and click on Dashboards

-	Click on the create dashboard and  then click on create a new dashboard button.

-	Click on the create visualisation button to add new visualisation object to the dashboard.

-	In the type select Bar vertical stacked

-	And data use apm.

-	In the horizontal axis select the Timestamp.

-	In the vertical axis select the event counts.

-	Click on save and the visualisation should be displayed.<br>

<img align="center" src="assets/images/dashboard1.png" /><br/>


## Task 7

### Create Rules/Alerts for security events.

-	click on the hamburger menu and then under Security click on Alerts.

-	Click on manage rules.

-	click on the create new rule button.

-	Under the define rule section select custom query.

-	For example to detect Nmap events we can use “event.action: “nmap_scan”

-	Continue and click on about and give it a name and description.

-	Select the severity level and few other options. It can be left as it is.

-	In the Actions menu you can choose how the alert is to be notified. I have chosen email as most of the other options may require API keys, and other credentials.

-	Create and enable the rule.<br>




<img align="center" src="assets/images/rule-1.png" /><br/>


<img align="center" src="assets/images/rule-1.png" /><br/>


<img align="center" src="assets/images/rule-3.png" /><br/>
