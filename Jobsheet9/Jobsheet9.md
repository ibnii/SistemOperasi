# Jobsheet 9 - Sistem Operasi

```text
+-----------------------------------------------------------+
| JOBSHEET 9 | BASH PROGRAMMING                        |
+-----------------------------------------------------------+
```

## Identitas

| Nama         | NIM          | Kelas |
| :----------- | :----------- | :---- |
| Ibni Andarta | 254107020258 | TI-1G |

---

## Praktikum 7.1

### Buat workspace praktikum:

```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO$ mkdir -p  week09/{scripts,logs,data}
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO$ cd week09
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09$ ls
data  logs  scripts
```

### Buat script dengan nano:

```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ nano laporan-sistem.sh
```

### Membuat laporan-sistem.sh

```bash
#!/bin/bash
# Script: laporan-sistem.sh
echo "================================"
echo "LAPORAN SISTEM"
echo "================================"
echo "Tanggal: $(date '+%A, %d %B %Y')"
echo "Jam: $(date '+%H:%M:%S')"
echo "Hostname: $(hostname)"
echo "User: $(whoami)"
echo "CPU core: $(nproc)"
echo "RAM bebas: $(free -h | awk '/^Mem/ { print $4 }')"
echo "Disk /: $(df -h / | awk 'NR==2 { print $5 }') terpakai"
echo "================================"
```

### Beri izin dan jalankan:

```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ chmod +x laporan-sistem.sh
./laporan-sistem.sh
================================
LAPORAN SISTEM
================================
Tanggal: Tuesday, 05 May 2026
Jam: 04:27:15
Hostname: SO
User: so
CPU core: 10
RAM bebas: 7.4Gi
Disk /: 2% terpakai
================================
```

---

## Latihan 9.1

```bash
o@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ nano laporan-sistem.sh

#!/bin/bash
# Script: laporan-sistem.sh

OUTPUT_FILE="laporan-$(date '+%Y-%m-%d').txt"
{
  echo "================================"
  echo "LAPORAN SISTEM"
  echo "================================"
  echo "Tanggal: $(date '+%A, %d %B %Y')"
  echo "Jam: $(date '+%H:%M:%S')"
  echo "Hostname: $(hostname)"
  echo "User: $(whoami)"
  echo "CPU core: $(nproc)"
  echo "RAM bebas: $(free -h | awk '/^Mem/ { print $4 }')"
  echo "Disk /: $(df -h / | awk 'NR==2 { print $5 }') terpakai"
  echo "================================"
} | tee "$OUTPUT_FILE"

so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ chmod +x laporan-sistem.sh
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ ./laporan-sistem.sh
================================
LAPORAN SISTEM
================================
Tanggal: Tuesday, 05 May 2026
Jam: 04:32:58
Hostname: SO
User: so
CPU core: 10
RAM bebas: 7.4Gi
Disk /: 2% terpakai
================================
```

---

## Praktikum 7.2

### Membuat script info-sistem.sh

```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ nano info-sistem.sh
```

### Mengisi info-sistem.sh

```bash
#!/bin/bash
# Penggunaan: ./info-sistem.sh [nama-admin] [batas-disk-persen]
ADMIN=${1:-"Tidak dikenal"}
BATAS=${2:-80}
TANGGAL=$(date '+%F %T')
DISK_PERSEN=$(df / | awk 'NR==2 { print $5 }' | tr -d '%')

echo "Admin: $ADMIN"
echo "Tanggal: $TANGGAL"
echo "Disk /: ${DISK_PERSEN}% terpakai"
echo "Batas: ${BATAS}%"

if [ "$DISK_PERSEN" -gt "$BATAS" ]; then
    echo "STATUS: PERINGATAN - disk melebihi batas!"
else
    SISA=$((BATAS - DISK_PERSEN))
    echo "STATUS: Normal (sisa toleransi ${SISA}%)"
fi
```

### Menguji Script

```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ chmod +x info-sistem.sh
./info-sistem.sh
./info-sistem.sh "Dian" 50
./info-sistem.sh "Dian" 10

Admin: Tidak dikenal
Tanggal: 2026-05-05 16:20:42
Disk /: 2% terpakai
Batas: 80%
STATUS: Normal (sisa toleransi 78%)
Admin: Dian
Tanggal: 2026-05-05 16:20:42
Disk /: 2% terpakai
Batas: 50%
STATUS: Normal (sisa toleransi 48%)
Admin: Dian
Tanggal: 2026-05-05 16:20:42
Disk /: 2% terpakai
Batas: 10%
STATUS: Normal (sisa toleransi 8%)
```

---

## Latihan 9.2

```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ nano kalkulator.sh

if [ $# -lt 3 ]; then
    echo "Error: Argumen tidak lengkap."
    echo "Penggunaan: ./kalkulator.sh [angka1] [operator] [angka2]"
    echo "Contoh: ./kalkulator.sh 20 + 5"
    exit 1
fi

ANGKA1=$1
OPERATOR=$2
ANGKA2=$3
case $OPERATOR in
    +)
        HASIL=$((ANGKA1 + ANGKA2))
        ;;
    -)
        HASIL=$((ANGKA1 - ANGKA2))
        ;;
    \*)
        HASIL=$((ANGKA1 * ANGKA2))
        ;;
    /)
        if [ $ANGKA2 -eq 0 ]; then
            echo "Error: Tidak bisa membagi dengan nol!"
            exit 1
        fi
        HASIL=$((ANGKA1 / ANGKA2))
        ;;
    *)
        echo "Error: Operator tidak dikenal. Gunakan +, -, *, atau /."
        exit 1
        ;;
esac
echo "Hasil: $ANGKA1 $OPERATOR $ANGKA2 = $HASIL"

so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ chmod +x kalkulator.sh
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ ./kalkulator.sh 20 + 5
Hasil: 20 + 5 = 25
```

---
## Praktikum 7.3

### Membuat script grading-batch.sh
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ nano grading-batch.sh
```

### Mengisi grading-batch.sh
```bash
MAHASISWA=("Andi:92" "Budi:73" "Citra:55" "Deni:80" "Eka:45")
echo "=== HASIL GRADING ==="
for ENTRI in "${MAHASISWA[@]}"; do
    NAMA=$(echo "$ENTRI" | cut -d: -f1)
    NILAI=$(echo "$ENTRI" | cut -d: -f2)
    if [ "$NILAI" -ge 85 ]; then
        GRADE="A"
    elif [ "$NILAI" -ge 75 ]; then
        GRADE="B"
    elif [ "$NILAI" -ge 65 ]; then
        GRADE="C"
    elif [ "$NILAI" -ge 55 ]; then
        GRADE="D"
    else
        GRADE="E"
    fi
    printf "%-10s %3d %s\n" "$NAMA" "$NILAI" "$GRADE"
done
echo "====================="
```

### Menjalankan script grading
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ chmod +x grading-batch.sh

./grading-batch.sh
=== HASIL GRADING ===
Andi        92 A
Budi        73 C
Citra       55 D
Deni        80 B
Eka         45 E
=====================
```

### Membuat script menu-sistem.sh
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ nano menu-sistem.sh
```

### Mengisi menu-sistem.sh
```bash
#!/bin/bash
# Menu interaktif pemantauan sistem
while true; do
    echo ""
    echo "===== MENU MONITOR====="
    echo "1) Info disk"
    echo "2) Info memori"
    echo "3) Proses teratas"
    echo "4) Keluar"
    echo -n "Pilih [1-4]: "
    read PILIHAN
    case $PILIHAN in
        1) df -h ;;
        2) free -h ;;
        3) ps aux --sort=-%cpu | head -6 ;;
        4) echo "Sampai jumpa!"; exit 0 ;;
        *) echo "Pilihan tidak valid." ;;
    esac
done
```

### Menjalankan menu
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ chmod +x menu-sistem.sh
./menu-sistem.sh

===== MENU MONITOR=====
1) Info disk
2) Info memori
3) Proses teratas
4) Keluar
Pilih [1-4]: 1
Filesystem      Size  Used Avail Use% Mounted on
/dev/vdb1        58G  960M   57G   2% /
none            492K  4.0K  488K   1% /dev
orbstack        4.0G  512K  4.0G   1% /opt/orbstack-guest
tmpfs           6.3G     0  6.3G   0% /tmp
/dev/vdb1        58G  960M   57G   2% /opt/orbstack-guest/data
orbstack        4.0G  4.0K  4.0G   1% /opt/orbstack-guest/run
mac             229G  169G   61G  74% /mnt/mac
machines        4.0G  4.0K  4.0G   1% /mnt/machines
tmpfs           4.0G     0  4.0G   0% /dev/shm
tmpfs           1.6G  404K  1.6G   1% /run
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           800M  8.0K  800M   1% /run/user/501

===== MENU MONITOR=====
1) Info disk
2) Info memori
3) Proses teratas
4) Keluar
Pilih [1-4]: 2
               total        used        free      shared  buff/cache   available
Mem:           7.8Gi       431Mi       7.4Gi        24Mi       104Mi       7.4Gi
Swap:          8.8Gi          0B       8.8Gi

===== MENU MONITOR=====
1) Info disk
2) Info memori
3) Proses teratas
4) Keluar
Pilih [1-4]: 3
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
so          4303  100  0.0  13620  3960 pts/1    R+   16:32   0:00 ps aux --sort=-%cpu
root         107  0.0  0.1 1245384 9956 ?        Ssl  Apr25   0:29 orbstack-agent: SO
so          3775  0.0  0.0  10324  1916 pts/1    Ss   09:10   0:00 -bash
root           1  0.0  0.0  21264  3332 ?        Ss   Apr25   0:17 /sbin/init
root         227  0.0  0.0   9360   480 ?        Ss   Apr25   0:16 /usr/sbin/cron -f -P

===== MENU MONITOR=====
1) Info disk
2) Info memori
3) Proses teratas
4) Keluar
Pilih [1-4]: 4
Sampai jumpa!
```

---
## Latihan 9.3 
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ nano grading-batch.sh
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ cat grading-batch.sh
#!/bin/bash
# Script: grading-batch.sh

MAHASISWA=("Andi:92" "Budi:73" "Citra:55" "Deni:80" "Eka:45")

echo "=== HASIL GRADING ==="
for ENTRI in "${MAHASISWA[@]}"; do
    NAMA=$(echo "$ENTRI" | cut -d: -f1)
    NILAI=$(echo "$ENTRI" | cut -d: -f2)

    if [ "$NILAI" -ge 85 ]; then
        GRADE="A"
    elif [ "$NILAI" -ge 75 ]; then
        GRADE="B"
    elif [ "$NILAI" -ge 65 ]; then
        GRADE="C"
    elif [ "$NILAI" -ge 55 ]; then
        GRADE="D"
    else
        GRADE="E"
    fi
    printf "%-10s %3d %s\n" "$NAMA" "$NILAI" "$GRADE"
done

echo "====================="
echo "RINGKASAN GRADE:"

countA=0; countB=0; countC=0; countD=0; countE=0

for ENTRI in "${MAHASISWA[@]}"; do
    NILAI=$(echo "$ENTRI" | cut -d: -f2)
    
    if [ "$NILAI" -ge 85 ]; then
        ((countA++))
    elif [ "$NILAI" -ge 75 ]; then
        ((countB++))
    elif [ "$NILAI" -ge 65 ]; then
        ((countC++))
    elif [ "$NILAI" -ge 55 ]; then
        ((countD++))
    else
        ((countE++))
    fi
done

echo "Grade A: $countA mahasiswa"
echo "Grade B: $countB mahasiswa"
echo "Grade C: $countC mahasiswa"
echo "Grade D: $countD mahasiswa"
echo "Grade E: $countE mahasiswa"
echo "====================="

so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ chmod +x grading-batch.sh
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ ./grading-batch.sh
=== HASIL GRADING ===
Andi        92 A
Budi        73 C
Citra       55 D
Deni        80 B
Eka         45 E
=====================
RINGKASAN GRADE:
Grade A: 1 mahasiswa
Grade B: 1 mahasiswa
Grade C: 1 mahasiswa
Grade D: 1 mahasiswa
Grade E: 1 mahasiswa
=====================
```

---
## Praktikum 7.4

### Membuat lib-validasi.sh
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ nano lib-validasi.sh
```

### Isi lib-validasi.sh
```bash
#!/bin/bash
# lib-validasi.sh - Library fungsi validasi
adalah_angka () {
    [[ "$1" =~ ^[0-9]+$ ]]
}
file_bisa_dibaca () {
    [ -f "$1" ] && [ -r "$1" ]
}
error_exit () {
    echo "ERROR: $1" >&2
    exit 1
}
info () { echo "[INFO] $1"; }
sukses () { echo "[OK] $1"; }
```

### Membuat script pakai-library.sh
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ nano pakai-library.sh
```

### Isi pakai-library.sh
```bash
#!/bin/bash
# Muat library (seperti import di Java)
source ~/praktikum-os/week09/scripts/lib-validasi.sh
ANGKA=$1
FILE=$2

[ -z "$ANGKA" ] || [ -z "$FILE" ] && \
error_exit "Penggunaan: $0 <angka> <file>"

if adalah_angka "$ANGKA"; then
    sukses "Input '$ANGKA' adalah angka valid"
else
    error_exit "'$ANGKA' bukan angka"
fi

if file_bisa_dibaca "$FILE"; then
    sukses "File '$FILE' bisa dibaca"
    info "Jumlah baris: $(wc -l < "$FILE")"
else
    error_exit "File '$FILE' tidak ada atau tidak bisa dibaca"
fi
```

### Menguji semua skenario
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ ./pakai-library.sh 42 /etc/hostname
./pakai-library.sh abc /etc/hostname
./pakai-library.sh 42 /tidak-ada.txt
./pakai-library.sh
[OK] Input '42' adalah angka valid
[OK] File '/etc/hostname' bisa dibaca
[INFO] Jumlah baris: 1
ERROR: 'abc' bukan angka
[OK] Input '42' adalah angka valid
ERROR: File '/tidak-ada.txt' tidak ada atau tidak bisa dibaca
ERROR: Penggunaan: ./pakai-library.sh <angka> <file>
```

## Latihan 9.4
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ nano lib-validasi.sh
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ cat lib-validasi.sh
#!/bin/bash
# lib-validasi.sh - Library fungsi validasi
adalah_angka () {
    [[ "$1" =~ ^[0-9]+$ ]]
}
file_bisa_dibaca () {
    [ -f "$1" ] && [ -r "$1" ]
}
error_exit () {
    echo "ERROR: $1" >&2
    exit 1
}
info () { echo "[INFO] $1"; }
sukses () { echo "[OK] $1"; }

konfirmasi () {
    echo -n "$1 (y/n): "
    read JAWABAN
    case "$JAWABAN" in
        [yY]|[yY][eE][sS]) return 0 ;;
        *) return 1 ;;
    esac
}
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ nano hapus-file.sh
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ cat hapus-file.sh
#!/bin/bash
# Script: hapus-file.sh

source ./lib-validasi.sh

FILE_TARGET=$1

if [ -z "$FILE_TARGET" ]; then
    error_exit "Tentukan file yang ingin dihapus. Contoh: $0 data.txt"
fi

if ! file_bisa_dibaca "$FILE_TARGET"; then
    error_exit "File '$FILE_TARGET' tidak ditemukan."
fi

if konfirmasi "Apakah Anda yakin ingin menghapus $FILE_TARGET?"; then
    rm "$FILE_TARGET"
    sukses "File '$FILE_TARGET' berhasil dihapus."
else
    info "Penghapusan dibatalkan."
fi
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ chmod +x hapus-file.sh
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ touch coba.txt
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ ./hapus-file.sh coba.txt
Apakah Anda yakin ingin menghapus coba.txt? (y/n): Y
[OK] File 'coba.txt' berhasil dihapus.
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ ls
grading-batch.sh  hapus-file.sh  info-sistem.sh  kalkulator.sh  laporan-2026-05-05.txt  laporan-sistem.sh  lib-validasi.sh  menu-sistem.sh  pakai-library.sh
```

---
## Praktikum 7.5

### Membuat backup-data.sh
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ nano backup-data.sh
```

### Isi backup-data.sh
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ cat backup-data.sh
#!/bin/bash
# Penggunaan : ./backup-data.sh [-v] [-c] [-l logfile]
VERBOSE=false
COMPRESS=false
LOG_FILE=""

while getopts "vcl:" OPSI; do
    case $OPSI in
        v) VERBOSE=true ;;
        c) COMPRESS=true ;;
        l) LOG_FILE="$OPTARG" ;;
        *) echo "Penggunaan: $0 [-v] [-c] [-l logfile]"; exit 1 ;;
    esac
done

shift $((OPTIND - 1))

SUMBER=$1
TUJUAN=$2

log () {
    local MSG="[$(date '+%T')] $1"
    echo "$MSG"
    [ -n "$LOG_FILE" ] && echo "$MSG" >> "$LOG_FILE"
}

[ -z "$SUMBER" ] || [ -z "$TUJUAN" ] && {
    echo "ERROR: sumber dan tujuan wajib diisi"; exit 1; 
}

[ ! -d "$SUMBER" ] && { 
    log "ERROR: $SUMBER tidak ada"; exit 2; 
}

mkdir -p "$TUJUAN"
TANGGAL=$(date '+%F-%H%M%S')

[ "$VERBOSE" = true ] && log "Sumber: $SUMBER | Tujuan: $TUJUAN"

if [ "$COMPRESS" = true ]; then
    ARSIP="$TUJUAN/backup-$(basename "$SUMBER")-$TANGGAL.tar.gz"
    tar -czf "$ARSIP" -C "$(dirname "$SUMBER")" "$(basename "$SUMBER")"
    log "Arsip: $ARSIP ($(du -sh "$ARSIP" | cut -f1))"
else
    cp -r "$SUMBER" "$TUJUAN/backup-$(basename "$SUMBER")-$TANGGAL"
    log "Backup selesai."
fi
```

### Menguji script backup
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ chmod +x backup-data.sh

./backup-data.sh ../data ../logs
[16:58:36] Backup selesai.
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ ./backup-data.sh -v -c -l ../logs/backup.log ../data ../logs
[16:58:45] Sumber: ../data | Tujuan: ../logs
[16:58:45] Arsip: ../logs/backup-data-2026-05-05-165845.tar.gz (4.0K)
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ cat ../logs/backup.log
[16:58:45] Sumber: ../data | Tujuan: ../logs
[16:58:45] Arsip: ../logs/backup-data-2026-05-05-165845.tar.gz (4.0K)
```

---
## Praktikum 7.6

### Membuat debug-latihan.sh
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ nano debug-latihan.sh
```

### Isi debug-latihan.sh
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ cat debug-latihan.sh
#!/bin/bash
# Script: debug-latihan.sh
# Penggunaan: ./debug-latihan.sh <direktori> <batas-mb>
DIREKTORI=$1
BATAS=$2

if [ $# -ne 2 ]; then
    echo "Penggunaan: $0 <direktori> <batas-mb>"
    exit 1
fi

UKURAN=$(du -sm "$DIREKTORI" | cut -f1)

echo "Direktori: $DIREKTORI"
echo "Ukuran: ${UKURAN} MB"
echo "Batas: ${BATAS} MB"

if [ "$UKURAN" -gt "$BATAS" ]; then
    echo "PERINGATAN: Ukuran melebihi batas!"
    echo "Kelebihan: $((UKURAN - BATAS)) MB"
else
    echo "Status: Normal (sisa: $((BATAS - UKURAN)) MB)"
```

### Menganalisis script dengan debugging
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ chmod +x debug-latihan.sh
bash -n debug-latihan.sh && echo "Sintaks OK"
bash -x debug-latihan.sh /etc 10
./debug-latihan.sh /var 50
./debug-latihan.sh

Sintaks OK
+ DIREKTORI=/etc
+ BATAS=10
+ '[' 2 -ne 2 ']'
++ du -sm /etc
++ cut -f1
du: cannot read directory '/etc/credstore': Permission denied
du: cannot read directory '/etc/credstore.encrypted': Permission denied
du: cannot read directory '/etc/ssl/private': Permission denied
+ UKURAN=4
+ echo 'Direktori: /etc'
Direktori: /etc
+ echo 'Ukuran: 4 MB'
Ukuran: 4 MB
+ echo 'Batas: 10 MB'
Batas: 10 MB
+ '[' 4 -gt 10 ']'
+ echo 'Status: Normal (sisa: 6 MB)'
Status: Normal (sisa: 6 MB)
du: cannot read directory '/var/cache/apt/archives/partial': Permission denied
du: cannot read directory '/var/cache/ldconfig': Permission denied
du: cannot read directory '/var/cache/private': Permission denied
du: cannot read directory '/var/lib/apt/lists/partial': Permission denied
du: cannot read directory '/var/lib/private': Permission denied
du: cannot read directory '/var/lib/ubuntu-advantage/apt-esm/var/lib/apt/lists/partial': Permission denied
du: cannot read directory '/var/log/private': Permission denied
du: cannot read directory '/var/spool/cron/crontabs': Permission denied
du: cannot read directory '/var/spool/rsyslog': Permission denied
Direktori: /var
Ukuran: 441 MB
Batas: 50 MB
PERINGATAN: Ukuran melebihi batas!
Kelebihan: 391 MB
Penggunaan: ./debug-latihan.sh <direktori> <batas-mb>
```

---
## Latihan 9.5
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ nano debug-latihan.sh
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ cat debug-latihan.sh
#!/bin/bash
set -e
# Script: debug-latihan.sh
# Penggunaan: ./debug-latihan.sh <direktori> <batas-mb>

DIREKTORI=$1
BATAS=$2

# 1. Validasi jumlah argumen
if [ $# -ne 2 ]; then
    echo "ERROR: Argumen tidak lengkap."
    echo "Penggunaan: $0 <direktori> <batas-mb>"
    exit 1
fi

# 2. Pengecekan apakah direktori ada
if [ ! -d "$DIREKTORI" ]; then
    echo "ERROR: Direktori '$DIREKTORI' tidak ditemukan atau bukan folder!"
    exit 1
fi

# 3. Hitung ukuran (du tidak akan error karena direktori sudah dipastikan ada)
UKURAN=$(du -sm "$DIREKTORI" | cut -f1)

echo "Direktori: $DIREKTORI"
echo "Ukuran: ${UKURAN} MB"
echo "Batas: ${BATAS} MB"

if [ "$UKURAN" -gt "$BATAS" ]; then
    echo "PERINGATAN: Ukuran melebihi batas!"
    echo "Kelebihan: $((UKURAN - BATAS)) MB"
else
    echo "Status: Normal (sisa: $((BATAS - UKURAN)) MB)"
fi
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ ./debug-latihan.sh ../data 100
Direktori: ../data
Ukuran: 0 MB
Batas: 100 MB
Status: Normal (sisa: 100 MB)
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ ./debug-latihan.sh /folder/ngawur 100
ERROR: Direktori '/folder/ngawur' tidak ditemukan atau bukan folder!
```

---
## Tugas Praktikum 1.8

### Script Absensi Kelas
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ nano absensi.sh
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ cat absensi.sh
#!/bin/bash
LOG_FILE="absensi-$(date '+%Y-%m-%d').txt"

tampilkan_bantuan() {
    echo "Penggunaan: $0 [nama] [status]"
    echo "Opsi:"
    echo "  -r    Tampilkan rekapitulasi kehadiran hari ini"
    echo "  -h    Tampilkan bantuan ini"
    echo "Status yang tersedia: hadir, izin, alpha"
}

tampilkan_rekap() {
    if [ ! -f "$LOG_FILE" ]; then
        echo "Belum ada data absensi untuk hari ini."
        exit 0
    fi

    echo "=== REKAPITULASI ABSENSI HARI INI ==="
    cat "$LOG_FILE"
    echo "-------------------------------------"
    
    for status in hadir izin alpha; do
        jumlah=$(grep -ic "$status" "$LOG_FILE")
        echo "Total $status: $jumlah"
    done
    echo "====================================="
}

while getopts "rh" opt; do
  case $opt in
    r) tampilkan_rekap; exit 0 ;;
    h) tampilkan_bantuan; exit 0 ;;
    *) tampilkan_bantuan; exit 1 ;;
  esac
done

NAMA=$1
STATUS=$2

if [ -z "$NAMA" ] || [ -z "$STATUS" ]; then
    echo "Error: Nama dan Status harus diisi."
    tampilkan_bantuan
    exit 1
fi

JAM=$(date '+%H:%M')
echo "[$JAM] $NAMA - $STATUS" >> "$LOG_FILE"

echo "Berhasil mencatat absensi: $NAMA ($STATUS)"
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ chmod +x absensi.sh
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ ./absensi.sh "Ibennn" hadir
./absensi.sh "Dian" hadir
./absensi.sh "Budi" izin
./absensi.sh "Citra" alpha
./absensi.sh "Andi" hadir
Berhasil mencatat absensi: Ibennn (hadir)
Berhasil mencatat absensi: Dian (hadir)
Berhasil mencatat absensi: Budi (izin)
Berhasil mencatat absensi: Citra (alpha)
Berhasil mencatat absensi: Andi (hadir)
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ ./absensi.sh -r
=== REKAPITULASI ABSENSI HARI INI ===
[17:08] Ibennn - hadir
[17:08] Dian - hadir
[17:08] Budi - izin
[17:08] Citra - alpha
[17:08] Andi - hadir
-------------------------------------
Total hadir: 3
Total izin: 1
Total alpha: 1
=====================================
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ ls absensi-*.txt
absensi-2026-05-05.txt
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ cat absensi-*.txt
[17:08] Ibennn - hadir
[17:08] Dian - hadir
[17:08] Budi - izin
[17:08] Citra - alpha
[17:08] Andi - hadir
```

### Script Health Check Sistem
```bash
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ nano healthcheck.sh
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ cat healthcheck.sh
#!/bin/bash

# set -e: berhenti jika ada error
# set -u: berhenti jika ada variabel yang belum didefinisikan
# set -o pipefail: memastikan error di dalam pipe tetap terdeteksi
set -euo pipefail

THRESHOLD=80
LOG_FILE="healthcheck-$(date '+%Y-%m-%d').log"

cleanup() {
    echo -e "\n[INFO] Proses dihentikan oleh pengguna."
    exit 0
}
trap cleanup SIGINT SIGTERM

show_help() {
    echo "Penggunaan: $0 [-t threshold]"
    echo "  -t    Set batas (threshold) peringatan disk dalam persen (default: 80)"
    echo "  -h    Menampilkan bantuan ini"
}

run_healthcheck() {
    local limit=$1 
    
    echo "================================================"
    echo "          SERVER HEALTHCHECK REPORT             "
    echo "================================================"
    echo "Tanggal/Waktu : $(date '+%Y-%m-%d %H:%M:%S')"
    echo "Hostname      : $(hostname)"
    echo "Uptime        : $(uptime -p)"
    echo "CPU Load      : $(top -bn1 | grep "load average" | awk '{print $12 $13 $14}')"
    echo "Memory Usage  : $(free -h | awk '/Mem:/ {print $3 "/" $2}')"
    echo "------------------------------------------------"
    echo "File System Usage:"
    
    df -h | tail -n +2 | while read -r line; do
        local fs_name=$(echo "$line" | awk '{print $1}')
        local fs_perc=$(echo "$line" | awk '{print $5}' | tr -d '%')
        local fs_mount=$(echo "$line" | awk '{print $6}')
        
        printf "%-20s %-5s terpakai di %s\n" "$fs_name" "${fs_perc}%" "$fs_mount"
        
        if [ "$fs_perc" -ge "$limit" ]; then
            echo "   >>> [PERINGATAN] $fs_mount melebihi batas ${limit}%!"
        fi
    done
    echo "================================================"
}

while getopts "t:h" opt; do
    case $opt in
        t) THRESHOLD=$OPTARG ;;
        h) show_help; exit 0 ;;
        *) show_help; exit 1 ;;
    esac
done

run_healthcheck "$THRESHOLD" | tee -a "$LOG_FILE"

so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ chmod +x healthcheck.sh
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ ./healthcheck.sh
================================================
          SERVER HEALTHCHECK REPORT             
================================================
Tanggal/Waktu : 2026-05-05 17:12:07
Hostname      : SO
Uptime        : up 3 week, 3 days, 1 hour, 8 minutes
CPU Load      : 0.00,0.00,0.00
Memory Usage  : 427Mi/7.8Gi
------------------------------------------------
File System Usage:
/dev/vdb1            2%    terpakai di /
none                 1%    terpakai di /dev
orbstack             1%    terpakai di /opt/orbstack-guest
tmpfs                0%    terpakai di /tmp
/dev/vdb1            2%    terpakai di /opt/orbstack-guest/data
orbstack             1%    terpakai di /opt/orbstack-guest/run
mac                  74%   terpakai di /mnt/mac
machines             1%    terpakai di /mnt/machines
tmpfs                0%    terpakai di /dev/shm
tmpfs                1%    terpakai di /run
tmpfs                0%    terpakai di /run/lock
tmpfs                1%    terpakai di /run/user/501
================================================
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ ./healthcheck.sh -t 10
================================================
          SERVER HEALTHCHECK REPORT             
================================================
Tanggal/Waktu : 2026-05-05 17:12:29
Hostname      : SO
Uptime        : up 3 week, 3 days, 1 hour, 8 minutes
CPU Load      : 0.00,0.00,0.00
Memory Usage  : 430Mi/7.8Gi
------------------------------------------------
File System Usage:
/dev/vdb1            2%    terpakai di /
none                 1%    terpakai di /dev
orbstack             1%    terpakai di /opt/orbstack-guest
tmpfs                0%    terpakai di /tmp
/dev/vdb1            2%    terpakai di /opt/orbstack-guest/data
orbstack             1%    terpakai di /opt/orbstack-guest/run
mac                  74%   terpakai di /mnt/mac
   >>> [PERINGATAN] /mnt/mac melebihi batas 10%!
machines             1%    terpakai di /mnt/machines
tmpfs                0%    terpakai di /dev/shm
tmpfs                1%    terpakai di /run
tmpfs                0%    terpakai di /run/lock
tmpfs                1%    terpakai di /run/user/501
================================================
so@SO:/Users/ibennn/OrbData/DataUser/Praktikum-SO/week09/scripts$ cat healthcheck-$(date '+%Y-%m-%d').log
================================================
          SERVER HEALTHCHECK REPORT             
================================================
Tanggal/Waktu : 2026-05-05 17:12:07
Hostname      : SO
Uptime        : up 3 week, 3 days, 1 hour, 8 minutes
CPU Load      : 0.00,0.00,0.00
Memory Usage  : 427Mi/7.8Gi
------------------------------------------------
File System Usage:
/dev/vdb1            2%    terpakai di /
none                 1%    terpakai di /dev
orbstack             1%    terpakai di /opt/orbstack-guest
tmpfs                0%    terpakai di /tmp
/dev/vdb1            2%    terpakai di /opt/orbstack-guest/data
orbstack             1%    terpakai di /opt/orbstack-guest/run
mac                  74%   terpakai di /mnt/mac
machines             1%    terpakai di /mnt/machines
tmpfs                0%    terpakai di /dev/shm
tmpfs                1%    terpakai di /run
tmpfs                0%    terpakai di /run/lock
tmpfs                1%    terpakai di /run/user/501
================================================
================================================
          SERVER HEALTHCHECK REPORT             
================================================
Tanggal/Waktu : 2026-05-05 17:12:29
Hostname      : SO
Uptime        : up 3 week, 3 days, 1 hour, 8 minutes
CPU Load      : 0.00,0.00,0.00
Memory Usage  : 430Mi/7.8Gi
------------------------------------------------
File System Usage:
/dev/vdb1            2%    terpakai di /
none                 1%    terpakai di /dev
orbstack             1%    terpakai di /opt/orbstack-guest
tmpfs                0%    terpakai di /tmp
/dev/vdb1            2%    terpakai di /opt/orbstack-guest/data
orbstack             1%    terpakai di /opt/orbstack-guest/run
mac                  74%   terpakai di /mnt/mac
   >>> [PERINGATAN] /mnt/mac melebihi batas 10%!
machines             1%    terpakai di /mnt/machines
tmpfs                0%    terpakai di /dev/shm
tmpfs                1%    terpakai di /run
tmpfs                0%    terpakai di /run/lock
tmpfs                1%    terpakai di /run/user/501
================================================
```
