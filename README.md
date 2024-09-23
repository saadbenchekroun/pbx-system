# Asterisk Configuration Files

Asterisk is a powerful open-source framework for building communications applications. The following configuration files are essential for setting up and managing various functionalities of your Asterisk system.

## 1. SIP Configuration
- **File:** `pjsip.conf`  
This configuration sets up a SIP application that can connect to a SIP service provider (trunk) and manage calls for two call center agents.
The application listens for incoming calls on all network interfaces and uses UDP for communication.
It authenticates with the trunk provider using a username and password.
Incoming calls are routed to specific contexts based on their origin (external or internal).
Each agent has a dedicated endpoint for handling calls and is authenticated with the application using separate credentials.

## 2. Extensions Configuration
- **File:** `extensions.conf`  
This dialplan provides a basic framework for handling incoming calls, routing them to external or internal extensions, and offering an IVR menu for navigation.

## 3. Queue Configuration
- **File:** `queues.conf`  
The "sales" and "support" queues in the Asterisk dialplan are configured with specific parameters to manage call distribution, wait times, and announcements. The "sales" queue uses a ring-all strategy, while the "support" queue uses a round-robin strategy. Both queues have a timeout of 15 seconds, a retry limit of 5, and a service level target of 30%. The "please-hold" message is announced periodically to callers waiting in both queues.
---

# Security Configuration

## 2.1. Firewall Configuration
- **File:** `iptables`  
This file defines a firewall configuration for an Asterisk system, allowing specific types of traffic (SIP, RTP, SSH, and established connections) while blocking all other incoming traffic. This helps to protect the Asterisk system from unauthorized access and potential security threats.

## 2.2. Fail2Ban Configuration
- **File:** `jail.local`  
The jail.local file configures the Asterisk jail to enable security measures, specify network settings, and define the system's logging and authentication behavior. By isolating different parts of the Asterisk system and implementing security measures like retry limits and bans, the jail helps to protect the PBX from unauthorized access and potential vulnerabilities.

It configures the Asterisk jail settings, enabling the jail and specifying its parameters. The jail is activated, listening on ports 5060 and 5061 using the UDP protocol. The filter is set to "asterisk," and log messages are stored in the "/var/log/asterisk/messages" directory. To protect against brute-force attacks, the jail is configured with a maximum of 5 retry attempts and a ban time of 3600 seconds (1 hour) for failed authentication attempts. This helps prevent unauthorized access to the Asterisk system.

---

# Call Recording Configuration
- **File:** `extensions.conf`  
  To enable automatic call recording, add specific applications to your dial plan. Key actions might include:
  - **Recording Calls:** Use the `MixMonitor()` application within relevant extensions to start recording when a call is answered.
  - **Storage Path:** Specify where the recorded files will be stored and how they are named for easy retrieval.

---

# Monitoring Configuration

## 4.1. Asterisk Manager Interface
- **File:** `manager.conf`  
The manager.conf file configures the Asterisk Manager interface, which allows external applications to interact with and control the Asterisk PBX. The enabled parameter is set to "yes" to enable the Manager interface. The port is set to 5038, which is the default port for the Manager interface. The bindaddr is set to "0.0.0.0" to allow connections from any IP address. The [admin] section defines the credentials for the "admin" user, with a password of "adminpassword" and full read and write permissions. This allows the "admin" user to perform all operations on the Asterisk PBX through the Manager interface.

## 4.2. Call Detail Records
- **File:** `cdr.conf`  
This file enables Call Detail Recording (CDR) in Asterisk, logging both answered and unanswered calls. The CSV format is used for CDR logging, with GMT time disabled and unique ID and user field information included.

---

# WebRTC Support Configuration

## 5.1. WebRTC in pjsip.conf
- **Enable WebRTC endpoints:** This involves configuring the transport layer and ensuring the necessary codecs (like Opus) are available. Key configurations include:
  - **Transport Definition:** Specify the transport settings for WebRTC, ensuring that WebSocket connections are enabled.
  - **Security:** Implement TLS/SSL certificates for secure communications over the WebRTC endpoints.

---

# CRM and API Integration

## 6.1. Asterisk REST Interface
- **File:** `http.conf`  
  This file configures the Asterisk REST Interface (ARI), allowing for advanced API-driven call handling. Key configurations include:
  - **Enabling ARI:** Activate the ARI module and define the base URI for the API.
  - **Authentication:** Set up secure authentication methods for accessing the API, including user credentials and permissions.
  - **Integration with CRM:** Provide endpoints for integrating with external CRM systems, enabling features like automated call logging and customer information retrieval.

---
