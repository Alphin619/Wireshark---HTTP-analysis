## 🦈Wireshark – HTTP Analysis

## Objective
The objective of this project is to analyze **HTTP (Hypertext Transfer Protocol)** traffic using Wireshark.  
This includes:
- Understanding HTTP request/response headers  
- Viewing browser-server communication  
- Detecting potential HTTP-based attacks, anomalies, or data leaks  

---

## 📥 Sample PCAP File
**[Download Sample PCAP](https://github.com/0xrajneesh/90-Days-SOC-Challenge-Beginner/raw/refs/heads/main/Protocol_Analysis_pcap.pcapng)**  
Open the file in Wireshark to begin HTTP analysis.

---

## What is HTTP?
HTTP is an **application-layer protocol** used for communication between web clients (browsers) and servers.  
It commonly runs over **TCP port 80** and is **not encrypted**, making it readable inside Wireshark.

---

## HTTP Packet Structure & Key Fields

| **Field Name**      | **Description**                                        |
|---------------------|--------------------------------------------------------|
| **Request Method**  | GET, POST, HEAD, PUT, DELETE, etc.                     |
| **Host**            | The domain being accessed                              |
| **User-Agent**      | Browser or client making the request                   |
| **URI**             | Resource path requested from the server                |
| **Status Code**     | Server's response (200 OK, 404 Not Found, etc.)        |
| **Content-Type**    | MIME type of returned content (e.g., text/html)        |
| **Cookie**          | Session, tracking, or authentication data              |

---

## Useful Wireshark HTTP Filters

1) Show all HTTP traffic - [http]
<img width="960" height="483" alt="Screenshot 2025-12-09 064132" src="https://github.com/user-attachments/assets/f4c87470-54cf-4ba5-af2f-435c4e466ca3" />

2️) Show traffic on port 80 (default HTTP port) - [tcp.port == 80]
<img width="956" height="461" alt="Screenshot 2025-12-09 064239" src="https://github.com/user-attachments/assets/36f4bf7a-5215-4fae-9e04-482fed9643d6" />

3️) Show all GET requests - [http.request.method == "GET"]
<img width="958" height="479" alt="Screenshot 2025-12-09 064306" src="https://github.com/user-attachments/assets/1997cfeb-ed5c-41a8-b632-a9c76ce4958f" />

4️) View requested URIs - [http.request.uri]
<img width="960" height="481" alt="Screenshot 2025-12-09 064353" src="https://github.com/user-attachments/assets/935746a4-f4f7-4ddf-b865-fc8b898a9f8c" />

5️) Show cookies set by the server - [http.set_cookie]
<img width="960" height="479" alt="Screenshot 2025-12-09 064415" src="https://github.com/user-attachments/assets/b32e7877-6090-4088-a5f7-25a383bcc58f" />

---

## Why HTTP Analysis Matters in Security & SOC Work
Analyzing HTTP traffic helps identify:

✔ Sensitive Data Exposure
Since HTTP is unencrypted, credentials or session tokens may leak via:

Query strings

Headers

Cookies

✔ Malware Beaconing
Malware often uses HTTP to:

Check in with Command & Control servers

Download payloads

Exfiltrate small amounts of data

✔ Suspicious File Downloads
Payloads such as .exe, .zip, .js, or encoded files can indicate infection.

✔ Unauthorized Access Attempts
Look for:

Repeated 401/403 errors

Requests to admin panels

Access to unusual URIs

---

## Conclusion
HTTP traffic is fully readable in Wireshark, making it ideal for analyzing:

Web browsing habits

Malware communication

Sensitive data leaks

Suspicious HTTP activity

Understanding HTTP at the packet level helps SOC analysts perform deeper investigations and harden vulnerabilities by using their secure versions like HTTPS(secure).
