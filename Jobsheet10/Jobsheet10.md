# Jobsheet 10

## Identitas

| Nama         | NIM          | Kelas |
| :----------- | :----------- | :---- |
| Ibni Andarta | 254107020258 | TI-1G |

---
## Melihat Penggunaan Memori

### Melihat penggunaan memori
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ free -h
               total        used        free      shared  buff/cache   available
Mem:           7.8Gi       441Mi       7.4Gi        24Mi        99Mi       7.4Gi
Swap:          8.8Gi          0B       8.8Gi
```

### Melihat detail memori kernel
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ cat /proc/meminfo | head -n 20
MemTotal:        8186700 kB
MemFree:         7787648 kB
MemAvailable:    7736328 kB
Buffers:              32 kB
Cached:            62100 kB
SwapCached:            0 kB
Active:            23328 kB
Inactive:         154964 kB
Active(anon):       4408 kB
Inactive(anon):   136792 kB
Active(file):      18920 kB
Inactive(file):    18172 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:       9235268 kB
SwapFree:        9235268 kB
Dirty:                 0 kB
Writeback:             0 kB
AnonPages:        115784 kB
Mapped:            11764 kB
```

Analisis :  
1. **Analisis Memori:**

   | Item | Deskripsi |
   | :--- | :--- |
   | **Available** | : 7.4 GiB |
   | **Total** | : 7.8 GiB |
   | **Persentase** | : $\left( \frac{7.4}{7.8} \right) \times 100\% \approx \mathbf{94.8\%}$ |
   | **Keterangan** | : Sistem memiliki 94.8% memori tersedia. |

2. **Status Penggunaan Swap**
   | Item | Deskripsi |
   | :--- | :--- |
   | **Used** | : 0B |
   | **Keterangan** | : Sistem belum menggunakan swap. |

3. **Korelasi Buffers dan Cached**

   | Item | Deskripsi |
   | :--- | :--- |
   | **Sumber Data** | : `/proc/meminfo` |
   | **Analisis** | : Nilai *Buffers* dan *Cached* diakumulasikan untuk mendapatkan total *buff/cache*. |

   **Tabel Perbandingan:**

   | Field di `/proc/meminfo` | Nilai (kB) | Konversi ke MiB (÷ 1024) |
   | :--- | :--- | :--- |
   | **Buffers** | 32 kB | ~0.03 MiB |
   | **Cached** | 62,100 kB | ~60.64 MiB |
   | **Total (Sum)** | **62,132 kB** | **~60.67 MiB** |

   **Keterangan:** Nilai total di atas akan muncul sebagai satu kesatuan dalam kolom `buff/cache` pada perintah `free -h`.



---
## Praktikum 10.2
### Melihat statistik memori virtual
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ vmstat 1 5
procs -----------memory---------- ---swap-- -----io---- -system-- -------cpu-------
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st gu
 1  0      0 7796032     28 100848    0    0   114     1    8    0  0  0 100  0  0  0
 0  0      0 7795992     28 100852    0    0     0     0   32   13  0  0 100  0  0  0
 0  0      0 7795992     28 100852    0    0     0     0   43   48  0  0 100  0  0  0
 0  0      0 7795992     28 100852    0    0     0     0   38   46  0  0 100  0  0  0
 0  0      0 7795992     28 100852    0    0     0     0   52   51  0  0 100  0  0  0
```

Analisis : 

1. **Aktivitas Swap (si/so):**
   | Item | Deskripsi |
   | :--- | :--- |
   | **Baris 1 - 5** | : Nilai `si` (swap-in) dan `so` (swap-out) semuanya adalah 0. |
   | **Analisis** | : Tidak ada aktivitas yang menyebabkan nilai `si` dan `so` di atas 0. |

2. **Statistik Memori (vmstat):**
   | Item | Deskripsi |
   | :--- | :--- |
   | **`free` (RAM Kosong)** | : 7.796.032 kB (sekitar 7.4 GiB) |
   | **`buff` (Buffer)** | : 28 kB |
   | **`cache`** | : 100.852 kB |

**Kesimpulan:**
Sistem bekerja secara optimal karena seluruh proses dijalankan langsung di RAM tanpa perlu menggunakan memori Swap.

---
## Praktikum 10.3 
### Membuat swap file 512MB
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week10$ sudo fallocate -l 512M /swapfile-week10
```

### Mengamankan permission swap file
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week10$ sudo chmod 600 /swapfile-week10
```

### Memformat dan mengaktifkan swap
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week10$ sudo dd if=/dev/zero of=swapfile-week10 bs=1M count=1024
1024+0 records in
1024+0 records out
1073741824 bytes (1.1 GB, 1.0 GiB) copied, 1.49103 s, 720 MB/s
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week10$ sudo chmod 600 swapfile-week10
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week10$ sudo mkswap swapfile-week10
Setting up swapspace version 1, size = 1024 MiB (1073737728 bytes)
no label, UUID=28509990-5732-4bd1-9b22-17966b986b32
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week10$ sudo swapon swapfile-week10
swapon: /Users/ibennn/OrbData/DataUser/Praktikum-SO/week10/swapfile-week10: swapon failed: Invalid argument
```

### Verifikasi swap aktif
```bash
o@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week10$ swapon --show
free -h
NAME       TYPE       SIZE USED  PRIO
/dev/zram0 partition  7.8G   0B 32767
/dev/vdc   partition 1024M   0B     1

               total        used        free      shared  buff/cache   available
Mem:           7.8Gi       445Mi       7.4Gi        24Mi       110Mi       7.4Gi
Swap:          8.8Gi          0B       8.8Gi
```

### Melihat dan mengubah swappiness
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week10$ cat /proc/sys/vm/swappiness
sudo sysctl vm.swappiness=10
cat /proc/sys/vm/swappiness
20
vm.swappiness = 10
10
```

Analisis:

1. **Nilai Swappiness Default**

   | Item | Deskripsi |
   | :--- | :--- |
   | **Nilai Default** | Berdasarkan output `cat` pertama sebelum diubah, nilai default-nya adalah **20**. |
   | **Arti bagi Perilaku Kernel** | Nilai swappiness berkisar antara 0 hingga 100. Nilai **20** tergolong cukup rendah (bawaan Ubuntu standar biasanya 60). Artinya, kernel cenderung **menunda** penggunaan swap dan akan memprioritaskan penggunaan RAM secara maksimal sebelum memindahkan data pasif ke swap. |

2. **Perubahan Nilai Swappiness ke 10**

   | Item | Deskripsi |
   | :--- | :--- |
   | **Konfirmasi Perubahan** | Nilai berhasil berubah. Terkonfirmasi pada output `cat` kedua yang memunculkan angka **10** setelah perintah `sudo sysctl vm.swappiness=10` dieksekusi. |
   | **Dampak Nilai 10 vs 60** | Nilai **10** membuat kernel menjadi **jauh lebih agresif untuk menahan data di dalam RAM** dan hanya menggunakan swap jika RAM benar-benar darurat hampir habis. Sebaliknya, jika nilainya **60**, kernel akan jauh lebih rajin dan cepat memindahkan proses-proses yang sedang *idle* (menganggur) dari RAM ke swap, meskipun RAM aslinya masih longgar. |

3. **Keberadaan Entri `/swapfile-week10`**

   | Item | Deskripsi |
   | :--- | :--- |
   | **Status di `swapon --show`** | **Tidak muncul.** Pada output `swapon --show`, hanya terdeteksi dua swap aktif yaitu `/dev/zram0` (7.8 GB) dan `/dev/vdc` (1024 MB). |
   | **Analisis Penyebab** | File `/swapfile-week10` tidak muncul karena perintah pembuatan swap di awal mengalami error akibat salah penulisan (terdapat spasi). Karena perintah `mkswap` dan `swapon` gagal dieksekusi oleh sistem, maka file tersebut belum terdaftar sebagai swap aktif di kernel. |

---

**Kesimpulan:**
Sistem saat ini memiliki total swap sebesar 8.8 GiB yang berasal dari `/dev/zram0` dan `/dev/vdc`. Dengan mengubah nilai `swappiness` menjadi 10, kernel diatur agar memaksimalkan kapasitas RAM 8 GB yang tersedia dan meminimalkan penggunaan swap, sehingga seluruh proses sistem berjalan secara optimal langsung pada memori utama.

---
## Praktikum 10.4
### Proses dengan memori terbesar
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week10$ ps aux --sort=-%mem | head
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         107  0.0  0.1 1245384 9944 ?        Ssl  May06   1:28 orbstack-agent: SO
so          8066  150  0.0  13620  3984 pts/1    R+   23:45   0:00 ps aux --sort=-%mem
root           1  0.0  0.0  21388  3496 ?        Ss   May06   0:47 /sbin/init
so          8021  0.0  0.0  10324  2780 pts/1    Ss   23:32   0:00 -bash
so           243  0.0  0.0  19912  1956 ?        Ss   May06   0:14 /usr/lib/systemd/systemd --user
so          8067  100  0.0   8308  1740 pts/1    S+   23:45   0:00 head
root         135  0.0  0.0  23632  1564 ?        Ss   May06   0:18 /usr/lib/systemd/systemd-udevd
so           244  0.0  0.0  22204  1504 ?        S    May06   0:05 (sd-pam)
syslog       240  0.0  0.0 222824  1368 ?        Ssl  May06   0:18 /usr/sbin/rsyslogd -n -iNONE
```

### Monitoring real-time
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week10$ top

top - 23:45:52 up 17 days,  9:58,  0 user,  load average: 0.00, 0.00, 0.00
Tasks:  14 total,   1 running,  13 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.0 us,  0.0 sy,  0.0 ni,100.0 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
MiB Mem :   7994.8 total,   7595.0 free,    449.5 used,    103.8 buff/cache     
MiB Swap:   9018.8 total,   9018.8 free,      0.0 used.   7545.3 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                                                   
      1 root      20   0   21388   3496    192 S   0.0   0.0   0:47.50 systemd                                                                                                   
    107 root      20   0 1245384   9944    280 S   0.0   0.1   1:28.73 orbstack-agent:                                                                                           
    119 root      19  -1  115632   1292    200 S   0.0   0.0   0:42.20 systemd-journal                                                                                           
    135 root      20   0   23632   1564     48 S   0.0   0.0   0:18.78 systemd-udevd                                                                                             
    219 systemd+  20   0   18712   1248     92 S   0.0   0.0   0:20.02 systemd-network                                                                                           
    227 root      20   0    9360    480    224 S   0.0   0.0   0:53.74 cron                                                                                                      
    228 message+  20   0    9508    816    188 S   0.0   0.0   0:13.81 dbus-daemon                                                                                               
    233 root      20   0   17784   1216    192 S   0.0   0.0   0:09.27 systemd-logind                                                                                            
    238 root      20   0    7904    156      8 S   0.0   0.0   0:02.19 agetty                                                                                                    
    240 syslog    20   0  222824   1736    556 S   0.0   0.0   0:18.72 rsyslogd                                                                                                  
    243 so        20   0   19912   1956    136 S   0.0   0.0   0:14.99 systemd                                                                                                   
    244 so        20   0   22204   1504      4 S   0.0   0.0   0:05.81 (sd-pam)                                                                                                  
   8021 so        20   0   10324   2896   2236 S   0.0   0.0   0:00.08 bash                                                                                                      
   8068 so        20   0   14768   5480   3208 R   0.0   0.1   0:00.01 top  
```

Analisis:

| No | Pertanyaan | Deskripsi / Jawaban |
| :--- | :--- | :--- |
| **1** | **Proses di Urutan Pertama** | Pada output `ps aux --sort=-%mem`, proses yang menempati urutan pertama adalah **`orbstack-agent`** (PID 107). <br>- **%MEM** = 0.1 <br>- **RSS** = 9944 |
| **2** | **Konversi RSS dan Kewajaran** | - **Konversi:** 9944 KB / 1024 = **9,71 MB**.<br>- **Kewajaran:** Sangat **wajar** (dan tergolong ringan). `orbstack-agent` adalah *background service* dari OrbStack (aplikasi container/VM environment) yang memang dirancang agar tidak memakan banyak resource RAM. |
| **3** | **Alasan VSZ > RSS** | **VSZ** (*Virtual Memory Size*) adalah total seluruh memori yang *didaftarkan/dialokasikan* untuk proses tersebut, yang mencakup memori kosong yang belum diisi, file *swap*, dan *shared libraries*. Sedangkan **RSS** (*Resident Set Size*) adalah porsi memori *fisik (RAM asli)* yang benar-benar sedang dipakai saat itu juga. Karena VSZ mencakup banyak hal abstrak selain RAM fisik, ukurannya selalu lebih besar dari RSS. |
| **4** | **Konsistensi `ps` dan `top`** | Pada tampilan di atas, urutannya **tidak konsisten/berbeda**. <br>- Perintah `ps` sudah dipaksa urut berdasarkan memori terbesar lewat flag `--sort=-%mem`.<br>- Tampilan `top` pada log di atas masih menggunakan *sorting* default bawaannya (terlihat berurut berdasarkan PID atau %CPU yang idle). Agar urutan `top` sama persis dengan `ps`, kamu harus menekan tombol **`Shift + M`** saat `top` sedang berjalan untuk mengurutkannya berdasarkan %MEM. |

---
## Praktikum 10.5
### Pindah ke direktori dan buka nano
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week10$ nano monitor-memori.sh
```

### Isi file monitor-memori.sh
```bash
#!/bin/bash
set -euo pipefail

THRESHOLD=20

echo "=== Monitor Memori ==="
date
echo
free -h
echo

AVAIL=$(free | awk '/Mem/ {printf "%d", $7/$2 * 100}')

if [ "$AVAIL" -lt "$THRESHOLD" ]; then
    echo "PERINGATAN: Memori tersedia hanya ${AVAIL}%!"
else
    echo "Status: Memori tersedia ${AVAIL}% (normal)"
fi

echo
echo "--- 5 Proses Memori Tertinggi ---"
ps aux --sort=-%mem | head -n 6 | tail -n 5
```

### Menjalankan script monitor
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week10$ chmod +x monitor-memori.sh
bash monitor-memori.sh
=== Monitor Memori ===
Sat May 23 23:50:28 WIB 2026

               total        used        free      shared  buff/cache   available
Mem:           7.8Gi       438Mi       7.4Gi        24Mi       102Mi       7.4Gi
Swap:          8.8Gi          0B       8.8Gi

Status: Memori tersedia 94% (normal)

--- 5 Proses Memori Tertinggi ---
root         107  0.0  0.1 1245384 9944 ?        Ssl  May06   1:28 orbstack-agent: SO
so          8077  0.0  0.0  13620  3960 pts/1    R+   23:50   0:00 ps aux --sort=-%mem
root           1  0.0  0.0  21388  3496 ?        Ss   May06   0:47 /sbin/init
so          8071  0.0  0.0  10060  3168 pts/1    S+   23:50   0:00 bash monitor-memori.sh
so          8021  0.0  0.0  10324  2896 pts/1    Ss   23:32   0:00 -bash
```

Analisis:

| No | Komponen / Pertanyaan | Deskripsi / Jawaban |
| :--- | :--- | :--- |
| **1** | **Logika Perhitungan Memori (awk)** | Variabel `THRESHOLD=20` digunakan sebagai batas persentase kritis. Perintah `awk` mengekstrak data dari baris `Mem:` pada perintah `free`. Ia membagi kolom `available` (sisa memori yang bisa dipakai) dengan kolom `total` (kapasitas RAM penuh), lalu dikalikan 100 untuk mendapatkan persentase bulat memori yang tersedia. Pada komputermu, hasilnya adalah **94%**. |
| **2** | **Kondisi Evaluasi (`if -lt`)** | Operator `-lt` singkatan dari *less than* (lebih kecil dari). Logika `if [ "$AVAIL" -lt "$THRESHOLD" ]` bertugas mengecek apakah sisa memori (94) lebih kecil dari batas (20). Karena 94 tidak lebih kecil dari 20, kondisi ini bernilai salah (*false*), sehingga *script* mengeksekusi blok `else` yang memunculkan tulisan **(normal)**. |
| **3** | **Dampak Perubahan THRESHOLD ke 90** | Jika kamu mengubah nilai THRESHOLD menjadi 90, outputnya kemungkinan besar **tidak akan berubah** (tetap "normal"). Alasannya karena memori tersedia kamu saat ini adalah **94%**. Angka 94 masih belum berada di bawah 90 (`94 -lt 90` tetap *false*). <br><br>*(Catatan: Status baru akan berubah menjadi **peringatan** jika kamu menyetel THRESHOLD ke angka yang lebih besar dari persentase AVAIL kamu saat ini, misalnya **95**. Jika diset 95, maka `94 -lt 95` akan bernilai benar/true).* |

---
## Praktikum 10.6
### Detail system call ls
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week10$ strace ls 2>&1 | head -n 30
execve("/usr/bin/ls", ["ls"], 0xffffdc5e2230 /* 29 vars */) = 0
brk(NULL)                               = 0xaaaac716a000
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xffffbe553000
faccessat(AT_FDCWD, "/etc/ld.so.preload", R_OK) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=10023, ...}) = 0
mmap(NULL, 10023, PROT_READ, MAP_PRIVATE, 3, 0) = 0xffffbe550000
close(3)                                = 0
openat(AT_FDCWD, "/lib/aarch64-linux-gnu/libselinux.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0\267\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=198800, ...}) = 0
mmap(NULL, 337472, PROT_NONE, MAP_PRIVATE|MAP_ANONYMOUS|MAP_DENYWRITE, -1, 0) = 0xffffbe4ca000
mmap(0xffffbe4d0000, 271936, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0) = 0xffffbe4d0000
munmap(0xffffbe4ca000, 24576)           = 0
munmap(0xffffbe513000, 38464)           = 0
mprotect(0xffffbe4fc000, 77824, PROT_NONE) = 0
mmap(0xffffbe50f000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2f000) = 0xffffbe50f000
mmap(0xffffbe511000, 5696, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xffffbe511000
close(3)                                = 0
openat(AT_FDCWD, "/lib/aarch64-linux-gnu/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0\267\0\1\0\0\0\360\206\2\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=1722920, ...}) = 0
mmap(NULL, 1892240, PROT_NONE, MAP_PRIVATE|MAP_ANONYMOUS|MAP_DENYWRITE, -1, 0) = 0xffffbe302000
mmap(0xffffbe310000, 1826704, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0) = 0xffffbe310000
munmap(0xffffbe302000, 57344)           = 0
munmap(0xffffbe4ce000, 8080)            = 0
mprotect(0xffffbe4aa000, 77824, PROT_NONE) = 0
mmap(0xffffbe4bd000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x19d000) = 0xffffbe4bd000
mmap(0xffffbe4c2000, 49040, PROT_READ|PROT_WRI
```

### Ringkasan dan perbandingan system call
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week10$ strace -c ls
strace -c ls /etc 2>&1 | tail -5
monitor-memori.sh  swapfile-week10
% time     seconds  usecs/call     calls    errors syscall
------ ----------- ----------- --------- --------- ----------------
 30.74    0.001064          31        34        12 openat
 22.02    0.000762         762         1           execve
 21.58    0.000747         373         2           getdents64
  8.96    0.000310          44         7           read
  4.39    0.000152           5        28           mmap
  3.12    0.000108          13         8           mprotect
  2.86    0.000099          49         2         2 statfs
  2.22    0.000077           3        24           close
  1.18    0.000041           1        23           fstat
  0.78    0.000027           3         7           munmap
  0.58    0.000020          10         2         2 faccessat
  0.55    0.000019          19         1           write
  0.29    0.000010          10         1           futex
  0.20    0.000007           3         2           ioctl
  0.20    0.000007           2         3           brk
  0.12    0.000004           4         1           getrandom
  0.06    0.000002           2         1           set_tid_address
  0.06    0.000002           2         1           set_robust_list
  0.06    0.000002           2         1           prlimit64
  0.03    0.000001           1         1           rseq
------ ----------- ----------- --------- --------- ----------------
100.00    0.003461          23       150        16 total
  0.12    0.000001           1         1           prlimit64
  0.12    0.000001           1         1           rseq
  0.00    0.000000           0         1           execve
------ ----------- ----------- --------- --------- ----------------
100.00    0.000867           5       150        17 total
```

Analisis:

| No | Pertanyaan | Deskripsi / Jawaban |
| :--- | :--- | :--- |
| **1** | **Identifikasi 4 System Call dan Fungsinya** | Dari output pertama, terdapat beberapa *system call*, di antaranya:<br>1. **`execve`**: Mengeksekusi program utama (dalam hal ini `"/usr/bin/ls"`).<br>2. **`openat`**: Membuka file atau direktori (contoh: membuka file konfigurasi `"/etc/ld.so.cache"`).<br>3. **`mmap`**: Mengalokasikan ruang di memori/RAM (memetakan file *shared library* ke dalam memori agar bisa dieksekusi).<br>4. **`read`**: Membaca data dari file yang sudah dibuka (contoh: membaca *header* file `ELF` yang berukuran 832 byte). |
| **2** | **System Call Paling Sering Dipanggil** | Berdasarkan output `strace -c`, *system call* yang paling sering dipanggil adalah **`openat`** (sebanyak 34 *calls*).<br>**Alasan:** Saat `ls` dijalankan, ia tidak hanya membaca direktori target, tetapi juga harus mencari dan membuka banyak file *shared library* bawaan sistem (seperti `.so`) dan file konfigurasi sebelum bisa berjalan seutuhnya. |
| **3** | **System Call dengan Error > 0** | **Ada**, contohnya `openat` (12 error) dan `faccessat` (2 error).<br>**Analisis:** Ini adalah **hal yang sangat normal** dan bukan berarti program bermasalah. Error ini biasanya berupa `ENOENT` (*No such file or directory*), yang terjadi karena program mencoba mengecek/mencari file opsional (seperti `/etc/ld.so.preload`). Jika file tersebut tidak ada, program akan memunculkan error secara internal lalu mengabaikannya dan lanjut berjalan normal. |
| **4** | **Perbedaan Jumlah System Call `ls` vs `ls /etc`** | **Ya, jumlahnya akan berbeda.**<br>**Faktor penyebab:** Faktor utamanya adalah **jumlah isi di dalam direktori tersebut**. Direktori `/etc` berisi ratusan file dan folder konfigurasi sistem. Untuk menampilkan isi `/etc`, perintah `ls` harus memanggil lebih banyak *system call* seperti `getdents64` (untuk membaca daftar entri direktori) dibandingkan saat menjalankan `ls` di folder aktifmu saat ini yang isinya hanya sedikit. |

---
## Tugas 10.1
### Buka file dengan nano
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week10$ nano memory-audit.sh
```

### Isi file memory-audit.sh
```bash
#!/bin/bash
set -euo pipefail

LAPORAN="memory-report.txt"

{
    echo "=== LAPORAN MEMORI SISTEM ==="
    date
    echo
    echo "--- Ringkasan free -h ---"
    free -h
    echo
    echo "--- /proc/meminfo ---"
    cat /proc/meminfo | head -n 20
} > "$LAPORAN"

echo "Laporan disimpan ke: $LAPORAN"
cat "$LAPORAN"
```

### Jalankan script audit
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week10$ chmod +x memory-audit.sh
bash memory-audit.sh
Laporan disimpan ke: memory-report.txt
=== LAPORAN MEMORI SISTEM ===
Sun May 24 00:01:38 WIB 2026

--- Ringkasan free -h ---
               total        used        free      shared  buff/cache   available
Mem:           7.8Gi       451Mi       7.4Gi        24Mi       100Mi       7.4Gi
Swap:          8.8Gi          0B       8.8Gi

--- /proc/meminfo ---
MemTotal:        8186700 kB
MemFree:         7776084 kB
MemAvailable:    7723756 kB
Buffers:              32 kB
Cached:            59596 kB
SwapCached:            0 kB
Active:           144828 kB
Inactive:          31908 kB
Active(anon):     137364 kB
Inactive(anon):     4500 kB
Active(file):       7464 kB
Inactive(file):    27408 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:       9235268 kB
SwapFree:        9235268 kB
Dirty:                 0 kB
Writeback:             0 kB
AnonPages:        116392 kB
Mapped:            17360 kB
```

Analisis:

| No | Pertanyaan | Deskripsi / Jawaban |
| :--- | :--- | :--- |
| **1** | **Persentase Memori & Kondisi Sistem** | - **Perhitungan:** Berdasarkan `/proc/meminfo`, `MemAvailable` (7.723.756) dibagi `MemTotal` (8.186.700) dikali 100% hasilnya adalah **~94,3%**.<br>- **Kondisi Sistem:** Sangat **normal dan sehat**. Dengan memori tersedia di atas 90%, sistem memiliki ruang yang sangat lega untuk menjalankan banyak proses tanpa hambatan. |
| **2** | **Alasan `buff/cache` Tidak Dihitung Sebagai "Used"** | Memori `buff/cache` adalah RAM kosong yang "dipinjam" sementara oleh kernel Linux untuk menyimpan data disk agar aksesnya lebih cepat. Namun, sifat memori ini **dinamis dan mengalah**. Jika ada aplikasi yang membutuhkan RAM tambahan, kernel akan langsung mengosongkan/membuang `buff/cache` tersebut dalam hitungan milidetik dan memberikannya ke aplikasi. Oleh karena itu, memori ini tetap dihitung sebagai *available* (tersedia). |
| **3** | **Nilai `SwapTotal` dan `SwapFree`** | - **Apakah `SwapTotal` > 0?** Ya. Nilai `SwapTotal` adalah **9.235.268 kB** (sekitar 8,8 GB), lebih besar dari 0.<br>- **Nilai `SwapFree`:** Nilainya adalah **9.235.268 kB**. Angka yang sama persis dengan totalnya membuktikan bahwa swap tidak terpakai sama sekali (0% *used*). |

---
### Tugas 10.2
###  Simpan dan tampilkan proses teratas
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week10$ ps aux --sort=-%mem | head -n 10 > top-memory-process.txt
cat top-memory-process.txt
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         107  0.0  0.1 1245384 9944 ?        Ssl  May06   1:28 orbstack-agent: SO
so          8458  100  0.0  13620  3960 pts/1    R+   00:04   0:00 ps aux --sort=-%mem
root           1  0.0  0.0  21388  3800 ?        Ss   May06   0:47 /sbin/init
so          8021  0.0  0.0  10324  2208 pts/1    Ss   May23   0:00 -bash
so           243  0.0  0.0  19912  1956 ?        Ss   May06   0:14 /usr/lib/systemd/systemd --user
so          8459  0.0  0.0   8308  1708 pts/1    S+   00:04   0:00 head -n 10
syslog       240  0.0  0.0 222824  1668 ?        Ssl  May06   0:18 /usr/sbin/rsyslogd -n -iNONE
root         119  0.0  0.0 115632  1608 ?        S<s  May06   0:42 /usr/lib/systemd/systemd-journald
root         135  0.0  0.0  23632  1564 ?        Ss   May06   0:18 /usr/lib/systemd/systemd-udevd
```

Analisis:

| No | Pertanyaan | Deskripsi / Jawaban |
| :--- | :--- | :--- |
| **1** | **Proses di Urutan Pertama** | Proses yang menempati urutan pertama adalah **`orbstack-agent`** (PID 107). <br>- **%MEM** = 0.1 <br>- **RSS** = 9944 |
| **2** | **Konversi RSS dan Kewajaran** | - **Konversi:** 9944 KB dibagi 1024 = **9,71 MB**.<br>- **Kewajaran:** Sangat **wajar**. Angka ini tergolong sangat kecil dan efisien untuk sebuah program *background agent* (OrbStack) yang bertugas menjembatani mesin virtual Linux dengan sistem macOS kamu. |
| **3** | **Total %MEM 5 Proses Teratas** | Jika kita menjumlahkan nilai `%MEM` dari 5 proses teratas pada daftar:<br>1. `orbstack-agent` = 0.1<br>2. `ps` = 0.0<br>3. `init` = 0.0<br>4. `bash` = 0.0<br>5. `systemd` = 0.0<br>**Total penggunaan RAM bersama:** **0.1%** |

---
## Tugas 10.3
### Buat dan aktifkan swap file tugas
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week10$ sudo fallocate -l 256M /swapfile-tugas-week10
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week10$ sudo chmod 600 /swapfile-tugas-week10
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week10$ sudo mkswap /swapfile-tugas-week10
Setting up swapspace version 1, size = 256 MiB (268431360 bytes)
no label, UUID=7434cb15-8746-4ca9-831c-6630f6b47d19
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week10$ sudo swapon /swapfile-tugas-week10
```

###  Verifikasi dan simpan hasil
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week10$ {
    echo "=== VERIFIKASI SWAP ==="
    swapon --show
    echo
    free -h
} > swap-check.txt
cat swap-check.txt
=== VERIFIKASI SWAP ===
NAME                   TYPE       SIZE USED  PRIO
/dev/zram0             partition  7.8G   0B 32767
/dev/vdc               partition 1024M   0B     1
/swapfile-tugas-week10 file       256M   0B    -2

               total        used        free      shared  buff/cache   available
Mem:           7.8Gi       444Mi       7.4Gi        24Mi       117Mi       7.4Gi
Swap:          9.1Gi          0B       9.1Gi
```

Analisis:

| No | Pertanyaan | Deskripsi / Jawaban |
| :--- | :--- | :--- |
| **1** | **Identifikasi Kolom `swapon --show`** | Berdasarkan output, saat ini terdapat 3 area swap yang aktif. Untuk swap yang baru saja kamu buat, rinciannya adalah:<br>- **NAME:** `/swapfile-tugas-week10`<br>- **TYPE:** `file` (karena dibuat sebagai file virtual, bukan partisi disk fisik)<br>- **SIZE:** `256M` (sesuai perintah `fallocate`)<br>- **USED:** `0B` (masih kosong, belum ada data RAM yang dipindahkan ke sini) |
| **2** | **Kenaikan Total Swap pada `free -h`** | **Ya, bertambah.** Pada log `free -h` sebelum kamu membuat file ini, kapasitas total Swap adalah **8.8Gi**. Setelah file swap baru sebesar 256 MB (sekitar 0.25 GiB) aktif, total kapasitas Swap sekarang terbaca meningkat menjadi **9.1Gi**. |
| **3** | **Pentingnya Permission 600 & Risiko 644** | - **Pentingnya 600:** Izin `600` memastikan bahwa **hanya `root`** yang memiliki akses untuk membaca dan menulis file tersebut. <br>- **Risiko 644:** Izin `644` berarti *semua pengguna* (termasuk user biasa) memiliki hak untuk **membaca** file tersebut. File swap pada dasarnya adalah "buangan" dari RAM mentah. Jika diset 644, user lain bisa membaca isi file swap tersebut dan mencuri informasi sensitif yang sebelumnya ada di RAM, seperti password yang belum dienkripsi, kredensial, atau *session token*. Ini adalah celah keamanan yang sangat berbahaya. |

---
## Tugas 10.4
### Simpan ringkasan dan detail system call
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week10$ strace -c ls 2> strace-summary.txt
strace ls /etc 2> strace-ls-etc.txt
cat strace-summary.txt
memory-audit.sh  memory-report.txt  monitor-memori.sh  strace-summary.txt  swap-check.txt  swapfile-week10  top-memory-process.txt
X11			cron.daily	e2scrub.conf  init.d	     locale.gen      netconfig		  profile.d    rsyslog.conf   subuid		 udev
adduser.conf		cron.hourly	environment   inputrc	     localtime	     netplan		  protocols    rsyslog.d      subuid-		 update-manager
alternatives		cron.monthly	ethertypes    iproute2	     logcheck	     network		  python3      security       sudo.conf		 update-motd.d
apparmor.d		cron.weekly	fstab	      issue	     login.defs      networkd-dispatcher  python3.12   selinux	      sudo_logsrvd.conf  vconsole.conf
apt			cron.yearly	fuse.conf     issue.net      logrotate.conf  networks		  rc0.d        services       sudoers		 vim
bash.bashrc		crontab		gai.conf      kernel	     logrotate.d     newt		  rc1.d        shadow	      sudoers.d		 vtrgb
bash_completion.d	dbus-1		gnutls	      ld.so.cache    lsb-release     nsswitch.conf	  rc2.d        shadow-	      supercat		 xattr.conf
bindresvport.blacklist	debconf.conf	group	      ld.so.conf     machine-id      opt		  rc3.d        shells	      sysctl.conf	 xdg
binfmt.d		debian_version	group-	      ld.so.conf.d   mime.types      os-release		  rc4.d        skel	      sysctl.d
ca-certificates		default		gshadow       ldap	     mke2fs.conf     pam.conf		  rc5.d        smartd.conf    systemd
ca-certificates.conf	deluser.conf	gshadow-      legal	     modprobe.d      pam.d		  rc6.d        smartmontools  terminfo
console-setup		depmod.d	gss	      libaudit.conf  modules	     passwd		  rcS.d        ssh	      timezone
credstore		dhcp		host.conf     libnl-3	     modules-load.d  passwd-		  resolv.conf  ssl	      tmpfiles.d
credstore.encrypted	dhcpcd.conf	hostname      locale.alias   mtab	     perl		  rmt	       subgid	      ubuntu-advantage
cron.d			dpkg		hosts	      locale.conf    nanorc	     profile		  rpc	       subgid-	      ucf.conf
% time     seconds  usecs/call     calls    errors syscall
------ ----------- ----------- --------- --------- ----------------
 52.56    0.001829        1829         1           execve
 12.41    0.000432          12        34        12 openat
  9.45    0.000329         164         2           getdents64
  8.53    0.000297          42         7           read
  5.06    0.000176           6        28           mmap
  2.93    0.000102           4        24           close
  2.82    0.000098          12         8           mprotect
  1.47    0.000051          25         2         2 statfs
  1.32    0.000046           2        23           fstat
  1.26    0.000044          44         1           write
  0.75    0.000026           3         7           munmap
  0.49    0.000017           8         2         2 faccessat
  0.26    0.000009           9         1           futex
  0.20    0.000007           3         2           ioctl
  0.20    0.000007           2         3           brk
  0.06    0.000002           2         1           set_tid_address
  0.06    0.000002           2         1           set_robust_list
  0.06    0.000002           2         1           prlimit64
  0.06    0.000002           2         1           getrandom
  0.06    0.000002           2         1           rseq
------ ----------- ----------- --------- --------- ----------------
100.00    0.003480          23       150        16 total
```

Analisis:

| No | Pertanyaan | Deskripsi / Jawaban |
| :--- | :--- | :--- |
| **1** | **5 System Call dan Fungsinya** | Dari data `strace-summary.txt`, berikut 5 system call yang digunakan:<br>1. **`execve`**: Memulai dan mengeksekusi program utama (binary `ls`).<br>2. **`openat`**: Membuka file atau direktori tertentu.<br>3. **`mmap`**: Mengalokasikan/memetakan ruang memori (biasanya untuk memuat *shared library* ke RAM).<br>4. **`read`**: Membaca data dari file yang sudah dibuka.<br>5. **`close`**: Menutup file atau resource setelah selesai dibaca agar memori tidak bocor. |
| **2** | **System Call Paling Sering Dipanggil** | Dilihat dari kolom *calls*, system call yang paling sering dipanggil adalah **`openat`** (sebanyak 34 kali).<br>**Alasan:** Saat perintah `ls` dijalankan, ia tidak hanya membaca folder target, tetapi di balik layar ia harus membuka banyak file *library* bawaan (`.so`) dan file konfigurasi (seperti bahasa/locale) sebelum program siap menampilkan teks ke layar terminal. |
| **3** | **Kondisi Error dan Jalannya Program** | - **Apakah ada error?** Ya, terdapat total 16 error (12 pada `openat`, 2 pada `statfs`, dan 2 pada `faccessat`).<br>- **Apakah program tetap berjalan normal?** **Ya, sangat normal**. Error ini biasanya karena program mencoba mencari file konfigurasi tambahan (opsional) yang memang tidak ada di komputermu (misalnya file `/etc/ld.so.preload`). Saat file itu tidak ditemukan, kernel akan mencatat error `ENOENT`, tetapi program `ls` akan mengabaikannya dan lanjut berjalan hingga selesai dengan sukses. |

---
## Tugas 10.5
### Buka file dengan nano
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week10$ nano diagnosa-server.sh
```

### Isi file diagnosa-server.sh
```bash
#!/bin/bash
set -euo pipefail

LAPORAN="diagnosa-server-lambat.txt"
WARN_MEM=false
WARN_SWAP=0

cek_memori() {
    echo "--- Kondisi Memori ---"
    free -h
    echo
    AVAIL_PCT=$(free | awk '/Mem/ {printf "%d", $7/$2 * 100}')
    if [ "$AVAIL_PCT" -lt 20 ]; then
        echo "PERINGATAN: Memori tersedia hanya ${AVAIL_PCT}%"
        WARN_MEM=true
    fi
}

cek_swap() {
    echo "--- Penggunaan Swap ---"
    swapon --show 2>/dev/null || echo "Tidak ada swap aktif"
    echo
    WARN_SWAP=$(free | awk '/Swap/ {print $3}')
    if [ "$WARN_SWAP" -gt 0 ]; then
        echo "INFO: Swap digunakan (${WARN_SWAP} kB)"
    fi
}

cek_proses() {
    echo "--- 10 Proses Memori Tertinggi ---"
    ps aux --sort=-%mem | head -n 11
    echo
}

cek_paging() {
    echo "--- Aktivitas Paging (5 sampel) ---"
    vmstat 1 5
    echo
}

ringkasan() {
    echo "=== RINGKASAN ==="
    if [ "$WARN_MEM" = true ]; then
        echo "- Memori: KRITIS - perlu tindakan segera"
    else
        echo "- Memori: normal"
    fi

    if [ "$WARN_SWAP" -gt 0 ]; then
        echo "- Swap: aktif - pantau aktivitas paging"
    else
        echo "- Swap: tidak digunakan"
    fi
}

{
    echo "=== LAPORAN DIAGNOSA SERVER ==="
    date
    echo
    cek_memori
    cek_swap
    cek_proses
    cek_paging
    ringkasan
} | tee "$LAPORAN"

echo
echo "Laporan disimpan ke: $LAPORAN"
```

### Jalankan script diagnosa
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week10$ chmod +x diagnosa-server.sh
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week10$ bash diagnosa-server.sh
=== LAPORAN DIAGNOSA SERVER ===
Sun May 24 00:17:47 WIB 2026

--- Kondisi Memori ---
               total        used        free      shared  buff/cache   available
Mem:           7.8Gi       448Mi       7.4Gi        24Mi       130Mi       7.4Gi
Swap:          9.1Gi          0B       9.1Gi

--- Penggunaan Swap ---
NAME                   TYPE       SIZE USED  PRIO
/dev/zram0             partition  7.8G   0B 32767
/dev/vdc               partition 1024M   0B     1
/swapfile-tugas-week10 file       256M   0B    -2

--- 10 Proses Memori Tertinggi ---
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         107  0.0  0.1 1245384 10404 ?       Ssl  May06   1:28 orbstack-agent: SO
root         119  0.0  0.0 115632  5852 ?        S<s  May06   0:42 /usr/lib/systemd/systemd-journald
so          8519  0.0  0.0  13620  3984 pts/1    R+   00:17   0:00 ps aux --sort=-%mem
root           1  0.0  0.0  21388  3568 ?        Ss   May06   0:47 /sbin/init
so          8507  0.0  0.0  10060  3180 pts/1    S+   00:17   0:00 bash diagnosa-server.sh
so          8021  0.0  0.0  10324  2684 pts/1    Ss   May23   0:00 -bash
so          8508  0.0  0.0  10060  2348 pts/1    S+   00:17   0:00 bash diagnosa-server.sh
syslog       240  0.0  0.0 222824  2292 ?        Ssl  May06   0:18 /usr/sbin/rsyslogd -n -iNONE
so           243  0.0  0.0  19912  1956 ?        Ss   May06   0:14 /usr/lib/systemd/systemd --user
so          8520  0.0  0.0   8308  1720 pts/1    S+   00:17   0:00 head -n 11

--- Aktivitas Paging (5 sampel) ---
procs -----------memory---------- ---swap-- -----io---- -system-- -------cpu-------
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa st gu
 1  0      0 7761756     40 134932    0    0   117     1    8    0  0  0 100  0  0  0
 0  0      0 7761756     40 135032    0    0     0     0   49   24  0  0 100  0  0  0
 0  0      0 7761756     40 135032    0    0     0     0   44   40  0  0 100  0  0  0
 0  0      0 7761756     40 135032    0    0     0     0   27   27  0  0 100  0  0  0
 0  0      0 7761756     40 135032    0    0     0     0   33   37  0  0 100  0  0  0

=== RINGKASAN ===
- Memori: normal
- Swap: tidak digunakan

Laporan disimpan ke: diagnosa-server-lambat.txt
```

Analisis:

| No | Pertanyaan | Deskripsi / Jawaban |
| :--- | :--- | :--- |
| **1** | **Peran Fungsi & Alasan Dipecah** | - **`cek_memori`**: Mengecek total kapasitas, penggunaan, dan sisa RAM sistem (`free`).<br>- **`cek_swap`**: Mengidentifikasi partisi atau file swap yang aktif beserta ukurannya (`swapon`).<br>- **`cek_proses`**: Mengurutkan proses yang memakan memori fisik paling besar (`ps aux`).<br>- **`cek_paging`**: Memantau perpindahan data memori (baca/tulis) secara aktual dari/ke disk (`vmstat`).<br>- **`ringkasan`**: Menyimpulkan status kewajaran memori dan swap secara otomatis.<br><br>**Alasan dipecah:** Penerapan konsep **modularitas** (mambagi program besar menjadi blok-blok kecil). Ini membuat kode jauh lebih mudah dibaca, mudah dilacak jika ada *error* (*debugging*), dan setiap fungsi bisa digunakan ulang di bagian lain tanpa harus menulis ulang kodenya. |
| **2** | **Kondisi Sistem Berdasarkan RINGKASAN** | Sistem dalam kondisi **Normal** dan sangat sehat. Berdasarkan perhitungan di belakang layar, persentase *Available Memory* kamu berada di kisaran 94%. Angka ini jauh di atas *threshold* (batas bawah) yang biasanya disetel oleh *script* pada kisaran 20% atau 10%. |
| **3** | **Alasan Penggunaan `tee` vs `>`** | - Perintah `>` (*redirection*) akan mengalihkan semua *output* perintah masuk ke dalam file secara sembunyi-sembunyi. Efeknya, layar terminalmu akan kosong selama *script* berjalan.<br>- Perintah **`tee`** berfungsi seperti pipa cabang. Keuntungannya adalah ia mencetak *output* tersebut **ke layar terminal (secara *real-time*) SEKALIGUS menyimpannya ke dalam file** (`diagnosa-server-lambat.txt`). Jadi kamu bisa melihat hasilnya sambil menyimpannya untuk arsip. |
| **4** | **Aktivitas `si`/`so` pada `cek_paging`** | **Tidak ada aktivitas.** Nilai `si` (swap-in) dan `so` (swap-out) pada kelima sampel semuanya stabil di angka **0**.<br><br>**Implikasi Performa:** Ini adalah tanda server yang kencang dan optimal. Karena RAM kamu (8GB) masih sangat lega, tidak ada satupun data yang perlu "dibuang" sementara ke storage (SSD/HDD). Semua proses berjalan murni dari RAM fisik tanpa adanya hambatan (*bottleneck*) baca/tulis disk. |