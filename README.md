# Asterisk Configuration Files

## 1. SIP Configuration
- **File:** `pjsip.conf`  
  This file handles the SIP endpoint configurations for agents and trunks.

## 2. Extensions Configuration
- **File:** `extensions.conf`  
  This file manages call routing logic, including IVR, queues, and dial plans.

## 3. Queue Configuration
- **File:** `queues.conf`  
  This file defines the behavior of the call center queues for routing calls to available agents.

---

# Security Configuration

## 2.1. Firewall Configuration
- **File:** `iptables`  
  Configure the firewall settings to protect the PBX system.

## 2.2. Fail2Ban Configuration
- **File:** `jail.local`  
  Protect the PBX system against unauthorized SIP login attempts.

---

# Call Recording Configuration
- **File:** `extensions.conf`  
  Enable automatic call recording for certain call flows.

---

# Monitoring Configuration

## 4.1. Asterisk Manager Interface
- **File:** `manager.conf`  
  Allow secure remote monitoring and control of calls via the Asterisk Management Interface (AMI).

## 4.2. Call Detail Records
- **File:** `cdr.conf`  
  Store call data for later reporting and analytics.

---

# WebRTC Support Configuration

## 5.1. WebRTC in pjsip.conf
- Enable WebRTC endpoints for browser-based calling.

---

# CRM and API Integration

## 6.1. Asterisk REST Interface
- **File:** `http.conf`  
  Enable ARI for advanced API-driven call handling and integration with external CRM systems.
