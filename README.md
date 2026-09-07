# ☕ Warkop Myhink V3 - Smart POS & Autonomous Multi-AI Platform

[![Vite](https://img.shields.io/badge/Vite-5.4-646CFF?logo=vite&logoColor=white)](https://vitejs.dev/)
[![React](https://img.shields.io/badge/React-18.3-61DAFB?logo=react&logoColor=black)](https://reactjs.org/)
[![Node.js](https://img.shields.io/badge/Node.js-18+-339933?logo=nodedotjs&logoColor=white)](https://nodejs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.6-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Prisma](https://img.shields.io/badge/Prisma-5.20-2D3748?logo=prisma&logoColor=white)](https://www.prisma.io/)
[![PostgreSQL](https://img.shields.io/badge/PostgreSQL-15+-4169E1?logo=postgresql&logoColor=white)](https://www.postgresql.org/)
[![PWA](https://img.shields.io/badge/PWA-Ready-FF6F00?logo=pwa&logoColor=white)](https://web.dev/progressive-web-apps/)

Platform Point of Sale (POS), Manajemen Operasional Multi-Cabang, dan Analisis Bisnis Cerdas untuk Warung Kopi Modern. Dilengkapi mesin **Multi-AI Engine (Gemini, OpenRouter, DeepSeek, Claude, Ollama)**, sistem **PWA Offline-First**, pemesanan mandiri via QR meja, serta **Workspace Customizer** berstandar WordPress.

---

## 📑 Daftar Isi

- [✨ Fitur Unggulan](#-fitur-unggulan)
- [🏗️ Arsitektur & Struktur Proyek](#️-arsitektur--struktur-proyek)
- [🚀 Panduan Memulai (Quick Start)](#-panduan-memulai-quick-start)
- [⚙️ Konfigurasi Environment (`.env`)](#️-konfigurasi-environment-env)
- [🤖 Multi-Provider AI Engine](#-multi-provider-ai-engine)
- [🌐 PWA & Manajemen Sistem / Cache](#-pwa--manajemen-sistem--cache)
- [🏬 Manajemen Multi-Cabang (Multi-Branch)](#-manajemen-multi-cabang-multi-branch)
- [🔐 Hak Akses & Akun Demo](#-hak-akses--akun-demo)
- [📡 Dokumentasi API Utama](#-dokumentasi-api-utama)
- [📄 Lisensi & Kontributor](#-lisensi--kontributor)

---

## ✨ Fitur Unggulan

### 1. 🤖 Multi-Provider AI Intelligence
- **Universal AI Engine:** Terintegrasi langsung dengan **Google Gemini** (Flash & Pro), **OpenRouter Live Catalog**, **DeepSeek**, **Claude/Anthropic**, **OpenAI**, **Groq**, dan **Ollama (Local LLM)**.
- **Barista AI Interaktif:** Rekomendasi racikan menu personal untuk pelanggan berdasarkan preferensi rasa, budget, atau suasana nongkrong.
- **Autonomous Business Insights:** Evaluasi penjualan harian/mingguan otomatis, proyeksi revenue, deteksi menu *deadstock*, dan rekomendasi strategi promo.

### 2. ⚡ Modern POS & Kitchen Display System (KDS)
- **POS Kasir Cepat:** Antarmuka layar sentuh responsif dengan filter kategori instan, pencarian real-time, opsi diskon voucher, dan kalkulator kembalian otomatis.
- **Kitchen / Barista Display (KDS):** Sinkronisasi pesanan dapur via **WebSocket (Socket.io)** seketika begitu kasir atau pelanggan membuat pesanan.
- **Pemesanan Mandiri Meja:** Pelanggan cukup scan QR di meja, memilih menu, dan membayar via QRIS tanpa perlu antre di kasir.

### 3. 🎨 Workspace Customizer (WordPress-Level Control)
- **Theme & Appearance Engine:** Pengaturan warna aksen dinamis (`--accent-rgb`), tone latar belakang (Ink, Graphite, Deep Ocean), font kustom (Outfit, Inter, Space Grotesk), dan radius kartu.
- **Identitas Toko:** Nama warkop, tagline, upload logo, banner, rekening bank, hingga gambar QRIS toko dinamis.
- **Struk & PDF:** Kustomisasi header/footer struk, ukuran kertas (58mm / 80mm), label pajak, dan printer thermal Bluetooth/USB.

### 4. 📶 PWA & Offline Resiliency
- **Progressive Web App (PWA):** Dapat diinstal di Android, iOS, Windows, dan macOS sebagai aplikasi desktop/mobile mandiri.
- **Offline Mutation Queue:** Transaksi kasir tetap tersimpan di IndexedDB saat koneksi internet terputus dan disinkronkan otomatis saat kembali online.
- **Owner System Power Tools:** Fitur pembersihan cache lokal dan **Broadcast Force Reload** via WebSocket untuk memperbarui seluruh layar kasir & tablet pelanggan secara serentak ke versi aplikasi terbaru.

### 5. 🔐 Redesigned Auth Experience
- Halaman **Login & Register** bertema *dark aesthetic glassmorphism* dengan pencahayaan ambient warm amber.
- Dilengkapi *Password Strength Meter*, validasi konfirmasi kata sandi live, toggle show/hide password, dan tombol pengisian cepat akun demo.

---

## 🏗️ Arsitektur & Struktur Proyek

```text
Warkop-Myhink/
├── web-v3/                      # Frontend App (Vite + React + TS)
│   ├── public/                  # PWA Manifest, Service Worker (sw.js), Ikon & Font
│   ├── src/
│   │   ├── components/          # Reusable UI, Modal, Toast, & Layout Widgets
│   │   ├── features/offline/    # Offline Queue & IndexedDB Sync Engine
│   │   ├── pages/               # Halaman: POS, Orders, Menu, Settings, Auth, Analytics
│   │   ├── stores/              # Zustand Stores (authStore, themeStore, cartStore)
│   │   ├── App.tsx              # Root Layout, Global Socket & Theme Listeners
│   │   └── main.tsx             # React Entrypoint & PWA Auto-Registration
│   └── vite.config.ts           # Proxy API, Compression (Gzip/Brotli), & PWA config
│
├── server-v3/                   # Backend REST & WebSocket Server (Express + Prisma)
│   ├── prisma/                  # Schema Data PostgreSQL & Migrations
│   ├── scripts/                 # Migration & Seed Helper Scripts
│   ├── src/
│   │   ├── middleware/          # JWT Authentication, RBAC, & Security Middleware
│   │   ├── routes/              # Modular API Endpoints (Auth, POS, Settings, AI, Branches)
│   │   ├── socket.ts            # WebSocket Real-Time Event Hub (Socket.io)
│   │   └── index.ts             # Server Entrypoint, Security Headers, & Rate Limiters
│   └── package.json
│
└── _archive/v1/                 # Arsip referensi kode legacy V1
```

---

## 🚀 Panduan Memulai (Quick Start)

### Prasyarat Sistem
- **Node.js**: Versi `18.0.0` atau lebih baru
- **NPM**: Versi `9.0.0` atau lebih baru
- **Database**: PostgreSQL `14+` (Bisa menggunakan PostgreSQL lokal atau layanan cloud seperti Supabase/Neon)

### 1. Kloning Repositori
```bash
git clone https://github.com/andra280502/Warkop-Myhink.git
cd Warkop-Myhink
```

### 2. Instalasi Dependensi
```bash
# Instal dependensi backend
cd server-v3
npm install

# Instal dependensi frontend
cd ../web-v3
npm install
```

### 3. Konfigurasi Database & Migrasi Prisma
Buat file `server-v3/.env` (ikuti panduan di bawah), kemudian jalankan:
```bash
cd server-v3
npx prisma db push
npx prisma generate
```

### 4. Menjalankan Server Development
Jalankan backend dan frontend pada terminal terpisah:

**Terminal 1 (Backend - Port 3001):**
```bash
cd server-v3
npm run dev
```

**Terminal 2 (Frontend - Port 5173):**
```bash
cd web-v3
npm run dev
```

Buka peramban Anda di: **`http://localhost:5173`**

---

## ⚙️ Konfigurasi Environment (`.env`)

Buat file `.env` di dalam direktori `server-v3/`:

```env
# Port Server
PORT=3001
NODE_ENV=development

# Database Connection (PostgreSQL)
DATABASE_URL="postgresql://postgres:password@localhost:5432/warkop_myhink?schema=public"

# Keamanan JWT
JWT_SECRET="ganti_dengan_random_secret_string_yang_sangat_panjang_dan_aman"

# Default AI Key (Opsional, dapat dikonfigurasi melalui Workspace Settings di UI)
GEMINI_API_KEY="AIzaSy..."
OPENROUTER_API_KEY="sk-or-v1-..."
```

---

## 🤖 Multi-Provider AI Engine

Warkop Myhink V3 mendukung integrasi multi-model AI fleksibel yang dapat diatur langsung oleh Owner di menu **Workspace Settings → Integrasi AI**:

| Provider | Model yang Didukung | Keunggulan Utama |
| :--- | :--- | :--- |
| **Google Gemini** | `gemini-2.5-flash`, `gemini-2.0-flash`, `gemini-1.5-pro` | Sangat cepat, biaya efisien, multimodal |
| **OpenRouter** | Akses ke 300+ Model (Claude 3.5, GPT-4o, Llama 3.3, Mistral) | Katalog model live & perbandingan harga |
| **DeepSeek** | `deepseek-chat`, `deepseek-reasoner` | Reasoning tajam untuk analisis finansial |
| **Groq** | `llama-3.3-70b-versatile`, `mixtral-8x7b-32768` | Inferensi ultra-cepat (< 300ms) |
| **Ollama** | Model Lokal (`llama3`, `mistral`, `qwen2.5`) | 100% Gratis, offline, data privat |

---

## 🌐 PWA & Manajemen Sistem / Cache

Aplikasi dilengkapi modul diagnostik & pemeliharaan sistem di **Settings → Sistem & Cache**:
- **Service Worker Caching:** Menggunakan strategi *Stale-While-Revalidate* untuk bundle statis, font, dan gambar, serta *Network-First* untuk navigasi halaman.
- **Bersihkan Cache Perangkat Ini:** Menghapus data cache browser usang dan memperbarui Service Worker lokal tanpa mengeluarkan sesi login.
- **Broadcast Force Update (Sinyal Seluruh Warkop):** Owner dapat menyiarkan sinyal WebSocket `system:reload` ke seluruh perangkat kasir, tablet barista, dan smartphone pelanggan untuk auto-refresh serentak ke versi aset terbaru.

---

## 🏬 Manajemen Multi-Cabang (Multi-Branch)

Sistem mendukung operasi multi-outlet warkop:
- **Routing Cabang:** Pelanggan dapat membuka menu spesifik cabang via URL seperti `/menu/MLG-01` (Malang) atau `/menu/SBY-01` (Surabaya).
- **Integrasi Google Maps:** Menampilkan titik koordinat live, rute arah navigasi, dan jam buka cabang.
- **Stok & Laporan Terisolasi:** Setiap cabang dapat memiliki manajemen stok bahan baku dan rekap kasir masing-masing.

---

## 🔐 Hak Akses & Akun Demo

Sistem menerapkan kontrol akses berbasis peran (*Role-Based Access Control*):

| Peran (Role) | Akses Fitur Utama |
| :--- | :--- |
| **👑 OWNER** | Kendali penuh sistem, customizer warkop, multi-AI, manajemen staf, laporan finansial, broadcast reload |
| **👔 MANAGER** | Manajemen menu, inventaris stok, laporan penjualan cabang, data voucher |
| **💼 CASHIER** | POS kasir, input pesanan, cetak struk pembayaran, status meja |
| **☕ CHEF / BARISTA**| Kitchen Display System (KDS), ubah status antrean pesanan (*Memasak / Siap Disajikan*) |
| **📱 CUSTOMER** | Pemesanan mandiri meja, tracking pesanan live, loyalty points, klaim voucher |

> 💡 **Tips Pengujian Cepat:** Pada halaman `/login`, klik menu akordeon **`⚡ Akun Akses Cepat`** untuk langsung mengisi akun Owner, Kasir, atau Barista dengan sekali klik.

---

## 📡 Dokumentasi API Utama

Base URL: **`http://localhost:3001/api`**

### Autentikasi & Pengguna
- `POST /auth/login` — Autentikasi akun & penerbitan JWT
- `POST /auth/register` — Pendaftaran akun pelanggan
- `GET /auth/profile` — Profil pengguna terautentikasi

### Point of Sale & Pesanan
- `GET /menus` — Mendapatkan daftar katalog menu aktif
- `POST /orders` — Membuat pesanan baru (Kasir / Meja)
- `GET /orders/active` — Mengambil antrean pesanan dapur aktif (KDS)
- `PATCH /orders/:id/status` — Memperbarui status pesanan dapur

### AI & Analisis Bisnis
- `POST /ai-insights/analyze` — Menghasilkan evaluasi bisnis berbasis AI
- `POST /ai-insights/test-connection` — Uji koneksi API key provider AI
- `POST /ai/barista-chat` — Konsultasi menu cerdas dengan Barista AI

### Pengaturan & Sistem
- `GET /settings` — Mengambil seluruh preferensi toko & tema warkop
- `PUT /settings` — Memperbarui konfigurasi toko (Khusus Owner)
- `POST /settings/broadcast-reload` — Menyiarkan sinyal force update ke seluruh perangkat aktif

---

## 🛠️ Perintah Build & Produksi

```bash
# Build bundle produksi frontend (termasuk kompresi Gzip & Brotli)
cd web-v3
npm run build

# Menjalankan preview hasil build lokal
npm run preview

# Build backend TypeScript
cd server-v3
npm run build
npm start
```

---

## 📄 Lisensi & Kontributor

Dikembangkan dan dirawat dengan penuh dedikasi oleh:

**Syailendra Andra P.** ([@andra280502](https://github.com/andra280502))  
- 📧 Kontak: [andrasyailendra280502@gmail.com](mailto:andrasyailendra280502@gmail.com)  
- ☕ Proyek: **Warkop Myhink V3 - Enterprise Smart Warkop Platform**

Hak Cipta &copy; 2026 Warkop Myhink. Seluruh hak cipta dilindungi undang-undang.