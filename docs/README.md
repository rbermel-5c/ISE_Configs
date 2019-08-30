# NX-OS

Enable TACACS+ Feature
```
feature tacacs+
```

TACACS+ Server Configuration
```
tacacs-server host <PSN_ip_address_1> key 7 "<ISE_node_shared_secret>" timeout 10

tacacs-server host <PSN_ip_address_2> key 7 "<ISE_node_shared_secret>" timeout 10

tacacs-server host <PSN_ip_address_3> key 7 "<ISE_node_shared_secret>" timeout 10

tacacs-server host <PSN_ip_address_4> key 7 "<ISE_node_shared_secret>" timeout 10

tacacs-server host <PSN_ip_address_1> test username ISE_TEST password ISE_TEST idle-time 15

tacacs-server host <PSN_ip_address_2> test username ISE_TEST password ISE_TEST idle-time 15

tacacs-server host <PSN_ip_address_3> test username ISE_TEST password ISE_TEST idle-time 15

tacacs-server host <PSN_ip_address_4> test username ISE_TEST password ISE_TEST idle-time 15
```
AAA Group Configuration
```
aaa group server tacacs+ Winston_ISE

server <PSN_ip_address_1>

server <PSN_ip_address_2>

server <PSN_ip_address_3>

server <PSN_ip_address_4>

deadtime 60

source-interface <interface_name>
```

Cisco TACACS+ Configuration Guide (https://community.cisco.com/t5/security-documents/cisco-ise-device-administration-prescriptive-deployment-guide/ta-p/3738365#toc-hId-1977002717)
