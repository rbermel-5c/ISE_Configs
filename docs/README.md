## TACACS
### ISE Network Device Configuraiton

### ASA OS
TACACS+ Server Configuration
```
aaa-server <group_name> protocol TACACS+
aaa-server <PSN_server_name> <(Interface_name)> host <PSN_ip_address_1>
key <ISE_node_shared_secret>
```
AAA configuration
```
aaa authentication ssh console <group_name> LOCAL
aaa authentication enable console <group_name> LOCAL
aaa authentication http console <group_name> LOCAL
aaa authentication secure-http-client
aaa authorization exec authentication-server auto-enable LOCAL
aaa accounting ssh console <group_name>
aaa accounting serial console <group_name>
aaa accounting enable console <group_name>

```
### IOS-XE
Enable new model
```
aaa new-model
```
TACACS+ Server Group Configuration
```
aaa group server tacacs+ <group_name>
server-private <PSN_ip_address_1> key <ISE_node_shared_secret>
server-private <PSN_ip_address_2> key <ISE_node_shared_secret>
```
AAA Configuration
```
aaa authentication login group <group_name> local]
aaa authorization exec default local
aaa authorization exec group <group_name> local
aaa accounting exec default start-stop group <group_name>
aaa accounting commands 1 default start-stop group <group_name>
aaa accounting commands 15 default start-stop group <group_name>

```
### NX-OS

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
TACACS+ username test configuration does not have to be successful. ISE just needs to respond.

AAA Group Configuration
```
aaa group server tacacs+ <Group_Name>
server <PSN_ip_address_1>
server <PSN_ip_address_2>
server <PSN_ip_address_3>
server <PSN_ip_address_4>
deadtime 60
source-interface <interface_name>
```
Deadtime says how long a failed TACACS+ server should be marked as FAILED.

AAA Configuration
```
aaa authentication login default group <Group_Name> local
aaa authentication login console group <Group_Name> local
aaa authorization config-commands default group <Group_Name> local
aaa authorization commands default group <Group_Name> local
aaa accounting default group <Group_Name>
```

### Testing aaa Configuration
```
test aaa server tacacs+ <PSN_ip_address_1> <username> <password>
test aaa server tacacs+ <PSN_ip_address_2> <username> <password>
test aaa server tacacs+ <PSN_ip_address_3> <username> <password>
test aaa server tacacs+ <PSN_ip_address_4> <username> <password>
```

Cisco TACACS+ Configuration Guide (https://community.cisco.com/t5/security-documents/cisco-ise-device-administration-prescriptive-deployment-guide/ta-p/3738365#toc-hId-1977002717)
