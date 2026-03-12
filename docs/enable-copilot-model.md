# Panduan Mengaktifkan Model AI di GitHub Copilot untuk VS Code

Panduan ini menjelaskan cara admin mengaktifkan atau mengelola model AI (termasuk model GPT terbaru) di GitHub Copilot untuk pengguna VS Code.

---

## Prasyarat

- Akun GitHub dengan lisensi **Copilot Business** atau **Copilot Enterprise**
- Peran **Owner** atau **Billing Manager** pada organisasi GitHub
- VS Code dengan ekstensi **GitHub Copilot** versi terbaru
- Koneksi internet aktif

---

## Bagian 1: Mengaktifkan Model melalui GitHub Copilot Admin Console

### Langkah-langkah

1. **Masuk ke GitHub** di [https://github.com](https://github.com) menggunakan akun admin/owner organisasi.

2. **Buka pengaturan organisasi**:
   - Klik foto profil Anda (kanan atas) → **Your organizations**
   - Pilih nama organisasi Anda

3. **Navigasi ke Copilot Settings**:
   - Pada sidebar kiri, klik **Settings**
   - Di bawah bagian **"Code, planning, and automation"**, klik **Copilot**

4. **Aktifkan akses model**:
   - Pilih tab **Policies** (atau **Access**)
   - Temukan bagian **"Allow GitHub Copilot to use additional AI models"** atau
     **"Model selection"** / **"Enable preview models"**
   - Aktifkan toggle/opsi yang tersedia untuk mengizinkan pengguna memilih model

5. **Simpan perubahan**:
   - Klik **Save** untuk menyimpan konfigurasi

> **Catatan:** Tampilan antarmuka admin console dapat berubah mengikuti pembaruan GitHub. Selalu lihat [dokumentasi resmi GitHub Copilot](https://docs.github.com/en/copilot) untuk panduan terkini.

---

## Bagian 2: Memilih Model di VS Code (Sisi Pengguna)

Setelah admin mengaktifkan akses model, pengguna dapat memilih model yang diinginkan langsung dari VS Code:

1. **Buka VS Code** dan pastikan ekstensi **GitHub Copilot Chat** sudah terinstal dan aktif.

2. **Buka Copilot Chat**:
   - Klik ikon Copilot Chat di sidebar, atau tekan `Ctrl+Alt+I` (Windows/Linux) / `Cmd+Option+I` (macOS)

3. **Pilih model**:
   - Di bagian atas panel chat, klik **dropdown pemilih model** (tertulis nama model aktif, misal "GPT-4o")
   - Pilih model yang Anda inginkan dari daftar yang tersedia

   ```
   ┌─────────────────────────────────┐
   │  GitHub Copilot Chat            │
   │                                 │
   │  Model: [ GPT-4o           ▼ ]  │  <-- Klik di sini
   │  ─────────────────────────────  │
   │  ✓ GPT-4o                       │
   │    GPT-4.1                      │
   │    Claude 3.5 Sonnet            │
   │    Gemini 1.5 Pro               │
   └─────────────────────────────────┘
   ```

4. **Mulai menggunakan model** yang sudah dipilih.

---

## Bagian 3: Troubleshooting — Model Tidak Muncul atau Tidak Bisa Dipilih

### 3.1 Verifikasi Paket/Lisensi Copilot

| Paket | Pilihan Model |
|-------|---------------|
| Copilot Free / Individual | Terbatas (biasanya hanya model default) |
| Copilot Business | Dapat mengakses lebih banyak model jika diaktifkan admin |
| Copilot Enterprise | Akses penuh ke semua model yang tersedia |

**Langkah:** Periksa lisensi aktif Anda di:
- [https://github.com/settings/copilot](https://github.com/settings/copilot) (untuk akun personal)
- Settings organisasi → Copilot → Billing

### 3.2 Verifikasi Izin Admin

Pastikan admin organisasi telah:
- ✅ Mengaktifkan **"Allow use of models other than the default"** di pengaturan Copilot organisasi
- ✅ Mengaktifkan **"Enable preview features"** jika model yang diinginkan bersifat preview
- ✅ Memberikan lisensi Copilot kepada pengguna yang bersangkutan

### 3.3 Verifikasi Region/Ketersediaan

Beberapa model AI mungkin belum tersedia di semua wilayah geografis. Jika model tidak muncul:
- Periksa [GitHub Copilot changelog](https://github.blog/changelog/label/copilot/) untuk status ketersediaan regional
- Hubungi [GitHub Support](https://support.github.com) untuk konfirmasi ketersediaan di region Anda

### 3.4 Perbarui Ekstensi VS Code

Model baru memerlukan versi ekstensi Copilot yang terbaru:

1. Buka VS Code
2. Pergi ke **Extensions** (`Ctrl+Shift+X` / `Cmd+Shift+X`)
3. Cari **"GitHub Copilot"** dan **"GitHub Copilot Chat"**
4. Klik **Update** jika tersedia, lalu **Reload Window**

### 3.5 Periksa Status Layanan GitHub

Jika masalah tiba-tiba muncul, periksa status layanan di:
[https://www.githubstatus.com](https://www.githubstatus.com)

### 3.6 Login Ulang ke GitHub di VS Code

1. Buka Command Palette (`Ctrl+Shift+P` / `Cmd+Shift+P`)
2. Ketik: `GitHub Copilot: Sign Out`
3. Konfirmasi sign out, lalu ketik: `GitHub Copilot: Sign In`
4. Ikuti proses autentikasi ulang

---

## Bagian 4: Menghubungi Admin (untuk Pengguna Akhir)

Jika Anda adalah **pengguna** (bukan admin) dan model tidak dapat diakses, kirimkan informasi berikut ke admin organisasi Anda:

```
Permintaan Aktifkan Model Copilot

Nama: [Nama Anda]
Username GitHub: [Username Anda]
Organisasi: [Nama Organisasi]
Model yang diminta: [Nama Model, misal: model terbaru yang tersedia]
Alasan: [Keperluan penggunaan]
```

Admin perlu:
1. Memastikan akun Anda memiliki lisensi Copilot aktif
2. Mengaktifkan model di pengaturan kebijakan Copilot organisasi
3. Mengonfirmasi bahwa model tersebut tersedia untuk paket organisasi Anda

---

## Referensi

- [GitHub Copilot Documentation](https://docs.github.com/en/copilot)
- [Managing Copilot policies for your organization](https://docs.github.com/en/copilot/managing-copilot/managing-github-copilot-in-your-organization/managing-policies-for-copilot-in-your-organization)
- [GitHub Copilot in VS Code](https://code.visualstudio.com/docs/copilot/overview)
- [GitHub Copilot Changelog](https://github.blog/changelog/label/copilot/)
