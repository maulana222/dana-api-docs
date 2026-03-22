# Folder `docs/` — dokumentasi `dana-node`

Folder ini berisi **dua jenis** dokumentasi:

## 1. Panduan MkDocs (Bahasa Indonesia)

| Item | Keterangan |
|------|------------|
| **`guide/`** | Sumber Markdown untuk situs panduan (beranda, konfigurasi, Payment Gateway, Widget, dll.) — **selaras `src/`**. |
| **`mkdocs.yml`** | Konfigurasi MkDocs (tema Material, navigasi). |
| **`requirements-docs.txt`** | Dependensi Python untuk build (`mkdocs`, `mkdocs-material`, …). |
| **`site/`** | Hasil `mkdocs build` (folder ini diabaikan Git; dibuat lokal). |

### Menjalankan panduan di lokal

Dari **folder ini** (`docs/`):

```bash
pip install -r requirements-docs.txt
mkdocs serve
```

Buka `http://127.0.0.1:8000`.  
Build statis: `mkdocs build` → output di **`site/`**.

Dari root repo `dana-node` tanpa `cd`:

```bash
mkdocs build --config-file docs/mkdocs.yml
```

## 2. Referensi API (Markdown otomatis)

Subfolder berikut berisi dokumentasi **bahasa Inggris** yang biasanya dihasilkan dari spesifikasi API (parameter, model, contoh):

- `payment_gateway/`
- `widget/`
- `disbursement/`
- `merchant_management/`
- `webhook/` (jika ada)

Buka file `.md` langsung di GitHub atau lewat IDE. Panduan Indonesia di **`guide/referensi-api.md`** menaut ke beberapa file penting di GitHub.

---

**README utama proyek SDK** ada satu tingkat di atas: [`../README.md`](../README.md).
