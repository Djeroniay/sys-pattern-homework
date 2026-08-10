
### Задание 2

2.1. Примеры команд резервирования и восстановления
    Бэкап в текстовый SQL-файл:
``` pg_dump -U postgres -d mydb > backup.sql  ```
    Восстановление :
``` psql -U postgres -d newdb < backup.sql```
    Бэкап в кастомный формат (рекомендуется):
``` pg_dump -Fc -U postgres -d mydb > mydb.dump  ```
    Восстановление :
``` pg_restore -d newdb -U postgres mydb.dump```
2.1.* Возможно ли автоматизировать этот процесс? Если да, то как?
    1. Планировщик CRON (Linux/Unix)
    2. Скрипт с полным циклом бэкапирования
    3. Готовые инструменты AutoPostgreSQLBackup

---
### Задание 3
3.1. С помощью официальной документации приведите пример команды инкрементного резервного копирования базы данных MySQL.
    1. Полное резервное копирование с обновлением логов
``` mysqldump -u root -p --all-databases --single-transaction --flush-logs --master-data=2 > full_backup.sql```
    Восстановление:
```mysql -u root -p < full_backup.sql```
    2. Инкрементное копирование
``` mysqlbinlog --start-position=4 /var/lib/mysql/mysql-bin.000001 > incremental_backup.sql```
    Восстановление:
```mysql -u root -p < incremental_backup.sql```
