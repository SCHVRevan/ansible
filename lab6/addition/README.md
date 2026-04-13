## Добавлено
Настройка journald, rsyslog и MySQL [центральной](./pb_central_log_conf.yml) и [удалённых](./pb_remote_log_conf.yml) машин для централизованного сбора логов.
```bash
# Пример собираемых данных
mysql -u rsyslog -p<pwd> -e "SELECT * FROM (SELECT * FROM logdb.logs ORDER BY Timestamp DESC LIMIT 10) t ORDER BY Timestamp ASC \G" > bd_logs.txt
```
Настройка [auditd](./pb_auditd_conf.yml) и установка правил.
Представлен [результат](./auditd-results.txt) настройки посредством конкатенации следующих выводов
```bash
sudo auditctl -s
sudo auditctl -l
```
