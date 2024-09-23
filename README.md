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
  This file manages the dial plan, which determines how incoming and outgoing calls are processed. Key components include:
  - **Contexts:** Define different routing paths for calls, such as internal calls, external calls, or IVR menus.
  - **Extensions:** Specify the actions taken when a particular number is dialed, including forwarding calls, playing prompts, or executing scripts.
  - **Applications:** Leverage Asterisk's built-in applications (like `Answer()`, `Dial()`, and `Playback()`) to create complex call flows and functionalities.

## 3. Queue Configuration
- **File:** `queues.conf`  
  This file defines the behavior of call queues within the call center environment. Key aspects include:
  - **Queue Definitions:** Set parameters like maximum wait time, number of callers allowed in the queue, and caller announcement options.
  - **Member Definitions:** Specify which agents or devices are included in the queue and their priorities for receiving calls.
  - **Strategy:** Define how calls are distributed among available agents (e.g., `ringall`, `leastrecent`, or `random`).

---

# Security Configuration

## 2.1. Firewall Configuration
- **File:** `iptables`  
  This file contains rules for configuring the firewall using `iptables`. Important considerations include:
  - **Allowing SIP Traffic:** Open ports typically used for SIP (UDP 5060) and RTP (typically UDP 10000-20000).
  - **Blocking Unauthorized Access:** Set up rules to block IPs that exhibit suspicious activity or fail authentication multiple times.

## 2.2. Fail2Ban Configuration
- **File:** `jail.local`  
  This configuration file is used to set up `fail2ban`, a security tool that scans log files and bans IP addresses that show malicious behavior. Key sections include:
  - **Jails:** Configure specific patterns to monitor (e.g., SIP authentication failures) and define actions to take (e.g., banning the offending IP).
  - **Ban Time:** Set durations for which an IP will be banned to prevent brute-force attacks.

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
  This file allows secure remote monitoring and control of Asterisk through the Asterisk Management Interface (AMI). Key configurations include:
  - **User Authentication:** Set up users with specific permissions to control which actions they can perform via the AMI.
  - **Event Notifications:** Enable event logging for call states, channel activity, and other important system events for monitoring purposes.

## 4.2. Call Detail Records
- **File:** `cdr.conf`  
  This file configures how call detail records (CDRs) are generated and stored. Key points include:
  - **CDR Storage:** Choose the storage method (e.g., CSV files, SQL database) and define the format of the records.
  - **Field Customization:** Customize the fields that will be logged for each call, such as start time, end time, call duration, and caller/callee IDs.

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
