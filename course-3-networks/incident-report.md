# Cybersecurity Incident Report: SYN Flood DoS Attack

## Part 1: Summary of the Problem Found in the Traffic Log

The Wireshark log shows legitimate users — such as 198.51.100.23, 198.51.100.14, and 198.51.100.5 — each sending one SYN request and successfully completing the handshake to load the sales page. However, IP address 203.0.113.0 sent 139 SYN requests without ever completing the handshake with a final ACK. This pattern identifies the incident as a **SYN flood Denial of Service (DoS) attack** — a single source overwhelming the server with incomplete connection requests.

Due to the SYN flood DoS attack, the server's connection resources were used up holding open all the half-finished connections from 203.0.113.0. This meant the server had nothing left to respond with when legitimate users sent their own SYN requests, causing the connection timeout error.

## Part 2: Analysis of the Data and Impact of the Incident

This attack affected the organization by preventing employees from accessing the website to do their day-to-day work, and also prevented external customers from browsing the website.

**Potential consequences:**
The potential consequences of this attack include lost employee productivity, lost sales during the outage, and damage to the organization's reputation, as customers may lose trust in the company's ability to keep its website secure and reliable.

**Recommended prevention (optional):**
To help prevent this type of attack in the future, the organization could implement rate limiting to cap the number of connection requests from a single source, and deploy a firewall or intrusion prevention system (IPS) with built-in SYN flood protection to automatically detect and drop malicious half-open connection patterns.
