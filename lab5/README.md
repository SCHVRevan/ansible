# Lab_5

## Постановка задачи
### 1. Написать плейбук, который проверяет, что следующие службы не активны (используя встроенный модуль service_facts): 
- autofs
- avahi
- dhcp
- dns
- ftp
- ldap
- nfs
- nis
- cups
- samba
- snmp
- tftp
- web
- xinetd
- mta  

### 2. Написать плейбук, который проверяет настройки по "уменьшению периметра атаки ядра Linux" ("Рекомендации ФСТЭК по защите ядра") (можно выбрать только несколько пунктов для проверки)

## Описание
Для конфигурирования системы были написаны плейбуки pb_deactivate_some_services.yml и pb_fstec_recs_setup.yml. Оба могут быть использованы в том числе для проверки корректности настроек 
путём запуска с изменением параметра check_mode. Реализованы все указанные рекомендации из раздела "Рекомендации ФСТЭК по защите ядра".  
Дополнительно был составлен pb_check_services.yml для проверки состояния указанных служб.  

## Команды
```bash
ansible-playbook pb_check_for_inactive_services.yml --ask-become-pass | tee check_running_services.txt
```
```bash
ansible-playbook pb_fstec_recs_setup.yml --ask-become-pass | tee check_fstec_recs.txt
```
```bash
ansible-playbook pb_check_services.yml --ask-become-pass | tee check_services_state.txt
```
Также были опробованы рекомендации по безопасной настройке systemd. Пример настройки службы secure shell (ограничением привилегий служб пренебрегаем, так как у службы имеется встроенный механизм privilege separation)  
<p align="center">
  <img width="682" height="595" alt="ssh_conf" src="https://github.com/user-attachments/assets/88f702ad-d769-4b93-9ef9-6d3a8a6166e8" />
</p>
