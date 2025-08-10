# Домашнее задание к занятию «Уязвимости и атаки на информационные системы»

## ` Дмитрий Климов `

Задание 1
Скачайте и установите виртуальную машину Metasploitable: https://sourceforge.net/projects/metasploitable/.

Это типовая ОС для экспериментов в области информационной безопасности, с которой следует начать при анализе уязвимостей.

Просканируйте эту виртуальную машину, используя nmap.

Попробуйте найти уязвимости, которым подвержена эта виртуальная машина.

Сами уязвимости можно поискать на сайте https://www.exploit-db.com/.

Для этого нужно в поиске ввести название сетевой службы, обнаруженной на атакуемой машине, и выбрать подходящие по версии уязвимости.

Ответьте на следующие вопросы:

Какие сетевые службы в ней разрешены?
Какие уязвимости были вами обнаружены? (список со ссылками: достаточно трёх уязвимостей)
Приведите ответ в свободной форме.

## Ответ:

Установка Metasploitable: Виртуальная машина Metasploitable была успешно скачана и установлена в VirtualBox.
Сканирование Nmap: После запуска Metasploitable, ей был присвоен IP-адрес. Затем была запущена команда nmap -sV -p- <ip-адрес> для сканирования всех портов и определения версий запущенных служб. -sV определяет версию сервиса, -p- сканирует все порты.
Анализ результатов сканирования Nmap и поиск уязвимостей: Результаты сканирования были тщательно изучены для идентификации уязвимых служб. Обнаруженные службы и их версии были использованы для поиска соответствующих уязвимостей на сайте Exploit-DB.
Результаты:

### Какие сетевые службы в ней разрешены?

Nmap обнаружил множество открытых портов и работающих служб, что и делает Metasploitable такой уязвимой. 

Вот некоторые из них:

```
21/tcp open ftp vsftpd 2.3.4
22/tcp open ssh OpenSSH 4.7p1 Debian 8ubuntu1 (protocol 2.0)
23/tcp open telnet Linux telnetd
25/tcp open smtp Postfix smtpd
53/tcp open domain ISC BIND 9.4.2
80/tcp open http Apache httpd 2.2.8 ((Ubuntu) DAV/2 PHP/5.2.4-2ubuntu5.10 with Suhosin-Patch)
111/tcp open rpcbind 2 (RPC v2 portmapper)
139/tcp open netbios-ssn Samba smbd 3.0.20-Debian
445/tcp open microsoft-ds Samba smbd 3.0.20-Debian
512/tcp open exec netkit-rsh rexecd
513/tcp open login netkit-rsh rlogind
514/tcp open shell netkit-rsh rshd
1099/tcp open java-rmi Java RMI Registry
1524/tcp open shell OpenBSD remote shell
2049/tcp open nfs_acl 2-3 (nfs-acl 100201)
3306/tcp open mysql MySQL 5.0.51a-3ubuntu5
3632/tcp open distccd distccd v1 ((GNU) 4.2.4 (Ubuntu 4.2.4-1ubuntu4))
5432/tcp open postgresql PostgreSQL 8.3.0
5900/tcp open vnc VNC (protocol 3.3)
6667/tcp open irc ircd
8009/tcp open ajp13 Apache JServ (Protocol v1.3)
8180/tcp open http Apache Tomcat/Coyote JSP engine 1.1
8787/tcp open ssl/http Apache Tomcat/Coyote JSP engine 1.1
31337/tcp open elite Elite
```

### Какие уязвимости были вами обнаружены? (список со ссылками: достаточно трёх уязвимостей)

На основании информации, полученной от Nmap и используя Exploit-DB, были найдены следующие уязвимости:

VSFTPD 2.3.4 Backdoor Command Execution: Версия VSFTPD, используемая на Metasploitable, содержит backdoor, добавленный злоумышленником. При подключении к сервису через FTP и вводе имени пользователя, заканчивающегося на :), открывается shell с правами root.

Ссылка на Exploit-DB: 

` https://www.exploit-db.com/exploits/17491 `

Samba 3.0.20 - “Username” map script Command Execution: Samba версии 3.0.20 подвержена уязвимости, связанной с использованием параметра username map script. При некорректной конфигурации позволяет выполнить произвольные команды на сервере с правами root.

Ссылка на Exploit-DB: 

` https://www.exploit-db.com/exploits/1632 `

DistCC Daemon Command Execution: Сервис DistCC, используемый для распределенных вычислений, в данной версии не требует аутентификации и позволяет удаленно выполнять команды на сервере.

Ссылка на Exploit-DB: 

` https://www.exploit-db.com/exploits/32702 `
Заключение:

Metasploitable предоставляет отличную платформу для изучения уязвимостей и методов их эксплуатации. Анализ с помощью Nmap и Exploit-DB показал, что в системе присутствует множество уязвимостей различной степени критичности. Эксперименты с этими уязвимостями помогут лучше понять механизмы атак и защиты. Важно помнить, что Metasploitable не должна использоваться в производственной среде, так как это намеренно уязвимая система.
