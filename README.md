# Deploy and monitor a cloud-based honeypot for Amazoomies Incorporated

This project involved the end-to-end design, deployment, and monitoring of a cloud-based honeypot system for "Amazoomies Incorporated," a small fictional business with limited security resources. The objective was to debunk the management's false sense of security by demonstrating real-world threat activity and gathering intelligence to harden their production network. Using the T-Pot suite on a Google Cloud virtual machine, the project successfully captured over 3 million attacks, providing critical data on attacker tactics, techniques, and procedures (TTPs).

Amazoomies faced significant risk due to budget constraints and a lack of technical expertise. Senior management operated under the assumption that their small size made them an unlikely target for cyberattacks. The organization needed a cost-effective, high-impact solution to visualize the threat landscape and identify vulnerabilities without risking their actual production environment.

**Infrastructure Design:** 

Deployed a virtual machine on Google Cloud Platform (GCP), selecting an e2-standard-4 instance with 16 GB of RAM and a 250 GB SSD to handle high-volume log ingestion.

![alt text](<Images/GoogleCloud_VM_Setup.png>)

Honeypot Suite: Installed T-Pot, a multi-honeypot platform, on Ubuntu 24.04 LTS to mimic various production services (SSH, HTTP, FTP).

![alt text](<Images/GoogleCloud_VM_Setup2.png>)

**Security Configuration:**

Configured VPC Firewall Rules to allow ingress traffic on ports 1–64,000 for attackers while strictly isolating administrative ports (SSH/Web Admin) to a specific IP whitelist.

![alt text](<Images/VPC_Firewall_Rules.png>)

Implemented daily snapshot backups to ensure network resilience and minimize downtime in case of critical failure.

**Volume of Attacks:** The system recorded over 3 million total attacks.

**Top Targeted Services:**

Honeytrap: 1 million hits.

Sentrypeer (VoIP/SIP): 853,000 hits.

Cowrie (SSH/Telnet): 807,000 hits.

![alt text](<Images/elastic.png>)

**Geographic Trends:** The most persistent threats originated from the United States, Romania, France, and Brazil.

![alt text](<Images/attackmap.png>)

**Credential Analysis:** Attackers frequently utilized brute-force tactics with common credentials such as "root," "admin," and "123456".

![alt text](<Images/elastic2.png>)

**Vulnerabilities Exploited:** Suricata identified specific CVE exploitation attempts, including:

CVE-2018-13379: FortiOS Directory Traversal.

CVE-2006-2369: VNC Server Information Leak.

**Strategic Recommendations & Outcomes**

Based on the intelligence gathered, I delivered a hardened security strategy to Amazoomies management, which included-

**Cultural Shift:** The data successfully shifted management's perspective, proving that small businesses are active targets for automated attacks.

**Network Hardening:** Recommended blocking traffic from non-operational geographic regions and patching identified CVEs immediately.

**Continuous Improvement:** Established a schedule for quarterly penetration testing and regular honeypot redeployments to stay ahead of evolving threats.
