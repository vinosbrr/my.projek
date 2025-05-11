## REMOTE SERVER (SSH)
Skrip setup server SSH khusus yang dibuat oleh Vinosbrr, dirancang untuk mengotomatiskan konfigurasi lingkungan server SSH dasar di Debian 9 menggunakan mesin virtual. Proyek ini bersifat eksperimental dan ditujukan hanya untuk tujuan edukasi atau pengujian.

## What is a SSH?
SSH (Secure Shell) adalah protokol jaringan yang digunakan untuk mengakses dan mengelola server atau perangkat lain secara remote dan aman melalui jaringan. SSH menggantikan telnet dan protokol lain yang kurang aman dengan menyediakan enkripsi untuk sesi yang terhubung.

Komponen inti dari server FTP:
- OpenSSH: Salah satu perangkat lunak server SSH yang paling banyak digunakan di sistem berbasis Unix/Linux. OpenSSH menyediakan SSH server dan SSH client yang memungkinkan pengguna untuk masuk ke server dari jarak jauh dan menjalankan perintah melalui terminal.
- Direktori Home dan Konfigurasi User: Setiap pengguna yang mengakses server SSH biasanya memiliki direktori home di server, yang 
berfungsi sebagai tempat penyimpanan data dan konfigurasi pribadi.
- Firewall dan Port: SSH menggunakan port 22 untuk koneksi kontrol, di mana koneksi yang aman dilakukan dengan menggunakan kunci publik dan privat untuk autentikasi.

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
> © Developed by Vinosbrr 2025

## Contributor
- [Vinosbrr](https://github.com/vinosbrr) (Developer)


---
## Disclaimer
[ RECOMMENDED INSTALL ON VIRTUAL MACHINE ]
This project is provided as-is and is still in an experimental phase. Not recommended for production use. For questions, feedback, or bug reports, please contact the developer.
> © Developed by Vinosbrr 2025
```bash
Debian 9 DVD 1,2,3.ISO
```

---
### Preparation All Packages Before 
- DVD 1,2,3 (Cdrom add) 
- Network (IPv4)
- Putty

---
## ProFTPD Configuration
Sebelum menggunakan server SSH, pastikan kamu telah menyiapkan akun pengguna dan direktori home yang sesuai. Pada contoh ini, direktori /home/sshuser/ digunakan, dan akun dikonfigurasi secara lokal. Server SSH menggunakan OpenSSH karena fleksibilitas dan keamanannya dalam mengelola koneksi remote, baik untuk akses administrator maupun pengguna terbatas.

---
###  Konfigurasi proftpd <<
[ 1.1 Update Repository dan install Package proftpd ]
```bash
apt update
apt install ssh
```

[ 1.2 Setelah Installasi masuk directory /etc/ssh dan edit file sshd_config ]

```bash
cd /etc/ssh
ls
nano sshd_config
```
File sshd_config merupakan komponen inti dari konfigurasi server SSH (OpenSSH) yang digunakan untuk mengatur perilaku layanan SSH. Di dalam file ini, kita dapat mendefinisikan berbagai parameter penting seperti port yang digunakan, izin akses pengguna, metode autentikasi, serta berbagai opsi keamanan dan logging.

![NCL](images/ncl.png)
[ 1.3 Setelah masuk  file sshd_config ]
Unncomment pada bagian Port 22  menjadi seperti ini.
```bash
Port 22
# Address Family any
# ListenAddress 0.0.0.0
# ListenAddress ::
```
Scroll kebawah.. Unncomment pada bagian PermitRoootLogin dan ganti prohibit-password = yes Seperti berikut ini.  
```bash
# LoginGraceTime 2m
PermitRootLogin yes
# StrictModes yes
```
[ 1.4 Restart proftpd ]
```bash
systemctl restart proftpd
cd
```



### Testing proftpd menggunakan FileZilla
1. Buka PuTTY di komputermu.
2. Di jendela utama PuTTY, kamu akan melihat kolom konfigurasi untuk mengatur koneksi SSH:
  - Host Name (or IP address): Masukkan IP address atau hostname server SSH yang ingin kamu hubungkan.
    - Contoh: 192.168.99.1
    - Port: Gunakan port 22 untuk koneksi SSH standar (atau port khusus jika dikonfigurasi berbeda).
    - Connection Type: Pilih opsi SSH (harus dicentang).
3. Setelah semua informasi terisi, klik tombol Open.
4. Jika ini adalah koneksi pertama ke server tersebut, akan muncul peringatan keamanan SSH key — klik Yes untuk melanjutkan.
Jendela terminal akan terbuka, lalu akan muncul prompt:
``` bash
login as:        # Masukkan username yang telah terdaftar di server SSH. Contoh: usermu
password:        # Lalu masukkan password saat diminta. Contoh: 1
```
Jika koneksi berhasil, kamu akan masuk ke shell terminal server tersebut dan dapat mulai menjalankan perintah Linux secara remote.
Selanjutnya jika berhasil akan muncul seperti gambar berikut.

> © Developed by Vinosbrr
---
### Connection Options
- Support putty
- Support FileZilla
- Support winscp

---
### Features 
- Automates FTP server installation steps
- Configures essential services (ssh, firewall rules, etc.)
- Uses Debian 9 base system for compatibility
- Lightweight and easy to modify

### Requirements
- Virtual Machine (VMware/VirtualBox)
- Debian 9 ISO installed
- Root access or sudo privileges
- Basic knowledge of Linux and shell scripting
  
---
License: [MIT License](../LICENSE)

#### Support Me
- [Instagram](https://www.instagram.com/vinosbrr?igsh=MWJ6dXU1eXdzdWcwbw==)
- [Group WhatsApp](https://chat.whatsapp.com/KZmCzNMege942CH7qa7176)
- [Youtube](https://youtube.com/@wongesbrr?si=RQbf8_FRIju8ACCU)


## Thanks to
| [![Vinosbrr](https://github.com/vinosbrr.png?size=100)](https://github.com/vinosbrr)
| --- | 
| [Vinosbrr](https://github.com/vinosbrr) |
> © Developed by Vinosbrr 2025




