# 🕵️ PCAP File Analysis

This project involves the analysis of network traffic captured in a `.pcap` file using tools like **Wireshark**, **tshark**, and Python-based parsers (e.g., `scapy`). The goal is to identify key insights from the traffic — such as protocols used, anomalies, potential security concerns, or performance metrics.

---

## 📁 File Details

- **File Name:** `yourfile.pcap`
- **Capture Date:** `YYYY-MM-DD`
- **Capture Tool:** Wireshark / tcpdump
- **Environment:** (e.g., Home network / CTF environment / Lab setup)

---

## 🔍 Objectives

- Inspect network communication patterns
- Identify suspicious activities or attack signatures
- Extract useful metadata (e.g., visited domains, IPs, file transfers)
- Optionally recreate sessions or files transferred

---

## 🛠️ Tools Used

- [Wireshark](https://www.wireshark.org/)
- `tshark` (CLI Wireshark)
- `scapy` (Python packet manipulation)
- `pyshark` (Wireshark wrapper for Python)

---

## 📊 Key Insights (examples)

- **Total Packets:** 12,345
- **Protocols Involved:** TCP, UDP, HTTP, DNS, ARP
- **Suspicious IPs:** 192.168.1.105 (repeated connections to unknown domain)
- **Anomalies:** Unusually high DNS queries, malformed TCP packets

---

## 📂 Output Files

- `parsed_summary.csv`: CSV summary of packet metadata
- `http_extract.txt`: Extracted HTTP requests
- `alerts.txt`: Flagged potential issues

---

## 🧪 How to Analyze

1. Open the `.pcap` file in Wireshark:
   ```bash
   wireshark yourfile.pcap
Or parse via CLI:

tshark -r yourfile.pcap -T fields -e frame.time -e ip.src -e ip.dst -e _ws.col.Protocol

Optional Python usage:

from scapy.all import rdpcap
packets = rdpcap("yourfile.pcap")
for pkt in packets:
    pkt.summary()

 📎 Notes
    Ensure sensitive IPs/domains are anonymized before sharing.
    Use filters in Wireshark to focus on specific conversations:
        http
        ip.addr == 192.168.1.1
        tcp.port == 80
