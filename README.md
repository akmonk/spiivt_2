# spiivt_2

1. Создать базовый профиль для программы lftp

aa-autodep lftp

2. Запустить утилиту профилировки genprof, в соседнем терминале нужно запустить lftp и выполнить все то, что является обычным для программы

aa-complain /usr/bin/lftp
aa-genprof lftp


Зайти на сервер по ftp, просмотреть каталог, походить по директориям, скачать файл

3. После отредактировать правила в файле /etc/apparmor.d/usr.bin.lftp

Добавил запрет на просмотр и редактирование ssh ключей


4. Перечитать профиль 

apparmor_parser -r /etc/apparmor.d/usr.bin.lftp

5. Переключить профиль в режим enforce

sudo aa-enforce /usr/bin/lftp

6. После этого попробовать подключиться к ftp и загрузить какой-нибдь файл + попробовать загрузить id_rsa.pub



get .ssh/id_rsa.pub
get: /home/ak/id_rsa.pub: Permission denied

