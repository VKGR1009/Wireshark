# Wireshark
Task 5 - Network Traffic Capture and Analysis (Wireshark)

Objective  
Capture and analyze network traffic generated while browsing websites using Wireshark on Linux. Identify DNS requests, TCP connections, and HTTPS handshakes.

Steps Performed

1. Install Wireshark  
sudo apt update  
sudo apt install wireshark -y  
Allowed non-root users to capture packets.

2. Start Wireshark  
wireshark &  
Selected the active network interface (eth0) for packet capture.

3. Generate Network Traffic  
- Opened a browser in the VM.  
- Visited:  
  - https://google.com (HTTPS traffic)  
  - http://example.com (HTTP traffic)  
- Let traffic run for ~1 minute.

4. Save Capture  
Stopped the capture and saved as capture.pcapng.

Analysis

DNS Requests  
Filter Used: dns  
- Observed DNS queries for google.com and example.com.  
- Response packets contained resolved IP addresses.

TCP Connection (3-Way Handshake)  
Filter Used: tcp  
- Found SYN → SYN/ACK → ACK sequence between client and server.  
- Confirms successful TCP connection establishment.

HTTPS/TLS Handshake  
Filter Used: tls  
- Detected Client Hello and Server Hello messages.  
- Server presented SSL certificate for secure session.

HTTP Requests  
Filter Used: http  
- Captured GET / requests to example.com.  
- Response headers and HTML content visible in plain text.

Key Findings  
- DNS successfully resolved domain names to IP addresses.  
- TCP connections were established before data transfer.  
- HTTPS traffic was encrypted after TLS handshake.  
- HTTP traffic was visible in plain text, demonstrating lack of encryption.

Files in Repository  
- capture.pcapng → Raw network capture file.  
- README.md → Steps, filters, and analysis.
