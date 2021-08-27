Kibana is the visualization and search frontend of the stack. It enables you search through your logs and apply needed filters. It enables you to visualize data in real-time too.

## Installation
```bash
apt update && apt install kibana
```

then make it to auto-start: 
```bash
systemctl enable kibana
```

Then start the service: 
```bash
systemctl start kibana
```
To test use:
```bash
journalctl -u kibana
```
Next, to be able to view this on the browser, you'll need to edit the kibana config file:
```bash
nano /etc/kibana/kibana.yml
```
uncomment and edit the server.host:
server.host:"0"
```bash
systemctl restart kibana
```
(netstat -tulpn can show u all running processes. It'll be using 0.0.0.0 and node)
- Open a brower and check: localhost:5601