# Memulai

## Persyaratan

- **Node.js 18.0 atau lebih baru** (`package.json` → `engines`).

## Instalasi paket

```bash
npm install dana-node@latest --save
```

Dukungan **TypeScript** sudah termasuk (berkas `.d.ts` di paket).

## Uji integrasi sebelum koding

Tim DANA menyediakan skrip otomatis untuk sandbox:

**[github.com/dana-id/uat-script](https://github.com/dana-id/uat-script)**

Menjalankan skrip ini memvalidasi kredensial dan alur — disarankan **sebelum** integrasi penuh.

## Impor minimal

```javascript
import { Dana } from "dana-node";

const client = new Dana();
// atau dengan opsi eksplisit — lihat bab Konfigurasi
```

## Dokumentasi resmi API

Spesifikasi endpoint, parameter bisnis, dan kode respons dari sisi produk DANA:

- [DANA API Reference](https://dashboard.dana.id/api-docs-v2/)
- Panduan kunci privat: [API Docs / kunci](https://dashboard.dana.id/api-docs/read/45)

Bab-bab berikutnya menjelaskan **cara SDK ini** membangun request (header, URL, lingkungan) sesuai `src/`.
