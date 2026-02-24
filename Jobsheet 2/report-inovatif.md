# Laporan Jobsheet 2

> **Mata Kuliah:** Sistem Operasi  
> **Topik:** Manajemen Perangkat Keras & Perintah Dasar Sistem Operasi

---

## Daftar Isi
1. [Praktikum 2.1 - Identifikasi CPU dan Memori](#praktikum-21---identifikasi-cpu-dan-memori)
2. [Praktikum 2.2 - Identifikasi Perangkat PCI/USB dan Driver](#praktikum-22---identifikasi-perangkat-pciusb-dan-driver)
3. [Praktikum 2.3 - Identifikasi Storage dan Filesystem](#praktikum-23---identifikasi-storage-dan-filesystem)
4. [Praktikum 2.4 - Melihat Modul Aktif dan Informasinya](#praktikum-24---melihat-modul-aktif-dan-informasinya)
5. [Praktikum 2.5 - Konfigurasi Auto-load dan Blacklist](#praktikum-25---konfigurasi-auto-load-dan-blacklist)
6. [Praktikum 2.6 - Mengenali Block vs Character Device](#praktikum-26---mengenali-block-vs-character-device)
7. [Praktikum 2.7 - Melihat Informasi udev](#praktikum-27---melihat-informasi-udev)
8. [Praktikum 2.8 - Membuat Workspace Praktikum](#praktikum-28---membuat-workspace-praktikum)
9. [Praktikum 2.9 - Pencarian Pola dengan grep](#praktikum-29---pencarian-pola-dengan-grep)
10. [Praktikum 2.10 - Substitusi dengan sed](#praktikum-210---substitusi-dengan-sed-aman-di-file-latihan)
11. [Praktikum 2.11 - Ekstraksi Kolom dengan awk](#praktikum-211---ekstraksi-kolom-dengan-awk)
12. [Praktikum 2.12 - Melihat Proses dengan ps](#praktikum-212---melihat-proses-dengan-ps)
13. [Praktikum 2.13 - Monitoring Real-time dengan top](#praktikum-213---monitoring-real-time-dengan-top)
14. [Praktikum 2.14 - Menghentikan Proses dengan kill](#praktikum-214---menghentikan-proses-dengan-kill)
15. [Praktikum 2.15 - Cek Disk, Load, dan Service](#praktikum-215---cek-disk-load-dan-service)
16. [Praktikum 2.16 - Monitoring Port dan Koneksi](#praktikum-216---monitoring-port-dan-koneksi-network-basics)
17. [Latihan Tambahan (2.A - 2.G)](#latihan-tambahan-19-latihan)

---

## Praktikum 2.1 - Identifikasi CPU dan Memori

### Tampilkan informasi CPU
```bash
lscpu
```
![lscpu](images/lscpu.png)

### Tampilkan ringkasan memori
```bash
free -h
```
![free-h](images/free-h.png)

### Cek informasi hardware
```bash
sudo dmidecode -t system
```
![informasiBios](images/InformasiBios.png)

### Latihan
**Catatan hasil:**
- Jumlah core: 4
- Jumlah thread: 8
- RAM: 4 GB
- Swap: 4 GB

**Penjelasan RAM vs swap:**  
RAM memiliki hardware tersendiri untuk menyimpan data sementara, sedangkan swap menggunakan SSD/HDD sebagai memori cadangan saat RAM utama tidak mencukupi.

---

## Praktikum 2.2 - Identifikasi Perangkat PCI/USB dan Driver

### Lihat daftar perangkat PCI
```bash
lspci
```
![lspci](images/lspci.png)

### Lihat perangkat PCI beserta driver kernel yang digunakan
```bash
lspci -nnk
```
![lspcinnk](images/lspcinnk.png)

### Mencari modul driver
```bash
lspci -nnk | grep -A3 -i ethernet
```
![modulDriver](images/modulDriver.png)

### Lihat perangkat USB
```bash
lsusb
```
![lsusb](images/lsusb.png)

### Lihat topologi USB (tree)
```bash
lsusb -t
```
![topologiUSB](images/lsusb.png)

### Latihan
**Perangkat PCI yang dipilih:**
- Vendor ID: `1af4` (Red Hat)
- Device ID: `1000` (Virtio Network Device)
- Nama driver: `virtio-pci`

**Deskripsi fungsi:**  
Perangkat ini berfungsi sebagai NIC virtual yang menghubungkan mesin virtual Ubuntu ke jaringan (internet/LAN) dengan performa tinggi melalui VirtIO.

---

## Praktikum 2.3 - Identifikasi Storage dan Filesystem

### Lihat daftar disk/partisi
```bash
lsblk -f
```
![lsblk-f](images/lsblk-f.png)

### Tampilkan UUID dan tipe filesystem
```bash
sudo blkid
```
![blkid](images/blkid.png)

### Lihat mount point untuk root filesystem
```bash
findmnt /
```
![findmnt](images/findmnt.png)

---

## Praktikum 2.4 - Melihat Modul Aktif dan Informasinya

### Cek versi kernel
```bash
uname -r
```
![uname-r](images/uname-r.png)

### Tampilkan daftar modul aktif
```bash
lsmod | head
```
![lsmod](images/lsmod.png)

### Pilih salah satu modul
```bash
modinfo loop
```
![modinfo](images/modinfo.png)

### Muat modul, lalu verifikasi
```bash
sudo modprobe loop
lsmod | grep -i loop
```
![muatModul](images/muatModul.png)

---

## Praktikum 2.5 - Konfigurasi Auto-load dan Blacklist

### Buat file auto-load
```bash
echo "loop" | sudo tee /etc/modules-load.d/loop.conf
```
![autoLoad](images/autoLoad.png)

### Simulasikan verifikasi (tanpa reboot)
```bash
lsmod | grep -i loop
```
![verifModul](images/verifModul.png)

---

## Praktikum 2.6 - Mengenali Block vs Character Device

### Lihat detail device node disk
```bash
ls -l /dev/sda
```
![nodeDisk](images/nodeDisk.png)

> Di lingkungan UTM, nama disk terdeteksi sebagai `/dev/vda`, sehingga disesuaikan dengan kondisi mesin.

### Lihat detail device terminal
```bash
ls -l /dev/tty
```
![deviceTerminal](images/deviceTerminal.png)

### Lihat disk dan partisi untuk mengaitkan dengan `/dev`
```bash
lsblk
```
![lsblk](images/lsblk.png)

### Latihan 2.3
Verifikasi modul dilakukan dengan `lsmod | grep -i loop`, di mana `sudo modprobe loop` yang tidak mengeluarkan output menandakan modul berhasil dimuat. Penulisan path perangkat pada terminal wajib tanpa spasi (contoh: `/dev/tty`) agar tidak terjadi error `cannot access`. Pada lingkungan UTM, disk utama biasanya terdeteksi sebagai `/dev/vda`, yang dapat dipastikan melalui `lsblk`. Perbedaan perangkat terlihat dari karakter awal pada `ls -l`: `b` untuk block device (media penyimpanan) dan `c` untuk character device (aliran karakter seperti terminal).

---

## Praktikum 2.7 - Melihat Informasi udev

### Cek atribut udev untuk disk
```bash
udevadm info --query=all --name=/dev/sda | head -n 30
```
![udevAtribut](images/udevAttribut.png)

> Di lingkungan UTM, nama disk terdeteksi sebagai `/dev/vda`, sehingga disesuaikan dengan kondisi mesin.

### Monitor event udev
```bash
sudo udevadm monitor
```
![udevEvent](images/udevEvent.png)

---

## Praktikum 2.8 - Membuat Workspace Praktikum

### Buat direktori praktikum dan masuk ke dalamnya
```bash
mkdir -p ~/praktikum-os/week02
cd ~/praktikum-os/week02
pwd
```
![mkdirPraktikum](images/mkdirPraktikum.png)

### Buat beberapa file contoh
```bash
touch notes.txt data.log config.txt
ls -lah
```
![fileContoh](images/fileContoh.png)

### Isi file log contoh (simulasi)
```bash
echo "INFO: service started" >> data.log
echo "WARN: disk usage high" >> data.log
echo "ERROR: failed to connect" >> data.log
cat data.log
```
![dataLog](images/dataLog.png)

### Baca file dengan `less`
```bash
less data.log
```
![lessDataLog](images/lessDataLog.png)

---

## Praktikum 2.9 - Pencarian Pola dengan grep

### Cari baris yang mengandung ERROR pada `data.log`
```bash
grep "ERROR" data.log
```
![grepERROR](images/grepERROR.png)

### Cari tanpa memperhatikan huruf besar/kecil
```bash
grep -i "error" data.log
```
![grepErrorLowerCase](images/grepErrorLC.png)

### Tampilkan nomor baris
```bash
grep -n "WARN" data.log
```
![grepWarn](images/grepWarn.png)

### Tampilkan baris yang tidak cocok (invert match)
```bash
grep -v "INFO" data.log
```
![grepInfo](images/grepInfo.png)

### Latihan 2.4
Gunakan `grep` untuk menampilkan hanya baris yang mengandung INFO atau WARN dari `data.log`.

```bash
grep -E "INFO|WARN" data.log
```
![latihan2.4](images/latihan2.4.png)

---

## Praktikum 2.10 - Substitusi dengan sed (Aman di File Latihan)

### Siapkan file konfigurasi latihan
```bash
cat > config.txt << 'EOF'
PORT=8080
MODE=dev
SERVICE_NAME=myserver
EOF
cat config.txt
```
![mkdirConfigLatihan](images/mkdirConfigLatihan.png)

### Ganti `dev` menjadi `prod` (tanpa mengubah file asli)
```bash
sed 's/MODE=dev/MODE=prod/' config.txt
```
![sedSubtitusi](images/sedSubtitusi.png)

### Terapkan perubahan langsung ke file (`-i`)
```bash
sed -i 's/MODE=dev/MODE=prod/' config.txt
cat config.txt
```
![sedInPlace](images/sedInPlace.png)

### Ganti semua kemunculan kata (global)
```bash
sed -i 's/myserver/node/g' config.txt
cat config.txt
```
![sedGlobal](images/sedGlobal.png)

---

## Praktikum 2.11 - Ekstraksi Kolom dengan awk

### Lihat output `df -h`
```bash
df -h
```
![df-h](images/df-h.png)

### Ambil kolom filesystem dan persentase pemakaian
```bash
df -h | awk 'NR==1 {printf "%-20s %-10s %-10s\n", $1, $5, $6} NR>1 {printf "%-20s %-10s %-10s\n", $1, $5, $6}'
```
![awkPrintSebagian](images/awkPrintSebagian.png)

### Filter hanya yang pemakaian disk di atas 80%
```bash
df -h | awk 'NR==1 || ($5+0) > 80 {print $1, $5, $6}'
```
![awkFilter](images/awkFilter.png)

---

## Praktikum 2.12 - Melihat Proses dengan ps

### Tampilkan semua proses (format BSD)
```bash
ps aux | head
```
![psAux](images/psAux.png)

### Cari proses tertentu (misal `sshd`)
```bash
ps aux | grep -i sshd
```
![psAuxFilter](images/psAuxFilter.png)

---

## Praktikum 2.13 - Monitoring Real-time dengan top

### Jalankan `top`
```bash
top
```
![top](images/top.png)

### Jalankan `htop`
```bash
htop
```
![htop](images/htop.png)

### Jalankan `btop`
```bash
btop
```
![btop](images/btop.png)

---

## Praktikum 2.14 - Menghentikan Proses dengan kill

### Jalankan proses dummy di background
```bash
sleep 300 &
```
![sleepPID](images/sleepPID.png)

### Cari PID proses sleep
```bash
ps aux | grep -E "sleep 300" | grep -v grep
```
![findSleepPID](images/findSleepPID.png)

### Hentikan dengan SIGTERM
```bash
kill <PID_ANDA>
```
![killByPID](images/killByPID.png)

PID saya: `32963`

### Verifikasi proses berhenti
```bash
ps aux | grep -E "sleep 300" | grep -v grep
```
![verifBerhenti](images/verifBerhenti.png)

Data sudah tidak ada karena proses sudah dihentikan.

### Jika proses sulit dihentikan, gunakan SIGKILL
```bash
kill -9 <PID_ANDA>
```
![killForce](images/killForce.png)

PID saya sebelumnya: `32963`

---

## Praktikum 2.15 - Cek Disk, Load, dan Service

### Cek penggunaan disk
```bash
df -h
```
![df-h](images/df-h.png)

### Cari direktori yang besar (contoh pada `/var`)
```bash
sudo du -sh /var/* 2>/dev/null | sort -h | tail -n 10
```
![cekUkuranDirectory](images/cekUkuranDirectory.png)

### Cek load dan uptime
```bash
uptime
```
![upTime](images/upTime.png)

### Cek service yang gagal
```bash
systemctl --failed
```
![serviceFailedCek](images/serviceFailedCek.png)

### Ambil log error terbaru (jika ada indikasi masalah)
```bash
journalctl -xe | tail -n 50
```
![logError](images/logError.png)

---

## Praktikum 2.16 - Monitoring Port dan Koneksi (Network Basics)

### Lihat interface dan IP
```bash
ip a
```
![ip-a](images/ipA.png)

### Lihat routing table
```bash
ip r
```
![ip-r](images/ip-r.png)

### Lihat port yang sedang listening
```bash
sudo ss -tulpn
```
![cekPort](images/cekPort.png)

### Latihan 2.5
Pilih satu port listening dari output `ss -tulpn`, lalu tuliskan service/proses yang membukanya dan kegunaannya.

**Jawaban:**
- Port: `631`
- Service: `cupsd`
- Kegunaan: Mengelola layanan pencetakan (printer) di Linux.

---

## Latihan Tambahan (1.9 Latihan)

### Latihan 2.A
Jalankan `lspci -nnk`, pilih 1 perangkat PCI, lalu tuliskan nama perangkat, ID vendor:device, dan kernel driver in use.

**Jawaban:**
- Nama perangkat: Ethernet controller: Red Hat, Inc. Virtio network device
- ID vendor:device: `[1af4:1000]`
- Kernel driver in use: `virtio-pci`

### Latihan 2.B
Tentukan device root filesystem dengan `findmnt /`, cocokkan dengan `lsblk -f`, lalu tuliskan tipe filesystem dan UUID.

**Jawaban:**
- Device root filesystem: `/dev/vda2`
- Tipe filesystem: `ext4`
- UUID: `39854352-d547-4bd4-ba0b-99a736100e4a`

### Latihan 2.C
Buat file `server.log` berisi minimal 10 baris dengan variasi INFO, WARN, ERROR. Gunakan `grep` untuk menampilkan hanya baris ERROR.

**Jawaban:**
![gambar1](images/L2-C1.png)
![gambar2](images/L2-C2.png)

### Latihan 2.D
Gunakan `sed` untuk mengganti semua kata `server` menjadi `node` pada file latihan. Tunjukkan sebelum dan sesudah.

**Jawaban:**
![gambar1](images/L2-D.png)

### Latihan 2.E
Gunakan `df -h` lalu `awk` untuk menampilkan filesystem yang penggunaan disk di atas 70%.

**Jawaban:**
![gambar1](images/L-2E.png)

Tidak ada disk yang mencapai 70%.

### Latihan 2.F
Jalankan `sleep 600 &`, temukan PID dengan `ps`, hentikan dengan SIGTERM, lalu jelaskan beda SIGTERM vs SIGKILL.

**Jawaban:**
![gambar1](images/L2-F.png)

SIGTERM bersifat lebih sopan (memberi kesempatan proses cleanup), sedangkan SIGKILL bersifat memaksa.

### Latihan 2.G
Gunakan `systemctl --failed`. Jika tidak ada yang gagal, pilih satu service aktif (misal `ssh`) dan tampilkan status serta 30 baris log terakhir.

**Jawaban:**
![gambar1](images/L2-G1.png)

Tidak ada layanan yang gagal (`0 loaded units listed`).

![gambar2](images/L2-G2.png)

- Service yang dipilih: `cups` (Common Unix Printing System)
- Status: `active (running)`
- Kegunaan: Mengelola antrean cetak dan koneksi printer pada Linux
- Main PID: `8217`
- Ringkasan log 30 baris terakhir:
  - Log terbaru menunjukkan `cups.service` berhasil dimulai (`Started`) pukul 08:11:53
  - Status terakhir: scheduler berjalan dengan pesan `Scheduler is running...`

---

## Penutup
Dokumen ini adalah versi tampilan ulang dari `report.md` dengan isi inti yang tetap sama, namun disajikan lebih terstruktur dan mudah dibaca.
