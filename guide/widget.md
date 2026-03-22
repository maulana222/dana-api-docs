# Widget API

Klien: `danaClient.widgetApi` — kelas **`WidgetApi`** (`src/widget/v1/apis/WidgetApi.ts`).

## Campuran skema Snap dan Open API

- Banyak endpoint memakai **Snap B2B**, **Snap Apply Token**, atau **Snap B2B2C** (butuh `accessToken`, IP perangkat, koordinat, dll. sesuai method).
- Satu endpoint memakai **Open API** + **`clientSecret`**:

### `queryUserProfile`

- Path: `/dana/member/query/queryUserProfile.htm`
- Header/body dibangun lewat **`populateOpenApiScenarioHeader`** dengan `functionName` = `dana.member.query.queryUserProfile`.
- **`this.clientSecret` wajib terisi** untuk skenario ini (dari konstruktor `Dana` / `CLIENT_SECRET`).
- Jika body berisi `accessToken`, nilai itu dipindahkan ke struktur head Open API dan dikeluarkan dari body sebelum di-sign.

## Daftar method

| Method |
|--------|
| `accountUnbinding` |
| `applyOTT` |
| `applyToken` |
| `balanceInquiry` |
| `cancelOrder` |
| `queryPayment` |
| `queryUserProfile` |
| `refundOrder` |
| `widgetPayment` |

Untuk path HTTP pasti dan skema header per baris, buka `WidgetApi.ts` di repositori.

## Referensi parameter

`docs/widget/v1/Apis/WidgetApi.md` dan model di `docs/widget/v1/Models/`.
