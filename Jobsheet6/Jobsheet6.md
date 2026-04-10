# Jobsheet 6

| Nama | NIM | Kelas |
| :--- | :--- | :--- |
| Ibni Andarta | 254107020258 | TI-1G |

---

## Daftar Isi
- [Latihan 6.1](#latihan-61)
- [Latihan 6.2](#latihan-62)
- [Latihan 6.3](#latihan-63)
- [Latihan 6.4](#latihan-64)
- [Latihan 6.5](#latihan-65)
- [Latihan 6.A](#latihan-6a)
- [Latihan 6.B](#latihan-6b)
- [Latihan 6.C](#latihan-6c)

---

## Latihan 6.1

### 1. Berapa total proses yang berjalan? Proses apa yang memiliki PID terkecil?
**Jawaban:**

```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ ps aux | wc -l
217
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ ps aux --sort=pid | head -n 2
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.0  0.4  26072 15468 ?        Ss   Apr08   0:12 /usr/lib/systemd/systemd --switched-root --system --deserialize=48 splash
```


* Total Proses: Terdapat 217 proses yang sedang berjalan (berdasarkan output wc -l).
* PID Terkecil: PID terkecil adalah 1, yaitu proses /usr/lib/systemd/systemd. Proses ini adalah init process yang menjadi induk dari seluruh proses di sistem Linux.

### 2. Jalankan pstree -p dan temukan proses bash Anda. Proses apa yang menjadi induk (PPID) dari bash tersebut?

**Jawaban:**

```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ pstree -ps $$
systemd(1)───systemd(1979)───ptyxis(3243)───ptyxis-agent(3250)───bash(3287)───pstree(9183)
```


* Proses Bash: Berjalan dengan PID 3287.
* Induk (PPID) dari Bash: Berdasarkan hirarki `pstree -ps $$`, induk langsung dari bash adalah ptyxis-agent dengan PID 3250.

### 3. Bandingkan output ps aux dan ps aux -L. Apa perbedaan yang Anda lihat?
* `ps aux`: Menampilkan daftar berdasarkan proses (satu baris untuk satu PID).
* `ps aux -L`: Menampilkan daftar berdasarkan thread (LWP - Lightweight Process).

---
## Latihan 6.2

### 1. Jalankan sleep 120 & dan amati kolom STAT pada ps aux. Kondisi apa yang ditampilkan? Mengapa proses sleep berada di kondisi tersebut?
**Jawaban:**

```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ sleep 120 &
[1] 9301
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week04$ ps aux | grep sleep
ibennn      9301  0.0  0.1  14424  6392 pts/0    S    04:08   0:00 sleep 120
ibennn      9305  0.0  0.0   9100  2068 pts/0    S+   04:08   0:00 grep --color=auto sleep
```


**Analisis:** Perintah sleep 120 &
* Hasil Pengamatan:
* *  Proses sleep berjalan dengan PID 9301.
* *  Kolom STAT menunjukkan kode S.
* Kondisi yang Ditampilkan:<br>
Kondisi tersebut adalah Interruptible Sleep (menunggu interupsi).
* Mengapa proses sleep berada di kondisi tersebut?<br>
Proses sleep tidak sedang melakukan pemrosesan data di CPU. Ia hanya menunggu interval waktu tertentu (dalam hal ini 120 detik) selesai. Oleh karena itu, kernel Linux menempatkannya dalam status sleeping agar sumber daya CPU dapat digunakan oleh proses lain yang lebih aktif.


### 2. Jalankan beberapa perintah yang berhasil dan yang gagal, lalu catat exit code masing-masing. Pola apa yang Anda temukan?

**Jawaban:**


```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week06$ ls /
echo $?
bin   cdrom  etc   lib         media  opt   root  sbin  srv       sys  usr
boot  dev    home  lost+found  mnt    proc  run   snap  swap.img  tmp  var
0
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week06$ ls /folder_ngasal_ibennn
echo $?
ls: cannot access '/folder_ngasal_ibennn': No such file or directory
2
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week06$ apa_ini
echo $?
apa_ini: command not found
[1]+  Done                    sleep 120  (wd: ~/praktikum-os/week04)
(wd now: ~/praktikum-os/week06)
127
```


Tabel Analisis Exit Code

| Perintah | Hasil Output | Exit Code (`$?`) | Status |
| :--- | :--- | :--- | :--- |
| `ls /` | Menampilkan isi direktori root | **0** | **Berhasil** |
| `ls /folder_ngasal_ibennn` | *No such file or directory* | **2** | **Gagal** (Error input/file) |
| `apa_ini` | *command not found* | **127** | **Gagal** (Perintah tidak ada) |

---
## Latihan 6.3

### 1. Jalankan nice -n 5 sleep 200 & dan verifikasi nilai NI-nya dengan ps.

**Jawaban:**

```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week06$ nice -n 5 sleep 200 &

ps -o pid,ni,comm -p $!

[1] 9482

    PID  NI COMMAND

   9482   5 sleep
```


* Perintah: nice -n 5 sleep 200 &
* Hasil: Proses berjalan dengan PID 9482
* Verifikasi: Kolom NI (Nice) menunjukkan nilai 5. Ini berarti proses dimulai dengan prioritas yang sedikit lebih rendah dari standar (standar/default = 0).

### 2. Ubah nilai nice menjadi 10 menggunakan renice, lalu verifikasi kembali.

**Jawaban:**

```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week06$ renice -n 10 -p 9482
ps -o pid,ni,comm -p 9482
9482 (process ID) old priority 5, new priority 10
    PID  NI COMMAND
   9482  10 sleep
```


* Perintah: renice -n 10 -p 9482
* Hasil: Sistem memberikan output 9482 (process ID) old priority 5, new priority 10.
* Verifikasi: Kolom NI berhasil berubah menjadi 10. Hal ini membuktikan bahwa renice dapat mengubah prioritas proses yang sudah berjalan (sedang running).


### 3. Coba ubah nilai nice menjadi -5 tanpa sudo. Apa yang terjadi? Mengapa Linux membatasi hal ini untuk user biasa?

**Jawaban:**

```bash 
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week06$ renice -n -5 -p 9482
renice: failed to set priority for 9482 (process ID): Permission denied
```


* Perintah: renice -n -5 -p 9482
* Hasil: Muncul pesan kesalahan: renice: failed to set priority for 9482 (process ID): Permission denied.
* Analisis/Alasan:
* * Keamanan Sistem: Linux membatasi user biasa agar hanya bisa menurunkan prioritas mereka sendiri (menaikkan nilai Nice).
* * Mencegah Monopoli: Jika user biasa diizinkan meningkatkan prioritas (nilai Nice negatif), mereka bisa mengambil alih jatah CPU secara berlebihan yang berisiko membuat sistem tidak stabil atau hang bagi pengguna lain.
* * Otoritas: Hanya Root/Sudo yang memiliki wewenang untuk meningkatkan prioritas proses (nilai Nice negatif) di atas level standar.

---
## Latihan 6.4

### 1. Jalankan sleep 400 &, kirim SIGSTOP, dan amati perubahan kolom STAT. Kondisi apa yang muncul?

**Jawaban:**

```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week06$ kill -SIGSTOP 9611
ps -o pid,stat,comm -p 9611
    PID STAT COMMAND
   9611 T    sleep

[1]+  Stopped                 sleep 400
```


* Perintah: kill -SIGSTOP 9611
* Hasil STAT: Berubah menjadi T (Stopped).
* Analisis: Saat menerima signal SIGSTOP, proses sleep langsung ditangguhkan oleh sistem. Status T menunjukkan bahwa proses berhenti sementara dan tidak akan menggunakan siklus CPU sampai ada instruksi untuk melanjutkan. Terminal juga memberikan notifikasi [1]+ Stopped.

### 2. Kirim SIGCONT dan verifikasi proses kembali berjalan.

**Jawaban:**

```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week06$ kill -SIGCONT 9611
ps -o pid,stat,comm -p 9611
    PID STAT COMMAND
   9611 S    sleep
```


* Perintah: kill -SIGCONT 9611
* Hasil STAT: Berubah kembali menjadi S (Interruptible Sleep).
* Analisis: Signal SIGCONT memerintahkan proses yang sebelumnya berhenti (T) untuk berjalan kembali. Status kembali ke S karena proses sleep sedang menunggu durasi waktu selesai.


### 3.  Hentikan proses dengan SIGTERM lalu verifikasi sudah tidak ada. Kapan Anda memilih SIGKILL daripada SIGTERM?

**Jawaban:**

```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week06$ kill -SIGTERM 9611
pgrep sleep
[1]+  Terminated              sleep 400
```


* Perintah: kill -SIGTERM 9611
* Hasil Verifikasi: Perintah pgrep sleep tidak menghasilkan output, dan muncul notifikasi [1]+ Terminated.
* Analisis: SIGTERM berhasil menghentikan proses secara normal.

### Perbandingan SIGTERM vs SIGKILL

| Aspek | SIGTERM (Signal 15) | SIGKILL (Signal 9) |
| :--- | :--- | :--- |
| **Sifat** | Permintaan berhenti secara sopan (*graceful*). | Paksaan berhenti seketika (*forced*). |
| **Respon Proses** | Proses dapat menangani signal ini untuk membersihkan memori atau menyimpan file sebelum mati. | Proses tidak diberi kesempatan untuk bersih-bersih; langsung dimatikan oleh kernel. |
| **Kapan Digunakan?** | Digunakan sebagai langkah pertama untuk mematikan proses dengan aman. | Digunakan sebagai langkah terakhir jika proses "hang", macet, atau tidak merespons SIGTERM. |

---
## Latihan 6.5

### 1. Jalankan top di foreground. Apa yang terjadi di terminal?
**Jawaban:**

```bash
top - 10:48:02 up 1 day,  7:48,  1 user,  load average: 0.10, 0.03, 0.01
Tasks: 217 total,   1 running, 212 sleeping,   0 stopped,   4 zombie
%Cpu(s):  4.8 us,  1.1 sy,  0.0 ni, 94.1 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
MiB Mem :   3383.0 total,    158.0 free,   1364.4 used,   2123.9 buff/cache     
MiB Swap:   3896.0 total,   3895.9 free,      0.1 used.   2018.6 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                                                                          
   2193 ibennn    20   0 4855552 498472 169404 S  11.2  14.4  10:43.63 gnome-shell                                                                                                                      
   3243 ibennn    20   0 1630972 293272 141104 S  10.9   8.5   2:40.16 ptyxis                                                                                                                           
   1783 root      20   0   94056   6464   5808 S   1.0   0.2   0:04.66 spice-vdagentd                                                                                                                   
  11444 ibennn    20   0   13324   5416   3284 R   0.3   0.2   0:00.55 top                                                                                                                              
      1 root      20   0   26208  15532  10192 S   0.0   0.4   0:15.73 systemd                                                                                                                          
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.14 kthreadd                                                                                                                         
      3 root      20   0       0      0      0 S   0.0   0.0   0:00.00 pool_workqueue_release                                                                                                           
      4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-rcu_gp                                                                                                                 
      5 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-sync_wq                                                                                                                
      6 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-kvfree_rcu_reclaim                                                                                                     
      7 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-slub_flushwq                                                                                                           
      8 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-netns                                                                                                                  
     11 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/0:0H-events_highpri                                                                                                      
     13 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-mm_percpu_wq                                                                                                           
     14 root      20   0       0      0      0 S   0.0   0.0   0:00.18 ksoftirqd/0                                                                                                                      
     15 root      20   0       0      0      0 I   0.0   0.0   0:11.13 rcu_preempt                                                                                                                      
     16 root      20   0       0      0      0 S   0.0   0.0   0:00.00 rcu_exp_par_gp_kthread_worker/0                                                                                                  
     17 root      20   0       0      0      0 S   0.0   0.0   0:00.17 rcu_exp_gp_kthread_worker                                                                                                        
     18 root      rt   0       0      0      0 S   0.0   0.0   0:01.24 migration/0                                                                                                                      
     19 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/0                                                                                                                    
     20 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/0                                                                                                                          
     21 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/1                                                                                                                          
     22 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/1                                                                                                                    
     23 root      rt   0       0      0      0 S   0.0   0.0   0:01.22 migration/1                                                                                                                      
     24 root      20   0       0      0      0 S   0.0   0.0   0:00.06 ksoftirqd/1                                                                                                                      
     26 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/1:0H-events_highpri                                                                                                      
     27 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/2                                                                                                                          
     28 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/2                                                                                                                    
     29 root      rt   0       0      0      0 S   0.0   0.0   0:01.24 migration/2                                                                                                                      
     30 root      20   0       0      0      0 S   0.0   0.0   0:00.08 ksoftirqd/2                                                                                                                      
     32 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/2:0H-events_highpri                                                                                                      
     33 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/3                                                                                                                          
     34 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/3                                                                                                                    
     35 root      rt   0       0      0      0 S   0.0   0.0   0:01.21 migration/3                                                                                                                      
     36 root      20   0       0      0      0 S   0.0   0.0   0:00.08 ksoftirqd/3                                                                                                                      
     38 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/3:0H-events_highpri                                                                                                      
     39 root      20   0       0      0      0 S   0.0   0.0   0:00.01 kdevtmpfs                                                                                                                        
     40 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-inet_frag_wq                                                                                                           
     41 root      20   0       0      0      0 I   0.0   0.0   0:00.00 rcu_tasks_kthread                                                                                                                
     42 root      20   0       0      0      0 I   0.0   0.0   0:00.00 rcu_tasks_rude_kthread                                                                                                           
     43 root      20   0       0      0      0 I   0.0   0.0   0:00.00 rcu_tasks_trace_kthread                                                                                                          
     44 root      20   0       0      0      0 S   0.0   0.0   0:00.01 kauditd                                                                                                                          
     45 root      20   0       0      0      0 S   0.0   0.0   0:01.53 khungtaskd                                                                                                                       
     46 root      20   0       0      0      0 S   0.0   0.0   0:00.00 oom_reaper                                                                                                                       
     48 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-writeback                                                                                                              
     49 root      20   0       0      0      0 S   0.0   0.0   0:09.20 kcompactd0  
```


**Top di Foreground:** Program `top` menguasai antarmuka terminal untuk menampilkan statistik sistem secara *real-time*.


### 2. Tekan Ctrl+Z dan cek statusnya dengan jobs. Kondisi apa yang ditampilkan?

**Jawaban:**

```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week06$ top

top - 10:49:11 up 1 day,  7:49,  1 user,  load average: 0.11, 0.04, 0.01
Tasks: 218 total,   1 running, 213 sleeping,   0 stopped,   4 zombie
%Cpu(s): 18.2 us,  2.3 sy,  0.0 ni, 79.5 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
MiB Mem :   3383.0 total,    158.1 free,   1364.3 used,   2123.9 buff/cache     
MiB Swap:   3896.0 total,   3895.9 free,      0.1 used.   2018.7 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                                                                          
   2193 ibennn    20   0 4862880 498516 169404 S  36.4  14.4  10:46.56 gnome-shell                                                                                                                      
   3243 ibennn    20   0 1630996 293160 140992 S  27.3   8.5   2:43.03 ptyxis                                                                                                                           
  11470 ibennn    20   0   13324   5020   2900 R   9.1   0.1   0:00.01 top                                                                                                                              
      1 root      20   0   26208  15532  10192 S   0.0   0.4   0:15.74 systemd                                                                                                                          
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.14 kthreadd                                                                                                                         
      3 root      20   0       0      0      0 S   0.0   0.0   0:00.00 pool_workqueue_release                                                                                                           
      4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-rcu_gp                                                                                                                 
      5 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-sync_wq                                                                                                                
      6 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-kvfree_rcu_reclaim                                                                                                     
      7 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-slub_flushwq                                                                                                           
      8 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-netns                                                                                                                  
     11 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/0:0H-events_highpri                                                                                                      
     13 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-mm_percpu_wq                                                                                                           
     14 root      20   0       0      0      0 S   0.0   0.0   0:00.18 ksoftirqd/0                                                                                                                      
     15 root      20   0       0      0      0 I   0.0   0.0   0:11.14 rcu_preempt                                                                                                                      
     16 root      20   0       0      0      0 S   0.0   0.0   0:00.00 rcu_exp_par_gp_kthread_worker/0                                                                                                  
     17 root      20   0       0      0      0 S   0.0   0.0   0:00.17 rcu_exp_gp_kthread_worker                                                                                                        
     18 root      rt   0       0      0      0 S   0.0   0.0   0:01.25 migration/0                                                                                                                      
     19 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/0                                                                                                                    
     20 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/0                                                                                                                          
     21 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/1                                                                                                                          
     22 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/1                                                                                                                    
     23 root      rt   0       0      0      0 S   0.0   0.0   0:01.22 migration/1                                                                                                                      
     24 root      20   0       0      0      0 S   0.0   0.0   0:00.06 ksoftirqd/1                                                                                                                      
     26 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/1:0H-events_highpri                                                                                                      
     27 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/2                                                                                                                          
     28 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/2                                                                                                                    
     29 root      rt   0       0      0      0 S   0.0   0.0   0:01.24 migration/2                                                                                                                      
     30 root      20   0       0      0      0 S   0.0   0.0   0:00.08 ksoftirqd/2                                                                                                                      
     32 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/2:0H-events_highpri                                                                                                      
     33 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/3                                                                                                                          
     34 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/3                                                                                                                    
     35 root      rt   0       0      0      0 S   0.0   0.0   0:01.21 migration/3                                                                                                                      
     36 root      20   0       0      0      0 S   0.0   0.0   0:00.08 ksoftirqd/3                                                                                                                      
     38 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/3:0H-events_highpri                                                                                                      
     39 root      20   0       0      0      0 S   0.0   0.0   0:00.01 kdevtmpfs                                                                                                                        
     40 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-inet_frag_wq                                                                                                           
     41 root      20   0       0      0      0 I   0.0   0.0   0:00.00 rcu_tasks_kthread                                                                                                                
     42 root      20   0       0      0      0 I   0.0   0.0   0:00.00 rcu_tasks_rude_kthread                                                                                                           
     43 root      20   0       0      0      0 I   0.0   0.0   0:00.00 rcu_tasks_trace_kthread                                                                                                          
     44 root      20   0       0      0      0 S   0.0   0.0   0:00.01 kauditd                                                                                                                          
     45 root      20   0       0      0      0 S   0.0   0.0   0:01.53 khungtaskd                                                                                                                       
     46 root      20   0       0      0      0 S   0.0   0.0   0:00.00 oom_reaper                                                                                                                       
     48 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-writeback                                                                                                              
     49 root      20   0       0      0      0 S   0.0   0.0   0:09.21 kcompactd0                                                                                                                       
     50 root      25   5       0      0      0 S   0.0   0.0   0:00.00 ksmd                                                                                                                             
[1]+  Stopped                 top
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week06$ jobs
[1]+  Stopped                 top
```


**Ctrl+Z & Jobs:** Menghasilkan status **Stopped**. Proses ditangguhkan sementara dan dipindahkan ke antrean pekerjaan (*job list*).

### 3. Pindahkan ke background dengan bg. Apakah top dapat berjalan dengan baik di background? Mengapa?
**Jawaban:**

```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week06$ bg
[1]+ top &

[1]+  Stopped                 top
```


**Pindah ke Background (bg):** Program `top` **tidak dapat berjalan dengan baik** di background. Karena `top` adalah aplikasi interaktif yang memerlukan akses terminal untuk menampilkan UI-nya, kernel akan menghentikannya kembali segera setelah dipindahkan ke background.

### 4. Kembalikan ke foreground dengan fg, lalu keluar dengan q .
**Jawaban:**

```bash
top - 10:55:32 up 1 day,  7:55,  1 user,  load average: 0.01, 0.02, 0.00
Tasks: 216 total,   1 running, 211 sleeping,   0 stopped,   4 zombie
%Cpu(s):  0.6 us,  0.2 sy,  0.0 ni, 99.1 id,  0.1 wa,  0.0 hi,  0.0 si,  0.0 st 
MiB Mem :   3383.0 total,    158.6 free,   1363.8 used,   2123.9 buff/cache     
MiB Swap:   3896.0 total,   3895.9 free,      0.1 used.   2019.2 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                                                                          
   3243 ibennn    20   0 1630996 293108 140940 S   1.7   8.5   2:54.18 ptyxis                                                                                                                           
   2193 ibennn    20   0 4862912 498764 169404 S   1.0  14.4  10:59.31 gnome-shell                                                                                                                      
   3250 ibennn    20   0  241092   6956   6232 S   0.3   0.2   0:10.87 ptyxis-agent                                                                                                                     
  11299 root      20   0       0      0      0 I   0.3   0.0   0:00.20 kworker/u16:1-flush-253:0                                                                                                        
  11470 ibennn    20   0   13324   5420   3284 R   0.3   0.2   0:00.10 top                                                                                                                              
      1 root      20   0   26208  15532  10192 S   0.0   0.4   0:15.76 systemd                                                                                                                          
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.14 kthreadd                                                                                                                         
      3 root      20   0       0      0      0 S   0.0   0.0   0:00.00 pool_workqueue_release                                                                                                           
      4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-rcu_gp                                                                                                                 
      5 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-sync_wq                                                                                                                
      6 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-kvfree_rcu_reclaim                                                                                                     
      7 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-slub_flushwq                                                                                                           
      8 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-netns                                                                                                                  
     11 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/0:0H-events_highpri                                                                                                      
     13 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-mm_percpu_wq                                                                                                           
     14 root      20   0       0      0      0 S   0.0   0.0   0:00.18 ksoftirqd/0                                                                                                                      
     15 root      20   0       0      0      0 I   0.0   0.0   0:11.20 rcu_preempt                                                                                                                      
     16 root      20   0       0      0      0 S   0.0   0.0   0:00.00 rcu_exp_par_gp_kthread_worker/0                                                                                                  
     17 root      20   0       0      0      0 S   0.0   0.0   0:00.17 rcu_exp_gp_kthread_worker                                                                                                        
     18 root      rt   0       0      0      0 S   0.0   0.0   0:01.25 migration/0                                                                                                                      
     19 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/0                                                                                                                    
     20 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/0                                                                                                                          
     21 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/1                                                                                                                          
     22 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/1                                                                                                                    
     23 root      rt   0       0      0      0 S   0.0   0.0   0:01.22 migration/1                                                                                                                      
     24 root      20   0       0      0      0 S   0.0   0.0   0:00.06 ksoftirqd/1                                                                                                                      
     26 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/1:0H-events_highpri                                                                                                      
     27 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/2                                                                                                                          
     28 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/2                                                                                                                    
     29 root      rt   0       0      0      0 S   0.0   0.0   0:01.24 migration/2                                                                                                                      
     30 root      20   0       0      0      0 S   0.0   0.0   0:00.08 ksoftirqd/2                                                                                                                      
     32 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/2:0H-events_highpri                                                                                                      
     33 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/3                                                                                                                          
     34 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/3                                                                                                                    
     35 root      rt   0       0      0      0 S   0.0   0.0   0:01.22 migration/3                                                                                                                      
     36 root      20   0       0      0      0 S   0.0   0.0   0:00.08 ksoftirqd/3                                                                                                                      
     38 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/3:0H-events_highpri                                                                                                      
     39 root      20   0       0      0      0 S   0.0   0.0   0:00.01 kdevtmpfs                                                                                                                        
     40 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-inet_frag_wq                                                                                                           
     41 root      20   0       0      0      0 I   0.0   0.0   0:00.00 rcu_tasks_kthread                                                                                                                
     42 root      20   0       0      0      0 I   0.0   0.0   0:00.00 rcu_tasks_rude_kthread                                                                                                           
     43 root      20   0       0      0      0 I   0.0   0.0   0:00.00 rcu_tasks_trace_kthread                                                                                                          
     44 root      20   0       0      0      0 S   0.0   0.0   0:00.01 kauditd                                                                                                                          
     45 root      20   0       0      0      0 S   0.0   0.0   0:01.53 khungtaskd                                                                                                                       
     46 root      20   0       0      0      0 S   0.0   0.0   0:00.00 oom_reaper                                                                                                                       
     48 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-writeback  
```


**Kembali ke Foreground (fg):** Menggunakan `fg` berhasil mengembalikan `top` ke layar utama, lalu keluar menggunakan tombol `q` menutup proses tersebut secara bersih.

---
## Latihan 6.6

### 1. Gunakan ps aux –sort=%mem untuk menemukan proses yang menggunakan memori paling banyak di VM Anda. Proses apa itu?
**Jawaban:**

```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week06$ ps aux --sort=-%mem | head -n 5
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
ibennn      2193  0.5 14.3 4862912 498744 ?      Ssl  Apr08  11:10 /usr/bin/gnome-shell
ibennn      3243  0.1  8.4 1630956 293372 ?      Sl   Apr08   3:06 /usr/bin/ptyxis --gapplication-service
ibennn      2879  0.0  3.0 843376 106416 ?       Sl   Apr08   0:01 /usr/libexec/mutter-x11-frames
ibennn     11387  0.0  1.8 2795608 65012 ?       Sl   10:43   0:00 gjs /usr/share/gnome-shell/extensions/ding@rastersoft.com/app/ding.js -E -P /usr/share/gnome-shell/extensions/ding@rastersoft.com/app
```


**Penggunaan Memori Terbanyak:**
   - Berdasarkan perintah `ps aux --sort=-%mem`, proses yang menggunakan memori paling banyak adalah **gnome-shell**. Hal ini terlihat dari persentase pada kolom `%MEM` yang paling tinggi dibandingkan proses lainnya.

### 2. Di dalam top, tekan 1 . Apa yang berubah pada tampilan? Mengapa informasi ini berguna?
**Jawaban:**

```bash
top - 11:03:23 up 1 day,  8:03,  1 user,  load average: 0.08, 0.10, 0.07
Tasks: 215 total,   1 running, 210 sleeping,   0 stopped,   4 zombie
%Cpu0  :  1.0 us,  0.3 sy,  0.0 ni, 98.7 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
%Cpu1  :  1.3 us,  0.3 sy,  0.0 ni, 98.3 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
%Cpu2  :  1.0 us,  0.3 sy,  0.0 ni, 98.7 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
%Cpu3  :  1.0 us,  0.7 sy,  0.0 ni, 98.3 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st 
MiB Mem :   3383.0 total,    157.9 free,   1364.3 used,   2124.0 buff/cache     
MiB Swap:   3896.0 total,   3895.9 free,      0.1 used.   2018.7 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                                                                                                          
   3243 ibennn    20   0 1631012 293560 141064 S   2.3   8.5   3:08.17 ptyxis                                                                                                                           
   2193 ibennn    20   0 4862928 498660 169404 S   2.0  14.4  11:13.88 gnome-shell                                                                                                                      
   2839 ibennn    20   0  784208  18624  14684 S   0.3   0.5   0:06.55 xdg-desktop-por                                                                                                                  
  11512 ibennn    20   0   13324   5408   3288 R   0.3   0.2   0:00.07 top                                                                                                                              
      1 root      20   0   26208  15532  10192 S   0.0   0.4   0:15.80 systemd                                                                                                                          
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.14 kthreadd                                                                                                                         
      3 root      20   0       0      0      0 S   0.0   0.0   0:00.00 pool_workqueue_release                                                                                                           
      4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-rcu_gp                                                                                                                 
      5 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-sync_wq                                                                                                                
      6 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-kvfree_rcu_reclaim                                                                                                     
      7 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-slub_flushwq                                                                                                           
      8 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-netns                                                                                                                  
     11 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/0:0H-events_highpri                                                                                                      
     13 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-mm_percpu_wq                                                                                                           
     14 root      20   0       0      0      0 S   0.0   0.0   0:00.18 ksoftirqd/0                                                                                                                      
     15 root      20   0       0      0      0 I   0.0   0.0   0:11.27 rcu_preempt                                                                                                                      
     16 root      20   0       0      0      0 S   0.0   0.0   0:00.00 rcu_exp_par_gp_kthread_worker/0                                                                                                  
     17 root      20   0       0      0      0 S   0.0   0.0   0:00.17 rcu_exp_gp_kthread_worker                                                                                                        
     18 root      rt   0       0      0      0 S   0.0   0.0   0:01.25 migration/0                                                                                                                      
     19 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/0                                                                                                                    
     20 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/0                                                                                                                          
     21 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/1                                                                                                                          
     22 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/1                                                                                                                    
     23 root      rt   0       0      0      0 S   0.0   0.0   0:01.23 migration/1                                                                                                                      
     24 root      20   0       0      0      0 S   0.0   0.0   0:00.06 ksoftirqd/1                                                                                                                      
     26 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/1:0H-events_highpri                                                                                                      
     27 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/2                                                                                                                          
     28 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/2                                                                                                                    
     29 root      rt   0       0      0      0 S   0.0   0.0   0:01.24 migration/2                                                                                                                      
     30 root      20   0       0      0      0 S   0.0   0.0   0:00.08 ksoftirqd/2                                                                                                                      
     32 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/2:0H-events_highpri                                                                                                      
     33 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/3                                                                                                                          
     34 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/3                                                                                                                    
     35 root      rt   0       0      0      0 S   0.0   0.0   0:01.22 migration/3                                                                                                                      
     36 root      20   0       0      0      0 S   0.0   0.0   0:00.08 ksoftirqd/3                                                                                                                      
     38 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/3:0H-events_highpri                                                                                                      
     39 root      20   0       0      0      0 S   0.0   0.0   0:00.01 kdevtmpfs                                                                                                                        
     40 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/R-inet_frag_wq                                                                                                           
     41 root      20   0       0      0      0 I   0.0   0.0   0:00.00 rcu_tasks_kthread                                                                                                                
     42 root      20   0       0      0      0 I   0.0   0.0   0:00.00 rcu_tasks_rude_kthread                                                                                                           
     43 root      20   0       0      0      0 I   0.0   0.0   0:00.00 rcu_tasks_trace_kthread                                                                                                          
     44 root      20   0       0      0      0 S   0.0   0.0   0:00.01 kauditd                                                                                                                          
     45 root      20   0       0      0      0 S   0.0   0.0   0:01.54 khungtaskd  
```


**Fitur Angka 1 pada `top`:**
   - **Perubahan:** Tampilan ringkasan CPU (`%Cpu(s)`) berubah menjadi tampilan per-core (`%Cpu0`, `%Cpu1`, dst).
   - **Kegunaan:** Informasi ini sangat berguna untuk memantau distribusi beban kerja antar CPU. Kita bisa mendeteksi jika terjadi *bottleneck* atau beban yang tidak merata pada core tertentu.

### 3.  Di dalam htop, navigasikan ke proses sshd menggunakan tombol panah. Tekan F9 dan amati opsi sinyal yang tersedia.

**Jawaban:**
**Menu Sinyal pada `htop` (F9):**
   - Menekan **F9** pada proses yang dipilih (seperti `sshd`) membuka daftar lengkap signal Linux. Ini memberikan fleksibilitas untuk menghentikan proses secara sopan (`SIGTERM`), memaksa berhenti (`SIGKILL`), atau menangguhkan proses (`SIGSTOP`) melalui antarmuka visual tanpa harus mengetik PID secara manual.

---
## Latihan 6.A

### 1.  Jalankan ps aux –forest dan temukan proses dengan PID 1. Apa nama dan fungsi proses tersebut dalam sistem Linux modern?
**Jawaban:**

```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week06$ ps aux --forest | grep -w "1"
root          10  0.0  0.0      0     0 ?        I    01:03   0:00  \_ [kworker/0:1-events]
root          21  0.0  0.0      0     0 ?        S    01:03   0:00  \_ [cpuhp/1]
root          22  0.0  0.0      0     0 ?        S    01:03   0:00  \_ [idle_inject/1]
root          23  0.0  0.0      0     0 ?        S    01:03   0:00  \_ [migration/1]
root          24  0.0  0.0      0     0 ?        S    01:03   0:00  \_ [ksoftirqd/1]
root          25  0.0  0.0      0     0 ?        I    01:03   0:00  \_ [kworker/1:0-cgroup_free]
root          26  0.0  0.0      0     0 ?        I<   01:03   0:00  \_ [kworker/1:0H-events_highpri]
root          47  0.0  0.0      0     0 ?        I    01:03   0:00  \_ [kworker/u16:1-events_unbound]
root          55  0.0  0.0      0     0 ?        I    01:03   0:00  \_ [kworker/1:1-cgroup_free]
root          56  0.0  0.0      0     0 ?        I    01:03   0:00  \_ [kworker/3:1-events]
root          57  0.0  0.0      0     0 ?        S<   01:03   0:00  \_ [pr/ttyAMA-1]
root          66  0.0  0.0      0     0 ?        I    01:03   0:00  \_ [kworker/2:1-events]
root          75  0.0  0.0      0     0 ?        I<   01:03   0:00  \_ [kworker/1:1H-kblockd]
root         219  0.0  0.0      0     0 ?        I    01:03   0:00  \_ [kworker/1:2-events]
root         718  0.0  0.0      0     0 ?        I    01:03   0:00  \_ [kworker/1:3-mm_percpu_wq]
root           1  0.4  0.4  25892 15512 ?        Ss   01:03   0:00 /usr/lib/systemd/systemd --switched-root --system --deserialize=48 splash
root         375  0.1  0.6  51828 21628 ?        S<s  01:03   0:00 /usr/lib/systemd/systemd-journald
avahi        958  0.0  0.1   6844  3824 ?        Ss   01:03   0:00 avahi-daemon: running [ibennn-QEMU-Virtual-Machine.local]
root         959  0.0  0.0   2680  1572 ?        Ss   01:03   0:00 /bin/sh /usr/lib/systemd/scripts/chronyd-starter.sh -n -F 1
_chrony     1110  0.0  0.3  24392 10492 ?        S    01:03   0:00  \_ /usr/sbin/chronyd -n -F 1
_chrony     1118  0.0  0.0  12164  3336 ?        S    01:03   0:00      \_ /usr/sbin/chronyd -n -F 1
message+     960  0.1  0.2  12316  7872 ?        Ss   01:03   0:00 @dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only
polkitd      970  0.1  0.3 390292 11444 ?        Ssl  01:03   0:00 /usr/lib/polkit-1/polkitd --no-debug --log-level=notice
root         977  0.1  1.1 1595480 39164 ?       Ssl  01:03   0:00 /usr/lib/snapd/snapd
root         982  0.0  0.1 311412  6724 ?        Ssl  01:03   0:00 /usr/libexec/switcheroo-control
syslog      1033  0.0  0.1 221088  4880 ?        Ssl  01:03   0:00 /usr/sbin/rsyslogd -n -iNONE
root        1186  0.0  0.1  18104  6232 ?        Ss   01:03   0:00 /usr/sbin/wpa_supplicant -u -s -O DIR=/run/wpa_supplicant GROUP=netdev
ibennn      2060  0.0  0.1 171472  5860 tty2     Ssl+ 01:03   0:00      \_ /usr/libexec/gdm-wayland-session env GNOME_SHELL_SESSION_MODE=ubuntu /usr/bin/gnome-session --session=ubuntu
ibennn      2069  0.0  0.1 165824  5872 tty2     Sl+  01:03   0:00          \_ /usr/libexec/gnome-session-init-worker ubuntu
root        1835  0.0  0.1  94008  6280 ?        Ssl  01:03   0:00 /usr/sbin/spice-vdagentd -x
root        1856  0.0  0.1 312864  6848 ?        Ssl  01:03   0:00 /usr/libexec/power-profiles-daemon
ibennn      1990  0.1  0.3  24080 13660 ?        Ss   01:03   0:00 /usr/lib/systemd/systemd --user
ibennn      1992  0.0  0.1  25836  3800 ?        S    01:03   0:00  \_ (sd-pam)
ibennn      2011  0.1  0.1  10288  6156 ?        Ss   01:03   0:00  \_ /usr/bin/dbus-daemon --session --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only
ibennn      2015  0.0  0.1  88136  4712 ?        Ssl  01:03   0:00  \_ /usr/bin/pipewire -c filter-chain.conf
ibennn      2097  0.0  0.1 692160  6864 ?        Ssl  01:03   0:00  \_ /usr/libexec/xdg-document-portal
ibennn      2115  0.0  0.1 310708  5988 ?        Ssl  01:03   0:00  \_ /usr/libexec/xdg-permission-store
ibennn      2166  0.0  0.1  98284  6712 ?        Ssl  01:03   0:00  \_ /usr/libexec/gcr-ssh-agent --base-dir /run/user/1000/gcr
ibennn      2167  0.0  0.1  90568  4968 ?        Ssl  01:03   0:00  \_ /usr/libexec/gnome-session-ctl --monitor
ibennn      2169  0.0  0.1  10316  6240 ?        Ss   01:03   0:00  \_ /usr/bin/ssh-agent -D
ibennn      2726  0.0  0.2 611932  8768 ?        Sl   01:03   0:00  |   \_ /usr/libexec/gvfsd-trash --spawner :1.21 /org/gtk/gvfs/exec_spaw/0
ibennn      2460  0.0  1.7 847604 59852 ?        Sl   01:03   0:00  |   \_ /usr/libexec/evolution-data-server/evolution-alarm-notify
ibennn      2472  0.0  0.1 211084  5380 ?        Sl   01:03   0:00  |   |       \_ /usr/libexec/glycin-loaders/2+/glycin-image-rs --dbus-fd 63
ibennn      2737  0.0  1.9 218784 67240 ?        S    01:03   0:00  |   \_ /usr/bin/Xwayland :0 -rootless -noreset -accessx -core -auth /run/user/1000/.mutter-Xwaylandauth.R4QHN3 -listenfd 4 -listenfd 5 -displayfd 6 -initfd 7 -byteswappedclients
ibennn      2821  0.2  1.8 2861180 65512 ?       Sl   01:03   0:00  |   \_ gjs /usr/share/gnome-shell/extensions/ding@rastersoft.com/app/ding.js -E -P /usr/share/gnome-shell/extensions/ding@rastersoft.com/app
ibennn      2293  0.0  0.1   8940  4304 ?        S    01:03   0:00  |   \_ /usr/bin/dbus-daemon --config-file=/usr/share/defaults/at-spi2/accessibility.conf --nofork --print-address 11 --address=unix:path=/run/user/1000/at-spi/bus
ibennn      2295  0.0  0.1 170652  6832 ?        Sl   01:03   0:00  \_ /usr/libexec/at-spi2-registryd --use-gnome-session
ibennn      2318  0.0  1.1 616372 40792 ?        Ssl  01:03   0:00  \_ /usr/libexec/evolution-source-registry
ibennn      2354  0.0  0.1 172972  6480 ?        Ssl  01:03   0:00  \_ /usr/libexec/gsd-screensaver-proxy
ibennn      2622  0.0  0.1 311488  6532 ?        Ssl  01:03   0:00  \_ /usr/libexec/gvfs-mtp-volume-monitor
ibennn      2643  0.0  0.1 311260  6376 ?        Ssl  01:03   0:00  \_ /usr/libexec/gvfs-goa-volume-monitor
ibennn      2720  0.0  0.1 165940  5552 ?        Ssl  01:03   0:00  \_ /usr/libexec/dconf-service
ibennn      2873  0.0  1.1 640932 41280 ?        Ssl  01:03   0:00  \_ /usr/libexec/xdg-desktop-portal-gnome
ibennn      2875  0.0  0.1 172512  6364 ?        Ssl  01:03   0:00  \_ /usr/libexec/gvfsd-metadata
ibennn      2876  0.0  1.9 380812 68468 ?        Sl   01:03   0:00  \_ /usr/libexec/ibus-x11
ibennn      3153  0.7  7.1 1980020 246504 ?      Sl   01:04   0:01  \_ /usr/bin/ptyxis --gapplication-service
ibennn      3173  0.0  0.1 241092  6928 ?        Ssl  01:04   0:00      \_ /usr/libexec/ptyxis-agent --socket-fd=3 --rlimit-nofile=1024
ibennn      3213  0.0  0.1  12048  5852 pts/0    Ss   01:04   0:00          \_ /usr/bin/bash
ibennn      3288  200  0.1  12304  3968 pts/0    R+   01:06   0:00              \_ ps aux --forest
ibennn      3289  0.0  0.0   9100  2132 pts/0    S+   01:06   0:00              \_ grep --color=auto -w 1
```


**PID 1 (Systemd):**
   - **Nama:** `systemd`.
   - **Fungsi:** Merupakan proses pertama yang dijalankan oleh kernel saat booting. `systemd` berfungsi sebagai induk dari seluruh proses di Linux, mengelola manajemen layanan (services), dan memastikan sistem operasi berjalan dengan stabil.

### 2. Hitung berapa proses yang dimiliki oleh user root dan berapa yang dimiliki oleh user Anda. Mengapa root memiliki lebih banyak proses?

**Jawaban:**

```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week06$ ps -u root | wc -l
130
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week06$ ps -u ibennn | wc -l
88
```


**Perbandingan Jumlah Proses (Root vs User):**
   - **Temuan:** Jumlah proses milik `root` jauh lebih banyak daripada user biasa.
   - **Alasan:** User `root` harus menjalankan berbagai layanan latar belakang (background services), manajemen perangkat keras, dan keamanan sistem agar OS tetap berfungsi. User biasa hanya menjalankan aplikasi yang terkait dengan aktivitas pengguna saja.

### 3. Temukan semua proses yang berada dalam kondisi S. Mengapa sebagian besar proses di sistem berada dalam kondisi ini?
**Jawaban:**

```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week06$ ps aux | awk '$8 ~ /^S/' | wc -l
159
```


**Dominasi Kondisi S (Sleeping):**
   - **Analisis:** Sebagian besar proses berada dalam kondisi **S** (*Interruptible Sleep*).
   - **Alasan:** Hal ini dilakukan demi efisiensi sistem. Proses hanya akan "bangun" (status **R**) saat ada tugas yang perlu dikerjakan (seperti input pengguna atau request jaringan). Jika tidak ada tugas, proses akan tidur agar tidak membebani penggunaan CPU secara terus-menerus.
---
## Latihan 6.B

### 1.  Jalankan tiga perintah sleep dengan durasi 100, 200, dan 300 detik di background. Verifikasi ketiganya dengan jobs.

**Jawaban:**

```bash 
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week06$ 
sleep 100 &
sleep 200 &
sleep 300 &
jobs
[1] 3503
[2] 3504
[3] 3505
[1]   Running                 sleep 100 &
[2]-  Running                 sleep 200 &
[3]+  Running                 sleep 300 &
```


**Verifikasi Background Jobs:**
   - Tiga perintah `sleep` berhasil dijalankan secara bersamaan di latar belakang menggunakan simbol `&`.
   - Perintah `jobs` menampilkan tiga identitas job: `[1]`, `[2]`, dan `[3]`.
### 2. Bawa job kedua ke foreground, jeda dengan Ctrl+Z , lalu kembalikan ke background dengan bg.
**Jawaban:**

```bash
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week06$ fg %2
sleep 200
^Z
[2]+  Stopped                 sleep 200
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week06$ bg %2
[2]+ sleep 200 &
```


**Manipulasi Job Kedua (`fg`, `Ctrl+Z`, `bg`):**
   - Menggunakan `fg %2` membawa proses ke kendali utama terminal.
   - `Ctrl+Z` berhasil memberikan sinyal **SIGTSTP** yang mengubah status job menjadi `Stopped`.
   - Perintah `bg %2` mengaktifkan kembali proses tersebut di latar belakang, sehingga terminal tetap bisa digunakan untuk perintah lain.


### 3. Hentikan job pertama dengan kill %1. Tampilkan kembali daftar job. Berapa job yang tersisa?

**Jawaban:**

```bash 
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week06$ kill %1
jobs
[1]   Running                 sleep 100 &
[2]-  Running                 sleep 200 &
[3]+  Running                 sleep 300 &
[1]   Terminated              sleep 100
```


**Terminasi Job Spesifik:**
   - Perintah `kill %1` berhasil menghentikan job pertama secara spesifik tanpa mengganggu job lainnya.
   - **Job tersisa:** Terdapat **2 job** yang masih aktif dalam daftar (Job [2] dan Job [3]).

---
## Latihan 6.C

### 1. Jalankan dua proses sleep: satu dengan nice +5 dan satu dengan nice +15. Verifikasi nilai NI keduanya dengan ps

**Jawaban:**

```bash 
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week06$ nice -n 5 sleep 500 &
nice -n 15 sleep 600 &
ps -o pid,ni,stat,comm -C sleep
[4] 3586
[2]   Done                    sleep 200
[3]   Done                    sleep 300
[5] 3587
    PID  NI STAT COMMAND
   3586   5 SN   sleep
   3587  15 SN   sleep
```


**Verifikasi Nilai Nice:**
   - Perintah `nice -n 5` dan `nice -n 15` berhasil dijalankan.
   - Melalui `ps -o ni`, terverifikasi bahwa masing-masing proses memiliki nilai **NI 5** dan **NI 15**.
### 2. Gunakan renice untuk mengubah nice proses pertama menjadi +10. Proses mana yang kini lebih diprioritaskan scheduler?
**Jawaban:**

```bash 
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week06$ pgrep sleep
3586
3587
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week06$ ps -o pid,ni,stat,comm -p 3586
    PID  NI STAT COMMAND
   3586   5 SN   sleep

```


**Efek `renice` terhadap Penjadwalan:**
   - Setelah mengubah proses pertama menjadi **NI 10**, proses tersebut tetap **lebih diprioritaskan** dibandingkan proses kedua (NI 15).
   - **Prinsip Scheduler:** Nilai *nice* yang lebih rendah menunjukkan prioritas yang lebih tinggi. Karena 10 < 15, maka proses pertama mendapatkan alokasi sumber daya CPU yang lebih besar.


### 3.  Kirim SIGSTOP ke salah satu proses, verifikasi kondisi T-nya, lalu kirim SIGCONT. Akhiri semua proses percobaan dengan pkill sleep.

**Jawaban:**

```bash 
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week06$ kill -SIGSTOP 3586 
ps -o pid,stat,comm -p 3586
    PID STAT COMMAND
   3586 TN   sleep

[4]+  Stopped                 nice -n 5 sleep 500
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week06$ kill -SIGCONT 3586 
ps -o pid,stat,comm -p 3586
    PID STAT COMMAND
   3586 SN   sleep
ibennn@ibennn-QEMU-Virtual-Machine:~/praktikum-os/week06$ pkill sleep
[4]-  Terminated              nice -n 5 sleep 500
[5]+  Terminated              nice -n 15 sleep 600
```


**Manajemen Sinyal dan Pembersihan:**
   - **SIGSTOP:** Berhasil mengubah status proses menjadi **T** (Stopped/Suspended).
   - **SIGCONT:** Berhasil membangunkan kembali proses ke status **S** (Sleeping).
   - **pkill:** Perintah `pkill sleep` sangat efektif untuk menghentikan seluruh proses `sleep` secara sekaligus tanpa harus memasukkan PID satu per satu.
