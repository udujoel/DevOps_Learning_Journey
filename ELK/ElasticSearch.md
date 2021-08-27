- ELK is great for CENTRALIZED LOGS.

- Instead of desipating your energy tracing down where a problem is comingg from in a non-central logging setup, ELK gives you a head start in fixing the problem.

- ELK is great generally for any usecase that needs to search and use a large data body. Its also used for web apps that uses a backend to power its search feature.

- Beats is a lightweight way of getting data into the Elk stack. Its written in Go, and includes sub programs like FileBeat, PacketBeat, etc.

- ElasticSearch is part of the stack that stores/holds data. It holds the index of the data, for easy searching.


## INSTALLATION
- (https://phoenixnap.com/kb/how-to-install-elk-stack-on-ubuntu)

```bash
sudo su -
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | apt-key add -
echo "deb https://artifacts.elastic.co/packages/7.x/apt stable main" | sudo tee -a /etc/apt/sources.list.d/elastic-7.x.list
apt-get update && apt-get install elasticsearch
```

- then make it to auto-start: 
```bash 
 systemctl enable elasticsearch
```
- Then start the service: 
```bash
systemctl start elasticsearch
```
- To test use:
curl localhost:9200
