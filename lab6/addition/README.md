# TBD (still experimenting)
```bash
mysql -u rsyslog -p123_qwe -e "SELECT * FROM (SELECT * FROM logdb.logs ORDER BY Timestamp DESC LIMIT 10) t ORDER BY Timestamp ASC \G" > bd_logs.txt
```
