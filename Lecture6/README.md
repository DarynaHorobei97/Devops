1. Встановити й налаштувати вебсервер Nginx через офіційний репозиторій.
Додати й видалити PPA-репозиторій для Nginx, а потім повернутися до офіційної версії 
пакета за допомогою ppa-purge.

У host_folder/task1.log знаходиться логування процесу виконання цього завдання
Або ось список команд:
sudo apt update
sudo apt install nginx
sudo systemctl status nginx
sudo add-apt-repository ppa:nginx/stable - додаємо PPA-репозиторій
sudo apt update
nginx -v
sudo apt upgrade nginx 
sudo add-apt-repository --remove ppa:nginx/stable - видаляємо PPA-репозиторій
sudo apt update
sudo apt install ppa-purge
sudo ppa-purge ppa:nginx/stable - повертаємося до офіційної версії

vagrant@private-server:~$ nginx -v
nginx version: nginx/1.24.0 (Ubuntu)


2. Написати й налаштувати власний systemd-сервіс для запуску простого скрипта 
(наприклад, скрипт, який пише поточну дату і час у файл щохвилини).

У host_folder/task2.log знаходиться логування процесу виконання цього завдання.
А також додаю скріни:
![l6_1](images/l6_1.png)
![image4](images/l6_2.png)
![image4](images/l6_3.png)
І результат:
![image4](images/l6_4.png)


3. Налаштувати брандмауер за допомогою UFW або iptables. Заборонити доступ до порту 22 (SSH) з певного IP, але дозволити з іншого IP. 
Налаштувати Fail2Ban для захисту від підбору паролів через SSH.
![image4](images/l6_6.png)
![image4](images/l6_7.png)
![image4](images/l6_8.png)