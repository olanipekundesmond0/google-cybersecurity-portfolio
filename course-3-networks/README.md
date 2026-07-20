# DNS Outage Incident Report, Network Traffic Analysis

## Overview
This repository documents a hands-on cybersecurity incident analysis exercise. It walks through diagnosing a website outage using `tcpdump` packet capture data, tracing the failure back to a DNS service issue on the client's domain server.

This was completed as part of the **Google Cybersecurity Professional Certificate** (Course 3: Networks and Network Security).

## Scenario
Multiple customers reported being unable to access a client's website, `www.yummyrecipesforme.com`, and were seeing a **"destination port unreachable"** error. As the analyst investigating the issue, I reproduced the error myself, then used `tcpdump` to capture and analyze the network traffic behind the failure.

## Files in this Repo
- [`incident-report.md`](./incident-report.md) — Full two-part incident report (traffic analysis + incident summary)
- [`tcpdump-log.txt`](./tcpdump-log.txt) — Raw captured packet data used for the analysis

## Key Finding
Every DNS lookup attempt from the client machine (`192.51.100.15`) to the DNS server (`203.0.113.2`) on **port 53** returned an ICMP `udp port 53 unreachable` error, consistently, across three separate attempts. This points to the DNS service itself being down on the domain server, rather than a network-level block, since the server was reachable and actively responding with an error (not silently dropping traffic).

## Skills Demonstrated
- Reading and interpreting `tcpdump` packet capture logs
- Understanding the DNS resolution process (UDP, port 53)
- Differentiating ICMP error responses from firewall-blocked traffic
- Writing a structured cybersecurity incident report
