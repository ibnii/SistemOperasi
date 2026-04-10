# Jobsheet 4

Nama: Ibni Andarta  
NIM: 254107020258  
Kelas: TI-1G

---

## Percobaan 1 - Direktori

### Melihat Direktori HOME

**Code**

```bash
pwd
echo $HOME
```

**Output**

```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week02$ pwd
/home/ibennn/praktikum-os/week02
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week02$ echo $HOME
/home/ibennn
```

### Melihat direktori aktual dan parent direktori

**Code**

```bash
pwd
cd .
pwd
cd ..
pwd
cd
```

**Output**

```bash
ibennn@ibennn-QEMU-Virtual-Machine:~$ pwd
/home/ibennn
ibennn@ibennn-QEMU-Virtual-Machine:~$ cd .
ibennn@ibennn-QEMU-Virtual-Machine:~$ pwd
/home/ibennn
ibennn@ibennn-QEMU-Virtual-Machine:~$ cd ..
ibennn@ibennn-QEMU-Virtual-Machine:/home$ pwd
/home
ibennn@ibennn-QEMU-Virtual-Machine:/home$ cd
```

### Membuat satu direktori, lebih dari satu direktori atau sub direktori

**Code**

```bash
pwd
mkdir A B C A/D A/E B/F A/D/A
ls -l
ls -l A
ls -l A/D
```

**Output**

```bash
ibennn@ibennn-QEMU-Virtual-Machine:~$ pwd
/home/ibennn
ibennn@ibennn-QEMU-Virtual-Machine:~$ mkdir A B C A/D A/E B/F A/D/A
ibennn@ibennn-QEMU-Virtual-Machine:~$ ls -l
total 84
-rw-r--r-- 1 root   root      7 Feb 24 11:03 -
drwxrwxr-x 4 ibennn ibennn 4096 Mar 11 10:28 A
drwxrwxr-x 3 ibennn ibennn 4096 Mar 11 10:28 B
drwxrwxr-x 2 ibennn ibennn 4096 Mar 11 10:28 C
drwxr-xr-x 2 ibennn ibennn 4096 Feb 11 21:51 Desktop
drwxr-xr-x 2 ibennn ibennn 4096 Feb 11 21:51 Documents
drwxr-xr-x 2 ibennn ibennn 4096 Feb 11 21:51 Downloads
drwxr-xr-x 2 ibennn ibennn 4096 Feb 11 21:51 Music
drwxr-xr-x 2 ibennn ibennn 4096 Feb 11 21:51 Pictures
drwxr-xr-x 2 ibennn ibennn 4096 Feb 11 21:51 Public
drwxr-xr-x 2 ibennn ibennn 4096 Feb 11 21:51 Templates
drwxr-xr-x 2 ibennn ibennn 4096 Feb 11 21:51 Videos
-rw-r--r-- 1 root   root      7 Feb 24 11:03 conf
-rw-r--r-- 1 root   root      7 Feb 24 11:03 d
-rw-r--r-- 1 root   root      7 Feb 24 11:03 etc
-rw-r--r-- 1 root   root      7 Feb 24 11:03 load
-rw-r--r-- 1 root   root      7 Feb 24 11:03 loop
-rw-r--r-- 1 root   root      7 Feb 24 11:03 modules
drwxrwxr-x 4 ibennn ibennn 4096 Feb 24 08:23 neofetch
drwxrwxr-x 4 ibennn ibennn 4096 Mar  3 18:57 praktikum-os
drwx------ 4 ibennn ibennn 4096 Feb 11 21:51 snap
ibennn@ibennn-QEMU-Virtual-Machine:~$ ls -l A
total 8
drwxrwxr-x 3 ibennn ibennn 4096 Mar 11 10:28 D
drwxrwxr-x 2 ibennn ibennn 4096 Mar 11 10:28 E
ibennn@ibennn-QEMU-Virtual-Machine:~$ ls -l A/D
total 4
drwxrwxr-x 2 ibennn ibennn 4096 Mar 11 10:28 A
```

### Menghapus Direktori

**Code :**

```bash
rmdir B
ls -l B
rmdir B/F B
ls -l B
```

**Output :**

```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ rmdir B
rmdir: failed to remove 'B': Directory not empty
```

> _Error karena direktori tidak kosong_

```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ ls -l B
total 4
drwxrwxr-x 2 ibennn ibennn 4096 Mar 11 19:39 F
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ rmdir B/F B
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ ls -l B
ls: cannot access 'B': No such file or directory
```

> _Error terakhir dikarenakan direktori sudah dihapus_

### Navigasi Direktori

**Code**

```bash
pwd
ls -l
cd A
pwd
cd ..
pwd
cd /home/<user>/C
pwd
cd /<user>/C
pwd
```

**Output :**

```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ pwd
/home/ibennn/praktikum-os/week04
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ ls -1
A
C
hasil.txt
proses.txt
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ cd A
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04/A$ pwd
/home/ibennn/praktikum-os/week04/A
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04/A$ cd ..
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ pwd
/home/ibennn/praktikum-os/week04
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ cd /home/<user>/C
bash: user: No such file or directory
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ cd /home/ibennn/praktikum-os/week04/C
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04/C$ pwd
/home/ibennn/praktikum-os/week04/C
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04/C$ cd /ibennn/C
bash: cd: /ibennn/C: No such file or directory
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04/C$ pwd
/home/ibennn/praktikum-os/week04/C
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04/C$
```

> _Error dikarenakan folder yang dituju tidak ada_

---

## Percobaan 2 - Manipulasi file

### Perintah `cp` untuk mengkopi file atau seluruh direktori

**Code :**

```bash
cat > contoh Membuat sebuah file [Ctrl-d]
cp contoh contoh1
ls -l
cp contoh A
ls –l A
cp contoh contoh1 A/D
ls –l A/D
```

**Output :**

```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ cat > contoh
membuat sebuah file
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ ls
A  C  contoh  hasil.txt  proses.txt
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ cp contoh contoh1
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ ls -1
A
C
contoh
contoh1
hasil.txt
proses.txt
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ cp contoh A
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ ls -1 A
D
E
contoh
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ cp contoh contoh1 A/D
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ ls -1 A/D
A
contoh
contoh1
```

### Perintah `mv` untuk memindah file

**Code :**

```bash
mv contoh contoh2
ls -l
mv contoh1 contoh2 A/D
ls –l A/D
mv contoh contoh1 C
ls –l C

```

**Output :**
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ mv contoh contoh2
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ ls
A  C  contoh1  contoh2  hasil.txt  proses.txt
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ mv contoh1 contoh2 A/D
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ ls A/D
A  contoh  contoh1  contoh2
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ mv contoh contoh1 C
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ ls C
contoh1 contoh2
```

### Perintah `rm` untuk menghapus file

**Code :** 
```bash
rm contoh2 
ls -l 
rm –i contoh 
rm –rf A C 
ls -l
```

**Output :** 
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ ls
A  C  hasil.txt  proses.txt contoh contoh2
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ rm contoh2
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ ls
A  C  hasil.txt  proses.txt contoh
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ rm -i contoh
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ ls
A  C  hasil.txt  proses.txt
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ rm -rf A C
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ ls
hasil.txt  proses.txt
```


---
## Percobaan 3 - Symbolic link

### Membuat shortcut

**Code :** 
```bash
echo "Hallo apa khabar" > halo.txt 
ls -l 
ln halo.txt z 
ls -l 
cat z 
mkdir mydir 
ln z mydir/halo.juga 
cat mydir/halo.juga 
ln -s z bye.txt 
ls -l bye.txt 
cat bye.txt
```

**Output:**
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ echo "Hallo apa khabar" > halo.txt 
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ ls
halo.txt  hasil.txt  proses.txt
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ ln halo.txt z 
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ ls
halo.txt  hasil.txt  proses.txt  z
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ cat z
Hallo apa khabar
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ mkdir mydir
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ ln z mydir/halo.juga 
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ cat mydir/halo.juga 
Hallo apa khabar
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ ln -s z bye.txt
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ ls -l bye.txt 
lrwxrwxrwx 1 ibennn ibennn 1 Apr  9 03:14 bye.txt -> z
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ cat bye.txt
Hallo apa khabar
```

---

## Percobaan 4 - Melihat isi file

**Code :** 
```bash
ls –l 
file halo.txt 
file bye.txt
```

**Output:**
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ ls
bye.txt  halo.txt  hasil.txt  mydir  proses.txt  z
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ file halo.txt
halo.txt: ASCII text
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ file bye.txt
bye.txt: symbolic link to z
```

---

## Percobaan 5 - Mencari file

### Perintah `find`
**Code :**
```bash
find /home -name "*.txt" -print > myerror.txt 
cat myerror.txt 
find . -name "*.txt" -exec wc -l {} \;
```

**Output :** 
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ find /home -name "*.txt" -print > myerror.txt
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ cat myerror.txt
/home/ibennn/praktikum-os/week02/latihan.txt
/home/ibennn/praktikum-os/week02/config.txt
/home/ibennn/praktikum-os/week02/notes.txt
/home/ibennn/praktikum-os/week04/proses.txt
/home/ibennn/praktikum-os/week04/hasil.txt
/home/ibennn/praktikum-os/week04/bye.txt
/home/ibennn/praktikum-os/week04/halo.txt
/home/ibennn/praktikum-os/week04/myerror.txt
/home/ibennn/praktikum-os/week03/sorted-users.txt
/home/ibennn/praktikum-os/week03/config-files.txt
/home/ibennn/praktikum-os/week03/large-logs.txt
/home/ibennn/.cache/tracker3/files/last-crawl.txt
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ find . -name "*.txt" -exec wc -l {} \;
10 ./proses.txt
1 ./hasil.txt
1 ./bye.txt
1 ./halo.txt
12 ./myerror.txt
```

### Perintah `which`

**Code :** 
```bash
which ls
```

**Output :** 
```bash 
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ which ls
/usr/bin/ls
```

### Perintah `locate`

**Code :** 
```bash
locate "*.txt"
```

**Output :** 
```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ locate "*.txt"
/etc/X11/rgb.txt
/etc/brltty/Input/ba/all.txt
/etc/brltty/Input/bd/all.txt
/etc/brltty/Input/bl/18.txt
/etc/brltty/Input/bl/40_m20_m40.txt
/etc/brltty/Input/ec/all.txt
/etc/brltty/Input/ec/spanish.txt
/etc/brltty/Input/eu/all.txt
/etc/brltty/Input/lb/all.txt
/etc/brltty/Input/lt/all.txt
/etc/brltty/Input/mb/all.txt
/etc/brltty/Input/mn/all.txt
/etc/brltty/Input/no/all.txt
/etc/brltty/Input/tn/all.txt
/etc/brltty/Input/tt/all.txt
/etc/brltty/Input/vd/all.txt
/etc/brltty/Input/vr/all.txt
/etc/brltty/Input/vs/all.txt
/home/ibennn/.cache/tracker3/files/last-crawl.txt
/home/ibennn/praktikum-os/week02/config.txt
/home/ibennn/praktikum-os/week02/latihan.txt
/home/ibennn/praktikum-os/week02/notes.txt
/home/ibennn/praktikum-os/week03/config-files.txt
/home/ibennn/praktikum-os/week03/large-logs.txt
/home/ibennn/praktikum-os/week03/sorted-users.txt
/home/ibennn/praktikum-os/week04/bye.txt
/home/ibennn/praktikum-os/week04/halo.txt
/home/ibennn/praktikum-os/week04/hasil.txt
/home/ibennn/praktikum-os/week04/myerror.txt
/home/ibennn/praktikum-os/week04/proses.txt
/snap/core22/2134/usr/lib/python3/dist-packages/Babel-2.8.0.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/Babel-2.8.0.egg-info/entry_points.txt
/snap/core22/2134/usr/lib/python3/dist-packages/Babel-2.8.0.egg-info/requires.txt
/snap/core22/2134/usr/lib/python3/dist-packages/Babel-2.8.0.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/Jinja2-3.0.3.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/Jinja2-3.0.3.egg-info/entry_points.txt
/snap/core22/2134/usr/lib/python3/dist-packages/Jinja2-3.0.3.egg-info/requires.txt
/snap/core22/2134/usr/lib/python3/dist-packages/Jinja2-3.0.3.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/MarkupSafe-2.0.1.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/MarkupSafe-2.0.1.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/PyJWT-2.3.0.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/PyJWT-2.3.0.egg-info/requires.txt
/snap/core22/2134/usr/lib/python3/dist-packages/PyJWT-2.3.0.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/PyYAML-5.4.1.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/PyYAML-5.4.1.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/attrs-21.2.0.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/attrs-21.2.0.egg-info/requires.txt
/snap/core22/2134/usr/lib/python3/dist-packages/attrs-21.2.0.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/certifi-2020.6.20.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/certifi-2020.6.20.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/chardet-4.0.0.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/chardet-4.0.0.egg-info/entry_points.txt
/snap/core22/2134/usr/lib/python3/dist-packages/chardet-4.0.0.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/cloud_init-25.1.4.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/cloud_init-25.1.4.egg-info/entry_points.txt
/snap/core22/2134/usr/lib/python3/dist-packages/cloud_init-25.1.4.egg-info/requires.txt
/snap/core22/2134/usr/lib/python3/dist-packages/cloud_init-25.1.4.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/configobj-5.0.6.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/configobj-5.0.6.egg-info/requires.txt
/snap/core22/2134/usr/lib/python3/dist-packages/configobj-5.0.6.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/cryptography-3.4.8.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/cryptography-3.4.8.egg-info/requires.txt
/snap/core22/2134/usr/lib/python3/dist-packages/cryptography-3.4.8.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/dbus_python-1.2.18.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/dbus_python-1.2.18.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/idna-3.3.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/idna-3.3.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/importlib_metadata-4.6.4.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/importlib_metadata-4.6.4.egg-info/requires.txt
/snap/core22/2134/usr/lib/python3/dist-packages/importlib_metadata-4.6.4.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/jsonpatch-1.32.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/jsonpatch-1.32.egg-info/requires.txt
/snap/core22/2134/usr/lib/python3/dist-packages/jsonpatch-1.32.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/jsonpointer-2.0.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/jsonpointer-2.0.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/jsonschema-3.2.0.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/jsonschema-3.2.0.egg-info/entry_points.txt
/snap/core22/2134/usr/lib/python3/dist-packages/jsonschema-3.2.0.egg-info/requires.txt
/snap/core22/2134/usr/lib/python3/dist-packages/jsonschema-3.2.0.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/more_itertools-8.10.0.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/more_itertools-8.10.0.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/netifaces-0.11.0.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/netifaces-0.11.0.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/oauthlib-3.2.0.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/oauthlib-3.2.0.egg-info/requires.txt
/snap/core22/2134/usr/lib/python3/dist-packages/oauthlib-3.2.0.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/probert-0.0.18.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/probert-0.0.18.egg-info/requires.txt
/snap/core22/2134/usr/lib/python3/dist-packages/probert-0.0.18.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/pyrsistent-0.18.1.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/pyrsistent-0.18.1.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/entry_points.txt
/snap/core22/2134/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/requires.txt
/snap/core22/2134/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/pytz-2022.1.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/pytz-2022.1.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/pyudev-0.22.0.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/pyudev-0.22.0.egg-info/requires.txt
/snap/core22/2134/usr/lib/python3/dist-packages/pyudev-0.22.0.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/requests-2.25.1.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/requests-2.25.1.egg-info/requires.txt
/snap/core22/2134/usr/lib/python3/dist-packages/requests-2.25.1.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/requests_unixsocket-0.2.0.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/requests_unixsocket-0.2.0.egg-info/requires.txt
/snap/core22/2134/usr/lib/python3/dist-packages/requests_unixsocket-0.2.0.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/setuptools-59.6.0.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/setuptools-59.6.0.egg-info/entry_points.txt
/snap/core22/2134/usr/lib/python3/dist-packages/setuptools-59.6.0.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/six-1.16.0.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/six-1.16.0.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/urllib3-1.26.5.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/urllib3-1.26.5.egg-info/requires.txt
/snap/core22/2134/usr/lib/python3/dist-packages/urllib3-1.26.5.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/urwid-2.1.2.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/urwid-2.1.2.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3/dist-packages/zipp-1.0.0.egg-info/dependency_links.txt
/snap/core22/2134/usr/lib/python3/dist-packages/zipp-1.0.0.egg-info/requires.txt
/snap/core22/2134/usr/lib/python3/dist-packages/zipp-1.0.0.egg-info/top_level.txt
/snap/core22/2134/usr/lib/python3.10/LICENSE.txt
/snap/core22/2134/usr/lib/python3.10/lib2to3/Grammar.txt
/snap/core22/2134/usr/lib/python3.10/lib2to3/PatternGrammar.txt
/snap/core22/2134/usr/lib/python3.11/lib2to3/Grammar.txt
/snap/core22/2134/usr/lib/python3.11/lib2to3/PatternGrammar.txt
/snap/core22/2134/usr/share/subiquity/subiquity-0.0.5.egg-info/dependency_links.txt
/snap/core22/2134/usr/share/subiquity/subiquity-0.0.5.egg-info/entry_points.txt
/snap/core22/2134/usr/share/subiquity/subiquity-0.0.5.egg-info/top_level.txt
/snap/core22/2134/usr/share/vim/vim82/doc/help.txt
/snap/core22/2293/usr/lib/python3/dist-packages/Babel-2.8.0.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/Babel-2.8.0.egg-info/entry_points.txt
/snap/core22/2293/usr/lib/python3/dist-packages/Babel-2.8.0.egg-info/requires.txt
/snap/core22/2293/usr/lib/python3/dist-packages/Babel-2.8.0.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/Jinja2-3.0.3.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/Jinja2-3.0.3.egg-info/entry_points.txt
/snap/core22/2293/usr/lib/python3/dist-packages/Jinja2-3.0.3.egg-info/requires.txt
/snap/core22/2293/usr/lib/python3/dist-packages/Jinja2-3.0.3.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/MarkupSafe-2.0.1.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/MarkupSafe-2.0.1.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/PyJWT-2.3.0.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/PyJWT-2.3.0.egg-info/requires.txt
/snap/core22/2293/usr/lib/python3/dist-packages/PyJWT-2.3.0.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/PyYAML-5.4.1.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/PyYAML-5.4.1.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/attrs-21.2.0.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/attrs-21.2.0.egg-info/requires.txt
/snap/core22/2293/usr/lib/python3/dist-packages/attrs-21.2.0.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/certifi-2020.6.20.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/certifi-2020.6.20.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/chardet-4.0.0.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/chardet-4.0.0.egg-info/entry_points.txt
/snap/core22/2293/usr/lib/python3/dist-packages/chardet-4.0.0.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/cloud_init-25.2.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/cloud_init-25.2.egg-info/entry_points.txt
/snap/core22/2293/usr/lib/python3/dist-packages/cloud_init-25.2.egg-info/requires.txt
/snap/core22/2293/usr/lib/python3/dist-packages/cloud_init-25.2.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/configobj-5.0.6.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/configobj-5.0.6.egg-info/requires.txt
/snap/core22/2293/usr/lib/python3/dist-packages/configobj-5.0.6.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/cryptography-3.4.8.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/cryptography-3.4.8.egg-info/requires.txt
/snap/core22/2293/usr/lib/python3/dist-packages/cryptography-3.4.8.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/dbus_python-1.2.18.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/dbus_python-1.2.18.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/idna-3.3.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/idna-3.3.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/importlib_metadata-4.6.4.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/importlib_metadata-4.6.4.egg-info/requires.txt
/snap/core22/2293/usr/lib/python3/dist-packages/importlib_metadata-4.6.4.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/jsonpatch-1.32.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/jsonpatch-1.32.egg-info/requires.txt
/snap/core22/2293/usr/lib/python3/dist-packages/jsonpatch-1.32.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/jsonpointer-2.0.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/jsonpointer-2.0.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/jsonschema-3.2.0.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/jsonschema-3.2.0.egg-info/entry_points.txt
/snap/core22/2293/usr/lib/python3/dist-packages/jsonschema-3.2.0.egg-info/requires.txt
/snap/core22/2293/usr/lib/python3/dist-packages/jsonschema-3.2.0.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/more_itertools-8.10.0.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/more_itertools-8.10.0.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/netifaces-0.11.0.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/netifaces-0.11.0.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/oauthlib-3.2.0.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/oauthlib-3.2.0.egg-info/requires.txt
/snap/core22/2293/usr/lib/python3/dist-packages/oauthlib-3.2.0.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/probert-0.0.18.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/probert-0.0.18.egg-info/requires.txt
/snap/core22/2293/usr/lib/python3/dist-packages/probert-0.0.18.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/pyrsistent-0.18.1.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/pyrsistent-0.18.1.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/entry_points.txt
/snap/core22/2293/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/requires.txt
/snap/core22/2293/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/pytz-2022.1.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/pytz-2022.1.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/pyudev-0.22.0.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/pyudev-0.22.0.egg-info/requires.txt
/snap/core22/2293/usr/lib/python3/dist-packages/pyudev-0.22.0.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/requests-2.25.1.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/requests-2.25.1.egg-info/requires.txt
/snap/core22/2293/usr/lib/python3/dist-packages/requests-2.25.1.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/requests_unixsocket-0.2.0.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/requests_unixsocket-0.2.0.egg-info/requires.txt
/snap/core22/2293/usr/lib/python3/dist-packages/requests_unixsocket-0.2.0.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/setuptools-59.6.0.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/setuptools-59.6.0.egg-info/entry_points.txt
/snap/core22/2293/usr/lib/python3/dist-packages/setuptools-59.6.0.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/six-1.16.0.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/six-1.16.0.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/urllib3-1.26.5.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/urllib3-1.26.5.egg-info/requires.txt
/snap/core22/2293/usr/lib/python3/dist-packages/urllib3-1.26.5.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/urwid-2.1.2.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/urwid-2.1.2.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3/dist-packages/zipp-1.0.0.egg-info/dependency_links.txt
/snap/core22/2293/usr/lib/python3/dist-packages/zipp-1.0.0.egg-info/requires.txt
/snap/core22/2293/usr/lib/python3/dist-packages/zipp-1.0.0.egg-info/top_level.txt
/snap/core22/2293/usr/lib/python3.10/LICENSE.txt
/snap/core22/2293/usr/lib/python3.10/lib2to3/Grammar.txt
/snap/core22/2293/usr/lib/python3.10/lib2to3/PatternGrammar.txt
/snap/core22/2293/usr/lib/python3.11/lib2to3/Grammar.txt
/snap/core22/2293/usr/lib/python3.11/lib2to3/PatternGrammar.txt
/snap/core22/2293/usr/share/subiquity/subiquity-0.0.5.egg-info/dependency_links.txt
/snap/core22/2293/usr/share/subiquity/subiquity-0.0.5.egg-info/entry_points.txt
/snap/core22/2293/usr/share/subiquity/subiquity-0.0.5.egg-info/top_level.txt
/snap/core22/2293/usr/share/vim/vim82/doc/help.txt
/snap/core24/1500/usr/lib/python3/dist-packages/Jinja2-3.1.2.egg-info/dependency_links.txt
/snap/core24/1500/usr/lib/python3/dist-packages/Jinja2-3.1.2.egg-info/entry_points.txt
/snap/core24/1500/usr/lib/python3/dist-packages/Jinja2-3.1.2.egg-info/requires.txt
/snap/core24/1500/usr/lib/python3/dist-packages/Jinja2-3.1.2.egg-info/top_level.txt
/snap/core24/1500/usr/lib/python3/dist-packages/MarkupSafe-2.1.5.egg-info/dependency_links.txt
/snap/core24/1500/usr/lib/python3/dist-packages/MarkupSafe-2.1.5.egg-info/top_level.txt
/snap/core24/1500/usr/lib/python3/dist-packages/PyJWT-2.7.0.dist-info/top_level.txt
/snap/core24/1500/usr/lib/python3/dist-packages/PyYAML-6.0.1.dist-info/top_level.txt
/snap/core24/1500/usr/lib/python3/dist-packages/certifi-2023.11.17.egg-info/dependency_links.txt
/snap/core24/1500/usr/lib/python3/dist-packages/certifi-2023.11.17.egg-info/top_level.txt
/snap/core24/1500/usr/lib/python3/dist-packages/chardet-5.2.0.dist-info/entry_points.txt
/snap/core24/1500/usr/lib/python3/dist-packages/chardet-5.2.0.dist-info/top_level.txt
/snap/core24/1500/usr/lib/python3/dist-packages/cloud_init-25.2.egg-info/dependency_links.txt
/snap/core24/1500/usr/lib/python3/dist-packages/cloud_init-25.2.egg-info/entry_points.txt
/snap/core24/1500/usr/lib/python3/dist-packages/cloud_init-25.2.egg-info/requires.txt
/snap/core24/1500/usr/lib/python3/dist-packages/cloud_init-25.2.egg-info/top_level.txt
/snap/core24/1500/usr/lib/python3/dist-packages/configobj-5.0.8.dist-info/top_level.txt
/snap/core24/1500/usr/lib/python3/dist-packages/cryptography-41.0.7.dist-info/top_level.txt
/snap/core24/1500/usr/lib/python3/dist-packages/cryptography.egg-info/dependency_links.txt
/snap/core24/1500/usr/lib/python3/dist-packages/cryptography.egg-info/requires.txt
/snap/core24/1500/usr/lib/python3/dist-packages/cryptography.egg-info/top_level.txt
/snap/core24/1500/usr/lib/python3/dist-packages/dbus_python-1.3.2.egg-info/dependency_links.txt
/snap/core24/1500/usr/lib/python3/dist-packages/dbus_python-1.3.2.egg-info/top_level.txt
/snap/core24/1500/usr/lib/python3/dist-packages/jsonpatch-1.32.egg-info/dependency_links.txt
/snap/core24/1500/usr/lib/python3/dist-packages/jsonpatch-1.32.egg-info/requires.txt
/snap/core24/1500/usr/lib/python3/dist-packages/jsonpatch-1.32.egg-info/top_level.txt
/snap/core24/1500/usr/lib/python3/dist-packages/jsonpointer-2.0.egg-info/dependency_links.txt
/snap/core24/1500/usr/lib/python3/dist-packages/jsonpointer-2.0.egg-info/top_level.txt
/snap/core24/1500/usr/lib/python3/dist-packages/jsonschema-4.10.3.dist-info/entry_points.txt
/snap/core24/1500/usr/lib/python3/dist-packages/netifaces-0.11.0.egg-info/dependency_links.txt
/snap/core24/1500/usr/lib/python3/dist-packages/netifaces-0.11.0.egg-info/top_level.txt
/snap/core24/1500/usr/lib/python3/dist-packages/oauthlib-3.2.2.egg-info/dependency_links.txt
/snap/core24/1500/usr/lib/python3/dist-packages/oauthlib-3.2.2.egg-info/requires.txt
/snap/core24/1500/usr/lib/python3/dist-packages/oauthlib-3.2.2.egg-info/top_level.txt
/snap/core24/1500/usr/lib/python3/dist-packages/pyrsistent-0.20.0.egg-info/dependency_links.txt
/snap/core24/1500/usr/lib/python3/dist-packages/pyrsistent-0.20.0.egg-info/top_level.txt
/snap/core24/1500/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/dependency_links.txt
/snap/core24/1500/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/entry_points.txt
/snap/core24/1500/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/requires.txt
/snap/core24/1500/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/top_level.txt
/snap/core24/1500/usr/lib/python3/dist-packages/requests-2.31.0.egg-info/dependency_links.txt
/snap/core24/1500/usr/lib/python3/dist-packages/requests-2.31.0.egg-info/requires.txt
/snap/core24/1500/usr/lib/python3/dist-packages/requests-2.31.0.egg-info/top_level.txt
/snap/core24/1500/usr/lib/python3.12/LICENSE.txt
/snap/core24/1500/usr/share/vim/vim91/doc/help.txt
/snap/core24/1500/usr/share/vim/vim91/doc/sponsor.txt
/snap/core24/1500/usr/share/vim/vim91/doc/uganda.txt
/snap/core24/1500/usr/share/vim/vim91/doc/version9.txt
/snap/core24/1588/usr/lib/python3/dist-packages/Jinja2-3.1.2.egg-info/dependency_links.txt
/snap/core24/1588/usr/lib/python3/dist-packages/Jinja2-3.1.2.egg-info/entry_points.txt
/snap/core24/1588/usr/lib/python3/dist-packages/Jinja2-3.1.2.egg-info/requires.txt
/snap/core24/1588/usr/lib/python3/dist-packages/Jinja2-3.1.2.egg-info/top_level.txt
/snap/core24/1588/usr/lib/python3/dist-packages/MarkupSafe-2.1.5.egg-info/dependency_links.txt
/snap/core24/1588/usr/lib/python3/dist-packages/MarkupSafe-2.1.5.egg-info/top_level.txt
/snap/core24/1588/usr/lib/python3/dist-packages/PyJWT-2.7.0.dist-info/top_level.txt
/snap/core24/1588/usr/lib/python3/dist-packages/PyYAML-6.0.1.dist-info/top_level.txt
/snap/core24/1588/usr/lib/python3/dist-packages/certifi-2023.11.17.egg-info/dependency_links.txt
/snap/core24/1588/usr/lib/python3/dist-packages/certifi-2023.11.17.egg-info/top_level.txt
/snap/core24/1588/usr/lib/python3/dist-packages/chardet-5.2.0.dist-info/entry_points.txt
/snap/core24/1588/usr/lib/python3/dist-packages/chardet-5.2.0.dist-info/top_level.txt
/snap/core24/1588/usr/lib/python3/dist-packages/cloud_init-25.3.egg-info/dependency_links.txt
/snap/core24/1588/usr/lib/python3/dist-packages/cloud_init-25.3.egg-info/entry_points.txt
/snap/core24/1588/usr/lib/python3/dist-packages/cloud_init-25.3.egg-info/requires.txt
/snap/core24/1588/usr/lib/python3/dist-packages/cloud_init-25.3.egg-info/top_level.txt
/snap/core24/1588/usr/lib/python3/dist-packages/configobj-5.0.8.dist-info/top_level.txt
/snap/core24/1588/usr/lib/python3/dist-packages/cryptography-41.0.7.dist-info/top_level.txt
/snap/core24/1588/usr/lib/python3/dist-packages/cryptography.egg-info/dependency_links.txt
/snap/core24/1588/usr/lib/python3/dist-packages/cryptography.egg-info/requires.txt
/snap/core24/1588/usr/lib/python3/dist-packages/cryptography.egg-info/top_level.txt
/snap/core24/1588/usr/lib/python3/dist-packages/dbus_python-1.3.2.egg-info/dependency_links.txt
/snap/core24/1588/usr/lib/python3/dist-packages/dbus_python-1.3.2.egg-info/top_level.txt
/snap/core24/1588/usr/lib/python3/dist-packages/jsonpatch-1.32.egg-info/dependency_links.txt
/snap/core24/1588/usr/lib/python3/dist-packages/jsonpatch-1.32.egg-info/requires.txt
/snap/core24/1588/usr/lib/python3/dist-packages/jsonpatch-1.32.egg-info/top_level.txt
/snap/core24/1588/usr/lib/python3/dist-packages/jsonpointer-2.0.egg-info/dependency_links.txt
/snap/core24/1588/usr/lib/python3/dist-packages/jsonpointer-2.0.egg-info/top_level.txt
/snap/core24/1588/usr/lib/python3/dist-packages/jsonschema-4.10.3.dist-info/entry_points.txt
/snap/core24/1588/usr/lib/python3/dist-packages/netifaces-0.11.0.egg-info/dependency_links.txt
/snap/core24/1588/usr/lib/python3/dist-packages/netifaces-0.11.0.egg-info/top_level.txt
/snap/core24/1588/usr/lib/python3/dist-packages/oauthlib-3.2.2.egg-info/dependency_links.txt
/snap/core24/1588/usr/lib/python3/dist-packages/oauthlib-3.2.2.egg-info/requires.txt
/snap/core24/1588/usr/lib/python3/dist-packages/oauthlib-3.2.2.egg-info/top_level.txt
/snap/core24/1588/usr/lib/python3/dist-packages/pyrsistent-0.20.0.egg-info/dependency_links.txt
/snap/core24/1588/usr/lib/python3/dist-packages/pyrsistent-0.20.0.egg-info/top_level.txt
/snap/core24/1588/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/dependency_links.txt
/snap/core24/1588/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/entry_points.txt
/snap/core24/1588/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/requires.txt
/snap/core24/1588/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/top_level.txt
/snap/core24/1588/usr/lib/python3/dist-packages/requests-2.31.0.egg-info/dependency_links.txt
/snap/core24/1588/usr/lib/python3/dist-packages/requests-2.31.0.egg-info/requires.txt
/snap/core24/1588/usr/lib/python3/dist-packages/requests-2.31.0.egg-info/top_level.txt
/snap/core24/1588/usr/lib/python3.12/LICENSE.txt
/snap/core24/1588/usr/share/vim/vim91/doc/help.txt
/snap/core24/1588/usr/share/vim/vim91/doc/sponsor.txt
/snap/core24/1588/usr/share/vim/vim91/doc/uganda.txt
/snap/core24/1588/usr/share/vim/vim91/doc/version9.txt
/snap/gnome-42-2204/228/etc/X11/rgb.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/Mako-1.1.3-py3.10.egg-info/dependency_links.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/Mako-1.1.3-py3.10.egg-info/entry_points.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/Mako-1.1.3-py3.10.egg-info/requires.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/Mako-1.1.3-py3.10.egg-info/top_level.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/Markdown-3.3.6.egg-info/dependency_links.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/Markdown-3.3.6.egg-info/entry_points.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/Markdown-3.3.6.egg-info/requires.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/Markdown-3.3.6.egg-info/top_level.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/MarkupSafe-2.0.1.egg-info/dependency_links.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/MarkupSafe-2.0.1.egg-info/top_level.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/PyGObject-3.42.1.egg-info/dependency_links.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/PyGObject-3.42.1.egg-info/requires.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/PyGObject-3.42.1.egg-info/top_level.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/dbus_python-1.2.18.egg-info/dependency_links.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/dbus_python-1.2.18.egg-info/top_level.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/importlib_metadata-4.6.4.egg-info/dependency_links.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/importlib_metadata-4.6.4.egg-info/requires.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/importlib_metadata-4.6.4.egg-info/top_level.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/more_itertools-8.10.0.egg-info/dependency_links.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/more_itertools-8.10.0.egg-info/top_level.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/pip/_vendor/vendor.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/pip-22.0.2.dist-info/entry_points.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/pip-22.0.2.dist-info/top_level.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/setuptools-59.6.0.egg-info/dependency_links.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/setuptools-59.6.0.egg-info/entry_points.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/setuptools-59.6.0.egg-info/top_level.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/wheel-0.37.1.egg-info/dependency_links.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/wheel-0.37.1.egg-info/entry_points.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/wheel-0.37.1.egg-info/requires.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/wheel-0.37.1.egg-info/top_level.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/zipp-1.0.0.egg-info/dependency_links.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/zipp-1.0.0.egg-info/requires.txt
/snap/gnome-42-2204/228/usr/lib/python3/dist-packages/zipp-1.0.0.egg-info/top_level.txt
/snap/gnome-42-2204/228/usr/lib/python3.10/LICENSE.txt
/snap/gnome-42-2204/228/usr/share/X11/rgb.txt
/snap/gnome-42-2204/228/usr/share/presage/abbreviations_en.txt
/snap/gnome-42-2204/228/usr/share/presage/abbreviations_it.txt
/snap/gnome-42-2204/245/etc/X11/rgb.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/Mako-1.1.3-py3.10.egg-info/dependency_links.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/Mako-1.1.3-py3.10.egg-info/entry_points.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/Mako-1.1.3-py3.10.egg-info/requires.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/Mako-1.1.3-py3.10.egg-info/top_level.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/Markdown-3.3.6.egg-info/dependency_links.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/Markdown-3.3.6.egg-info/entry_points.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/Markdown-3.3.6.egg-info/requires.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/Markdown-3.3.6.egg-info/top_level.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/MarkupSafe-2.0.1.egg-info/dependency_links.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/MarkupSafe-2.0.1.egg-info/top_level.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/PyGObject-3.42.1.egg-info/dependency_links.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/PyGObject-3.42.1.egg-info/requires.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/PyGObject-3.42.1.egg-info/top_level.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/dbus_python-1.2.18.egg-info/dependency_links.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/dbus_python-1.2.18.egg-info/top_level.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/importlib_metadata-4.6.4.egg-info/dependency_links.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/importlib_metadata-4.6.4.egg-info/requires.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/importlib_metadata-4.6.4.egg-info/top_level.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/more_itertools-8.10.0.egg-info/dependency_links.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/more_itertools-8.10.0.egg-info/top_level.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/pip/_vendor/vendor.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/pip-22.0.2.dist-info/entry_points.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/pip-22.0.2.dist-info/top_level.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/setuptools-59.6.0.egg-info/dependency_links.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/setuptools-59.6.0.egg-info/entry_points.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/setuptools-59.6.0.egg-info/top_level.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/wheel-0.37.1.egg-info/dependency_links.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/wheel-0.37.1.egg-info/entry_points.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/wheel-0.37.1.egg-info/requires.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/wheel-0.37.1.egg-info/top_level.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/zipp-1.0.0.egg-info/dependency_links.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/zipp-1.0.0.egg-info/requires.txt
/snap/gnome-42-2204/245/usr/lib/python3/dist-packages/zipp-1.0.0.egg-info/top_level.txt
/snap/gnome-42-2204/245/usr/lib/python3.10/LICENSE.txt
/snap/gnome-42-2204/245/usr/share/X11/rgb.txt
/snap/gnome-42-2204/245/usr/share/presage/abbreviations_en.txt
/snap/gnome-42-2204/245/usr/share/presage/abbreviations_it.txt
/snap/prompting-client/105/flutter/apps/prompting_client_ui/linux/CMakeLists.txt
/snap/prompting-client/105/flutter/apps/prompting_client_ui/linux/flutter/CMakeLists.txt
/usr/lib/python3/dist-packages/Brlapi-0.8.6.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/Brlapi-0.8.6.egg-info/top_level.txt
/usr/lib/python3/dist-packages/MarkupSafe-2.1.5.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/MarkupSafe-2.1.5.egg-info/top_level.txt
/usr/lib/python3/dist-packages/PyJWT-2.10.1.dist-info/top_level.txt
/usr/lib/python3/dist-packages/PyYAML-6.0.2.dist-info/top_level.txt
/usr/lib/python3/dist-packages/aptdaemon-2.0.2.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/aptdaemon-2.0.2.egg-info/top_level.txt
/usr/lib/python3/dist-packages/autocommand-2.2.2.dist-info/top_level.txt
/usr/lib/python3/dist-packages/babel-2.17.0.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/babel-2.17.0.egg-info/entry_points.txt
/usr/lib/python3/dist-packages/babel-2.17.0.egg-info/requires.txt
/usr/lib/python3/dist-packages/babel-2.17.0.egg-info/top_level.txt
/usr/lib/python3/dist-packages/bcc-0.31.0.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/bcc-0.31.0.egg-info/top_level.txt
/usr/lib/python3/dist-packages/bcrypt-4.2.0.dist-info/top_level.txt
/usr/lib/python3/dist-packages/certifi-2025.1.31.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/certifi-2025.1.31.egg-info/top_level.txt
/usr/lib/python3/dist-packages/chardet-5.2.0.dist-info/entry_points.txt
/usr/lib/python3/dist-packages/chardet-5.2.0.dist-info/top_level.txt
/usr/lib/python3/dist-packages/configobj-5.0.9.dist-info/top_level.txt
/usr/lib/python3/dist-packages/cupshelpers-1.0.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/cupshelpers-1.0.egg-info/top_level.txt
/usr/lib/python3/dist-packages/dasbus-1.7.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/dasbus-1.7.egg-info/top_level.txt
/usr/lib/python3/dist-packages/dbus_python-1.4.0.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/dbus_python-1.4.0.egg-info/top_level.txt
/usr/lib/python3/dist-packages/defer-1.0.6.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/defer-1.0.6.egg-info/top_level.txt
/usr/lib/python3/dist-packages/distro-1.9.0.dist-info/entry_points.txt
/usr/lib/python3/dist-packages/distro-1.9.0.dist-info/top_level.txt
/usr/lib/python3/dist-packages/distro_info-1.14.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/distro_info-1.14.egg-info/top_level.txt
/usr/lib/python3/dist-packages/httplib2-0.22.0.dist-info/top_level.txt
/usr/lib/python3/dist-packages/inflect-7.3.1.dist-info/top_level.txt
/usr/lib/python3/dist-packages/jaraco.functools-4.1.0.dist-info/top_level.txt
/usr/lib/python3/dist-packages/jaraco_context-6.0.1.dist-info/top_level.txt
/usr/lib/python3/dist-packages/jinja2-3.1.6.dist-info/entry_points.txt
/usr/lib/python3/dist-packages/jsonpatch-1.32.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/jsonpatch-1.32.egg-info/requires.txt
/usr/lib/python3/dist-packages/jsonpatch-1.32.egg-info/top_level.txt
/usr/lib/python3/dist-packages/jsonpointer-2.4.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/jsonpointer-2.4.egg-info/top_level.txt
/usr/lib/python3/dist-packages/jsonschema-4.19.2.dist-info/entry_points.txt
/usr/lib/python3/dist-packages/language_selector-0.1.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/language_selector-0.1.egg-info/entry_points.txt
/usr/lib/python3/dist-packages/language_selector-0.1.egg-info/top_level.txt
/usr/lib/python3/dist-packages/launchpadlib-2.1.0.dist-info/top_level.txt
/usr/lib/python3/dist-packages/lazr.restfulclient-0.14.6.dist-info/namespace_packages.txt
/usr/lib/python3/dist-packages/lazr.restfulclient-0.14.6.dist-info/top_level.txt
/usr/lib/python3/dist-packages/lazr.uri-1.0.6.dist-info/namespace_packages.txt
/usr/lib/python3/dist-packages/lazr.uri-1.0.6.dist-info/top_level.txt
/usr/lib/python3/dist-packages/linkify_it_py-2.0.3.dist-info/top_level.txt
/usr/lib/python3/dist-packages/louis-3.33.0.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/louis-3.33.0.egg-info/top_level.txt
/usr/lib/python3/dist-packages/markdown_it_py-3.0.0.dist-info/entry_points.txt
/usr/lib/python3/dist-packages/netaddr/eui/iab.txt
/usr/lib/python3/dist-packages/netaddr/eui/oui.txt
/usr/lib/python3/dist-packages/netaddr/tests/eui/sample_iab.txt
/usr/lib/python3/dist-packages/netaddr/tests/eui/sample_oui.txt
/usr/lib/python3/dist-packages/netaddr-1.3.0.dist-info/entry_points.txt
/usr/lib/python3/dist-packages/netaddr-1.3.0.dist-info/top_level.txt
/usr/lib/python3/dist-packages/oauthlib-3.2.2.dist-info/top_level.txt
/usr/lib/python3/dist-packages/olefile-0.47.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/olefile-0.47.egg-info/requires.txt
/usr/lib/python3/dist-packages/olefile-0.47.egg-info/top_level.txt
/usr/lib/python3/dist-packages/passlib/_data/wordsets/bip39.txt
/usr/lib/python3/dist-packages/passlib/_data/wordsets/eff_long.txt
/usr/lib/python3/dist-packages/passlib/_data/wordsets/eff_prefixed.txt
/usr/lib/python3/dist-packages/passlib/_data/wordsets/eff_short.txt
/usr/lib/python3/dist-packages/passlib-1.7.4.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/passlib-1.7.4.egg-info/requires.txt
/usr/lib/python3/dist-packages/passlib-1.7.4.egg-info/top_level.txt
/usr/lib/python3/dist-packages/pexpect-4.9.0.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/pexpect-4.9.0.egg-info/requires.txt
/usr/lib/python3/dist-packages/pexpect-4.9.0.egg-info/top_level.txt
/usr/lib/python3/dist-packages/pillow-11.3.0.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/pillow-11.3.0.egg-info/requires.txt
/usr/lib/python3/dist-packages/pillow-11.3.0.egg-info/top_level.txt
/usr/lib/python3/dist-packages/pkg_resources/api_tests.txt
/usr/lib/python3/dist-packages/pkg_resources/tests/data/my-test-package_unpacked-egg/my_test_package-1.0-py3.7.egg/EGG-INFO/SOURCES.txt
/usr/lib/python3/dist-packages/pkg_resources/tests/data/my-test-package_unpacked-egg/my_test_package-1.0-py3.7.egg/EGG-INFO/dependency_links.txt
/usr/lib/python3/dist-packages/pkg_resources/tests/data/my-test-package_unpacked-egg/my_test_package-1.0-py3.7.egg/EGG-INFO/top_level.txt
/usr/lib/python3/dist-packages/psutil-7.0.0.dist-info/top_level.txt
/usr/lib/python3/dist-packages/pycups-2.0.4.dist-info/top_level.txt
/usr/lib/python3/dist-packages/pygments-2.18.0.dist-info/entry_points.txt
/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/entry_points.txt
/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/requires.txt
/usr/lib/python3/dist-packages/pyserial-3.5.egg-info/top_level.txt
/usr/lib/python3/dist-packages/python_apt-3.0.0+ubuntu1.1.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/python_apt-3.0.0+ubuntu1.1.egg-info/top_level.txt
/usr/lib/python3/dist-packages/python_dateutil-2.9.0.dist-info/top_level.txt
/usr/lib/python3/dist-packages/python_debian-1.0.1+ubuntu1.dist-info/top_level.txt
/usr/lib/python3/dist-packages/pyxdg-0.28.dist-info/top_level.txt
/usr/lib/python3/dist-packages/requests-2.32.3.dist-info/top_level.txt
/usr/lib/python3/dist-packages/setproctitle-1.3.6.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/setproctitle-1.3.6.egg-info/requires.txt
/usr/lib/python3/dist-packages/setproctitle-1.3.6.egg-info/top_level.txt
/usr/lib/python3/dist-packages/setuptools/_vendor/jaraco/text/Lorem ipsum.txt
/usr/lib/python3/dist-packages/setuptools/_vendor/jaraco.text-3.12.1.dist-info/top_level.txt
/usr/lib/python3/dist-packages/systemd_python-235.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/systemd_python-235.egg-info/top_level.txt
/usr/lib/python3/dist-packages/typeguard-4.4.2.dist-info/entry_points.txt
/usr/lib/python3/dist-packages/typeguard-4.4.2.dist-info/top_level.txt
/usr/lib/python3/dist-packages/ubuntu_drivers_common-0.0.0.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/ubuntu_drivers_common-0.0.0.egg-info/top_level.txt
/usr/lib/python3/dist-packages/ubuntu_pro_client-8001.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/ubuntu_pro_client-8001.egg-info/entry_points.txt
/usr/lib/python3/dist-packages/ubuntu_pro_client-8001.egg-info/requires.txt
/usr/lib/python3/dist-packages/ubuntu_pro_client-8001.egg-info/top_level.txt
/usr/lib/python3/dist-packages/uc_micro_py-1.0.3.dist-info/top_level.txt
/usr/lib/python3/dist-packages/ufw-0.36.2.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/ufw-0.36.2.egg-info/top_level.txt
/usr/lib/python3/dist-packages/unattended_upgrades-0.1.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/unattended_upgrades-0.1.egg-info/top_level.txt
/usr/lib/python3/dist-packages/wadllib-2.0.0.dist-info/top_level.txt
/usr/lib/python3/dist-packages/xkit-0.0.0.egg-info/dependency_links.txt
/usr/lib/python3/dist-packages/xkit-0.0.0.egg-info/top_level.txt
/usr/lib/python3.13/LICENSE.txt
/usr/lib/xorg/protocol.txt
/usr/share/X11/rgb.txt
/usr/share/cups/doc-root/robots.txt
/usr/share/doc/alsa-base/driver/Bt87x.txt
/usr/share/doc/alsa-base/driver/ControlNames.txt
/usr/share/doc/alsa-base/driver/Joystick.txt
/usr/share/doc/alsa-base/driver/MIXART.txt
/usr/share/doc/alsa-base/driver/VIA82xx-mixer.txt
/usr/share/doc/alsa-base/driver/alsa-parameters.txt
/usr/share/doc/alsa-base/driver/emu10k1-jack.txt
/usr/share/doc/alsa-base/driver/powersave.txt
/usr/share/doc/alsa-base/driver/serial-u16550.txt
/usr/share/doc/bpfcc-tools/examples/doc/argdist_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/bashreadline_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/bindsnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/biolatency_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/biolatpcts_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/biopattern_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/biosnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/biotop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/bitesize_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/bpflist_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/btrfsdist_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/btrfsslower_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/cachestat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/cachetop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/capable_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/cobjnew_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/compactsnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/cpudist_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/cpuunclaimed_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/criticalstat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/cthreads_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/dbslower_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/dbstat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/dcsnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/dcstat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/deadlock_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/dirtop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/drsnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/execsnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/exitsnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/ext4dist_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/ext4slower_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/f2fsslower_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/filegone_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/filelife_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/fileslower_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/filetop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/funccount_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/funcinterval_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/funclatency_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/funcslower_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/gethostlatency_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/hardirqs_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/inject_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/javacalls_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/javaflow_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/javagc_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/javaobjnew_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/javastat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/javathreads_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/killsnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/klockstat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/kvmexit_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/llcstat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/mdflush_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/memleak_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/mountsnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/mysqld_qslower_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/netqtop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/nfsdist_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/nfsslower_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/nodegc_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/nodestat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/offcputime_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/offwaketime_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/oomkill_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/opensnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/perlcalls_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/perlflow_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/perlstat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/phpcalls_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/phpflow_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/phpstat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/pidpersec_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/ppchcalls_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/profile_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/pythoncalls_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/pythonflow_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/pythongc_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/pythonstat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/rdmaucma_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/readahead_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/reset-trace_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/rubycalls_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/rubyflow_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/rubygc_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/rubyobjnew_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/rubystat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/runqlat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/runqlen_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/runqslower_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/shmsnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/slabratetop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/sofdsnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/softirqs_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/solisten_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/sslsniff_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/stackcount_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/statsnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/swapin.txt
/usr/share/doc/bpfcc-tools/examples/doc/swapin_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/syncsnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/syscount_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tclcalls_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tclflow_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tclobjnew_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tclstat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tcpaccept_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tcpcong_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tcpconnect_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tcpconnlat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tcpdrop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tcplife_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tcpretrans_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tcprtt_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tcpstates_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tcpsubnet_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tcpsynbl_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tcptop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tcptracer_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/threadsnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/tplist_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/trace_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/ttysnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/vfscount_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/vfsstat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/virtiostat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/wakeuptime_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/wqlat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/xfsdist_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/xfsslower_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/zfsdist_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/zfsslower_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/lib/ucalls_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/lib/uflow_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/lib/ugc_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/lib/uobjnew_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/lib/ustat_example.txt
/usr/share/doc/bpfcc-tools/examples/doc/lib/uthreads_example.txt
/usr/share/doc/bpfcc-tools/examples/networking/neighbor_sharing/README.txt
/usr/share/doc/bpfcc-tools/examples/networking/vlan_learning/README.txt
/usr/share/doc/bpfcc-tools/examples/tracing/CMakeLists.txt
/usr/share/doc/bpfcc-tools/examples/tracing/biolatpcts_example.txt
/usr/share/doc/bpfcc-tools/examples/tracing/bitehist_example.txt
/usr/share/doc/bpfcc-tools/examples/tracing/dddos_example.txt
/usr/share/doc/bpfcc-tools/examples/tracing/disksnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/tracing/kvm_hypercall.txt
/usr/share/doc/bpfcc-tools/examples/tracing/mysqld_query_example.txt
/usr/share/doc/bpfcc-tools/examples/tracing/nodejs_http_server_example.txt
/usr/share/doc/bpfcc-tools/examples/tracing/stacksnoop_example.txt
/usr/share/doc/bpfcc-tools/examples/tracing/tcpv4connect_example.txt
/usr/share/doc/bpfcc-tools/examples/tracing/undump_example.txt
/usr/share/doc/bpfcc-tools/examples/tracing/urandomread_example.txt
/usr/share/doc/bpfcc-tools/examples/tracing/vfsreadlat_example.txt
/usr/share/doc/bpftrace/examples/bashreadline_example.txt
/usr/share/doc/bpftrace/examples/biolatency_example.txt
/usr/share/doc/bpftrace/examples/biosnoop_example.txt
/usr/share/doc/bpftrace/examples/biostacks_example.txt
/usr/share/doc/bpftrace/examples/bitesize_example.txt
/usr/share/doc/bpftrace/examples/capable_example.txt
/usr/share/doc/bpftrace/examples/cpuwalk_example.txt
/usr/share/doc/bpftrace/examples/dcsnoop_example.txt
/usr/share/doc/bpftrace/examples/execsnoop_example.txt
/usr/share/doc/bpftrace/examples/gethostlatency_example.txt
/usr/share/doc/bpftrace/examples/killsnoop_example.txt
/usr/share/doc/bpftrace/examples/loads_example.txt
/usr/share/doc/bpftrace/examples/mdflush_example.txt
/usr/share/doc/bpftrace/examples/naptime_example.txt
/usr/share/doc/bpftrace/examples/oomkill_example.txt
/usr/share/doc/bpftrace/examples/opensnoop_example.txt
/usr/share/doc/bpftrace/examples/pidpersec_example.txt
/usr/share/doc/bpftrace/examples/runqlat_example.txt
/usr/share/doc/bpftrace/examples/runqlen_example.txt
/usr/share/doc/bpftrace/examples/setuids_example.txt
/usr/share/doc/bpftrace/examples/ssllatency_example.txt
/usr/share/doc/bpftrace/examples/sslsnoop_example.txt
/usr/share/doc/bpftrace/examples/statsnoop_example.txt
/usr/share/doc/bpftrace/examples/swapin_example.txt
/usr/share/doc/bpftrace/examples/syncsnoop_example.txt
/usr/share/doc/bpftrace/examples/syscount_example.txt
/usr/share/doc/bpftrace/examples/tcpaccept_example.txt
/usr/share/doc/bpftrace/examples/tcpconnect_example.txt
/usr/share/doc/bpftrace/examples/tcpdrop_example.txt
/usr/share/doc/bpftrace/examples/tcplife_example.txt
/usr/share/doc/bpftrace/examples/tcpretrans_example.txt
/usr/share/doc/bpftrace/examples/tcpsynbl_example.txt
/usr/share/doc/bpftrace/examples/threadsnoop_example.txt
/usr/share/doc/bpftrace/examples/undump_example.txt
/usr/share/doc/bpftrace/examples/vfscount_example.txt
/usr/share/doc/bpftrace/examples/vfsstat_example.txt
/usr/share/doc/bpftrace/examples/writeback_example.txt
/usr/share/doc/bpftrace/examples/xfsdist_example.txt
/usr/share/doc/cloud-init/examples/boothook.txt
/usr/share/doc/cloud-init/examples/cloud-config-add-apt-repos.txt
/usr/share/doc/cloud-init/examples/cloud-config-ansible-managed.txt
/usr/share/doc/cloud-init/examples/cloud-config-ansible-pull.txt
/usr/share/doc/cloud-init/examples/cloud-config-archive-launch-index.txt
/usr/share/doc/cloud-init/examples/cloud-config-archive.txt
/usr/share/doc/cloud-init/examples/cloud-config-boot-cmds.txt
/usr/share/doc/cloud-init/examples/cloud-config-ca-certs.txt
/usr/share/doc/cloud-init/examples/cloud-config-chef-oneiric.txt
/usr/share/doc/cloud-init/examples/cloud-config-datasources.txt
/usr/share/doc/cloud-init/examples/cloud-config-gluster.txt
/usr/share/doc/cloud-init/examples/cloud-config-install-packages.txt
/usr/share/doc/cloud-init/examples/cloud-config-launch-index.txt
/usr/share/doc/cloud-init/examples/cloud-config-lxd.txt
/usr/share/doc/cloud-init/examples/cloud-config-mount-points.txt
/usr/share/doc/cloud-init/examples/cloud-config-ntp.txt
/usr/share/doc/cloud-init/examples/cloud-config-reporting.txt
/usr/share/doc/cloud-init/examples/cloud-config-run-cmds.txt
/usr/share/doc/cloud-init/examples/cloud-config-ssh-keys.txt
/usr/share/doc/cloud-init/examples/cloud-config-update-apt.txt
/usr/share/doc/cloud-init/examples/cloud-config-update-packages.txt
/usr/share/doc/cloud-init/examples/cloud-config-wireguard.txt
/usr/share/doc/cloud-init/examples/cloud-config-write-files.txt
/usr/share/doc/cloud-init/examples/cloud-config-yum-repo.txt
/usr/share/doc/cloud-init/examples/include-once.txt
/usr/share/doc/cloud-init/examples/include.txt
/usr/share/doc/cloud-init/examples/kernel-command-line.txt
/usr/share/doc/cloud-init/examples/part-handler-v2.txt
/usr/share/doc/cloud-init/examples/part-handler.txt
/usr/share/doc/cloud-init/examples/plain-ignored.txt
/usr/share/doc/cloud-init/examples/user-script.txt
/usr/share/doc/cups/HOWTO_BUGREPORT.txt
/usr/share/doc/fonts-ubuntu/CONTRIBUTING.txt
/usr/share/doc/fonts-ubuntu/README.txt
/usr/share/doc/fonts-ubuntu/TRADEMARKS.txt
/usr/share/doc/gdb/contrib/common-misspellings.txt
/usr/share/doc/git/contrib/buildsystems/CMakeLists.txt
/usr/share/doc/gnupg/examples/qualified.txt
/usr/share/doc/gnupg/examples/trustlist.txt
/usr/share/doc/gpg-agent/examples/trustlist.txt
/usr/share/doc/hplip/users-guide.txt
/usr/share/doc/libasound2t64/examples/asoundrc.txt
/usr/share/doc/libauthen-sasl-perl/api.txt
/usr/share/doc/libbpfcc/FAQ.txt
/usr/share/doc/libdb5.3t64/build_signature_arm64.txt
/usr/share/doc/libgphoto2-6/OUTDATED.txt
/usr/share/doc/libio-socket-ssl-perl/debugging.txt
/usr/share/doc/libsane-common/leo/leo.txt
/usr/share/doc/libsane-common/plustek/Plustek-PARPORT-TODO.txt
/usr/share/doc/libsane-common/plustek/Plustek-PARPORT.txt
/usr/share/doc/libsane-common/plustek/Plustek-USB-TODO.txt
/usr/share/doc/libsane-common/sceptre/s1200.txt
/usr/share/doc/libsane-common/umax/negative-types.txt
/usr/share/doc/mount/mount.txt
/usr/share/doc/openssl/fingerprints.txt
/usr/share/doc/powermgmt-base/power_supply.txt
/usr/share/doc/publicsuffix/examples/test_psl.txt
/usr/share/doc/sssd-common/BUILD.txt
/usr/share/doc/util-linux/00-about-docs.txt
/usr/share/doc/util-linux/PAM-configuration.txt
/usr/share/doc/util-linux/blkid.txt
/usr/share/doc/util-linux/cal.txt
/usr/share/doc/util-linux/col.txt
/usr/share/doc/util-linux/deprecated.txt
/usr/share/doc/util-linux/getopt.txt
/usr/share/doc/util-linux/getopt_changelog.txt
/usr/share/doc/util-linux/howto-build-sys.txt
/usr/share/doc/util-linux/howto-compilation.txt
/usr/share/doc/util-linux/howto-debug.txt
/usr/share/doc/util-linux/howto-man-page.txt
/usr/share/doc/util-linux/howto-tests.txt
/usr/share/doc/util-linux/hwclock.txt
/usr/share/doc/util-linux/modems-with-agetty.txt
/usr/share/doc/util-linux/mount.txt
/usr/share/doc/util-linux/pg.txt
/usr/share/doc/util-linux/release-schedule.txt
/usr/share/gnupg/help.be.txt
/usr/share/gnupg/help.ca.txt
/usr/share/gnupg/help.cs.txt
/usr/share/gnupg/help.da.txt
/usr/share/gnupg/help.de.txt
/usr/share/gnupg/help.el.txt
/usr/share/gnupg/help.eo.txt
/usr/share/gnupg/help.es.txt
/usr/share/gnupg/help.et.txt
/usr/share/gnupg/help.fi.txt
/usr/share/gnupg/help.fr.txt
/usr/share/gnupg/help.gl.txt
/usr/share/gnupg/help.hu.txt
/usr/share/gnupg/help.id.txt
/usr/share/gnupg/help.it.txt
/usr/share/gnupg/help.ja.txt
/usr/share/gnupg/help.nb.txt
/usr/share/gnupg/help.pl.txt
/usr/share/gnupg/help.pt.txt
/usr/share/gnupg/help.pt_BR.txt
/usr/share/gnupg/help.ro.txt
/usr/share/gnupg/help.ru.txt
/usr/share/gnupg/help.sk.txt
/usr/share/gnupg/help.sv.txt
/usr/share/gnupg/help.tr.txt
/usr/share/gnupg/help.txt
/usr/share/gnupg/help.zh_CN.txt
/usr/share/gnupg/help.zh_TW.txt
/usr/share/ibus-table/tables/template.txt
/usr/share/ieee-data/iab.txt
/usr/share/ieee-data/mam.txt
/usr/share/ieee-data/oui.txt
/usr/share/ieee-data/oui36.txt
/usr/share/perl/5.40.1/Unicode/Collate/allkeys.txt
/usr/share/perl/5.40.1/Unicode/Collate/keys.txt
/usr/share/perl/5.40.1/unicore/Blocks.txt
/usr/share/perl/5.40.1/unicore/NamedSequences.txt
/usr/share/perl/5.40.1/unicore/SpecialCasing.txt
/usr/share/snmp/mibs/LM-SENSORS-MIB.txt
/usr/share/snmp/mibs/NET-SNMP-AGENT-MIB.txt
/usr/share/snmp/mibs/NET-SNMP-EXAMPLES-MIB.txt
/usr/share/snmp/mibs/NET-SNMP-EXTEND-MIB.txt
/usr/share/snmp/mibs/NET-SNMP-MIB.txt
/usr/share/snmp/mibs/NET-SNMP-PASS-MIB.txt
/usr/share/snmp/mibs/NET-SNMP-TC.txt
/usr/share/snmp/mibs/NET-SNMP-VACM-MIB.txt
/usr/share/snmp/mibs/UCD-DEMO-MIB.txt
/usr/share/snmp/mibs/UCD-DISKIO-MIB.txt
/usr/share/snmp/mibs/UCD-DLMOD-MIB.txt
/usr/share/snmp/mibs/UCD-IPFWACC-MIB.txt
/usr/share/snmp/mibs/UCD-SNMP-MIB.txt
/usr/share/vim/vim91/doc/help.txt
/usr/share/vim/vim91/doc/sponsor.txt
/usr/share/vim/vim91/doc/uganda.txt
/usr/share/vim/vim91/doc/version9.txt
/usr/src/linux-headers-6.17.0-14/arch/sh/include/mach-ecovec24/mach/partner-jet-setup.txt
/usr/src/linux-headers-6.17.0-14/arch/sh/include/mach-kfr2r09/mach/partner-jet-setup.txt
/usr/src/linux-headers-6.17.0-14/scripts/head-object-list.txt
/usr/src/linux-headers-6.17.0-14/scripts/spelling.txt
/usr/src/linux-headers-6.17.0-14-generic/scripts/head-object-list.txt
/usr/src/linux-headers-6.17.0-14-generic/scripts/spelling.txt
/var/cache/dictionaries-common/ispell-dicts-list.txt
/var/lib/cloud/instances/iid-datasource-none/cloud-config.txt
/var/lib/cloud/instances/iid-datasource-none/user-data.txt
/var/lib/cloud/instances/iid-datasource-none/vendor-data.txt
/var/lib/cloud/instances/iid-datasource-none/vendor-data2.txt
/var/lib/ieee-data/iab.txt
/var/lib/ieee-data/mam.txt
/var/lib/ieee-data/oui.txt
/var/lib/ieee-data/oui36.txt
/var/log/installer/installer-journal.txt
```

