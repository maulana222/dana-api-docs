# Konfigurasi & lingkungan

## `import 'dotenv/config'`

File `src/index.ts` mengimpor **`dotenv/config`**. Jika aplikasi Anda memuat `dana-node`, variabel dari file **`.env`** di direktori kerja proses ikut terbaca (kecuali Anda override perilaku dotenv).

## Kelas `Dana` dan `DanaOpts`

Konstruktor (`src/index.ts`) mengisi opsi dengan prioritas: **argumen konstruktor** lalu **variabel lingkungan**.

| Opsi | Lingkungan (`process.env`) | Wajib |
|------|------------------------------|--------|
| `partnerId` | `X_PARTNER_ID` | Ya — jika kosong, error |
| `privateKey` | `PRIVATE_KEY` | Ya — jika kosong, error |
| `origin` | `ORIGIN` | Tidak (boleh string kosong) |
| `env` | `DANA_ENV` atau `ENV`, default **`sandbox`** | Ya setelah fallback |
| `clientSecret` | `CLIENT_SECRET` | Opsional string; **wajib untuk beberapa API** (lihat bawah) |
| `debugMode` | `X_DEBUG` (non-kosong), atau default **`true`** jika `env === 'sandbox'` | — |

**Penting:** Di konstruktor `Dana` **tidak** ada pembacaan `PRIVATE_KEY_PATH`. Private key harus berupa **string** (atau Anda baca file PEM sendiri lalu pass ke `privateKey`).

## Nilai `env` dan base URL

Fungsi `getBasePathByEnv` di `src/runtime.ts` **hanya** menerima string persis:

| `env` | Host API |
|-------|-----------|
| `sandbox` | `https://api.sandbox.dana.id` |
| `production` | `https://api.saas.dana.id` |

Nilai lain → **Error** (`Invalid env value provided`). Gunakan **huruf kecil** `sandbox` / `production` di `.env` agar cocok dengan `switch` di kode.

**Default perilaku:** jika `DANA_ENV` dan `ENV` tidak di-set, kode memakai **`sandbox`** — jadi default request mengarah ke **sandbox**, bukan production.

## `CLIENT_SECRET` — kapan dipakai di kode?

| Modul | Peran `clientSecret` di signature/header |
|-------|------------------------------------------|
| `PaymentGatewayApi` | Tidak dipakai (Snap B2B: `privateKey`, `origin`, `partnerId`) |
| `DisbursementApi` | Tidak dipakai (Snap B2B) |
| `WidgetApi` | Dipakai pada **`queryUserProfile`** (`populateOpenApiScenarioHeader`) |
| `MerchantManagementApi` | Dipakai pada **semua** method |

README npm yang menyebut `CLIENT_SECRET` wajib untuk Disbursement **tidak selaras** dengan implementasi header di `src/disbursement` saat ini; ikuti tabel di atas.

## Mode debug

Jika `debugMode` (string) **`'true'`** (case insensitive) **dan** `env` sandbox, header **`X-Debug-Mode: true`** dikirim pada permintaan Snap B2B yang relevan. Respons sandbox dapat menyertakan detail tambahan (mis. `additionalInfo.debugMessage`) sesuai kebijakan API DANA.

## Contoh `.env`

```env
X_PARTNER_ID=...
PRIVATE_KEY=-----BEGIN PRIVATE KEY-----...-----END PRIVATE KEY-----
ORIGIN=https://merchant-anda.com
DANA_ENV=sandbox
CLIENT_SECRET=...   # jika pakai Merchant Management atau queryUserProfile
# X_DEBUG=true      # opsional; di sandbox debug sering sudah aktif secara default
```

## Subpath `package.json`

Impor modul tanpa melalui kelas `Dana`:

```javascript
import { WebhookParser } from "dana-node/webhook/v1";
import * as runtime from "dana-node/runtime";
```

Daftar lengkap ada di `package.json` → `exports`.
