# MAIL SERVER

the repository here is My Project, experiments and assignments from school 
## Information



<div align="center">
<a href="https://github.com/vinosbrr/Sbrr-Bot/watchers"><img title="Watchers" src="https://img.shields.io/github/watchers/vinosbrr/Sbrr-Bot?label=Watchers&color=green&style=flat-square"></a>
<a href="https://github.com/vinosbrr/Sbrr-Bot/network/members"><img title="Forks" src="https://img.shields.io/github/forks/vinosbrr/Sbrr-Bot?label=Forks&color=blue&style=flat-square"></a>
<a href="https://github.com/vinosbrr/Sbrr-Bot/stargazers"><img title="Stars" src="https://img.shields.io/github/stars/vinosbrr/Sbrr-Bot?label=Stars&color=yellow&style=flat-square"></a>
<a href="https://github.com/vinosbrr/Sbrr-Bot/issues"><img title="Issues" src="https://img.shields.io/github/issues/vinosbrr/Sbrr-Bot?label=Issues&color=success&style=flat-square"></a>
<a href="https://github.com/vinosbrr/Sbrr-Bot/issues?q=is%3Aissue+is%3Aclosed"><img title="Issues" src="https://img.shields.io/github/issues-closed/vinosbrr/Sbrr-Bot?label=Issues&color=red&style=flat-square"></a>
<a href="https://github.com/vinosbrr/Sbrr-Bot/pulls"><img title="Pull Request" src="https://img.shields.io/github/issues-pr/vinosbrr/Sbrr-Bot?label=PullRequest&color=success&style=flat-square"></a>
<a href="https://github.com/vinosbrr/Sbrr-Bot/pulls?q=is%3Apr+is%3Aclosed"><img title="Pull Request" src="https://img.shields.io/github/issues-pr-closed/vinosbrr/Sbrr-Bot?label=PullRequest&color=red&style=flat-square"></a>
</div>



This script was developed by [Vinosbrr](https://github.com/vinosbrr) using a Virtual Machine environment with the Debian 9 ISO and the "brain" library. It is currently an experimental project and may include unexpected behavior. Users are encouraged to test and explore its features, but it is not recommended for use in production environments.

If you encounter persistent issues, feel free to contact the developer. Contributions, suggestions, and improvements are welcome. Please make sure to review the license before using or modifying this script. ~ By Vinosbrr


## Contributor
- [Vinosbrr](https://github.com/vinosbrr) (Created)


#### Join Group
[![Grup WhatsApp](https://img.shields.io/badge/WhatsApp%20Group-25D366?style=for-the-badge&logo=whatsapp&logoColor=white)](https://chat.whatsapp.com/KZmCzNMege942CH7qa7176) 


---
## For Windows/VPS/RDP User
* Download And Install Git [`Click Here`](https://git-scm.com/downloads)

```bash
git clone https://github.com/vinosbrr/source-code-python
cd source-code-python 
```

---
## For Termux/Ubuntu/SSH User

```bash
pkg update && pkg upgrade
pkg install python
pkg install git
git clone https://github.com/vinosbrr/source-code-python
cd source-code-python
```

---
[ RECOMMENDED INSTALL ON VIRTUAL MACHINE ]

```bash
Debian 9 DVD 1,2,3.ISO
```

---
### Preparation All Packages Before 
- DVD 1,2,3 (Cdrom add) 
- Network (IPv4)
- DNS Server (Bind9)


---
## Postfix and Dovecot Configuration
###  Konfigurasi Postfix <<
[ 1.1 Update Repository dan install Package Postfix ]

```bash
apt update
apt install postfix dovecot-imapd dovecot-pop3d
```
🫡
[ 1.2 Setelah Installasi edit file ]
```bash
nano /etc/postfix/main.cf
```
```bash
....
inet_interfaces = all
inet_protocols = all

#tambahkan baris berikut pada baris paling bawah
home_mailbox = Maildir/
```
[ 1.3 Buat mail directory di directory /etc/skel dan masukkan perintah ]
```bash
cd /etc/skel
maildirmake.dovecot /etc/skel/Maildir
dpkg-reconfigure postfix
```
🫡
[ 1.4 Restart Postfix ]
```bash
systemctl restart postfix
```
###  Konfigurasi Dovecot >>
[ 2.1 Edit file konfigurasi /etc/dovecot/dovecot.conf & Uncomment pada baris ]
```bash
nano /etc/dovecot/dovecot.conf
...
# If you want to specify non-default ports or anything more complex,
# edit conf.d/master.conf.
listen = *       # Uncomment baris ini
......
```
[ 2.2 Edit file konfigurasi /etc/dovecot/conf.d/10-auth.conf & Uncomment, yes = no ]
```bash
nano /etc/dovecot.conf/conf.d/10-auth.conf
...
# connection is considered secure and plaintext authentication is allowed.
# See also ssl=required setting.
disable_plaintext_auth = no     # Uncomment baris ini, ganti yes ke no
...
```
[ 2.3 Edit file konfigurasi /etc/dovecot/conf.d/10-mail.conf & Uncomment, Comment ]
```bash
nano /etc/dovecot.conf/conf.d/10-mail.conf
...
mail_location = maildir:~/Maildir       # Uncomment baris ini
...
...
# mail_location = mbox:~/mail:INBOX=/var/mail/%u   # Beri comment baris berikut
...
```
[ 2.4 Restart Dovecot ]
```bash
systemctl restart dovecot
cd
```

---
### Menambahkan user Email 
```bash
adduser saya
adduser dia
```

---
### Restart Postfix dan Dovecot
```bash
systemctl restart postfix dovecot
```

---
### Testing Postfix dan Dovecot menggunakan Telnet
```bash
apt install telnet 
```
```bash
telnet mail.contoh.com 25
```
```bash
Trying 192.168.99.1...
Connected to mail.contoh.com.
Escape character is '^]'.
220 debian ESMTP Postfix (Debian/GNU)
```
```bash
mail from: satu@mail.contoh.com
```
```bash
250 2.1.0 Ok
```
```bash
rcpt to: dua@mail.contoh.com
```
```bash
250 2.1.5 Ok
```
```bash
data
```
```bash
354 End data with <CR><LF>.<CR><LF>
```
```bash
Subject: Testing
Hello Pakkk!
.
```
```bash
250 2.0.0 Ok: queued as 7DEAD11DF
```
```bash
quit
```
```bash
221 2.0.0 Bye
Connection closed by foreign host.
```
---
Melihat pesan menggunakan perintah telnet <nama domain> <port>. 
Login user menggunakan user <nama user>. 
Dan masukkan password menggunakan pass <password>. 
Untuk melihat list pesan yang diterima menggunakan perintah list. 
Dan untuk membuka pesan yang diterima menggunakan perintah retr <nomer pesan>.<br> Perintah quit untuk keluar dari telnet.

```bash
Trying 192.168.99.1...
Connected to mail.contoh.com.
Escape character is '^]'.
+OK Dovecot (Debian) ready.
user dua
+OK
pass 0909
+OK Logged in.
list
+OK 1 messages:
1 436
.
retr 1
+OK 436 octets
Return-Path: <satu@mail.contoh.com>
X-Original-To: dua@mail.contoh.com
Delivered-To: dua@mail.contoh.com
Received: from unknown (unknown [192.168.99.1])
	by debian (Postfix) with SMTP id 7DEAD11DF
	for <dua@mail.contoh.com>; Sun,  20 Apr 2025 16:28:48 +0700 (WIB)
Subject: Testing
Message-Id: <20250420174142.7DEAD11DF@debian>
Date: Sun,  20 Apr 2025 16:28:48 +0700 (WIB)
From: satu@mail.contoh.com

Hello Pakkk!
.
quit
+OK Logging out.
Connection closed by foreign host.
```
---
### Konfigurasi Roundcube
[ 3.1 Install MariaDB dan Roundcube ]
```bash
apt install mariadb-server roundcube
```
🫡
[ 3.2 Edit file /etc/roundcube/config.inc.php. isi sesuaikan berikut ]
```bash
nano /etc/roundcube/config.inc.php.
...
// For example %n = mail.domain.tld, %t = domain.tld
$config['default_host'] = 'mail.contoh.com';
...
```
```bash
...
// For example %n = mail.domain.tld, %t = domain.tld
$config['smtp_server'] = 'mail.contoh.com';
...
```
```bash
...
// SMTP port. Use 25 for cleartext, 465 for Implicit TLS, or 587 for STARTTLS (default)
$config['smtp_port'] = 25;
...
```
```bash
...
// will use the current username for login
$config['smtp_user'] = '';
...
```
```bash
...
// will use the current user's password for login
$config['smtp_pass'] = '';
...
```
[ 3.3 Configure ulang ( langkah ini bisa dilewati )]
```bash
dpkg-reconfigure roundcube-core
```
🫡
[ 3.3 Edit file /etc/apache2/apache2.conf dan konfigurasi ]
```bash
nano /etc/apache2/apache2.conf
...
#tambahkan baris paling bawah
Include /etc/roundcube/apache.conf
```
[ 3.4 Masuk directory dan tambahkan file ]
```bash
cd /etc/apache2/sites-available
touch mail.conf
nano mail.conf
```
```bash
<VirtualHost *:80>
    ServerName mail.contoh.local
    DocumentRoot /usr/share/roundcube
</VirtualHost>
```
[ 3.5 Disable config default dan enable mail config ]
```bash
a2dissite 000-default.conf
a2ensite mail.conf
```
[ 3.6 Restart Apache2 ]
```bash
systemctl restart apache2
```
---
### Testing
Selanjutnya buka web browser pada sisi client dan masukkan domain dari mail server, maka akan muncul interface dari roundcube. Lalu login menggunakan salah satu user yang telah dibuat.


---
### Connection Options
- Support Telnet
- Support Mariadb
- Support Roundcube

---
### Features Script
| Script   | Kasir | Group | Search | Download | Tools | Ai | Game | Fun | Owner |
| -------- | ----- | ----- | ------ | -------- | ----- | -- | ---- | --- | ----- |
| Work     |  ✅   |   ✅  |   ✅   |    ✅    |  ✅   | ✅ |  ✅  | ✅  |  ✅   |

---
License: [MIT](https://choosealicense.com/licenses/mit/)

#### Support Me
- [Instagram](https://www.instagram.com/vinosbrr?igsh=MWJ6dXU1eXdzdWcwbw==)

## Thanks to
| [![Vinosbrr](https://github.com/vinosbrr.png?size=100)](https://github.com/vinosbrr)
| --- | 
| [Vinosbrr](https://github.com/vinosbrr) |


