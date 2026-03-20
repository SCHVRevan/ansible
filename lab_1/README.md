# Lab_1

## Постановка задачи
Не создавая playbook, используя только ansible и модуль setup, из командной строки получите информацию по основной машине, на которой установлен ansible (localhost), и с удаленных тестовых машин.

## Описание
Использовал две команды, потому что не нашел решения для сбора информации с локального и удаленных хостов без использования файла с inventory.  
Решил оставить связанную с localhost ошибку в файле в качестве учебного артефакта.

## Команды
```bash
ansible all -i "localhost,10.0.47.2,10.0.47.3" -u sys_conf_deb -m setup -a "filter=ansible_all_ipv4_addresses,ansible_board_name,ansible_board_vendor,ansible_fqdn,ansible_os_family,ansible_uptime_seconds,ansible_user_id" > facts_hosts.txt
```
```
ansible localhost -m setup -a "filter=ansible_all_ipv4_addresses,ansible_board_name,ansible_board_vendor,ansible_fqdn,ansible_os_family,ansible_uptime_seconds,ansible_user_id" >> facts_hosts.txt
```
