# Jobsheet 7

| Nama | NIM | Kelas |
| :--- | :--- | :--- |
| Ibni Andarta | 254107020258 | TI-1G |

---

## Praktikum 6.1 
### Lihat shell login dan shell aktif saat ini
Output : 
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ echo " Shell login : $SHELL " 
 Shell login : /bin/bash 
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ echo " Shell aktif : $0"
 Shell aktif : /usr/bin/bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ bash -- version | head -n 1
bash: version: No such file or directory
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ bash --version | head -n 1
GNU bash, version 5.2.37(1)-release (aarch64-unknown-linux-gnu)
```

### Lihat proses shell yang sedang berjalan
Output : 
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ echo $$
3213
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ ps -p $$ -o pid,ppid,args=
    PID    PPID 
   3213    3173 /usr/bin/bash
```

### Buat workspace praktikum
Output : 
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ mkdir -p {bin,backup,logs,sampel,ruang-nama}
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ pwd
/home/ibennn/praktikum-os/week07
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ ls
backup  bin  logs  ruang-nama  sampel
```

### Buat beberapa file contoh yang akan dipakai pada praktikum berikutnya
Output :
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ touch sampel/app.conf
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ touch logs/app-01.log logs/app-02.log logs/app-03.log
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ touch sampel/catatan-a.txt sampel/catatan-b.txt
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ touch sampel/backup-01.tar sampel/backup-02.tar
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ touch sampel/laporan-harian.log sampel/laporan-mingguan.log sampel/laporan-bulanan.log
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ touch "ruang-nama/laporan server april.txt"
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ touch "ruang-nama/backup [mingguan] server.conf"
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ ls -R
.:
backup  bin  logs  ruang-nama  sampel

./backup:

./bin:

./logs:
app-01.log  app-02.log  app-03.log

./ruang-nama:
'backup [mingguan] server.conf'  'laporan server april.txt'

./sampel:
app.conf  backup-01.tar  backup-02.tar  catatan-a.txt  catatan-b.txt  laporan-bulanan.log  laporan-harian.log  laporan-mingguan.log
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ 
```

---
## Praktikum 6.2
### Simpan informasi sesi terminal ke file laporan
Output : 
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ {
  echo "=== RINGKASAN SESI BASH ==="
  date
  echo "User         : $(whoami)"
  echo "Hostname     : $(hostname)"
  echo "Shell login  : $SHELL"
  echo "Shell aktif  : $0"
  echo "PID shell    : $$"
  echo "Direktori    : $(pwd)"
} | tee session-info.txt
=== RINGKASAN SESI BASH ===
Sat Apr 11 11:59:14 WIB 2026
User         : ibennn
Hostname     : ibennn-QEMU-Virtual-Machine
Shell login  : /bin/bash
Shell aktif  : /usr/bin/bash
PID shell    : 3213
Direktori    : /home/ibennn/praktikum-os/week07
```

### Verifikasi isi file laporan
Output : 
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ cat session-info.txt
=== RINGKASAN SESI BASH ===
Sat Apr 11 11:59:14 WIB 2026
User         : ibennn
Hostname     : ibennn-QEMU-Virtual-Machine
Shell login  : /bin/bash
Shell aktif  : /usr/bin/bash
PID shell    : 3213
Direktori    : /home/ibennn/praktikum-os/week07
```
---
## Praktikum 6.3
### Lihat file konfigurasi Bash pada home directory
Output : 
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ ls -la ~ | grep -E 'bashrc|bash_profile|profile'
-rw-r--r--  1 ibennn ibennn 3771 Sep  8  2025 .bashrc
-rw-r--r--  1 ibennn ibennn  807 Sep  8  2025 .profile
```
### Buat backup .bashrc
Output : 
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ cp ~/.bashrc ~/.bashrc.bak-praktikum
```
### Tambahkan blok konfigurasi praktikum
Output : 
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ cat << 'EOF' >> ~/.bashrc
export PRAKTIKUM_BASH_DIR="$HOME/praktikum-os/week07"
export EDITOR=nano
EOF
```
### Terapkan konfigurasi tanpa logout
Output :
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ source ~/.bashrc
echo "$PRAKTIKUM_BASH_DIR"
echo "$EDITOR"
/home/ibennn/praktikum-os/week07
nano
```

---
## Praktikum 6.4 
### Backup .bash_profile jika sudah ada
Output :
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ [ -f ~/.bash_profile ] && cp ~/.bash_profile ~/.bash_profile.bak-praktikum
```

### Tambahkan konfigurasi login shell
Output :
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ cat << 'EOF' >> ~/.bash_profile
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi

echo "Login Bash pada $(date '+%F %T')" >> "$HOME/praktikum-os/week07/login-audit.log"
EOF
```

### Uji dengan membuka login shell baru
Output :
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ bash -l
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ tail -n 3 ~/praktikum-os/week07/login-audit.log
Login Bash pada 2026-04-11 12:11:32
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ exit
logout
```

---
## Praktikum 6.5
### Buat variabel lokal
Output :
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ KELAS_OS="Sistem Operasi A"
echo "$KELAS_OS"
Sistem Operasi A
```

### Buka subshell dan cek apakah variabel masih ada
Output :
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ bash
echo " $KELAS_OS "
exit
```

### Sekarang ubah menjadi environment variable
Output :
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ export KELAS_OS="Sistem Operasi A"
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ echo "$KELAS_OS"
Sistem Operasi A
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ exit
exit
```

### Lihat isi PATH dan lokasi beberapa perintah
Output :
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ echo "$PATH"
which bash
type ls
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin
/usr/bin/bash
ls is aliased to `ls --color=auto'
```

---
## Praktikum 6.6
### Pastikan direktori bin praktikum tersedia
Output :
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ mkdir -p ~/praktikum-os/week07/bin
```

### Tambahkan direktori tersebut ke PATH melalui .bashrc
Output :
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ cat << 'EOF' >> ~/.bashrc
export PATH="$HOME/praktikum-os/week07/bin:$PATH"
EOF

source ~/.bashrc
echo "$PATH"

/home/ibennn/praktikum-os/week07/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin:/snap/bin
```

### Buat script ringkasan sistem
Output :
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ cat << 'EOF' > ~/praktikum-os/week07/bin/ringkas-sistem
> echo "Hostname : $(hostname)"
echo "User     : $(whoami)"
echo "Uptime   : $(uptime -p)"
echo "Disk /   :"
df -h /
EOF
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ chmod +x ~/praktikum-os/week07/bin/ringkas-sistem
```

### Jalankan script dari direktori yang berbeda
Output :
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07$ cd ~
ringkas-sistem
Hostname : ibennn-QEMU-Virtual-Machine
User     : ibennn
Uptime   : up 11 hours, 19 minutes
Disk /   :
Filesystem      Size  Used Avail Use% Mounted on
/dev/vda2        24G   13G   11G  55% /
```

---
## Praktikum 6.7
### Tambahkan alias ke .bashrc
Output : 
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~$ cat << 'EOF' >> ~/.bashrc
alias ll='ls -lah --color=auto'
alias hist10='history | tail -n 10'
alias cdbashlab='cd $HOME/praktikum-os/week07'
EOF
source ~/.bashrc
```

### Uji alias
Output : 
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~$ ll
total 136K
-rw-r--r--  1 root   root      7 Feb 24 11:03 -
drwxr-x--- 21 ibennn ibennn 4.0K Apr 11 12:10 .
drwxr-xr-x  3 root   root   4.0K Feb 11 21:51 ..
-rw-------  1 ibennn ibennn 2.4K Apr 11 12:17 .bash_history
-rw-r--r--  1 ibennn ibennn  220 Sep  8  2025 .bash_logout
-rw-rw-r--  1 ibennn ibennn  133 Apr 11 12:10 .bash_profile
-rw-r--r--  1 ibennn ibennn 4.0K Apr 11 12:26 .bashrc
-rw-r--r--  1 ibennn ibennn 3.7K Apr 11 12:03 .bashrc.bak-praktikum
drwx------ 12 ibennn ibennn 4.0K Feb 22 20:13 .cache
drwx------ 18 ibennn ibennn 4.0K Mar  3 18:54 .config
drwx------  2 ibennn ibennn 4.0K Apr 11 11:45 .gnupg
drwx------  4 ibennn ibennn 4.0K Feb 11 21:51 .local
-rw-r--r--  1 ibennn ibennn  807 Sep  8  2025 .profile
drwx------  2 ibennn ibennn 4.0K Feb 11 21:51 .ssh
drwxrwxr-x  4 ibennn ibennn 4.0K Mar 11 10:28 A
drwxrwxr-x  3 ibennn ibennn 4.0K Mar 11 10:28 B
drwxrwxr-x  2 ibennn ibennn 4.0K Mar 11 10:28 C
drwxr-xr-x  2 ibennn ibennn 4.0K Feb 11 21:51 Desktop
drwxr-xr-x  2 ibennn ibennn 4.0K Feb 11 21:51 Documents
drwxr-xr-x  2 ibennn ibennn 4.0K Feb 11 21:51 Downloads
drwxr-xr-x  2 ibennn ibennn 4.0K Feb 11 21:51 Music
drwxr-xr-x  2 ibennn ibennn 4.0K Feb 11 21:51 Pictures
drwxr-xr-x  2 ibennn ibennn 4.0K Feb 11 21:51 Public
drwxr-xr-x  2 ibennn ibennn 4.0K Feb 11 21:51 Templates
drwxr-xr-x  2 ibennn ibennn 4.0K Feb 11 21:51 Videos
-rw-r--r--  1 root   root      7 Feb 24 11:03 conf
-rw-r--r--  1 root   root      7 Feb 24 11:03 d
-rw-r--r--  1 root   root      7 Feb 24 11:03 etc
-rw-r--r--  1 root   root      7 Feb 24 11:03 load
-rw-r--r--  1 root   root      7 Feb 24 11:03 loop
-rw-r--r--  1 root   root      7 Feb 24 11:03 modules
drwxrwxr-x  4 ibennn ibennn 4.0K Feb 24 08:23 neofetch
drwxrwxr-x  7 ibennn ibennn 4.0K Apr 11 11:48 praktikum-os
drwx------  4 ibennn ibennn 4.0K Feb 11 21:51 snap
ibennn@ibennn-QEMU-Virtual-Machine:~$ hist10

alias hist10='history | tail -n 10'

alias cdbashlab='cd $HOME/praktikum-os/week07'

EOF

  136  source ~/.bashrc
  137  ll
  138  hist10
```

---
## Praktikum 6.8
### Siapkan file konfigurasi contoh
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~$ echo "PORT=8080" > ~/praktikum-os/week07/sample-app.conf
ibennn@ibennn-QEMU-Virtual-Machine:~$ cat ~/praktikum-os/week07/sample-app.conf
PORT=8080
```

### Tambahkan fungsi ke .bashrc
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~$ cat << 'EOF' >> ~/.bashrc
backup_conf() {
    if [ $# -ne 1 ]; then
        echo "Usage: backup_conf <file>"
        return 1
    fi
    local src="$1"
    local dst="$HOME/praktikum-os/week07/backup"
    if [ ! -f "$src" ]; then
        echo "File tidak ditemukan: $src"
        return 2
    fi
    mkdir -p "$dst"
    cp -- "$src" "$dst/$(basename "$src").$(date +%F-%H%M%S).bak"
    echo "Backup selesai di: $dst"
}
EOF
source ~/.bashrc
```

### Uji fungsi
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~$ backup_conf ~/praktikum-os/week07/sample-app.conf
Backup selesai di: /home/ibennn/praktikum-os/week07/backup
ibennn@ibennn-QEMU-Virtual-Machine:~$ ls -lah ~/praktikum-os/week07/backup
total 12K
drwxrwxr-x 2 ibennn ibennn 4.0K Apr 11 12:32 .
drwxrwxr-x 7 ibennn ibennn 4.0K Apr 11 12:28 ..
-rw-rw-r-- 1 ibennn ibennn   10 Apr 11 12:32 sample-app.conf.2026-04-11-123234.bak
ibennn@ibennn-QEMU-Virtual-Machine:~$ type backup_conf
backup_conf is a function
backup_conf () 
{ 
    if [ $# -ne 1 ]; then
        echo "Usage: backup_conf <file>";
        return 1;
    fi;
    local src="$1";
    local dst="$HOME/praktikum-os/week07/backup";
    if [ ! -f "$src" ]; then
        echo "File tidak ditemukan: $src";
        return 2;
    fi;
    mkdir -p "$dst";
    cp -- "$src" "$dst/$(basename "$src").$(date +%F-%H%M%S).bak";
    echo "Backup selesai di: $dst"
}
```

---
## Praktikum 6.9
### Pastikan file contoh tersedia
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~$ cd ~/praktikum-os/week07/sampel
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07/sampel$ touch laporan-harian.log laporan-mingguan.log laporan-bulanan.log
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07/sampel$ ls
app.conf  backup-01.tar  backup-02.tar  catatan-a.txt  catatan-b.txt  laporan-bulanan.log  laporan-harian.log  laporan-mingguan.log
```

### Pastikan file contoh tersedia
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07/sampel$ cat laporan-
laporan-bulanan.log   laporan-harian.log    laporan-mingguan.log  
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07/sampel$ cat laporan-harian.log 
```

### Jalankan beberapa perintah sederhana
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07/sampel$ pwd
/home/ibennn/praktikum-os/week07/sampel
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07/sampel$ ls -lah
total 8.0K
drwxrwxr-x 2 ibennn ibennn 4.0K Apr 11 11:54 .
drwxrwxr-x 7 ibennn ibennn 4.0K Apr 11 12:28 ..
-rw-rw-r-- 1 ibennn ibennn    0 Apr 11 11:53 app.conf
-rw-rw-r-- 1 ibennn ibennn    0 Apr 11 11:53 backup-01.tar
-rw-rw-r-- 1 ibennn ibennn    0 Apr 11 11:53 backup-02.tar
-rw-rw-r-- 1 ibennn ibennn    0 Apr 11 11:53 catatan-a.txt
-rw-rw-r-- 1 ibennn ibennn    0 Apr 11 11:53 catatan-b.txt
-rw-rw-r-- 1 ibennn ibennn    0 Apr 11 12:35 laporan-bulanan.log
-rw-rw-r-- 1 ibennn ibennn    0 Apr 11 12:35 laporan-harian.log
-rw-rw-r-- 1 ibennn ibennn    0 Apr 11 12:35 laporan-mingguan.log
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07/sampel$ date
Sat Apr 11 12:38:56 WIB 2026
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07/sampel$ whoami
ibennn
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07/sampel$ history | tail -n 10
  147  clear
  148  cd ~/praktikum-os/week07/sampel
  149  touch laporan-harian.log laporan-mingguan.log laporan-bulanan.log
  150  ls
  151  cat lap
  152  pwd
  153  ls -lah
  154  date
  155  whoami
  156  history | tail -n 10
```

---
## Praktikum 6.10
### Jalankan beberapa perintah diagnostik
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07/sampel$ df -h
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           677M  2.2M  675M   1% /run
/dev/vda2        24G   13G   11G  55% /
tmpfs           1.7G     0  1.7G   0% /dev/shm
efivarfs        256K   17K  240K   7% /sys/firmware/efi/efivars
tmpfs           5.0M  8.0K  5.0M   1% /run/lock
tmpfs           1.0M     0  1.0M   0% /run/credentials/systemd-journald.service
tmpfs           1.0M     0  1.0M   0% /run/credentials/systemd-resolved.service
/dev/vda1       1.1G  6.6M  1.1G   1% /boot/efi
tmpfs           1.7G  8.0K  1.7G   1% /tmp
tmpfs           1.0M     0  1.0M   0% /run/credentials/serial-getty@ttyAMA0.service
tmpfs           339M   92K  339M   1% /run/user/1000
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07/sampel$ free -h
               total        used        free      shared  buff/cache   available
Mem:           3.3Gi       1.4Gi        73Mi        95Mi       2.1Gi       1.9Gi
Swap:          3.8Gi       128Ki       3.8Gi
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07/sampel$ uptime
 12:40:37 up 11:37,  1 user,  load average: 0.08, 0.11, 0.04
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07/sampel$ ps aux | head
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.4  26264 15728 ?        Ss   01:03   0:05 /usr/lib/systemd/systemd --switched-root --system --deserialize=48 splash
root           2  0.0  0.0      0     0 ?        S    01:03   0:00 [kthreadd]
root           3  0.0  0.0      0     0 ?        S    01:03   0:00 [pool_workqueue_release]
root           4  0.0  0.0      0     0 ?        I<   01:03   0:00 [kworker/R-rcu_gp]
root           5  0.0  0.0      0     0 ?        I<   01:03   0:00 [kworker/R-sync_wq]
root           6  0.0  0.0      0     0 ?        I<   01:03   0:00 [kworker/R-kvfree_rcu_reclaim]
root           7  0.0  0.0      0     0 ?        I<   01:03   0:00 [kworker/R-slub_flushwq]
root           8  0.0  0.0      0     0 ?        I<   01:03   0:00 [kworker/R-netns]
root          11  0.0  0.0      0     0 ?        I<   01:03   0:00 [kworker/0:0H-events_highpri]
```

### Cari ulang perintah diagnostik dari history
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07/sampel$ history | grep -E 'df -h|free -h|uptime|ps aux'
   27  df -h
   28  free -h
echo "Uptime   : $(uptime -p)"
df -h /
  158  df -h
  159  free -h
  160  uptime
  161  ps aux | head
  162  history | grep -E 'df -h|free -h|uptime|ps aux'
```

### Jalankan ulang salah satu perintah berdasarkan nomor history
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07/sampel$ !158
df -h
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           677M  2.2M  675M   1% /run
/dev/vda2        24G   13G   11G  55% /
tmpfs           1.7G     0  1.7G   0% /dev/shm
efivarfs        256K   17K  240K   7% /sys/firmware/efi/efivars
tmpfs           5.0M  8.0K  5.0M   1% /run/lock
tmpfs           1.0M     0  1.0M   0% /run/credentials/systemd-journald.service
tmpfs           1.0M     0  1.0M   0% /run/credentials/systemd-resolved.service
/dev/vda1       1.1G  6.6M  1.1G   1% /boot/efi
tmpfs           1.7G  8.0K  1.7G   1% /tmp
tmpfs           1.0M     0  1.0M   0% /run/credentials/serial-getty@ttyAMA0.service
tmpfs           339M   92K  339M   1% /run/user/1000
```

### Simpan potongan history ke file dokumentasi
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07/sampel$ history | tail -n 20 > ~/praktikum-os/week07/diag-history.txt
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week07/sampel$ cat ~/praktikum-os/week07/diag-history.txt
  145  ls -lah ~/praktikum-os/week07/backup
  146  type backup_conf
  147  clear
  148  cd ~/praktikum-os/week07/sampel
  149  touch laporan-harian.log laporan-mingguan.log laporan-bulanan.log
  150  ls
  151  cat lap
  152  pwd
  153  ls -lah
  154  date
  155  whoami
  156  history | tail -n 10
  157  clear
  158  df -h
  159  free -h
  160  uptime
  161  ps aux | head
  162  history | grep -E 'df -h|free -h|uptime|ps aux'
  163  df -h
  164  history | tail -n 20 > ~/praktikum-os/week07/diag-history.txt
```




