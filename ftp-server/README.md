## FTP SERVER
FTP SERVER
Skrip setup server FTP khusus yang dibuat oleh Vinosbrr, dirancang untuk mengotomatiskan konfigurasi lingkungan server FTP dasar di Debian 9 menggunakan mesin virtual. Proyek ini bersifat eksperimental dan ditujukan hanya untuk tujuan edukasi atau pengujian.
 
## What is a FTP Server?
FTP (File Transfer Protocol) adalah protokol jaringan standar yang digunakan untuk mentransfer file antara komputer client dan server melalui jaringan TCP/IP seperti internet. Server FTP memungkinkan pengguna mengunggah dan mengunduh file ke dan dari server dengan kredensial tertentu.

Komponen inti dari server FTP:
- vsftpd: Salah satu perangkat lunak FTP server yang paling aman dan banyak digunakan dalam sistem berbasis Unix/Linux.
- Direktori Home dan Konfigurasi User: Tempat penyimpanan file yang diakses oleh user FTP, dapat disesuaikan untuk pengguna anonim maupun autentik.
- Firewall dan Port: FTP menggunakan port 21 untuk koneksi kontrol dan port dinamis untuk transfer data aktif/pasif.
- Mode Aktif dan Pasif:
  - Aktif: Server menghubungi client untuk mentransfer data.
  - Pasif: Client yang membuka koneksi ke server untuk transfer data—mode ini lebih kompatibel dengan firewall modern.

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
- Putty, Filezilla, Winscp

---
## ProFTPD Configuration
Sebelum menginstal FTP server, siapkan direktori dan akun pengguna yang akan digunakan. Pada contoh ini, direktori /home/ftpuser/ digunakan dan akun dikonfigurasi secara lokal. Server FTP menggunakan ProFTPD karena fleksibel dan mudah dikonfigurasi, baik untuk akses anonim maupun pengguna autentikasi.

---
###  Konfigurasi proftpd <<
[ 1.1 Update Repository dan install Package proftpd ]
```bash
apt update
apt install proftpd
```

[ 1.2 Setelah Installasi masuk directory /etc/bind dan edit file proftpd.conf ]

```bash
cd /etc/proftpd
ls
nano proftpd.conf
```
proftpd.conf adalah bagian utama dari konfigurasi ProFTPD yang digunakan untuk mengatur perilaku server FTP. Di dalam file ini, kita mendefinisikan berbagai parameter seperti port yang digunakan, direktori root pengguna, jenis autentikasi, serta opsi keamanan dan logging. File ini bersifat modular dan mudah disesuaikan untuk berbagai kebutuhan, baik untuk akses lokal, pengguna virtual, maupun akses anonim.

![NCL](images/ncl.png)
[ 1.3 Setelah masuk  file proftpd.conf ]
Unncomment pada bagian DefaultRoot  menjadi seperti ini.
```bash
# Use this to jail all users in their homes
DefaultRoot                     ~  
```
Scroll kebawah.. Unncomment pada bagian anonymous dan user, Hapus " ~ " lalu tambahkan /home/ dan ganti ftp = usermu. Seperti berikut ini.  
```bash
# A basic anonymous configuration, no upload directories.

 <Anonymous    /home/usermu>
  User                usermu
```
Scroll kebawah.. Unncomment pada bagian anonymous
```bash
#  # </Directory>
#
 </Anonymous>
```
[ 1.4 Keluar directory dan buat user "usermu" ]
Pada baian ini tambahkan user masukkan password saja, lalu enter hingga selesai.
```bash
cd
adduser usermu
```

[ 1.5 Masuk ke user dan coba buat file nano testing.txt ]
```bash
cd /home
ls
cd usermu
nano testing.txt
```
[ 1.6 Setelah masuk coba isikan seperti ini  ]
![tes](images/tes.png)

File testing.txt digunakan untuk bahan menguji apakah nanti file ini bisa di akeses dan melihat tampilannya.

[ 1.7 Berikan izin dan akses seperti ini ]
```bash
chmod 777 /home/usermu
```
Command ini digunakan untuk mengizinkan user group dan other, supaya bisa diotak atik.

[ 1.4 Restart proftpd ]
```bash
systemctl restart proftpd
cd
```

### Testing proftpd menggunakan FileZilla
1. Buka FileZilla.
2. Di bagian atas, kamu akan melihat kolom untuk mengonfigurasi Host, Username, Password, dan Port.
 - Host: Masukkan IP address atau hostname server ProFTPD yang ingin kamu hubungkan misalnya = 192.168.99.1
 - Username: Masukkan username yang telah terdaftar di server FTP ProFTPD. = usermu
 - Password: Masukkan password untuk username tersebut. = 1
 - Port: Gunakan port 21 untuk koneksi FTP standar.
5. Setelah semua informasi terisi, klik tombol Quickconnect.
Selanjutnya jika berhasil akan muncul seperti gambar berikut

> © Developed by Vinosbrr
---
### Connection Options
- Support putty
- Support FileZilla
- Support winscp

---
### Features 
- Automates FTP server installation steps
- Configures essential services (ProFTPD, firewall rules, etc.)
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



