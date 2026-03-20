Used two commands because I didn't figure out a possible solution to collecting information from localhost and remote machines without using inventory file.  
Decided to leave the error in the file as an educational artifact.

```bash
ansible all -i "localhost,10.0.47.2,10.0.47.3" -u sys_conf_deb -m setup -a "filter=ansible_all_ipv4_addresses,ansible_board_name,ansible_board_vendor,ansible_fqdn,ansible_os_family,ansible_uptime_seconds,ansible_user_id" > facts_hosts.txt
```
```
ansible localhost -m setup -a "filter=ansible_all_ipv4_addresses,ansible_board_name,ansible_board_vendor,ansible_fqdn,ansible_os_family,ansible_uptime_seconds,ansible_user_id" >> facts_hosts.txt
```
