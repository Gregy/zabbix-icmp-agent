# zabbix-icmp-agent
Zabbix template and accompanying scripts for icmp monitoring done by agent. Allows multiple ping targets from single host and automatically generates items, triggers and graphs based on target list. Monitors max,avg,min rtt and loss. You can specify number of packets, interval and custom description.

## Installation
### Agent
Copy zaping shell script over to a machine with zabbix agent. Modify zabbix agent config as shown in zaping.conf. Restart zabbix agent.

### Server
Copy zabbix-icmp-lld to external scripts directory on your zabbix server. Import template.

## How does it work
This template bypasses zabbix limitation of only allowing one template link per host by misusing low level discovery. To use it you have to link the template with a host and then define a special macro {$PINGTARGETS} on the host. This macro's contents is fed to the zabbix-icmp-lld script which returns LLD JSON. Zabbix generates items, triggers and graphs based on this data.
