Домашнее задание к занятию "5.2. Применение принципов IaaC в работе с виртуальными машинами"

***ЗАДАЧА 1***
1)Опишите своими словами основные преимущества применения на практике IaaC паттернов.
2)Какой из принципов IaaC является основополагающим?

*ОТВЕТ*
1) IaaC позволяет запуская код, поднимать большое количество машин необходимой конфигурации под текущие задачи и  автоматически сократить инфраструктуру донеобходимого масштаба в текущий момент для экономии
2)-Скорость, уменьшение затрат, Масштабируемость и стандартизация.




***ЗАДАЧА 2***
1)Чем Ansible выгодно отличается от других систем управление конфигурациями?
2)Какой, на ваш взгляд, метод работы систем конфигурации более надёжный push или pull?

*ОТВЕТ*
1) -На управляемые узлы не нужно устанавливать никакого дополнительного ПО, всё работает через SSH
  -Низкий порог вхождения: обучиться работе с Ansible можно за очень короткое время
2)Мне кажеться, что всетаки подход на основе pull надежней так как, что все изменения применяются изнутри.


***ЗАДАЧА 3***
Установить на личный компьютер:

VirtualBox
Vagrant
Ansible
Приложить вывод команд установленных версий каждой из программ, оформленный в markdown.

*ОТВЕТ*
1)VirtualBox
Графический интерфейс VirtualBox
Версия 6.1.34 r150636 (Qt5.6.2)
![](https://github.com/albertiger/devops-netology/blob/780a729414a85c862576123edeea8870292e619d/less5.2/z3-1.JPG)

2)Vagrant
Вагрант у меня уже был установлен поэтому просто выведу версию
C:\VM\vagrantvm>vagrant -v
Vagrant 2.2.19
![](https://github.com/albertiger/devops-netology/blob/780a729414a85c862576123edeea8870292e619d/less5.2/z3-2.JPG)

3)Ansible
3.1-Сначала обновим и установим используя комманды:
sudo apt update
sudo apt install ansible
3.2-Потом проверим установленную версию Ansible
vagrant@vagrant:~$ ansible --version
ansible 2.9.6
![](https://github.com/albertiger/devops-netology/blob/780a729414a85c862576123edeea8870292e619d/less5.2/z3-3.JPG)


***ЗАДАЧА 4*** (*)
Воспроизвести практическую часть лекции самостоятельно.

Создать виртуальную машину.
Зайти внутрь ВМ, убедиться, что Docker установлен с помощью команды
docker ps

*ОТВЕТ*
1) на заранее созданную ВМ установим Docker, предварительно обновив:
sudo apt update
sudo apt install docker-ce


2) проверим что демон-процесс запущен и добавлен в автозапуск:
sudo systemctl status docker
![](https://github.com/albertiger/devops-netology/blob/780a729414a85c862576123edeea8870292e619d/less5.2/z4-1.JPG)

3) Проверим запущенный процесс:
vagrant@vagrant:~$ ps -A | grep docker
  21154 ?        00:00:00 dockerd
![](https://github.com/albertiger/devops-netology/blob/780a729414a85c862576123edeea8870292e619d/less5.2/z4-2.JPG)
