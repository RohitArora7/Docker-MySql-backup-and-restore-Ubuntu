# Docker---MySql---Ubuntu

**---------------Backup-------------------**

1. Enter Docker sql container in bash mode
```bash
docker exec -it tutor_local_mysql_1 bash
```
2. mysqldump has to be run in shell not in sql ,backup taken 
```bash
mysqldump -pqbbGos0S --all-databases > sql.sql
```
3. copy from bash dir to home dir 
```bash
docker cp tutor_local_mysql_1:sql.sql . 
```

--Docker One Line Command
```bash
docker exec tutor_local_mysql_1 /usr/bin/mysqldump -u root --password=qbbGos0S --all-databases > backup.sql
```
**--------------Restore-------------------**
```bash
cat backup.sql | docker exec -i tutor_local_mysql_1 /usr/bin/mysql -u root --password=qbbGos0S --all-databases
```

cons- 

Incase any database having issue in restoring create a database manually then run restore script 
```bash
create database DATABASENAME
```

