# Load Balancing DNS server

Dns Server:

-   runs an **authoritative DNS server** (UDP/TCP 53) choosing the best web-server IP by `load`, `geo location`, or `round robin` (`src/dnsserver/`)
-   deploys a tiny **agent** on each web node to POST its CPU load to the DNS box over HTTP 8080 (`src/webserver*/`)

---

## Requirements

-   Python 3.8+ on all hosts
-   Install Required Libraries: `pip install dnslib pyyaml requests psutil`

---

## 1 . DNS Server

```bash
# edit config.yml:
#   ip_addresses
#   dns_ip_address
#   algorithm: load | geo | round
sudo python3 dnsserver.py --port 53 --tcp --udp   # start
# logs to logs/dnsserver.log
sudo python3 dnsserver.py stop                    # stop
```
