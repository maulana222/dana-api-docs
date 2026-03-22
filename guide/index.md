# Beranda — dokumentasi `dana-node`

Selamat datang di panduan **SDK Node.js resmi DANA** (`dana-node`). Dokumen ini disusun dalam **Bahasa Indonesia** dan diselaraskan dengan kode di repositori (`src/`), bukan menggantikan [referensi API resmi DANA](https://dashboard.dana.id/api-docs-v2/).

## Apa itu `dana-node`

Pustaka untuk memanggil REST API DANA dari **Node.js 18+** dengan TypeScript. Entry utama adalah kelas **`Dana`**, yang menyediakan empat klien:

| Klien | Properti di `Dana` | Fungsi ringkas |
|-------|---------------------|----------------|
| Payment Gateway | `paymentGatewayApi` | Debit / order / konsultasi bayar / query / refund (skema Snap B2B) |
| Widget | `widgetApi` | Widget, token, OTT, saldo, pembayaran, profil pengguna, dll. |
| Disbursement | `disbursementApi` | Transfer & inquiry disbursement |
| Merchant Management | `merchantManagementApi` | Shop, division, resource (skema Open API + `clientSecret`) |

Modul **webhook** diimpor terpisah: `dana-node/webhook/v1` (bukan dari entry `dana-node` utama).

## Isi panduan

Gunakan menu kiri untuk membuka bab berikut:

1. **Memulai** — instalasi, skrip UAT DANA  
2. **Konfigurasi & lingkungan** — `DanaOpts`, `.env`, base URL, `CLIENT_SECRET`  
3. **Payment Gateway / Widget / Disbursement / Merchant Management** — method yang ada di kode  
4. **Webhook** — `WebhookParser`  
5. **Referensi API** — tautan ke Markdown otomatis di folder `docs/`

## Build dokumentasi ini (MkDocs)

Dari folder **`docs/`** di repositori `dana-node` (folder yang berisi `mkdocs.yml` dan `guide/`):

```bash
cd docs
pip install -r requirements-docs.txt
mkdocs serve
```

Buka `http://127.0.0.1:8000`. Untuk HTML statis: `mkdocs build` → folder **`docs/site/`** (diabaikan Git).

## Repositori

Kode sumber: [github.com/dana-id/dana-node](https://github.com/dana-id/dana-node)
