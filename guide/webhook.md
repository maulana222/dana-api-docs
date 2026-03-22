# Webhook

Parser notifikasi dari DANA: kelas **`WebhookParser`** di `src/webhook/v1/webhook.ts`.

## Impor

Webhook **tidak** diekspor dari paket utama `dana-node` (`index.ts`). Gunakan subpath:

```javascript
import { WebhookParser } from "dana-node/webhook/v1";
```

## Kunci publik

- Jika `DANA_ENV` / `ENV` **`sandbox`** atau **kosong**, konstruktor dapat memakai **kunci publik sandbox bawaan** yang tertanam di kode (`SANDBOX_WEBHOOK_PUBLIC_KEY`).
- **Produksi:** sediakan kunci publik DANA lewat argumen konstruktor atau **`DANA_PUBLIC_KEY`** / **`DANA_PUBLIC_KEY_PATH`** (baca `webhook.ts` untuk prioritas).

## Tujuan

Memverifikasi tanda tangan notifikasi dan mem-parse payload ke tipe **`FinishNotifyRequest`** (dan turunannya) sesuai model di `dana-node/webhook/v1`.

## Dokumentasi tambahan

Contoh dan penjelasan bahasa Inggris ada di `docs/webhook/v1/` (jika tersedia di salinan repo) dan di komentar sumber `webhook.ts`.
