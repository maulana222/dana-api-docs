# Merchant Management API

Klien: `danaClient.merchantManagementApi` — kelas **`MerchantManagementApi`** (`src/merchant_management/v1/apis/MerchantManagementApi.ts`).

## Skema Open API

**Semua** method memanggil **`populateOpenApiScenarioHeader`** dengan **`this.clientSecret`**. Tanpa `CLIENT_SECRET` / `clientSecret` yang benar, request akan gagal di sisi API.

## Method

| Method |
|--------|
| `createDivision` |
| `createShop` |
| `queryDivision` |
| `queryMerchantResource` |
| `queryShop` |
| `updateDivision` |
| `updateShop` |

Beberapa method menangani `accessToken` di body dengan pola serupa widget (ekstraksi ke head jika ada).

## Referensi parameter

`docs/merchant_management/v1/Apis/MerchantManagementApi.md`.
