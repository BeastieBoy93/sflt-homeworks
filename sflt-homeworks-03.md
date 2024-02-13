Домашнее задание к занятию 2 «Кластеризация и балансировка нагрузки» - `Эсадов Роман`
---
### Задание 1
`Команда rsync`
```
rsync -acv --progress --exclude '.*' . /tmp/backup
```
![Rsync /tmp/backup](https://github.com/BeastieBoy93/sflt-homeworks/blob/main/tmp-backup.png)
### Задание 2
`Файл crontab с условием выполнения джоба раз в сутки в 23:59`
```
# Edit this file to introduce tasks to be run by cron.
#
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
#
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').
#
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
#
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
#
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
#
# For more information see the manual pages of crontab(5) and cron(8)
#
# m h  dom mon dow   command
59 23 * * * rsync -acv --progress --delete . /tmp/backup | /usr/bin/logger -t CRONOUTPUT
```
`Пример логирования выполнения джоба при условии выполнения джоба каждую минуту`
```
# Edit this file to introduce tasks to be run by cron.
#
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
#
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').
#
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
#
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
#
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
#
# For more information see the manual pages of crontab(5) and cron(8)
#
# m h  dom mon dow   command
* * * * * rsync -acv --progress --delete . /tmp/backup | /usr/bin/logger -t CRONOUTPUT
```
![cron](https://github.com/BeastieBoy93/sflt-homeworks/blob/main/cron.png)
---
