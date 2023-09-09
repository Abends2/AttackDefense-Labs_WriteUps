# AttackDefense: Vulnerable FTP Server

---

Instructions: 

1. This lab is dedicated to you! No other users are on this network :)
2. Once you start the lab, you will have access to a root terminal of a Kali instance
3. Your Kali has an interface with IP address 192.X.Y.Z. Run "ip addr" to know the values of X and Y.
4. The target server should be located at the IP address 192.X.Y.3.
5. Do not attack the gateway located at IP address 192.X.Y.1
6. postgresql is not running by default so Metasploit may give you an error about this when starting

---

Сетевые адаптеры нашей Kali Linux:

![ScreenShot](screenshots/1.png)

Для начала проводим сканирование подсети 192.239.173.0/24 на наличие хостов:

```sh
nmap -n -PE 192.239.173.0/24
```

![ScreenShot](screenshots/2.png)

Сканируем хост 192.239.173.3:

```sh
nmap -sC -sV 192.239.173.3
```

![ScreenShot](screenshots/3.png)

Более детально сканируем FTP-сервис:

![ScreenShot](screenshots/4.png)

Таким образом, узнаем, что служба уязвима, поэтому дальше переходим в **Metasploit** и ищем эксплойты на версию **vsftpd 2.3.4**:

![ScreenShot](screenshots/5.png)

Опции:

![ScreenShot](screenshots/6.png)

Устанавливаем параметр RHOSTS - указываем IP жертвы:

![ScreenShot](screenshots/7.png)

Активируем и получаем шелл от рута:

![ScreenShot](screenshots/8.png)
