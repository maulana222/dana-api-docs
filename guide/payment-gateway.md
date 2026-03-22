# Payment Gateway API

Klien: `danaClient.paymentGatewayApi` — kelas **`PaymentGatewayApi`** (`src/payment_gateway/v1/apis/PaymentGatewayApi.ts`).

## Skema request

Semua method di file ini memakai **`populateSnapB2BScenarioHeader`**: tanda tangan **RSA-SHA256** dengan `privateKey`, header **`ORIGIN`**, **`X-PARTNER-ID`**, timestamp, hash body, dll. **`clientSecret` tidak digunakan** di path ini (field tetap ada di instance tapi tidak masuk header PG).

## Method (nama di TypeScript)

| Method | Path relatif (di `PaymentGatewayApi.ts`) | Keterangan singkat |
|--------|------------------------------------------|---------------------|
| `cancelOrder` | `/payment-gateway/v1.0/debit/cancel.htm` | Batalkan order |
| `consultPay` | `/v1.0/payment-gateway/consult-pay.htm` | Konsultasi metode/channel bayar |
| `createOrder` | `/payment-gateway/v1.0/debit/payment-host-to-host.htm` | Buat order / pembayaran host-to-host |
| `queryPayment` | `/payment-gateway/v1.0/debit/status.htm` | Status / info pembayaran |
| `refundOrder` | `/payment-gateway/v1.0/debit/refund.htm` | Refund |

Setiap method menerima objek request bertipe model yang diekspor dari `dana-node/payment_gateway/v1` (validasi struktur sebelum HTTP).

## Validasi

Sebelum fetch, request divalidasi (`validate*`). Gagal → `ValidationError`. Domain ini dapat memanggil **`CustomValidation`** jika file `CustomValidation` ada di folder payment gateway.

## Referensi parameter

Detail field request/response per endpoint: lihat Markdown otomatis di repo, misalnya  
`docs/payment_gateway/v1/Apis/PaymentGatewayApi.md`.
