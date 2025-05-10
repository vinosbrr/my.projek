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

File db.domain digunakan untuk menerjemahkan nama domain menjadi alamat IP. Di dalam file ini, terdapat beberapa record penting. Record SOA (Start of Authority) berisi informasi utama tentang zona, seperti nama domain utama dan alamat email administrator. Record NS (Nameserver) menunjukkan server DNS yang mengelola domain tersebut. Record A (Address) memetakan subdomain seperti www atau mail ke alamat IP tertentu. Selain itu, terdapat juga record MX (Mail Exchange) yang menunjukkan server email untuk domain tersebut.
![domain](images/d.png)
```bash
nano db.192
```
file db.ip digunakan untuk menerjemahkan alamat IP menjadi nama domain. File ini biasanya digunakan untuk keperluan reverse DNS lookup. Di dalam file ini, terdapat record PTR (Pointer) yang memetakan alamat IP tertentu ke nama domain yang sesuai. Misalnya, alamat IP 192.168.56.10 dapat dipetakan ke nama domain ns1.dns.contoh.com. Konfigurasi ini penting untuk memastikan bahwa server DNS dapat melakukan pencarian terbalik (reverse lookup) dengan benar.
![ip](images/192.png)


[ 1.4 Restart bind9 ]
```bash
systemctl restart bind9
cd
```

### Konfigurasi Resolv.conf
```bash
nano /etc/resolv.conf
```
```bash
search contoh.com
nameserver 192.168.99.1
```

### Testing bind9 menggunakan dnsutils
Uji coba ​bind9 dengan nslookup, dnsutils adalah kumpulan utilitas baris perintah di sistem operasi berbasis Linux yang digunakan untuk melakukan query dan mendiagnosis masalah terkait Domain Name System (DNS). Paket ini sering terinstal secara default pada distribusi seperti Debian dan Ubuntu
```bash
apt install dnsutils
nslookup contoh.com
nslookup mail.contoh.com
nslookup 192.168.99.1 
```
Selanjutnya jika berhasil akan muncul seperti gambar berikut
![tes](images/ns.png)

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



