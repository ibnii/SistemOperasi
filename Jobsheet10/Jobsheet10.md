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
