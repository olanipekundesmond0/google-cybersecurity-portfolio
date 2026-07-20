# Cybersecurity Incident Report: Network Traffic Analysis

## Part 1: Summary of the Problem Found in the DNS and ICMP Traffic Log

**The UDP protocol reveals that:**
At 13:24 PM, my computer (192.51.100.15) sent a request to the domain server (203.0.113.2) asking for the IP address of yummyrecipesforme.com, using query ID 35084.

**The ICMP echo reply returned the error message:**
The domain server (203.0.113.2) replied to my computer (192.51.100.15) with an ICMP error message saying the domain (port 53) was unreachable.

**The port noted in the error message is used for:**
Port 53, which is used for DNS (domain name resolution) service.

**The most likely issue is:**
The DNS service isn't running on my client's domain server, which is why I keep getting the "port 53 unreachable" response.

---

## Part 2: Analysis of the Data and Cause of the Incident

**Time incident occurred:**
13:24 PM

**How the IT team became aware of the incident:**
The IT team became aware of this incident due to multiple users reporting that they were unable to access the website.

**Actions taken by the IT department to investigate the incident:**
The IT department took action by first attempting to access the website themselves, which reproduced the same error. They then ran tcpdump to capture network traffic and analyze the response directly from the domain server.

**Key findings of the investigation:**
Key findings from the investigation include a repeated ICMP error message from the domain server (203.0.113.2) stating "udp port 53 unreachable." This error was returned consistently across multiple attempts, indicating the issue was not a one-time glitch.

**Likely cause of the incident:**
A likely cause of this incident is that the DNS service on the domain server (203.0.113.2) is not running, which is preventing DNS lookups for the client's website.
