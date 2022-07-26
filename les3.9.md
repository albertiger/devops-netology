Домашнее задание к занятию "3.9. Элементы безопасности информационных систем"
Задание-1. Установите Bitwarden плагин для браузера. Зарегестрируйтесь и сохраните несколько паролей.

Ответ:
1)Установил плагин bitwarden в google chrome, показано на скриншите:
![](https://github.com/albertiger/devops-netology/blob/3ad3809ef6254635b28de524d73eb13b61eae42a/less%203.9/%D0%97%D0%B0%D0%B4.1.1.jpg)
2)Привязал в приложении bitwarden аккаунт от netology, показано на скриншите:
![](https://github.com/albertiger/devops-netology/blob/789dab57850ba40660ee6ab9a55f0b58dd13ed46/less%203.9/%D0%97%D0%B0%D0%B4.1.2.JPG)


Задание-2. Установите Google authenticator на мобильный телефон. Настройте вход в Bitwarden акаунт через Google authenticator OTP.

Ответ:
1)Установил Google authenticator на мобильный телефон, показано на скриншите:
![](https://github.com/albertiger/devops-netology/blob/56a15b1867e8ec05302ea1c163891c508a9cf605/less%203.9/%D0%97%D0%B0%D0%B4.2.1.JPG)
2)Настроил вход в Bitwarden акаунт через Google authenticator OTP, включив данную функцию в настройках аккаунта bitwarden,
как на скриншоте:
![](https://github.com/albertiger/devops-netology/blob/56a15b1867e8ec05302ea1c163891c508a9cf605/less%203.9/%D0%97%D0%B0%D0%B4.2.2.JPG) 
потом добавил в мобильном приложении, авторизацию на bitwarden по данному аккаунту, как на скриншоте:
![](https://github.com/albertiger/devops-netology/blob/56a15b1867e8ec05302ea1c163891c508a9cf605/less%203.9/%D0%97%D0%B0%D0%B4.2.1.JPG)


Задание-3. Установите apache2, сгенерируйте самоподписанный сертификат, настройте тестовый сайт для работы по HTTPS.

Ответ:
1) устанавливаем apache2, предварительно обновив, используя комманды:
 sudo apt install apache2
2) После завершения установки нужно добавить веб-сервер в автозагрузку:
 sudo systemctl enable apache2
3) сгенерируйте самоподписанный сертификат:
 sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048
заполнив все необхоимые данные для генерации, имя фирмы, страна, город, имя домена итп.
показано на скриншоте:
![](https://github.com/albertiger/devops-netology/blob/56a15b1867e8ec05302ea1c163891c508a9cf605/less%203.9/%D0%97%D0%B0%D0%B4.3.3.JPG)
4) Создадим конфиг запуска для apache2 под наш домен:
 sudo vim /etc/apache2/sites-available/your_domain_or_ip.conf
показано на скриншоте выделенный блок 1:
![](https://github.com/albertiger/devops-netology/blob/56a15b1867e8ec05302ea1c163891c508a9cf605/less%203.9/%D0%97%D0%B0%D0%B4.3.4.JPG)
так же создадим тестовую страничку которая будет открываться:
 sudo mkdir /var/www/your_domain_or_ip
 sudo vim /var/www/your_domain_or_ip/index.html
показано на скриншоте выделенный блок 2:
![](https://github.com/albertiger/devops-netology/blob/56a15b1867e8ec05302ea1c163891c508a9cf605/less%203.9/%D0%97%D0%B0%D0%B4.3.4.JPG)
5) проверяем работу apache2, загружаемся по имени нашего сайта(домена):
показано на скриншоте:
![](https://github.com/albertiger/devops-netology/blob/56a15b1867e8ec05302ea1c163891c508a9cf605/less%203.9/%D0%97%D0%B0%D0%B4.4.1.JPG)


Задание-4. Проверьте на TLS уязвимости произвольный сайт в интернете (кроме сайтов МВД, ФСБ, МинОбр, НацБанк, РосКосмос, РосАтом, РосНАНО и любых госкомпаний, объектов КИИ, ВПК ... и тому подобное).

Ответ:
- Для проверки я использовал ресурс ssllabs.com
- Выбрал сайт ozon.ru для проверки по tls, как показано на скриншоте:
![](https://github.com/albertiger/devops-netology/blob/56a15b1867e8ec05302ea1c163891c508a9cf605/less%203.9/%D0%97%D0%B0%D0%B4.3.1.JPG)

далее видно результаты тестирования tls разных версий, как показано на скриншотах:
![](https://github.com/albertiger/devops-netology/blob/56a15b1867e8ec05302ea1c163891c508a9cf605/less%203.9/%D0%97%D0%B0%D0%B4.4.2.JPG)
![](https://github.com/albertiger/devops-netology/blob/56a15b1867e8ec05302ea1c163891c508a9cf605/less%203.9/%D0%97%D0%B0%D0%B4.4.3.JPG)
![](https://github.com/albertiger/devops-netology/blob/56a15b1867e8ec05302ea1c163891c508a9cf605/less%203.9/%D0%97%D0%B0%D0%B4.4.4.JPG)
![](https://github.com/albertiger/devops-netology/blob/56a15b1867e8ec05302ea1c163891c508a9cf605/less%203.9/%D0%97%D0%B0%D0%B4.4.5.JPG)


Задание-5. Установите на Ubuntu ssh сервер, сгенерируйте новый приватный ключ. Скопируйте свой публичный ключ на другой сервер. Подключитесь к серверу по SSH-ключу.

Ответ:
1) установка ssh сервер и добавляем его в автозагрузку, используя комманды:
apt install openssh-server
systemctl start sshd.service
systemctl enable sshd.service
2)Проверим работоспособность службы, и убедимся что работает:
service ssh status
как показано на скриншоте:
![](https://github.com/albertiger/devops-netology/blob/56a15b1867e8ec05302ea1c163891c508a9cf605/less%203.9/%D0%97%D0%B0%D0%B4.5.1.JPG)
3)генерируем ключи
/home/<username>/.ssh/id_rsa - приватный ключ
id_rsa.pub - публичный ключ
коммандой:
ssh-keygen
как показано на скриншоте:
![](https://github.com/albertiger/devops-netology/blob/56a15b1867e8ec05302ea1c163891c508a9cf605/less%203.9/%D0%97%D0%B0%D0%B4.5.2.JPG)
4)Скопируем публичный ключ на удаленный сервер 192.168.56.106
5)Пробуем подключиться к серверу по ssh 192.168.56.105, как показано на скриншотах:
![](https://github.com/albertiger/devops-netology/blob/56a15b1867e8ec05302ea1c163891c508a9cf605/less%203.9/%D0%97%D0%B0%D0%B4.5.3.JPG)
![](https://github.com/albertiger/devops-netology/blob/56a15b1867e8ec05302ea1c163891c508a9cf605/less%203.9/%D0%97%D0%B0%D0%B4.5.4.JPG)


Задание-6. Переименуйте файлы ключей из задания 5. Настройте файл конфигурации SSH клиента, так чтобы вход на удаленный сервер осуществлялся по имени сервера.

Ответ:
1) Настроим конфигурационный файл для подключения по ssh использую заранее подготовленный конфиг, используя комманды:
mkdir -p ~/.ssh && chmod 700 ~/.ssh
touch ~/.ssh/config && chmod 600 ~/.ssh/config
как показано на скришоте, блок 1, результат конфига, используем имя хоста pak:
![](https://github.com/albertiger/devops-netology/blob/56a15b1867e8ec05302ea1c163891c508a9cf605/less%203.9/%D0%97%D0%B0%D0%B4.6.1.JPG)
2) как показано на скришоте, блок 2, используя имя хоста pak, пробуем подключиться:
![](https://github.com/albertiger/devops-netology/blob/56a15b1867e8ec05302ea1c163891c508a9cf605/less%203.9/%D0%97%D0%B0%D0%B4.6.1.JPG)


Задание-7. Соберите дамп трафика утилитой tcpdump в формате pcap, 100 пакетов. Откройте файл pcap в Wireshark.

Ответ:
1) установим необходимый пакет:
apt install tcpdump
2) Соберем дамп с ограничением на 100 пакетов в формате pcap, коммандой:
sudo tcpdump -c 100 -w 0100.pcap -i enp0s3
как показано на скриншоте:
![](https://github.com/albertiger/devops-netology/blob/56a15b1867e8ec05302ea1c163891c508a9cf605/less%203.9/%D0%97%D0%B0%D0%B4.7.1.JPG)
3)И откроем данный дамп в wireshark, где видно на какой и с какого хоста мы его получили, как показано на скриншоте:
![](https://github.com/albertiger/devops-netology/blob/56a15b1867e8ec05302ea1c163891c508a9cf605/less%203.9/%D0%97%D0%B0%D0%B4.7.2.JPG)

