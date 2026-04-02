# Lab_4

## Постановка задачи
### 1. Установить chkrootkit и проверить диск на наличие rootkit-ов.

### 2. Написать скрипт который проверяет, что модули неиспользуемых файловых систем отключены.  
Неиспользуемые файловые системы:
- cramfs
- freevxfs
- jffs2
- hfs
- hfsplus
- squashfs

### 3. Написать скрипт(ы), который проверяет следующие требования стандарта:
1) В конфигурационном файле /etc/login.defs изменить параметр UMASK:  
UMASK 027
2) В директории /etc/profile.d/ создать скрипт orgnm.sh и указать в нем следующие команды:  
umask 027
3) В конфигурационном файле /etc/adduser.conf изменить параметр DIR_MODE следующим образом:  
DIR_MODE=0700
4) Для файлов и директорий находящихся в /var/log необходимо у группы владельца отозвать права на запись и исполнение, у группы other отозвать все права доступа  
find /var/log -type f -exec chmod g-wx,o-rwx "{}" + -o -type d -exec chmod g-w,o-rwx "{}" +

## Описание
После ручной настройки системы предпринял попытки автоматизировать данный процесс. Для этого составил несколько вспомогательных [плейбуков](./conf_target_state).  

## Команды
```bash
ansible-playbook pb_useless_filesystems_check.yml --ask-become-pass | tee fs_check-out.txt
```
```bash
ansible-playbook pb_other_checks.yml --ask-become-pass | tee permissions_check_out.txt
```
```bash
ansible-playbook pb_rootkit_check.yml --ask-become-pass | tee rootkit_check_out.txt
```
