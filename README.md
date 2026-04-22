# suricata-detection-lab
Suricata is used as a network IDS in ubuntu live server for monitoring a traffic between Kali and ubuntu live server. Suricata will catch packets and write a log in eve.json and then the alerts that show up can be analyzed from terminal or kibana.
# On This Project
- run as service
- write events to eve.json
- successfully detect :
    - Port scan
    - Brute force
    - Web probing
    - Flood
# Suricata Setup Guide
- install suricata
  using: sudo apt install -y suricata suricata-update
- edit suricata configuration
  using: sudo nano /etc/suricata/suricata.yaml

  add rules. For example:
  
  rule-files:
  - suricata.rules
  - local.rules
- update rules
  using: sudo suricata-update
- add custom rules in local rules
- test configuration
  using : sudo suricata -T -c /etc/suricata/suricata.yaml -v
- run suricata service
- check alert event only by using :
  grep -a '"event_type":"alert"' /var/log/suricata/eve.json | tail -20

# Topology
Ubuntu live server
  - Elasticsearch
  - Kibana
  - Fleet Server
  - Elastic Agent
  - Suricata IDS
  - Nginx for web probing target

Kali Linux
  - Elastic Agent
