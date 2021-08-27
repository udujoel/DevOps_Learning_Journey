- LogStash doen't just ingest data, but main purpose is to transform data as it comes in. eg transform plaintext data into structured data. The transformed data is what is stored instead of the former data state. Logstash is 

- Beats and Logstash can be used together, with Beats shipping the data to a Logstash server.

- LogStash is resource intensive. 

## Installation

- LogStash requires Java, so first:
```bash
apt install openjdk-11-jre
```
- then
```bash
apt install logstash
```
- Set the java home default:
```bash
nano /etc/default/logstash
```
- add: JAVA_HOME="/usr/lib/jvm/java-11-openjdk-amd64"

- Set logstash to autostart
```bash
systemctl enable logstash
```
- start service: 

```bash
systemctl start logstash
```
- Check the status with:
```bash
systemctl status logstash
```

LogStash config file contains basically: Input, Output, filter parts.
Example:
-------------------------------
```
input {
  file {
    path => "/var/log/kern.log"
    start_position => "beginning"
    #Uncomment the following line to force logstash to reingest file
    #sincedb_path => "/dev/null"
  }
}

filter {
  if [type] == "syslog" {
    grok {
      match => { "message" => "%{SYSLOGTIMESTAMP:syslog_timestamp} %{SYSLOG$    }
  }
}

output {
  elasticsearch { hosts => ["localhost:9200"] }
  stdout { codec => rubydebug }
}

```
------------------------

- The input specifies from whence to get data. File/network/etc. 
- The output defines where to put the data. generally elasticsearch, but can also be file on disk or network location.

- The filter part is where data is manipulated. Here raw data is tagged and parsed into structured data. 
- Grok is a common command used to transform raw into structured data. Another is Mutate.

- http://grokconstructor.appspot.com/


