### logs - _журналирование в Linux включает два типа механизмов_:

1. **Журналирование пространства ядра**. Ядро использует кольцевой буфер для хранения сообщений журнала, начиная с процесса загрузки системы. Этот буфер имеет фиксированный размер, и как только он заполнится, новые сообщения будут перезаписывать старые.
2. **Журналирование пользовательского пространства**. Основано на протоколе системного журнала (Syslog). Он используется как стандарт для производства, пересылки и сбора логов в экземпляре Linux. 

**По умолчанию события журналируются в каталог /var/log**. В нём имеется множество файлов *.log, содержащих события от различных источников в текстовом виде. В зависимости от установленных в системе приложений, в каталоге /var/log могут находиться различные файлы журналов:

* **Файлы /var/log/syslog или /var/log/messages** — глобальный системный журнал. В нём можно найти события, произошедшие с момента запуска системы от различных компонентов ОС — ядра, служб, устройств и т. д..
* **Журнал событий var/log/kern.log** — содержит сообщения от ядра и предупреждения, которые могут быть полезны при устранении ошибок, произошедших при работе пользовательских модулей, встроенных в ядро.
* **Журналы /var/log/auth.log или /var/log/secure** — содержат информацию об авторизации пользователей, то есть попытки неудачных и успешных входов в систему и методов аутентификации.
* **События от оборудования и драйверов устройств** находятся в файле /var/log/dmesg. В этом файле фиксируются ошибки работы драйверов и оборудования.
* **События установки системы** можно найти в файле /var/log/anaconda.log, а в файле /var/log/boot.log — логи загрузки системы. 

**Для просмотра журналов** в дистрибутивах Linux, использующих systemd, применяется команда journalctl. Если дистрибутив использует syslog, для просмотра используются: cat, less или grep. 




* /var/log
* /etc/logrotate.conf
* /etc/rsyslog.d/50-default.conf

**Команды**

* sudo apt  install lnav
* tail -f /var/log/syslog
* sudo journalctl --list-boots
* sudo journalctl -b -1
* sudo journalctl -b -1 -u NetworkManager
* sudo journalctl -p err -b -0
* sudo journalctl -u NetworkManager
* sudo journalctl -k

* grep { warning | error | info }  /var/log/syslog

* sudo journalctl -S today | grep ikozhuhar

* sudo systemd-analyze
* sudo systemd-analyze blame

**Приоритеты сообщений**

* emerg - наивысший приоритет
* alert - тревога
* crit - критическое событие
* err - ошибка
* warning - внимание
* notice - уведомление
* info - информационное сообщение
* debug - отладочная информация


https://habr.com/ru/companies/ruvds/articles/533918/

