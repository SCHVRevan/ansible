# Lab_3

## Постановка задачи
### Проверка настройки TMOUT
Необходимо убедится, что в случае неактивности, сессия пользователя закроется через 15 минут.  
Для этого, нужно проверить, что в одном из конфигурационных файлов /etc/bash.bashrc, /etc/profile или /etc/profile.d/*.sh присутствуют следующие строки  
TMOUT=900
readonly TMOUT

### Проверка настроек подключения к AD
1. Проверка настроек клиента Kerberos
Необходимо проверить выполнение следующих требований:

В файле /etc/krb5.conf должны присутствовать следующие настройки

default_etypes = aes128-cts-hmac-sha1-96, aes256-cts-hmac-sha1-96
default_as_etypes = aes128-cts-hmac-sha1-96, aes256-cts-hmac-sha1-96
default_tgs_etypes = aes128-cts-hmac-sha1-96, aes256-cts-hmac-sha1-96

2. Проверка настроек /etc/sssd/sssd.conf
Проверить, что отключено хранение закэшированных доменных учетных данных
- cache_credentials = False
Для обеспечения уникальности нужно проконтролировать, чтобы в файле /etc/ssshd/sssd.conf или /etc/sssd/conf.d/*.conf в настройке формата fallback_homedir присутствовал домен (подстановка «%d»)  
- fallback_homedir = /home/%u@%d

## Описание
Для установки желаемого состояния целевой машины (настройки параметров, политик) составил несколько дополнительных [плейбуков](./conf_target_state).  

## Команды
```bash
ansible-playbook pb_AD_check.yml --ask-become-pass | tee AD_check.txt
```
```bash
ansible-playbook pb_tmout_check.yml | tee tmout_check.txt
```
