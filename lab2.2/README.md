# Lab_2.2

## Постановка задачи
На одном из тестовых ПК с помощью ansible установить nginx и произвести настройку сервера путем создания конфигурационного файла из шаблона  

## Команды
```bash
ansible-playbook pb_install_nginx.yml --ask-become-pass | tee output.txt
```
