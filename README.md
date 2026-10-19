# PROMPT DEVELOPMENT — WEBSITE ORDER APPS PREMIUM

Saya ingin membangun sebuah website **Order Apps Premium / Produk Digital** menggunakan **Next.js sebagai full-stack framework**, sehingga frontend dan backend/API berada dalam satu project.

Gunakan pendekatan yang modern, clean, scalable, aman, dan mudah dikembangkan.

## 1. TUJUAN PROJECT

Buat website untuk menjual produk digital/premium seperti:

- CapCut Premium
- Canva Pro
- Netflix
- Spotify Premium
- YouTube Premium
- Disney+
- ChatGPT Plus
- dan produk digital lainnya.

Website digunakan oleh customer untuk:

1. Melihat produk.
2. Memilih produk dan varian.
3. Mengisi data yang diperlukan sesuai varian.
4. Menambahkan produk ke keranjang.
5. Checkout beberapa produk sekaligus.
6. Mengisi nama dan nomor WhatsApp.
7. Menyetujui Syarat & Ketentuan.
8. Membuat order.
9. Mengirim detail order ke WhatsApp admin/owner.
10. Sistem backend juga dapat mengirim notifikasi status order melalui **Fonnte WhatsApp API**.

Tidak menggunakan payment gateway untuk versi awal.

Tidak membutuhkan:

- Customer account/login.
- Customer dashboard.
- Riwayat order customer.
- Sistem pengiriman otomatis.
- Payment gateway.
- Sistem subscription otomatis.

Fokus utama adalah **simple, cepat, modern, dan mudah digunakan**.

---

# 2. TECH STACK

Gunakan:

- Next.js terbaru
- TypeScript
- App Router
- React
- Tailwind CSS
- shadcn/ui
- Supabase
  - PostgreSQL Database
  - Storage untuk gambar produk
- Vercel untuk deployment
- Fonnte WhatsApp API untuk pengiriman pesan
- Zod untuk validation
- React Hook Form untuk form
- Server Actions / Route Handlers Next.js untuk backend
- TanStack Query jika memang diperlukan
- Lucide React untuk icon

Gunakan struktur project yang rapi dan production-ready.

Jangan membuat backend terpisah.

Next.js harus menangani:

- frontend
- API
- server actions
- authentication admin
- database access
- Fonnte integration
- business logic

---

# 3. DESIGN / UI

Buat desain:

- Modern
- Minimalis
- Premium
- Clean
- Profesional
- Mobile-first
- Responsive
- Fast loading

Gunakan tema:

### Dark Mode

Warna dominan:

- hitam
- dark gray
- charcoal
- slate

Dengan accent color yang modern.

### Light Mode

Gunakan:

- putih
- gray
- slate

Jangan membuat desain terlalu ramai.

Hindari gradient berlebihan.

Hindari terlalu banyak animasi.

Gunakan spacing yang konsisten.

Gunakan rounded corners yang modern.

Gunakan shadow secara minimal.

---

# 4. BAHASA

Seluruh interface customer menggunakan Bahasa Indonesia.

Contoh:

- Beranda
- Produk
- Kategori
- Produk Unggulan
- Beli Sekarang
- Tambah ke Keranjang
- Checkout
- Total
- Pesanan
- Nama Lengkap
- Nomor WhatsApp
- Syarat & Ketentuan
- Lanjutkan
- Kirim Pesanan
- Pesanan Berhasil

Dashboard admin juga menggunakan Bahasa Indonesia.

---

# 5. CUSTOMER WEBSITE

Buat halaman:

## `/`

Homepage.

Isi:

### Hero Section

Contoh:

> Premium Apps & Digital Products  
> Dapatkan akses aplikasi premium dengan harga terjangkau.

CTA:

- Lihat Produk
- Produk Unggulan

### Kategori

Tampilkan kategori produk.

Contoh:

- Entertainment
- Design
- Productivity
- AI
- Music
- Video
- Lainnya

### Produk Unggulan

Tampilkan produk yang ditandai sebagai featured.

### Semua Produk

Grid produk.

Setiap product card memiliki:

- gambar
- nama
- deskripsi singkat
- harga mulai
- badge
- status tersedia
- tombol Beli Sekarang
- tombol Tambah ke Keranjang

---

# 6. PRODUCT DETAIL

Route:

`/produk/[slug]`

Tampilkan:

- gambar produk
- nama produk
- deskripsi
- kategori
- informasi produk
- pilihan varian
- pilihan durasi
- harga
- status tersedia/tidak
- form pemesanan berdasarkan varian
- tombol Beli Sekarang
- tombol Tambah ke Keranjang

Contoh:

## Netflix Premium

Varian:

- 1P
- 2P
- 3P
- Private

Durasi:

- 7 Hari
- 30 Hari
- 60 Hari
- 90 Hari

Setiap kombinasi varian/durasi dapat memiliki harga berbeda.

---

# 7. SISTEM VARIAN PRODUK

Setiap produk dapat memiliki banyak varian.

Contoh:

Product:

`Netflix Premium`

Variant:

`Private`

Durasi:

`30 Hari`

Harga:

`Rp25.000`

Variant lain:

`Sharing`

Durasi:

`30 Hari`

Harga:

`Rp15.000`

Jangan hardcode varian.

Semua harus berasal dari database.

Admin dapat:

- menambah varian
- mengedit varian
- menghapus varian
- mengaktifkan/nonaktifkan varian

---

# 8. FORM PEMESANAN DINAMIS

Setiap varian produk dapat memiliki form pemesanan yang berbeda.

Contoh Netflix:

- Email
- Password

Contoh Canva:

- Email

Contoh CapCut:

- Username
- Email

Contoh produk lain:

- ID akun
- Email
- Username
- Catatan

Karena kebutuhan setiap produk berbeda, jangan hardcode field.

Buat sistem dynamic order fields.

Admin dapat menentukan field yang dibutuhkan untuk setiap varian.

Contoh konfigurasi:

```text
Field:
email

Label:
Email Akun

Type:
email

Required:
true
```

Field lain:

```text
Field:
username

Label:
Username

Type:
text

Required:
false
```

Support minimal:

- text
- email
- tel
- textarea
- select

Untuk `select`, admin dapat menentukan pilihan.

Contoh:

```text
Device:
Android
iPhone
Windows
Mac
```

---

# 9. CART / KERANJANG

Customer dapat membeli beberapa produk sekaligus.

Contoh:

- Canva Pro 1 bulan
- Spotify Premium 3 bulan
- CapCut Pro 1 bulan

Keranjang harus menyimpan:

- product
- variant
- duration
- quantity
- unit price
- dynamic form values
- subtotal

Tampilkan:

- daftar produk
- varian
- durasi
- quantity
- subtotal
- total order

Customer dapat:

- mengubah quantity
- menghapus item
- kembali berbelanja

Gunakan localStorage atau mekanisme client-side yang sesuai untuk cart.

Tidak perlu menyimpan cart ke database.

---

# 10. CHECKOUT

Route:

`/checkout`

Checkout harus menampilkan:

## Data Customer

- Nama Lengkap
- Nomor WhatsApp

Validasi:

- nama wajib diisi
- nomor WhatsApp wajib diisi

Normalisasi nomor WhatsApp agar konsisten.

Contoh:

`08123456789`

dapat dinormalisasi menjadi:

`628123456789`

Jangan menyimpan nomor customer sebagai data permanen jika memang tidak diperlukan.

---

# 11. DYNAMIC ORDER FORM

Di checkout, tampilkan field tambahan sesuai item yang dibeli.

Contoh:

### Netflix Premium

Email:
`customer@email.com`

Password:
`******`

### Canva Pro

Email:
`customer@email.com`

Setiap item memiliki form masing-masing.

Validasi semua field berdasarkan konfigurasi variant.

---

# 12. SYARAT & KETENTUAN

Customer wajib menyetujui:

> Saya telah membaca dan menyetujui Syarat & Ketentuan.

Checkbox wajib dicentang.

Jika belum dicentang:

- tombol checkout tidak dapat digunakan.

Sediakan:

- Syarat & Ketentuan umum
- Syarat & Ketentuan per produk

Jika produk memiliki T&C khusus, tampilkan T&C tersebut di checkout.

Admin dapat mengubah:

- T&C umum
- T&C per produk

---

# 13. ORDER SYSTEM

Ketika customer menekan checkout:

Buat order melalui backend Next.js.

Jangan membuat order langsung dari client ke database menggunakan service role.

Gunakan:

- Server Action
atau
- Route Handler API

Order memiliki status:

```text
PENDING
PROCESSING
SUCCESS
FAILED
CANCELLED
```

Default order:

```text
PENDING
```

---

# 14. DATABASE

Gunakan Supabase PostgreSQL.

Buat schema database yang scalable.

Minimal tabel:

### categories

```text
id
name
slug
description
image_url
is_active
sort_order
created_at
updated_at
```

### products

```text
id
category_id
name
slug
description
image_url
is_featured
is_active
terms_conditions
created_at
updated_at
```

### product_variants

```text
id
product_id
name
description
is_active
sort_order
created_at
updated_at
```

### variant_durations

```text
id
variant_id
name
duration_value
duration_unit
price
is_active
created_at
updated_at
```

Contoh:

```text
name: 30 Hari
duration_value: 30
duration_unit: days
price: 25000
```

### variant_form_fields

```text
id
variant_id
field_name
label
field_type
placeholder
is_required
options
sort_order
created_at
updated_at
```

### orders

```text
id
order_number
customer_name
customer_phone
status
subtotal
total
terms_accepted
created_at
updated_at
```

### order_items

```text
id
order_id
product_id
variant_id
duration_id
product_name
variant_name
duration_name
unit_price
quantity
subtotal
form_data
created_at
```

Simpan snapshot nama produk/variant/duration dan harga pada order item agar order lama tidak berubah jika admin mengedit produk di kemudian hari.

`form_data` dapat menggunakan JSONB.

---

# 15. ORDER NUMBER

Generate nomor order unik.

Contoh:

```text
ORD-20261019-0001
```

atau format random yang aman.

Nomor order harus mudah dibaca admin.

Pastikan tidak terjadi duplicate order number.

---

# 16. WHATSAPP CHECKOUT

Setelah order berhasil dibuat, sistem membuat pesan WhatsApp untuk admin/owner.

Contoh:

```text
🛒 ORDER BARU

No. Order: ORD-20261019-0001

👤 Customer
Nama: Andika
WhatsApp: 628123456789

📦 Detail Pesanan

1. Netflix Premium
Varian: Private
Durasi: 30 Hari
Harga: Rp25.000
Jumlah: 1

2. Canva Pro
Varian: Personal
Durasi: 30 Hari
Harga: Rp20.000
Jumlah: 1

💰 Total: Rp45.000

Status: PENDING

Silakan proses pesanan customer.
```

Pesan harus dibuat secara dinamis berdasarkan order.

---

# 17. INTEGRASI FONNTE

Tambahkan integrasi dengan **Fonnte WhatsApp API**.

Fonnte digunakan untuk mengirim pesan WhatsApp otomatis.

Jangan expose token Fonnte ke client/browser.

Token harus digunakan hanya di server.

Buat service khusus:

```text
lib/fonnte.ts
```

Contoh fungsi:

```text
sendWhatsAppMessage()
```

Semua request Fonnte dilakukan dari server.

---

# 18. KONFIGURASI FONNTE DI ADMIN

Di dashboard admin, buat halaman:

`/admin/settings`

Buat section:

## WhatsApp / Fonnte

Field:

- Fonnte Token
- Nomor WhatsApp Owner
- Aktifkan Fonnte
- Nomor pengirim jika diperlukan oleh konfigurasi Fonnte

Admin dapat:

- memasukkan token
- mengubah token
- mengaktifkan/nonaktifkan integrasi
- memasukkan nomor owner

Token jangan pernah ditampilkan secara plaintext setelah disimpan jika memungkinkan.

Tampilkan:

```text
••••••••••••••••
```

Sediakan tombol:

- Simpan
- Test Connection
- Kirim Test Message

---

# 19. SECURITY FONNTE

Sangat penting:

Jangan:

```text
NEXT_PUBLIC_FONNTE_TOKEN
```

Jangan expose token melalui frontend.

Gunakan environment variable sebagai fallback jika diperlukan:

```text
FONNTE_TOKEN
```

Tetapi jika token dikelola melalui dashboard, simpan secara aman di database.

Gunakan server-only code untuk mengambil credential.

Jangan pernah mengirim token ke browser.

Jangan memasukkan token ke:

- HTML
- client component
- API response
- log
- error message

---

# 20. SISTEM NOTIFIKASI ORDER

Sistem harus mendukung pengiriman WhatsApp berdasarkan status order.

Minimal:

### Order Pending

Ketika order dibuat:

```text
PENDING
```

kirim pesan ke owner/admin.

Contoh:

```text
🔔 ORDER MASUK

No. Order: ORD-20261019-0001

Customer:
Andika

WhatsApp:
628123456789

Total:
Rp45.000

Status:
PENDING

Silakan cek dashboard admin dan proses pesanan.
```

---

# 21. ORDER BERHASIL

Ketika admin mengubah status order menjadi:

```text
SUCCESS
```

sistem mengirim WhatsApp ke customer.

Contoh:

```text
✅ PESANAN BERHASIL

Halo Andika 👋

Pesanan kamu dengan nomor:

ORD-20261019-0001

telah berhasil diproses.

Terima kasih telah melakukan pembelian.
```

Jika diperlukan, admin dapat memasukkan pesan/detail akses secara manual sebelum mengirim pesan berhasil.

---

# 22. ORDER GAGAL

Ketika status menjadi:

```text
FAILED
```

kirim WhatsApp ke customer.

Contoh:

```text
❌ PESANAN GAGAL

Halo Andika,

Pesanan kamu:

ORD-20261019-0001

mengalami kendala dan belum dapat diproses.

Silakan hubungi admin untuk informasi lebih lanjut.

Terima kasih.
```

---

# 23. ORDER PROCESSING

Ketika admin mengubah status:

```text
PROCESSING
```

opsional kirim WhatsApp:

```text
⏳ PESANAN SEDANG DIPROSES

Pesanan:
ORD-20261019-0001

Pesanan kamu sedang diproses oleh admin.

Mohon tunggu beberapa saat.
```

Admin dapat mengaktifkan/nonaktifkan notifikasi ini dari Settings.

---

# 24. NOTIFIKASI KE OWNER

Setiap order baru harus dapat dikirim ke nomor owner melalui Fonnte.

Admin dapat mengatur:

```text
Owner WhatsApp Number
```

Format nomor harus divalidasi.

Contoh:

```text
628123456789
```

---

# 25. TEMPLATE PESAN FONNTE

Jangan hardcode seluruh pesan.

Buat sistem template message.

Admin dapat mengatur template:

### Template Order Masuk

```text
🔔 ORDER MASUK

No. Order: {{order_number}}

Customer: {{customer_name}}
WhatsApp: {{customer_phone}}

Total: {{total}}

{{items}}

Status: {{status}}
```

### Template Pending

```text
⏳ PESANAN DITERIMA

Halo {{customer_name}},

Pesanan {{order_number}} telah diterima dan sedang menunggu proses.
```

### Template Success

```text
✅ PESANAN BERHASIL

Halo {{customer_name}},

Pesanan {{order_number}} telah berhasil diproses.

{{message}}
```

### Template Failed

```text
❌ PESANAN GAGAL

Halo {{customer_name}},

Pesanan {{order_number}} mengalami kendala.

Silakan hubungi admin.
```

Gunakan placeholder:

```text
{{order_number}}
{{customer_name}}
{{customer_phone}}
{{total}}
{{status}}
{{items}}
{{product_name}}
{{variant_name}}
{{duration}}
{{message}}
```

Admin dapat mengubah template melalui dashboard.

---

# 26. PENGIRIMAN PESAN

Buat service notification terpusat.

Contoh:

```text
sendOrderNotification(order, type)
```

Type:

```text
NEW_ORDER
PENDING
PROCESSING
SUCCESS
FAILED
```

Service akan:

1. mengambil template.
2. mengganti placeholder.
3. menentukan nomor tujuan.
4. memanggil Fonnte API.
5. menyimpan hasil pengiriman.
6. menangani error.

---

# 27. LOG FONNTE

Buat tabel:

### whatsapp_logs

```text
id
order_id
recipient
message_type
message
status
provider_response
error_message
created_at
```

Status:

```text
PENDING
SENT
FAILED
```

Tujuannya agar admin dapat melihat apakah WhatsApp berhasil dikirim atau gagal.

---

# 28. RETRY NOTIFICATION

Jika Fonnte gagal mengirim pesan:

Admin dapat menekan:

```text
Kirim Ulang
```

pada dashboard order.

Jangan membuat retry loop tanpa batas.

Sediakan manual retry.

---

# 29. DASHBOARD ADMIN

Route:

```text
/admin
```

Admin harus login.

Gunakan Supabase Auth.

Tidak perlu customer authentication.

Admin authentication saja.

Dashboard:

### Statistik

Tampilkan:

- Total order
- Pending
- Processing
- Success
- Failed
- Total produk
- Produk aktif

---

# 30. ADMIN ORDER MANAGEMENT

Halaman:

`/admin/orders`

Tampilkan:

- nomor order
- nama customer
- WhatsApp
- total
- status
- tanggal
- action

Filter:

- Pending
- Processing
- Success
- Failed
- Cancelled

Admin dapat membuka detail order.

---

# 31. ORDER DETAIL ADMIN

Tampilkan:

### Customer

- Nama
- WhatsApp

### Order

- Order number
- status
- tanggal
- total

### Item

- product
- variant
- duration
- quantity
- price
- form data

Admin dapat mengubah status:

```text
PENDING
PROCESSING
SUCCESS
FAILED
CANCELLED
```

Ketika status berubah:

- tampilkan confirmation dialog.
- kirim notifikasi Fonnte sesuai konfigurasi.
- simpan log pengiriman.

---

# 32. ADMIN PRODUCTS

Halaman:

`/admin/products`

CRUD:

- tambah
- edit
- hapus
- aktif/nonaktif

Product fields:

- nama
- slug
- deskripsi
- kategori
- gambar
- featured
- active
- terms & conditions

---

# 33. ADMIN VARIANTS

Di dalam product:

Admin dapat mengelola:

```text
Variant
```

Contoh:

```text
Netflix
 ├── Private
 │    ├── 7 Hari
 │    ├── 30 Hari
 │    └── 90 Hari
 │
 └── Sharing
      ├── 7 Hari
      └── 30 Hari
```

Admin dapat:

- tambah variant
- edit variant
- delete variant
- enable/disable variant

---

# 34. ADMIN FORM BUILDER

Buat UI sederhana untuk mengatur form setiap variant.

Admin dapat menambahkan field:

```text
Nama field
Label
Placeholder
Type
Required
Options
Urutan
```

Contoh:

```text
Field Name: email
Label: Email Akun
Type: email
Required: Yes
```

Admin dapat drag/drop atau tombol naik/turun untuk mengatur urutan field.

---

# 35. ADMIN CATEGORY

CRUD kategori:

- nama
- slug
- deskripsi
- gambar
- active
- sort order

---

# 36. FEATURED PRODUCT

Admin dapat menentukan produk unggulan.

Field:

```text
is_featured
```

Homepage hanya menampilkan produk yang:

```text
is_active = true
is_featured = true
```

---

# 37. PRODUCT AVAILABILITY

Admin dapat menonaktifkan produk sementara.

Contoh:

```text
Netflix Premium
Status: Tidak tersedia
```

Customer tetap dapat melihat produk tetapi tidak dapat checkout.

Tampilkan:

```text
Tidak tersedia sementara
```

---

# 38. TERMS & CONDITIONS

Admin dapat mengatur:

### Global Terms

Syarat & Ketentuan website.

### Product Terms

Syarat & Ketentuan khusus produk.

Jika product terms kosong:

gunakan global terms.

Jika product terms tersedia:

tampilkan product terms.

---

# 39. ADMIN SETTINGS

Buat:

`/admin/settings`

Sections:

### General

- Nama website
- Logo
- Deskripsi
- WhatsApp owner

### Fonnte

- Enabled
- Token
- Owner phone
- Test message

### WhatsApp Templates

- New Order
- Pending
- Processing
- Success
- Failed

### Terms

- Global Terms

---

# 40. API / BACKEND STRUCTURE

Buat API atau server actions yang terorganisir.

Contoh:

```text
app/
  api/
    orders/
      route.ts
    orders/
      [id]/
        route.ts
    whatsapp/
      test/
        route.ts
```

Atau gunakan Server Actions jika lebih sesuai.

Buat service layer:

```text
lib/
  supabase/
  fonnte/
  orders/
  notifications/
  validation/
```

Jangan mencampurkan business logic langsung di UI component.

---

# 41. VALIDATION

Gunakan Zod.

Validasi:

- customer name
- phone number
- cart item
- variant
- duration
- dynamic form
- terms acceptance
- admin forms

Semua input dari client harus dianggap tidak terpercaya.

Validasi kembali di server.

---

# 42. SECURITY

Perhatikan:

- Supabase RLS
- admin authorization
- server-only secrets
- Fonnte token protection
- input validation
- SQL injection prevention
- XSS prevention
- CSRF considerations
- rate limiting untuk endpoint order
- rate limiting untuk Fonnte
- jangan percaya harga dari client
- jangan percaya product ID dari client tanpa validasi
- ambil harga terbaru dari database ketika membuat order

Sangat penting:

**Harga yang dikirim client tidak boleh menjadi sumber kebenaran.**

Backend harus mengambil:

```text
product
variant
duration
price
```

langsung dari database.

Kemudian backend menghitung ulang:

```text
subtotal
total
```

---

# 43. ORDER CREATION FLOW

Gunakan flow berikut:

```text
Customer
   ↓
Add Product
   ↓
Cart
   ↓
Checkout
   ↓
Validate Customer Data
   ↓
Validate Dynamic Fields
   ↓
Validate Terms
   ↓
Send request to Next.js Server
   ↓
Backend validates product/variant/duration
   ↓
Backend gets current price from Supabase
   ↓
Backend calculates total
   ↓
Create Order
   ↓
Create Order Items
   ↓
Order status = PENDING
   ↓
Send WhatsApp notification to Owner
   ↓
Return Order Number
   ↓
Customer sees success page
```

Jika Fonnte gagal:

**order tetap berhasil dibuat.**

Jangan membuat order gagal hanya karena WhatsApp notification gagal.

Order harus tetap:

```text
PENDING
```

dan error Fonnte disimpan ke log.

---

# 44. SUCCESS PAGE

Setelah order berhasil:

Route:

```text
/order/success/[orderNumber]
```

Tampilkan:

```text
Pesanan berhasil dibuat 🎉

Nomor Pesanan:
ORD-20261019-0001

Silakan lanjutkan komunikasi dengan admin melalui WhatsApp.
```

Sediakan tombol:

```text
Hubungi Admin
```

Jika nomor owner tersedia, buat WhatsApp link.

Jangan menampilkan data sensitif secara berlebihan.

---

# 45. WHATSAPP CUSTOMER

Sediakan tombol:

```text
Hubungi Admin via WhatsApp
```

Pesan otomatis:

```text
Halo Admin, saya ingin menanyakan pesanan ORD-20261019-0001.
```

---

# 46. ERROR HANDLING

Buat error handling yang baik.

Jika order gagal:

```text
Terjadi kesalahan saat membuat pesanan.
Silakan coba lagi.
```

Jangan tampilkan:

- stack trace
- database error
- Fonnte token
- internal API response

kepada customer.

Log error di server.

---

# 47. FONNTE ERROR HANDLING

Jika Fonnte API error:

Simpan:

```text
provider_response
error_message
status = FAILED
```

Tetapi order tetap dibuat.

Admin dapat melihat:

```text
WhatsApp: Gagal
```

dan tombol:

```text
Kirim Ulang
```

---

# 48. IDEAL ADMIN ORDER UI

Buat interface seperti:

```text
┌─────────────────────────────────────────┐
│ Order #ORD-20261019-0001               │
│                                         │
│ Customer                                │
│ Andika                                  │
│ 628123456789                            │
│                                         │
│ Status                                  │
│ [ PENDING ▼ ]                           │
│                                         │
│ Products                                │
│ Netflix Premium                         │
│ Private · 30 Hari                       │
│ Rp25.000                                │
│                                         │
│ Canva Pro                               │
│ Personal · 30 Hari                      │
│ Rp20.000                                │
│                                         │
│ Total: Rp45.000                         │
│                                         │
│ WhatsApp Notification                   │
│ ✓ Owner notification sent               │
│                                         │
│ [ Kirim Ulang ]                         │
└─────────────────────────────────────────┘
```

---

# 49. RESPONSIVE

Website harus sangat bagus di mobile karena customer kemungkinan besar menggunakan smartphone.

Prioritaskan:

```text
Mobile
↓
Tablet
↓
Desktop
```

Admin dashboard juga responsive.

---

# 50. SEO

Implementasikan:

- metadata
- title
- description
- Open Graph
- favicon
- sitemap
- robots.txt
- semantic HTML

Product pages harus memiliki SEO metadata dinamis.

Contoh:

```text
Netflix Premium Murah - Nama Website
```

---

# 51. PERFORMANCE

Optimalkan:

- Next.js Image
- lazy loading
- server components
- caching
- database query
- pagination admin orders
- avoid unnecessary client components

Jangan menjadikan seluruh website sebagai `"use client"`.

Gunakan Server Components secara default.

---

# 52. SUPABASE STORAGE

Gunakan Supabase Storage untuk gambar produk.

Admin dapat:

1. Upload gambar.
2. Menggunakan URL gambar eksternal.

Jika upload:

```text
product-images/
```

Gunakan nama file yang aman dan unique.

---

# 53. ADMIN AUTH

Gunakan Supabase Auth untuk admin.

Customer tidak perlu login.

Buat proteksi route:

```text
/admin/*
```

Hanya admin yang terautentikasi yang dapat mengakses.

Jika menggunakan role:

```text
admin
```

pastikan role diverifikasi di server.

Jangan hanya menyembunyikan halaman admin di frontend.

---

# 54. DATABASE RLS

Aktifkan Row Level Security di Supabase.

Pastikan customer tidak dapat:

- membaca data order orang lain
- mengubah order
- membaca Fonnte token
- mengubah settings
- mengubah product

Admin dapat mengelola data sesuai permission.

---

# 55. ENVIRONMENT VARIABLES

Buat `.env.example`.

Minimal:

```env
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=

SUPABASE_SERVICE_ROLE_KEY=

FONNTE_TOKEN=
```

Jika Fonnte token dikelola dari dashboard, jangan wajibkan `FONNTE_TOKEN` untuk runtime production kecuali digunakan sebagai fallback.

Jangan pernah commit `.env`.

---

# 56. FOLDER STRUCTURE

Gunakan struktur yang bersih, misalnya:

```text
src/
├── app/
│   ├── (store)/
│   │   ├── page.tsx
│   │   ├── produk/
│   │   │   └── [slug]/
│   │   │       └── page.tsx
│   │   ├── checkout/
│   │   │   └── page.tsx
│   │   └── order/
│   │       └── success/
│   │           └── [orderNumber]/
│   │               └── page.tsx
│   │
│   ├── admin/
│   │   ├── page.tsx
│   │   ├── products/
│   │   ├── categories/
│   │   ├── orders/
│   │   └── settings/
│   │
│   └── api/
│       ├── orders/
│       └── whatsapp/
│
├── components/
│   ├── ui/
│   ├── store/
│   ├── checkout/
│   └── admin/
│
├── lib/
│   ├── supabase/
│   ├── fonnte/
│   ├── orders/
│   ├── notifications/
│   └── validation/
│
├── actions/
│   ├── orders.ts
│   ├── products.ts
│   └── settings.ts
│
└── types/
```

Boleh menyesuaikan struktur jika ada alasan teknis yang lebih baik.

---

# 57. UX CUSTOMER

Customer harus bisa melakukan order sesingkat mungkin.

Ideal flow:

```text
Homepage
↓
Product
↓
Variant
↓
Duration
↓
Form
↓
Add to Cart
↓
Checkout
↓
Nama + WhatsApp
↓
Agree T&C
↓
Buat Pesanan
↓
Success
↓
WhatsApp Admin
```

Jangan membuat terlalu banyak halaman atau langkah yang tidak diperlukan.

---

# 58. ADMIN UX

Admin harus dapat mengelola seluruh sistem tanpa menyentuh database secara manual.

Admin harus bisa:

- CRUD produk
- CRUD kategori
- CRUD variant
- CRUD duration
- CRUD form field
- mengubah harga
- mengaktifkan/nonaktifkan produk
- featured product
- melihat order
- mengubah status order
- melihat data order
- retry WhatsApp
- mengatur Fonnte
- test Fonnte
- mengatur template WhatsApp
- mengatur T&C

---

# 59. WHATSAPP MESSAGE ENGINE

Buat sistem template yang reusable.

Contoh fungsi:

```ts
renderTemplate(template, data)
```

Input:

```ts
{
  order_number,
  customer_name,
  customer_phone,
  total,
  status,
  items
}
```

Output:

```text
Pesan WhatsApp final
```

Gunakan engine yang aman untuk mengganti placeholder.

Jika placeholder tidak tersedia, jangan membuat error fatal.

---

# 60. FONNTE SERVICE

Buat abstraction sehingga jika nanti Fonnte diganti provider lain, tidak perlu mengubah seluruh aplikasi.

Contoh:

```ts
interface WhatsAppProvider {
  sendMessage(
    phone: string,
    message: string
  ): Promise<{
    success: boolean
    providerResponse?: unknown
    error?: string
  }>
}
```

Kemudian:

```text
FonnteProvider
```

mengimplementasikan interface tersebut.

---

# 61. NOTIFICATION SETTINGS

Admin dapat memilih notifikasi yang aktif.

Contoh:

```text
[x] Order baru ke Owner
[x] Pending ke Customer
[x] Processing ke Customer
[x] Success ke Customer
[x] Failed ke Customer
```

Admin dapat mengaktifkan/nonaktifkan masing-masing.

---

# 62. IMPORTANT: ORDER STATUS CHANGE

Ketika admin mengubah status:

```text
PENDING → PROCESSING
```

kirim notifikasi processing jika aktif.

```text
PROCESSING → SUCCESS
```

kirim notifikasi success.

```text
PROCESSING → FAILED
```

kirim notifikasi failed.

Jangan mengirim notifikasi berulang jika status tidak berubah.

Contoh:

```text
PENDING → PENDING
```

tidak perlu mengirim ulang.

Simpan history perubahan status jika memungkinkan.

---

# 63. ORDER STATUS HISTORY

Tambahkan tabel:

```text
order_status_history
```

Fields:

```text
id
order_id
old_status
new_status
changed_by
note
created_at
```

Admin dapat memberikan catatan ketika mengubah status.

---

# 64. ADMIN TEST WHATSAPP

Di Settings:

```text
Nomor WhatsApp Test
[ 628123456789 ]

[ Kirim Test Message ]
```

Backend akan mengirim:

```text
✅ Test WhatsApp berhasil.

Integrasi Fonnte sudah aktif.
```

Tampilkan response secara aman.

Jangan expose token.

---

# 65. SEED DATA

Buat seed data untuk development.

Minimal:

Categories:

```text
Entertainment
Design
Music
AI
Productivity
Video
```

Products:

```text
Netflix Premium
Spotify Premium
Canva Pro
CapCut Pro
YouTube Premium
```

Buat beberapa variant dan duration sebagai contoh.

---

# 66. ADMIN DASHBOARD DESIGN

Dashboard harus terlihat profesional.

Sidebar:

```text
Dashboard
Orders
Products
Categories
Settings
```

Header:

```text
Admin
Theme Toggle
Profile
```

Gunakan responsive sidebar.

---

# 67. SEARCH & FILTER

Admin Orders:

- search order number
- search customer
- filter status
- filter tanggal

Admin Products:

- search product
- filter category
- filter active/inactive

---

# 68. PAGINATION

Gunakan pagination untuk:

- orders
- products jika jumlah besar
- logs

Jangan mengambil seluruh database sekaligus.

---

# 69. AUDIT / LOGGING

Untuk operasi penting admin, jika memungkinkan simpan:

- siapa yang mengubah
- kapan
- apa yang diubah

Minimal untuk perubahan status order.

---

# 70. PRINCIPLE

Prioritaskan:

1. Simplicity
2. Security
3. Maintainability
4. Performance
5. Good UX
6. Clean architecture

Jangan over-engineering.

Tetapi struktur harus cukup baik agar fitur baru mudah ditambahkan.

---

# 71. OUTPUT YANG SAYA INGINKAN DARI AI CODING AGENT

Jangan hanya memberikan contoh kode.

Bangun aplikasi secara bertahap.

Tahapan:

### Phase 1
Setup project:

- Next.js
- TypeScript
- Tailwind
- shadcn
- Supabase

### Phase 2
Database:

- schema
- migrations
- RLS
- seed

### Phase 3
Customer storefront:

- homepage
- category
- product
- product detail
- cart
- checkout

### Phase 4
Order backend:

- order creation
- validation
- price calculation
- order status

### Phase 5
Admin:

- auth
- dashboard
- products
- variants
- duration
- dynamic forms
- categories
- orders

### Phase 6
Fonnte:

- provider
- settings
- test message
- templates
- notification
- logs
- retry

### Phase 7
Polishing:

- responsive
- loading state
- error state
- empty state
- toast
- SEO
- accessibility
- performance

---

# 72. CODING RULES

Gunakan TypeScript strict.

Hindari:

```ts
any
```

kecuali benar-benar diperlukan.

Gunakan reusable components.

Jangan duplicate logic.

Pisahkan:

- UI
- validation
- database
- business logic
- integrations

Gunakan server-side access untuk operasi sensitif.

Jangan expose service role key.

Jangan expose Fonnte token.

Jangan percaya data harga dari client.

Jangan percaya status order dari client.

Semua operasi sensitif harus divalidasi di server.

---

# 73. IMPORTANT FONNTE IMPLEMENTATION

Implementasikan Fonnte menggunakan server-side HTTP request berdasarkan dokumentasi API Fonnte yang berlaku.

Jangan menebak endpoint, parameter, atau response Fonnte jika dokumentasi belum tersedia.

Buat adapter/provider sehingga detail API Fonnte terisolasi di:

```text
lib/fonnte/
```

Jika perlu, buat:

```text
lib/fonnte/client.ts
lib/fonnte/types.ts
lib/fonnte/service.ts
```

Semua error dari Fonnte harus ditangani dengan graceful fallback.

---

# 74. FINAL REQUIREMENT

Saya ingin hasil akhirnya terasa seperti website toko digital premium yang benar-benar siap digunakan.

Customer:

```text
Cepat
Simple
Tidak membingungkan
Mobile friendly
```

Admin:

```text
Mudah mengelola produk
Mudah mengelola harga
Mudah mengelola order
Mudah mengelola Fonnte
```

Backend:

```text
Secure
Validated
Scalable
Maintainable
```

Fonnte:

```text
Order baru → Owner
Pending → Customer
Processing → Customer
Success → Customer
Failed → Customer
```

Semua harus configurable dari dashboard admin.

---

# 75. JANGAN MELAKUKAN

Jangan menambahkan:

- payment gateway
- customer login
- customer registration
- subscription billing
- shipping
- marketplace
- wallet
- point system
- affiliate
- sistem yang terlalu kompleks

kecuali memang dibutuhkan untuk fitur inti.

Jangan membuat fitur hanya untuk terlihat kompleks.

---

# 76. ACCEPTANCE CRITERIA

Aplikasi dianggap selesai jika:

### Customer

- [ ] Bisa melihat produk.
- [ ] Bisa filter berdasarkan kategori.
- [ ] Bisa melihat produk unggulan.
- [ ] Bisa memilih variant.
- [ ] Bisa memilih durasi.
- [ ] Bisa mengisi dynamic form.
- [ ] Bisa add to cart.
- [ ] Bisa membeli banyak produk.
- [ ] Bisa checkout.
- [ ] Bisa mengisi nama.
- [ ] Bisa mengisi nomor WhatsApp.
- [ ] Wajib menyetujui T&C.
- [ ] Order berhasil dibuat.
- [ ] Mendapat nomor order.
- [ ] Bisa menghubungi admin melalui WhatsApp.

### Admin

- [ ] Admin login.
- [ ] Dashboard statistik.
- [ ] CRUD product.
- [ ] CRUD category.
- [ ] CRUD variant.
- [ ] CRUD duration.
- [ ] Dynamic form builder.
- [ ] Upload gambar.
- [ ] URL gambar.
- [ ] Featured product.
- [ ] Enable/disable product.
- [ ] Melihat order.
- [ ] Filter order.
- [ ] Search order.
- [ ] Mengubah status order.
- [ ] Melihat detail order.
- [ ] Retry WhatsApp.

### Fonnte

- [ ] Token dapat dikonfigurasi.
- [ ] Owner WhatsApp dapat dikonfigurasi.
- [ ] Test message.
- [ ] Template dapat dikonfigurasi.
- [ ] Order baru dikirim ke owner.
- [ ] Pending notification.
- [ ] Processing notification.
- [ ] Success notification.
- [ ] Failed notification.
- [ ] Notification log.
- [ ] Manual retry.
- [ ] Token tidak pernah expose ke client.

### Technical

- [ ] Next.js App Router.
- [ ] TypeScript.
- [ ] Supabase.
- [ ] RLS.
- [ ] Server-side validation.
- [ ] Secure secrets.
- [ ] Responsive.
- [ ] Dark/light mode.
- [ ] SEO.
- [ ] Error handling.
- [ ] Loading states.
- [ ] Empty states.
- [ ] Production-ready structure.

---

# 77. CARA BEKERJA

Sebelum menulis kode:

1. Analisis requirement.
2. Buat arsitektur.
3. Buat database schema.
4. Jelaskan relasi tabel.
5. Tentukan route.
6. Tentukan Server Actions/API.
7. Tentukan security model.
8. Tentukan flow order.
9. Tentukan flow Fonnte.

Setelah itu implementasikan secara bertahap.

**Jangan membuat seluruh aplikasi dalam satu file atau satu komponen besar.**

Jika ada keputusan teknis yang belum jelas, pilih solusi yang paling sederhana, aman, dan maintainable.

Jika ada dependency atau library yang sudah deprecated, gunakan alternatif modern yang kompatibel dengan versi Next.js yang digunakan.

Pastikan setiap phase dapat dijalankan dan diuji sebelum lanjut ke phase berikutnya.

Untuk bagian Fonnte, gunakan dokumentasi resmi Fonnte sebagai source of truth untuk endpoint dan payload API.
