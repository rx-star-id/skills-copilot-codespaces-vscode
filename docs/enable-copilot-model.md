# Panduan Mengaktifkan Model AI di GitHub Copilot (VS Code)

Panduan ini menjelaskan cara mengaktifkan model AI (termasuk model GPT terbaru) pada GitHub Copilot di VS Code, baik dari sisi **admin organisasi** maupun **pengguna akhir**.

---

## Daftar Isi

1. [Prasyarat](#prasyarat)
2. [Langkah Admin: Mengaktifkan Model di GitHub Organization/Enterprise](#langkah-admin-mengaktifkan-model-di-github-organizationenterprise)
3. [Langkah Pengguna: Memilih Model di VS Code](#langkah-pengguna-memilih-model-di-vs-code)
4. [Konfigurasi VS Code Settings](#konfigurasi-vs-code-settings)
5. [Troubleshooting](#troubleshooting)

---

## Prasyarat

Sebelum mengaktifkan model, pastikan kondisi berikut terpenuhi:

- Anda memiliki lisensi **GitHub Copilot Business** atau **GitHub Copilot Enterprise** yang aktif.
- Akun Anda merupakan anggota organisasi GitHub yang memiliki Copilot diaktifkan.
- Extension **GitHub Copilot** dan **GitHub Copilot Chat** sudah terinstal di VS Code.
- Anda sudah login ke GitHub di VS Code.

> **Catatan:** Model tertentu (seperti versi GPT terbaru) hanya tersedia pada paket **Copilot Business** atau **Enterprise**, dan harus diaktifkan terlebih dahulu oleh admin organisasi.

---

## Langkah Admin: Mengaktifkan Model di GitHub Organization/Enterprise

Admin organisasi perlu mengaktifkan akses model AI di pengaturan kebijakan Copilot sebelum pengguna dapat memilihnya.

### 1. Masuk ke GitHub Organization Settings

1. Buka [github.com](https://github.com) dan login sebagai **Owner** atau **Admin** organisasi.
2. Klik foto profil → **Your organizations**.
3. Pilih organisasi yang ingin dikonfigurasi.
4. Klik tab **Settings** (ikon roda gigi).

### 2. Navigasi ke Copilot Policies

1. Di sidebar kiri, klik **Copilot** → **Policies**.
2. Atau akses langsung: `https://github.com/organizations/<NAMA_ORG>/settings/copilot/policies`

### 3. Aktifkan Model AI Pilihan

1. Scroll ke bagian **"Models"** atau **"Copilot in IDEs"**.
2. Temukan daftar model yang tersedia (contoh: `Claude 3.5 Sonnet`, `o1`, `GPT-4o`, dll.).
3. Klik toggle atau pilih **"Enabled"** untuk model yang ingin diaktifkan.
4. Klik **Save** untuk menyimpan perubahan.

> **Catatan:** Ketersediaan model bergantung pada paket dan kebijakan GitHub. Tidak semua model tersedia untuk semua tier. Jika model tidak muncul di daftar, kemungkinan belum didukung untuk paket Anda atau belum tersedia di region Anda.

### 4. (Enterprise) Izinkan Anggota Memilih Model

Untuk **GitHub Copilot Enterprise**, admin juga bisa mengatur apakah anggota boleh mengubah pilihan model secara mandiri:

1. Masih di halaman **Copilot → Policies**.
2. Temukan pengaturan **"Model selection by members"**.
3. Pilih **"Allowed"** agar anggota bisa memilih model sendiri di IDE.
4. Simpan perubahan.

---

## Langkah Pengguna: Memilih Model di VS Code

Setelah admin mengaktifkan model, pengguna dapat memilihnya di VS Code.

### Menggunakan Copilot Chat

1. Buka **Copilot Chat** di VS Code (ikon chat di sidebar atau tekan `Ctrl+Shift+I` / `Cmd+Shift+I`).
2. Di bagian atas panel Copilot Chat, klik **pemilih model** (dropdown yang menampilkan nama model aktif, biasanya di sudut kanan atas atau bawah input chat).
3. Dari daftar model yang tersedia, pilih model yang diinginkan.
4. Mulai percakapan — model yang dipilih akan langsung digunakan.

### Menggunakan Copilot Inline (Editor)

Untuk completions di editor, model dipilih melalui pengaturan (lihat bagian [Konfigurasi VS Code Settings](#konfigurasi-vs-code-settings)).

---

## Konfigurasi VS Code Settings

Anda dapat mengatur preferensi model Copilot melalui `settings.json` VS Code.

### Membuka Settings JSON

- Tekan `Ctrl+Shift+P` (Windows/Linux) atau `Cmd+Shift+P` (macOS).
- Ketik **"Open User Settings (JSON)"** dan tekan Enter.

### Contoh Konfigurasi

```json
{
  // Aktifkan Copilot
  "github.copilot.enable": {
    "*": true
  },

  // Pilih model untuk Copilot Chat (sesuaikan dengan nama model yang tersedia)
  "github.copilot.chat.defaultModel": "gpt-4o",

  // Aktifkan fitur Copilot terbaru (Next Edit Suggestions, dsb.)
  "github.copilot.nextEditSuggestions.enabled": true,

  // Aktifkan pengambilan data melalui proses utama Electron untuk meningkatkan
  // kompatibilitas jaringan (misal di lingkungan dengan proxy perusahaan).
  // Aktifkan hanya jika mengalami masalah koneksi Copilot Chat di VS Code.
  "github.copilot.chat.experimental.useElectronFetcher": true
}
```

> **Catatan:** Nilai `"github.copilot.chat.defaultModel"` harus diisi dengan nama model yang valid dan tersedia untuk akun/organisasi Anda. Nama model yang tersedia dapat dilihat di dropdown Copilot Chat.

---

## Troubleshooting

### ❌ Model tidak muncul di dropdown Copilot Chat

**Penyebab:** Model belum diaktifkan oleh admin organisasi, atau belum tersedia untuk paket Anda.

**Solusi:**
1. Minta admin organisasi untuk mengaktifkan model di **GitHub Organization Settings → Copilot → Policies**.
2. Pastikan Anda menggunakan versi terbaru extension **GitHub Copilot Chat** di VS Code.
3. Coba restart VS Code setelah admin melakukan perubahan.
4. Logout dan login ulang ke GitHub di VS Code:
   - Tekan `Ctrl+Shift+P` → ketik **"Sign Out of GitHub"** → login ulang.

---

### ❌ Pesan error: "This model is not available" atau "Access denied"

**Penyebab:** Akun Anda tidak memiliki izin untuk menggunakan model tersebut.

**Solusi:**
1. Hubungi admin organisasi untuk memastikan model sudah diaktifkan di policy.
2. Verifikasi bahwa akun Anda sudah ditambahkan ke seat Copilot yang aktif.
3. Cek status lisensi di: `https://github.com/settings/copilot`

---

### ❌ Model disable / diminta diaktifkan oleh admin

**Penyebab:** Admin organisasi belum mengaktifkan model tersebut untuk digunakan oleh anggota.

**Solusi untuk Admin:**
1. Ikuti langkah di bagian [Langkah Admin](#langkah-admin-mengaktifkan-model-di-github-organizationenterprise).
2. Pastikan toggle model sudah dalam posisi **"Enabled"**.
3. Simpan perubahan dan minta pengguna melakukan restart VS Code.

**Solusi untuk Pengguna:**
1. Hubungi admin organisasi GitHub Anda dengan informasi:
   - Nama model yang ingin diaktifkan.
   - Screenshot pesan "disabled" yang Anda lihat.
2. Gunakan model lain yang sudah tersedia sementara menunggu admin mengaktifkan model yang diinginkan.

---

### ❌ Extension Copilot tidak mendeteksi model baru setelah admin mengaktifkan

**Solusi:**
1. Tekan `Ctrl+Shift+P` → **"GitHub Copilot: Refresh Session"**.
2. Atau restart VS Code sepenuhnya.
3. Pastikan extension Copilot & Copilot Chat sudah versi terbaru:
   - Buka **Extensions** panel → cari **GitHub Copilot** → klik **Update** jika tersedia.

---

### ❌ Copilot tidak aktif sama sekali di VS Code

**Solusi:**
1. Verifikasi login: Klik ikon akun di sudut kiri bawah VS Code → pastikan akun GitHub Anda terlihat.
2. Cek status Copilot di VS Code: Status bar bagian bawah harus menampilkan ikon Copilot aktif.
3. Verifikasi lisensi aktif di `https://github.com/settings/copilot`.
4. Reinstall extension jika perlu.

---

## Referensi

- [Dokumentasi GitHub Copilot](https://docs.github.com/en/copilot)
- [Mengelola Kebijakan Copilot untuk Organisasi](https://docs.github.com/en/copilot/managing-copilot/managing-github-copilot-in-your-organization)
- [Menggunakan Copilot Chat di VS Code](https://docs.github.com/en/copilot/using-github-copilot/using-github-copilot-chat-in-your-ide)
- [Pemilihan Model di GitHub Copilot](https://docs.github.com/en/copilot/using-github-copilot/ai-model-selection-in-copilot)
