# Disbursement API

Klien: `danaClient.disbursementApi` — kelas **`DisbursementApi`** (`src/disbursement/v1/apis/DisbursementApi.ts`).

## Skema request

Semua method memakai **`populateSnapB2BScenarioHeader`** (sama seperti Payment Gateway untuk aspek tanda tangan server-ke-server). Di kode saat ini **`clientSecret` tidak dipakai** pada header disbursement.

## Method

| Method | Keterangan singkat |
|--------|--------------------|
| `bankAccountInquiry` | Inquiry rekening bank |
| `danaAccountInquiry` | Inquiry akun DANA |
| `transferToBank` | Transfer ke bank |
| `transferToBankInquiryStatus` | Cek status transfer bank |
| `transferToDana` | Transfer ke DANA |
| `transferToDanaInquiryStatus` | Cek status transfer ke DANA |

## Referensi parameter

`docs/disbursement/v1/Apis/DisbursementApi.md`.
