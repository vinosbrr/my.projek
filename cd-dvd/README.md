## CD/DVD ISO
A setup script created by Vinosbrr, designed to automate the process of using CD/DVD ISO files within a Debian 9-based virtual machine environment. This project is experimental and intended for educational or testing purposes only.
 
## What is a CD/DVD ISO?
A CD/DVD ISO is an image file archive that contains an exact copy of the data and file structure found on a physical CD or DVD. These files typically have a .iso extension and are widely used for distributing operating systems, software installation packages, or bootable media.

Core components of a Web server:
- Bootloader: Enables the ISO to boot a system when mounted or burned to physical media.
- Installer File System: Contains the operating system or software package to be installed.
- Checksum: A validation tool used to verify the integrity of the ISO file.
- Mounting Tools: Software or built-in OS features that treat an ISO file as if it were a physical CD/DVD.
- Virtual Machine (VM): A commonly used environment for ISO deployment, allowing OS installation without needing physical hardware.
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
- DVD ISO 1,2,3 (Cdrom add) 
- Network (IPv4)

---
##  Configuration

---
###  Konfigurasi CD/DVD <<
[ 1.1 Update Repository dan masukkan DVD ]
```bash
apt-cdrom add
```
Masukkan Dvd kalian bertahap DVD 2 lalu enter, ulangi diatas, sampai dvd 3.
![tes](images/dvd.png)
```bash
nano /etc/apt/sources.list
```
Selanjutnya jika berhasil akan muncul seperti gambar berikut
![tes](images/list.png)

> © Developed by Vinosbrr
---
### Connection Options
- Support all DVD
- Support VMware

---
### Features 
- Utilizes Debian 9 CD/DVD ISO files for offline package installation
- Allows mounting of multiple ISO discs (DVD 1, 2, and 3) to access complete package repositories
- Suitable for environments without internet access
- Easy to adapt for automated setups using mounted ISO media

### Requirements
- CD/DVD ISO files for Debian 9 (discs 1, 2, and 3)
- CD/DVD drive or virtual optical drive (for mounting ISOs in VM or physical machine)
- System configured to mount ISO as local repository (e.g., via /etc/apt/sources.list)
- Basic understanding of mounting ISO files and using Debian package tools (apt, dpkg)

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




