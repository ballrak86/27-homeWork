#26-homeWork. 43 - MySQL: Backup + Репликация  
## Описание файлов в директории
logFileFull.log - полный лог выполнения  

Vagrant_folder - все что понадобится для поднятия ВМ и краткое описание файлов в ней  
Vagrantfile - вагрант файл  
provisioning - директория с файлами провижинга  
```
├── bet.dmp
├── conf
│   └── conf.d
│       ├── 01-base.cnf
│       ├── 02-max-connections.cnf
│       ├── 03-performance.cnf
│       ├── 04-slow-query.cnf
│       └── 05-binlog.cnf
├── defaults
│   └── main.yml
├── master.sql
├── playbook.yml
└── Vagrantfile
```

## Описание как запустить виртуальную машину (кратко)
```
vagrant up
vagrant ssh master
mysql -p'Otus-Linux2019' -D bet -e "INSERT INTO bookmaker (id, bookmaker_name) VALUES('1','1xbet')";

vagrant ssh slave
mysql -p'Otus-Linux2019' -D bet -e "SELECT * FROM bookmaker";
```

## Проверка работы

1. Master  
Заходим на Master и выполняем запрос  
```
[root@master ~]# mysql -p'Otus-Linux2019' -D bet -e "INSERT INTO bookmaker (id, bookmaker_name) VALUES('1','1xbet')";
```

2. Slave  
Проверяем что репликация выполняетсяна slave  
![Image 1](https://github.com/ballrak86/27-homeWork/blob/main/screenshots/check_replication1.jpg)

Проверяем что данные появлись на slave  
![Image 2](https://github.com/ballrak86/27-homeWork/blob/main/screenshots/check_replication2.JPG)

📚Домашнее задание/проектная работа разработано(-на) для курса ["Administrator Linux. Professional"](https://otus.ru/lessons/linux-professional/)
