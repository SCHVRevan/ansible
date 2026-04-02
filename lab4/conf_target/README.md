## Вспомогательные плейбуки для настройки целевого узла

### Команды
```bash
ansible-playbook pb_new_disk_processing.yml --ask-become-pass
```
Если разметка и монтирование уже выполнены, можно использовать исключительно группу задач для конфигурирования прав доступа
```bash
ansible-playbook pb_new_disk_processing.yml --tags "permissions" --ask-become-pass
```
