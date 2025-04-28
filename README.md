# Домашнее задание к занятию «Уязвимости и атаки на информационные системы»
#### Грибанов Антон. FOPS-31

### Задание 1

Скачайте и установите виртуальную машину Metasploitable: https://sourceforge.net/projects/metasploitable/.

Это типовая ОС для экспериментов в области информационной безопасности, с которой следует начать при анализе уязвимостей.

Просканируйте эту виртуальную машину, используя **nmap**.

Попробуйте найти уязвимости, которым подвержена эта виртуальная машина.

Сами уязвимости можно поискать на сайте https://www.exploit-db.com/.

Для этого нужно в поиске ввести название сетевой службы, обнаруженной на атакуемой машине, и выбрать подходящие по версии уязвимости.

Ответьте на следующие вопросы:

- Какие сетевые службы в ней разрешены?
- Какие уязвимости были вами обнаружены? (список со ссылками: достаточно трёх уязвимостей)
  
*Приведите ответ в свободной форме.*  

#### Решение:

   1. Разворачиваем машину:

![13-01](https://github.com/Qshar1408/13-01/blob/main/img/hw_13_01_001.png)

   2. Сканируем машину на предмет уязвимостей:

```bash
nmap -sSV 192.168.2.143 # инфомация по открытым TCP портам (TCP SYN)
```
![13-01](https://github.com/Qshar1408/13-01/blob/main/img/hw_13_01_002.png)

```bash
nmap -sTV 192.168.2.143 # инфомация по открытым TCP портам (TCP Connect)
```
![13-01](https://github.com/Qshar1408/13-01/blob/main/img/hw_13_01_003.png)

```bash
nmap -sV 192.168.2.143 # инфомация по всем открытым TCP портам
```
![13-01](https://github.com/Qshar1408/13-01/blob/main/img/hw_13_01_004.png)

```bash
nmap -A 192.168.2.143 # агресивный режим - инфомация по всем открытым TCP портам
```
![13-01](https://github.com/Qshar1408/13-01/blob/main/img/hw_13_01_005.png)
![13-01](https://github.com/Qshar1408/13-01/blob/main/img/hw_13_01_006.png)
![13-01](https://github.com/Qshar1408/13-01/blob/main/img/hw_13_01_007.png)

   3. Описание уязвимостей:
- vsftpd 2.3.4: [Backdoor Command Execution (Metasploit)](https://www.exploit-db.com/exploits/17491)
- MySQL 5.0.x: [Single Row SubSelect Remote Denial of Service](https://www.exploit-db.com/exploits/29724)
- UnrealIRCd 3.2.8.1: [Backdoor Command Execution (Metasploit)](https://www.exploit-db.com/exploits/16922)

### Задание 2

Проведите сканирование Metasploitable в режимах SYN, FIN, Xmas, UDP.
