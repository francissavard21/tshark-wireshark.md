## 📘 Tshark & Wireshark Command Notes

### 🔧 Tshark Commands

- `tshark -r file.pcap`  
  Read and display packets from a pcap file.

- `tshark -r file.pcap -Y "http.request"`  
  Filter and show only HTTP request packets.

- `tshark -r file.pcap -Y "dns.qry.name"`  
  Display only DNS query packets.

- `tshark -r file.pcap -T fields -e dns.qry.name`  
  Extract only the DNS query names.

- `tshark -r file.pcap -Y "http.request" -T fields -e http.host -e http.request.uri`  
  Extract requested domains and URLs.

- `tshark -r file.pcap -qz follow,tcp,ascii,0`  
  Follow the first TCP stream in ASCII view.

- `tshark -r file.pcap -Y "http.host == \"domain.com\"" -T fields -e http.host | wc -l`  
  Count the number of HTTP requests to a specific domain.

- `tshark -r file.pcap -z conv,tcp`  
  Show TCP conversations (useful for session analysis).

- `tshark -r file.pcap -z io,stat,0`  
  Display I/O statistics by time intervals.

---

### 🧪 Wireshark GUI Tips

- **Common Display Filters:**
  - `http` – Show HTTP traffic  
  - `dns` – Show DNS packets  
  - `tcp.port == 443` – Filter packets on port 443  
  - `ip.addr == x.x.x.x` – Show all traffic to/from an IP  
  - `dns.qry.name contains "example.com"` – DNS queries containing a domain  

- **Right-click any packet** → “Follow TCP Stream” to reconstruct conversations.

- **File > Export Objects > HTTP**  
  Download files transferred over HTTP.

- **Color rules** can be used to highlight traffic patterns (via `View > Coloring Rules`).

- Combine filters like:  
  `ip.src == 192.168.1.10 && tcp.port == 80` – Source IP and specific port.

---

