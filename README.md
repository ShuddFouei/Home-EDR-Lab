# Home-EDR-Lab
Utilizing Wazuh to monitor traffic on all home endpoints, providing a look into the typical home traffic patterns, alerting for dangerous activity, and opening the doors to mock SOC activity


## Brief Wazuh Introduction
- Wazuh is an incredible Open-Source security platform consisting of an Indexer based off Elasticsearch, a server, and a dashboard that can provide a clean UI similar to what SOC analyst see day-to-day. You can set up rules and experiment within these nodes, something I will be documenting here.
- IMPORTANT NOTE : Many of my fellow students have only one device, typically running either Windows or Mac. The indexer, server, and dashboard MUST be installed on one of the supported linux distribtutions. As such, you will need to utilize a VM to have a server to host these nodes on.
    - I will post an update here if WSL functions as an alternative way to host.


# DEVICE LIST:
- ISP Provided Router
- Laptop 1 - Ubuntu - Wazuh Server/Indexer/Dashboard node location
- Laptop 2 - Windows 11 instance hosting game server
- Desktop - Windows 10 - Daily Driver with the most vulnerabilities

# Wazuh Setup
  - Follow documentation at documentation.wazuh.com/current/installation-guide
  - IF UTILIZING ONE SERVER FOR MONITORING - Install Indexer, Server, then Dashboard

 ### Note: In this scenario, my logging and monitoring device is a laptop also used for school work; as such it leaves the network. To allow the Server and Indexer to be a consistent connection:
 - Go into router (typical home networks can be accessed via web browser - input your IP with 1 for the final quarter: ex. 192.168.1.1)
 - Configure DHCP/IP Address distribution and set your server hosting device to STATIC
 - Optionally: Set up DNS so a hostname will always route to a set device with the correct MAC address (beware MAC spoofing, however in a home lab environment this is most likely negligible)

# Timeline
## 10/1/2025 - Agent and Server Setup
- Router DHCP configured to provide static IP to Wazuh Server device
- Fresh Ubuntu Desktop installation onto Laptop 1: Wazuh installation scripts will provide dependencies such as Curl
- Follow Indexer, Server, and Dashboard documentation
- Connected to Wazuh Server IP via separate device, Desktop, to ensure connectivity over home network
- Perforce Puppet master installed onto Laptop 1: Experimenting with automated agent rollout
- MSI agent installer used for both Laptop 2 and Desktop. Data now all congregating within Laptop 1

### Result / Lessons Learned
- By Adding an agent to my daily driver desktop, I immediately discovered 38 High Severity vulnerabilities, with the CVE for each listed as well as the problem application. As such, this lab has already shown me how many vulnerabilities I had hidden and lying around
- 
## 10/2/2025 - Attack Simulation & Interface Familiarity
