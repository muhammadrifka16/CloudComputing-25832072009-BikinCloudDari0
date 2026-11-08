# ev07 - TCO 12 bulan dan kredit Azure

Diambil: 08-11-2026 (WIB). Sumber: Portal Azure (Cost Management, Pendidikan Ikhtisar, Anggaran).

## 1. Kredit Azure for Students (FAKTA, ev07-kredit-azure.png)
- Kredit tersedia: US$87 dari US$100
- Kedaluwarsa: 18-09-2027 (315 hari dari 08-11-2026)
- Biaya November (sampai 08-11-2026): US$2,37
- Pembayaran uang tunai: tidak ada; biaya dipotong dari kredit.

## 2. Biaya aktual Sep sampai Okt 2026 (FAKTA, ev07-biaya-agt-okt.png)
Total US$10,85 (Agustus tidak ada biaya; VM dibuat 24-09-2026).
| Jenis sumber daya (nama terpotong di portal) | Biaya (US$) |
|---|---|
| microsoft.compute/d... (ASUMSI: disk) | 6,39 |
| microsoft.network/p... (ASUMSI: IP publik) | 4,47 |
| microsoft.compute/v... (ASUMSI: VM) | di bawah 0,01 |
| tanpa tipe sumber daya | -0,01 |
Biaya VM hampir nol diduga karena kuota gratis 750 jam per bulan untuk VM B2ats v2 pada Azure for Students (halaman azure.microsoft.com/free/students, diakses 08-11-2026). Ini ASUMSI; kuota dapat berubah.

## 3. Burn-rate (hitungan dari data di atas)
- Sep-Okt: US$10,85 / 38 hari (24-09 sampai 31-10) = US$0,286 per hari, sekitar US$8,6 per bulan.
- November: US$2,37 / 8 hari = US$0,296 per hari, sekitar US$8,9 per bulan (data bisa tertunda).
- Kredit terpakai sejak 24-09-2026: US$13 (100 - 87); cocok dengan 10,85 + 2,37 = 13,22.

## 4. Skenario 12 bulan (HITUNGAN)
Kurs JISDOR 6-11-2026 Rp18.130 per US$ (dari berita Metro TV, belum dari situs BI).
| Skenario | Per bulan | 12 bulan | Kredit US$87 habis sekitar |
|---|---|---|---|
| A. Kuota gratis VM berlaku (kondisi sekarang) | US$8,6 sampai 8,9 (Rp156.000 sampai 161.000) | US$103 sampai 107 (Rp1,87 sampai 1,94 juta) | akhir Agustus sampai awal September 2027 |
| B. Tanpa kuota gratis (tambah VM harga list US$7,81 per bulan) | US$16,4 sampai 16,7 (Rp297.000 sampai 303.000) | US$197 sampai 200 (Rp3,57 sampai 3,63 juta) | pertengahan April 2027 |
Skenario B memakai harga list dari azurespeed.com (belum termasuk disk dan IP), bukan hasil ukur.

## 5. Komponen TCO
| Komponen | Status |
|---|---|
| VM (compute) | di bawah US$0,01 aktual (kuota gratis); harga list US$7,81 per bulan |
| Disk Premium SSD LRS 30 GiB | sekitar US$5 per bulan (hitungan dari 6,39 per 38 hari) |
| IP publik | sekitar US$3,5 per bulan (hitungan dari 4,47 per 38 hari) |
| Domain | belum ada (disediakan dosen, detail belum jelas) |
| Backup eksternal | belum ada (M05) |
| Transfer data keluar | tidak terpisah di rincian portal |
| API/AI eksternal | belum ada (fitur AI belum diputuskan) |
| Pajak | belum ada informasi |

## 6. Anggaran dan peringatan (ev07-budget-alert.png)
- FAKTA (daftar anggaran): budget-bulanan-10usd, US$10 per bulan, reset bulanan, 01-11-2026 sampai 30-10-2027.
- FAKTA (dilihat di halaman detail portal, 08-11-2026): peringatan biaya aktual 80% (US$8) dan 100% (US$10) ke email, tanpa grup tindakan. Screenshot detail belum dilampirkan karena memuat email dan ID akun.
- Kolom pengeluaran anggaran masih US$0,00 pada 08-11-2026 (belum tersinkron).
- Burn-rate sekitar US$8,6 sampai 8,9 melewati US$8, sehingga peringatan 80% kemungkinan sering terpicu.

## 7. Skenario setelah kredit habis atau kedaluwarsa
Opsi: (1) hentikan dan hapus sumber daya, data diekspor lebih dulu; (2) pindah ke pay-as-you-go (perlu kartu kredit); (3) migrasi ke layanan lain.
- Keputusan penyusun (disetujui 08-11-2026): opsi 1 bila sisa kredit di bawah US$15 atau 30 hari sebelum 18-09-2027, mana yang lebih dulu.

## 8. Keterbatasan
- Data November belum lengkap dan dapat tertunda.
- Nama jenis sumber daya terpotong di portal; pengelompokan ke disk, IP, dan VM adalah asumsi.
- Kurs dari berita, bukan situs BI; kuota gratis VM berdasar halaman Microsoft dan dapat berubah.
- Domain, backup, dan API belum ada, sehingga TCO belum lengkap.
- Screenshot rincian biaya diambil 08-11-2026 pukul 13.11 WIB, sebelum anggaran dibuat, sehingga tertulis Anggaran tidak ada pada gambar itu.

## 9. Status temuan
- 04 (TCO 12 bulan): Belum lulus; komponen domain dan backup belum ada.
- 07 (kredit, burn-rate, budget alert): Lulus (08-11-2026); catatan: screenshot detail peringatan anggaran belum dilampirkan karena memuat email dan ID akun.
