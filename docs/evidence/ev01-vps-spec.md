# ev01 - Spesifikasi VM

Diambil: 2026-11-08 01:25 UTC (= 08-11-2026 08:25 WIB)

## Tipe VM menurut Azure (metadata instance)
```
vmSize : Standard_B2ats_v2
region : IndonesiaCentral
zone   : 1
```

## OS
```
PRETTY_NAME="Ubuntu 24.04.5 LTS"
VERSION="24.04.5 LTS (Noble Numbat)"
```

## nproc
```
2
```

## lscpu (ringkas)
```
CPU(s):                                  2
Model name:                              AMD EPYC 7763 64-Core Processor
Thread(s) per core:                      2
Core(s) per socket:                      1
Socket(s):                               1
Hypervisor vendor:                       Microsoft
```

## free -h
```
               total        used        free      shared  buff/cache   available
Mem:           887Mi       273Mi        48Mi       3.9Mi       592Mi       613Mi
Swap:          1.0Gi       4.0Ki       1.0Gi
```

## lsblk
```
NAME    MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS
sda       8:0    0   30G  0 disk 
├─sda1    8:1    0   29G  0 part /
├─sda14   8:14   0    4M  0 part 
├─sda15   8:15   0  106M  0 part /boot/efi
└─sda16 259:0    0  913M  0 part /boot
```

## df -h /
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/root        29G  4.2G   24G  15% /
```

## Port listen (ss -lnt)
```
State  Recv-Q Send-Q Local Address:Port Peer Address:PortProcess
LISTEN 0      2048       127.0.0.1:8000      0.0.0.0:*          
LISTEN 0      4096       127.0.0.1:2019      0.0.0.0:*          
LISTEN 0      4096         0.0.0.0:22        0.0.0.0:*          
LISTEN 0      4096   127.0.0.53%lo:53        0.0.0.0:*          
LISTEN 0      4096      127.0.0.54:53        0.0.0.0:*          
LISTEN 0      4096               *:80              *:*          
LISTEN 0      4096            [::]:22           [::]:*          
```

## Penjelasan vCPU
- nproc = 2 dan lscpu: CPU(s) = 2, terdiri dari 1 core x 2 thread per core (sudut pandang guest VM).
- vCPU adalah unit virtual, bukan core fisik khusus. Seri B bersifat burstable (kredit CPU terbatas).
- SKU Standard_B2ats_v2 menurut metadata Azure sama dengan yang tercatat di portal dan di dokumen.

## Tabel deviasi terhadap batas template
| Item | Batas template | Nilai nyata | Sumber bukti | Status |
|---|---|---|---|---|
| vCPU | 1 | 2 | nproc, lscpu, metadata Azure | Deviasi dilaporkan; keputusan dosen belum ada |
| RAM | 1 GB | 1 GiB (887 MiB terlihat OS) | free -h | Sesuai |
| Disk | 20 GB | 30 GiB (partisi root 29G) | lsblk, df -h / | Deviasi dilaporkan; keputusan dosen belum ada |
| OS | Ubuntu 24.04 | Ubuntu 24.04.5 LTS | /etc/os-release | Sesuai |

## Sumber katalog penyedia
Microsoft, "Basv2-series sizes", Azure Virtual Machines:
https://learn.microsoft.com/azure/virtual-machines/sizes/general-purpose/basv2-series

## Bukti portal
Screenshot portal Azure (diambil 08-11-2026): ev01-portal-vm.png (Ikhtisar VM), ev01-portal-disk.png (Disk), ev01-katalog-basv2.png (katalog Microsoft Basv2).

## Rujukan lain
Konfigurasi firewall (UFW) dan SSH dari M03: docs/evidence/m03/ (ufw, ssh-hardening).

## Status temuan 01
Lulus (08-11-2026): SKU, vCPU, RAM, dan disk konsisten antara metadata Azure, nproc/free/lsblk, portal, dan katalog Microsoft.
