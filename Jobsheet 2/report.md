# JOBSHEET 2 - Manajemen Perangkat Keras & Perintah Dasar Sistem Operasi
---
## Praktium 2.1: Identifikasi CPU dan Memori

### Tampilkan informasi CPU :
```bash
lscpu 
```
![lcpu](images/lscpu.png)

### Tampilkan ringkasan memori : 
```bash
free -h
```
![free-h](images/free-h.png)

### Cek informasi Hardware : 
```bash
sudo dmidecode -t system
```
![informasiBios](images/InformasiBios.png)

### Latihan
#### Catat: (1) jumlah CPU(s), core/thread, (2) total RAM, (3) total swap. Jelaskan perbedaan RAM vs swap dalam 2–3 kalimat.
> Jumlah core     : 4<br>
> Jumlah Thread   : 8<br>
> Ram             : 4 GB<br>
> Swap            : 4 GB<br>

Ram memiliki hardware tersendiri yang berfungsi untuk menyimpan data sementara sedangkan swap menggunakan ssd/hardisk untuk menjalankan fungsi dari ram.

---
## Praktikum 2.2 : Identifikasi Perangkat PCI/USB dan Driver

### Lihat daftar perangkat PCI :
```bash
lspci
```
![lspci](images/lspci.png)

### Lihat perangkat PCI beserta driver kernel yang digunakan :
```bash
lspci - nnk
```
![lspcinnk](images/lspcinnk.png)

### Mencari modul driver : 
```bash 
lspci - nnk | grep - A3 -i ethernet
```
![modulDriver](images/modulDriver.png)

### Lihat perangkat USB :
```bash
lsusb
```
![modulDriver](images/lsusb.png)

### Lihat topologi USB (tree) :
```bash
lsusb -t
```
![topologiUSB](images/lsusb.png)

#### Temukan 1 perangkat PCI (misal NIC) dan tuliskan: Vendor:Device ID (angka heksadesimal), nama driver/modul kernel, dan deskripsi singkat fungsinya.
> Vendor ID       : 1af4 (Red hat)<br>
> Device ID       : 1000 (Virtio Network Device)<br>
> Nama Driver     : virtio-pci<br>

**Deskripsi Singkat Fungsi**: Perangkat ini berfungsi sebagai kartu jaringan (NIC) virtual yang menghubungkan mesin virtual Ubuntu Anda ke jaringan, memungkinkan komunikasi data (internet/LAN) dengan kecepatan tinggi melalui protokol VirtIO.

---
## Praktikum 2.3 : Identifikasi Storage dan Filesystem 
### Lihat daftar disk/partisi :
```bash
lsblk -f
```
![lsblk-f](images/lsblk-f.png)

### Tampilkan UUID dan tipe filesystem :
```bash
sudo blkid
```
![blkid](images/blkid.png)

### Lihat mount point untuk root filesystem :
```bash
findmnt /
```
![findmnt](images/findmnt.png)

---
## Praktikum 2.4 : Melihat Modul Aktif dan Informasinya
### Cek versi kernel :
```bash
uname -r
```
![uname-r](images/uname-r.png)

### Tampilkan daftar modul aktif :
```bash
lsmod | head
```
![lsmod](images/lsmod.png)

### Pilih salah satu modul : 
```bash
modinfo loop
```
![modinfo](images/modinfo.png)

### Muat modul, lalu verifikasi:
```bash
sudo modprobe loop
lsmod | grep -i loop
```
![muatModul](images/muatModul.png)

---
## Praktikum : Konfigurasi Auto-load dan Blacklist
### Buat file auto-load : 
```bash
echo " loop " | sudo tee / etc / modules - load . d / loop . conf
```
![autoLoad](images/autoLoad.png)

### Simulasikan verifikasi (tanpa reboot) dengan memastikan modul sudah aktif :
```bash
lsmod | grep -i loop
```
![verifModul](images/verifModul.png)

---
## Praktikum 2.6 : Mengenali Block vs Character Device
### Lihat detail device node disk :
```bash
ls -l /dev/sda
```
![nodeDisk](images/nodeDisk.png)
*dikarenakan di UTM nama foldernya bukan sda tetapi vda jadi saya ganti sesuai kondisi*

### Lihat detail device terminal : 
```bash
lls -l /dev/tty
```
![deviceTerminal](images/deviceTerminal.png)

### Lihat disk dan partisi untuk mengaitkan dengan /dev :
```bash
lsblk
```
![lsblk](images/lsblk.png)

### Latihan 2.3 
>Verifikasi modul dilakukan dengan lsmod | grep -i loop, di mana penggunaan sudo modprobe loop yang tidak mengeluarkan output menandakan modul berhasil dimuat. Penulisan path perangkat pada terminal wajib menyambung tanpa spasi (contoh: /dev/tty) agar tidak terjadi error cannot access. Pada lingkungan UTM, disk utama biasanya terdeteksi sebagai /dev/vda, yang dapat dipastikan melalui perintah lsblk. Perbedaan jenis perangkat terlihat pada karakter pertama izin file di ls -l, yaitu b untuk block device (penyimpanan data per blok seperti HDD/SSD) dan c untuk character device (aliran data per karakter seperti terminal).

---
## Praktikum 2.7 : Melihat Informasi udev
### Cek atribut udev untuk disk :
```bash
udevadm info --query=all --name=/dev/sda | head -n 30
```
![udevAtribut](images/udevAttribut.png)
*dikarenakan di UTM nama foldernya bukan sda tetapi vda jadi saya ganti sesuai kondisi*

### Monitor event udev (jalankan, lalu colok/lepas USB pada mesin fisik) :
```bash
sudo udevadm monitor
```
![udevEvent](images/udevEvent.png)

---
## Praktikum 2.8 :  Membuat Workspace Praktikum
### Buat direktori praktikum dan masuk ke dalamnya :
```bash
mkdir -p ~/praktikum-os/week02
cd ~/praktikum-os/week02
pwd
```
![mkdirPraktikum](images/mkdirPraktikum.png)

### Buat beberapa file contoh :
```bash
touch notes.txt data.log config.txt
ls -lah
```
![fileContoh](images/fileContoh.png)

### Isi file log contoh (simulasi):
```bash
echo "INFO: service started" >> data.log
echo "WARN: disk usage high" >> data.log
echo "ERROR: failed to connect" >> data.log
cat data.log
```
![dataLog](images/dataLog.png)

### Baca file dengan less:
```bash
less data.log
```
![lessDataLog](images/lessDataLog.png)

---
## Praktikum 2.9 : Pencarian Pola dengan grep
### Cari baris yang mengandung ERROR pada data.log :
```bash
grep "ERROR" data.log
```
![grepERROR](images/grepERROR.png)

### Cari tanpa memperhatikan huruf besar/kecil :
```bash
grep -i "error" data.log
```
![grepErrorLowerCase](images/grepErrorLC.png)

### Tampilkan nomor baris :
```bash
grep -n "WARN" data.log
```
![grepWarn](images/grepWarn.png)

### Tampilkan baris yang tidak cocok (invert match) :
```bash
grep -v "INFO" data.log
```
![grepInfo](images/grepInfo.png)

### Latihan 2.4 :
> Gunakan grep untuk menampilkan hanya baris yang mengandung INFO atau WARN dari data.log. (Hint: gunakan grep -E dengan pola alternatif)
#### Gunakan Command : 
```bash
grep -E "INFO|WARN" data.log
```
![latihan2.4](images/latihan2.4.png)

---
## Praktikum 2.10 : Substitusi dengan sed (Aman di File Latihan)
### Siapkan file konfigurasi latihan :
```bash
cat > config.txt << 'EOF'
PORT=8080
MODE=dev
SERVICE_NAME=myserver
EOF
cat config.txt
```
![mkdirConfigLatihan](images/mkdirConfigLatihan.png)

### Ganti dev menjadi prod (tanpa mengubah file asli) :
```bash
sed 's/MODE=dev/MODE=prod/' config.txt
```
![sedSubtitusi](images/sedSubtitusi.png)

### Terapkan perubahan langsung ke file (-i) :
```bash
sed -i 's/MODE=dev/MODE=prod/' config.txt
cat config.txt
```
![sedInPlace](images/sedInPlace.png)

### Ganti semua kemunculan kata (g untuk global), contoh ubah myserver menjadi node:
```bash
sed -i 's/myserver/node/g' config.txt
cat config.txt
```
![sedGlobal](images/sedGlobal.png)

---
## Praktium 2.11 :  Ekstraksi Kolom dengan awk
### Lihat output df -h :
```bash 
 df -h
```
![df-h](images/df-h.png)

### Ambil kolom filesystem dan persentase pemakaian :
```bash
df -h | awk 'NR==1 {printf "%-20s %-10s %-10s\n", $1, $5, $6} NR>1 {printf "%-20s %-10s %-10s\n", $1, $5, $6}'
```
![awkPrintSebagian](images/awkPrintSebagian.png)

### Filter hanya yang pemakaian disk di atas 80% :
```bash
df -h | awk 'NR==1 || ($5+0) > 80 {print $1, $5, $6}'
```
![awkFilter](images/awkFilter.png)

---
## Praktikum 2.12 :  Melihat Proses dengan ps
###  Tampilkan semua proses (format BSD) :
```bash
ps aux | head
```
![psAux](images/psAux.png)

### Cari proses tertentu (misal sshd) : 
```bash
ps aux | grep -i sshd
```
![psAuxFilter](images/psAuxFilter.png)

---
## Praktikum 2.13 : Monitoring Real-time dengan top
### Jalankan top :
```bash
top
```
![top](images/top.png)

### Htop :
```bash
htop
```
![htop](images/htop.png)

### Btop : 
```bash
btop
```
![btop](images/btop.png)

---
## Praktikum 2.14 : Menghentikan Proses dengan kill
### Jalankan proses dummy di background :
```bash
sleep 300 &
```
![sleepPID](images/sleepPID.png)

### Cari PID proses sleep :
```bash
ps aux | grep -E "sleep 300" | grep -v grep
```
![findSleepPID](images/findSleepPID.png)

### Hentikan dengan SIGTERM :
```bash
kill < PID_ANDA >
```
![killByPID](images/killByPID.png)<br>
*PID saya : 32963*

### Verifikasi proses berhenti :
```bash
ps aux | grep -E "sleep 300" | grep -v grep
```
![verifBerhenti](images/verifBerhenti.png)<br>
*Data sudah tidak ada karena sudah di kill sebelumnya*

### Jika proses sulit untuk dihentikan dan Anda membutukan untuk menghentikan proses tersebut, gunakan SIGKILL:
```bash
kill -9 < PID_ANDA >
```
![fillForce](images/killForce.png)<br>
*PID saya sebelumnya : 32963*

---
## Praktikum 2.15 : Cek Disk, Load, dan Service
### Cek penggunaan disk : 
```bash
df -h
```
![df-h](images/df-h.png)

### Cari direktori yang besar (contoh pada /var) :
```bash
sudo du -sh /var/* 2>/dev/null | sort -h | tail -n 10
```
![cekUkuranDirectory](images/cekUkuranDirectory.png)

### Cek load dan uptime :
```bash
uptime
```
![upTime](images/upTime.png)

### Cek service yang gagal :
```bash
systemctl --failed
```
![serviceFailedCek](images/serviceFailedCek.png)

###  Ambil log error terbaru (jika ada indikasi masalah) :
```bash
journalctl -xe | tail -n 50
```
![logError](images/logError.png)

---
## Praktikum 2.16 :  Monitoring Port dan Koneksi (Network Basics)
### Lihat interface dan IP :
```bash
ip a
```
![ip-a](images/ipA.png)

### Lihat routing table :
```bash
ip r
```
![ip-r](images/ip-r.png)

### Lihat port yang sedang listening :
```bash
sudo ss -tulpn
```
![cekPort](images/cekPort.png)

### Latihan 2.5 
> Pilih satu port yang listening dari output `ss -tulpn`(misal port 22), lalu tuliskan service/proses yang membukanya. Jelaskan kegunaan port tersebut secara singkat.
>> **Jawaban** <br> Port : 631 <br> Service : Cupsd <br> Kegunaan : Kegunaannya adalah untuk mengelola layanan pencetakan (printer) di sistem Linux. 

---
## 1.9 Latihan
### Latihan 2.A
> Jalankan `lspci -nnk`. Pilih 1 perangkat PCI dan tuliskan: nama perangkat, ID vendor:device, dan kernel driver in use.
>> **Jawaban** <br> Nama Perangkat : Ethernet controller: Red Hat, Inc. Virtio network device <br> ID Vendor : Device [1af4:1000] <br> Kernel driver in use: virtio-pci

### Latihan 2.B
> Tentukan device root filesystem dengan `findmnt /`. Lalu cocokkan dengan `lsblk -f` dan tuliskan tipe filesystem serta UUID-nya.
>> **Jawaban** <br> Device Root Filesystem: /dev/vda2 <br> Tipe Filesystem: ext4 <br> UUID: 39854352-d547-4bd4-ba0b-99a736100e4a

### Latihan 2.C
> Buat file server.log berisi minimal 10 baris dengan variasi kata: INFO, WARN, ERROR. Gunakan `grep` untuk menampilkan hanya baris ERROR.
>> **Jawaban :** <br> ![gambar1](images/L2-C1.png) <br> ![gambar1](images/L2-C2.png)

### Latihan 2.D
> Gunakan `sed` untuk mengganti semua kata server menjadi node pada file latihan. Tunjukkan sebelum dan sesudah.
>> **Jawaban :** <br> ![gambar1](images/L2-D.png)

### Latihan 2.E
> Gunakan `df -h` lalu awk untuk menampilkan filesystem yang penggunaan disk di atas 70%.
>> **Jawaban :** <br> ![gambar1](images/L-2E.png) <br> *Tidak ada disk yang mencapai 70%*

### Latihan 2.F
> Jalankan `sleep 600` &. Temukan PID-nya dengan `ps`. Hentikan dengan SIGTERM. Jelaskan beda SIGTERM vs SIGKILL.
>> **jawaban :** <br> ![gambar1](images/L2-F.png) <br> SIGTERM hanya bersifat sopan sedangkan SIGKILL bersifat memaksa (Force)

### Latihan 2.G
> Gunakan `systemctl –failed`. Jika tidak ada yang gagal, pilih satu service aktif (misal ssh) dan tampilkan status serta 30 baris log terakhirnya
>> **jawaban :** <br> ![gambar1](images/L2-G1.png) <br> *Tidak ada layanan yang gagal (0 loaded units listed)* <br> ![gambar1](images/L2-G2.png) <br> **Service yang dipilih**: cups (Common Unix Printing System).<br> **Status**: Active (Running). <br> **Kegunaan**: Mengelola antrean cetak dan koneksi ke printer pada sistem Linux. <br> **Main PID**: 8217<br> **Ringkasan Log (30 baris terakhir)**:
>>> * Log terbaru menunjukkan cups.service berhasil dimulai (Started) pada pukul 08:11:53.<br>
>>> * Status terakhir menunjukkan penjadwal (scheduler) sedang berjalan dengan pesan: "Scheduler is running...".
