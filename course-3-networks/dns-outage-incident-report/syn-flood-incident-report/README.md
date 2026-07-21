# SYN Flood DoS Attack — Network Traffic Analysis

## Overview
This repository documents a hands-on cybersecurity incident analysis exercise identifying and explaining a SYN flood Denial of Service (DoS) attack using a Wireshark TCP/HTTP traffic log.

This was completed as part of the **Google Cybersecurity Professional Certificate** (Course 3: Networks and Network Security).

## Scenario
As a security analyst for a travel agency, I received an automated alert about a problem with the company's web server, then received a connection timeout error trying to visit the site myself. Using a packet sniffer, I captured and analyzed traffic to and from the server to identify the cause.

## Files in this Repo
- [`incident-report.md`](./incident-report.md) — Full two-part incident report (attack analysis + organizational impact)
- [`wireshark-tcp-log.xlsx`](./wireshark-tcp-log.xlsx) — Captured TCP/HTTP traffic log used for the analysis

## Key Finding
Legitimate users (e.g. 198.51.100.23, 198.51.100.14, 198.51.100.5) each completed a normal 3-way TCP handshake (SYN → SYN-ACK → ACK) to successfully load the site. In contrast, IP address **203.0.113.0** sent **139 SYN requests** without ever completing a single handshake — exhausting the server's connection resources and causing it to stop responding to legitimate traffic. This is a classic **SYN flood DoS attack**.

## Skills Demonstrated
- Reading and interpreting Wireshark TCP/HTTP traffic logs
- Understanding the TCP three-way handshake and how it can be exploited
- Differentiating a DoS attack (single source) from a DDoS attack (distributed sources)
- Assessing business impact of a network security incident
- Recommending mitigation strategies (rate limiting, IPS/firewall SYN flood protection)
