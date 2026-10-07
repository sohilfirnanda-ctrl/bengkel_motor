# AI Validation Log

## 1. Informasi Proyek

*Nama Proyek:* Sistem Informasi Manajemen Bengkel Motor  
*Jenis Proyek:* Perancangan Sistem Informasi  
*Teknologi:* Database SQL dan REST API  
*Dokumentasi:* ERD, Database SQL, dan API Contract

AI digunakan sebagai alat bantu dalam proses perancangan sistem, khususnya untuk membantu menyusun struktur database, memeriksa hubungan antar tabel, menyusun endpoint API, serta melakukan validasi awal terhadap rancangan sistem.

AI tidak digunakan sebagai pengganti proses analisis dan pengambilan keputusan. Setiap hasil yang diberikan AI diperiksa kembali dan disesuaikan dengan kebutuhan sistem.

---

## 2. Penggunaan AI dalam Perancangan Sistem

AI digunakan pada beberapa tahap perancangan Sistem Informasi Manajemen Bengkel Motor, yaitu:

1. Membantu mengidentifikasi entitas yang dibutuhkan dalam sistem.
2. Membantu menentukan atribut pada setiap tabel.
3. Membantu menentukan Primary Key (PK) dan Foreign Key (FK).
4. Membantu memeriksa hubungan antar tabel pada ERD.
5. Membantu menyusun struktur database menggunakan SQL.
6. Membantu menyusun rancangan endpoint REST API.
7. Membantu menentukan metode HTTP yang sesuai.
8. Membantu menyusun contoh request dan response API.
9. Membantu mengidentifikasi kemungkinan kesalahan pada rancangan sistem.
10. Membantu memastikan dokumentasi sistem memiliki struktur yang konsisten.

---

## 3. Validasi Struktur Database

AI digunakan untuk melakukan pemeriksaan awal terhadap struktur database.

Database dirancang menggunakan beberapa tabel utama yang saling berhubungan, yaitu:

- roles
- users
- customers
- motorcycles
- mechanics
- services
- spare_parts
- service_transactions
- service_details

Hasil validasi menunjukkan bahwa setiap tabel memiliki Primary Key berupa id. Foreign Key juga digunakan untuk menghubungkan tabel yang memiliki hubungan.

Contoh hubungan yang divalidasi:

- users.role_id mengacu pada roles.id
- motorcycles.customer_id mengacu pada customers.id
- service_transactions.motorcycle_id mengacu pada motorcycles.id
- service_transactions.mechanic_id mengacu pada mechanics.id
- service_transactions.user_id mengacu pada users.id
- service_details.transaction_id mengacu pada service_transactions.id
- service_details.service_id mengacu pada services.id
- service_details.spare_part_id mengacu pada spare_parts.id

Dari pemeriksaan tersebut, hubungan antara tabel utama dan tabel detail dinilai sudah sesuai dengan kebutuhan sistem bengkel.

---

## 4. Validasi Normalisasi dan Penamaan

AI juga digunakan untuk melakukan pemeriksaan terhadap prinsip normalisasi dan konsistensi penamaan database.

Beberapa aturan yang digunakan adalah:

- Nama tabel menggunakan bentuk jamak.
- Nama tabel menggunakan format snake_case.
- Primary Key menggunakan nama id.
- Foreign Key menggunakan format <nama_tabel>_id.
- Setiap tabel memiliki atribut created_at dan updated_at.
- Data pelanggan dipisahkan dari data kendaraan.
- Data transaksi dipisahkan dari detail transaksi.
- Data layanan dan suku cadang disimpan pada tabel masing-masing.

Pemisahan tersebut membantu mengurangi pengulangan data dan membuat struktur database lebih mudah dikembangkan.

---

## 5. Validasi API Contract

AI digunakan untuk membantu memeriksa rancangan REST API yang dibuat.

API menggunakan beberapa metode HTTP, yaitu:

- GET untuk mengambil data.
- POST untuk membuat data baru.
- PATCH untuk memperbarui data tertentu.
- Endpoint autentikasi digunakan untuk proses login dan logout.

Beberapa endpoint yang diperiksa antara lain:

- POST /api/auth/login
- POST /api/auth/logout
- GET /api/users
- POST /api/users
- GET /api/customers
- POST /api/customers
- GET /api/motorcycles
- POST /api/motorcycles
- GET /api/mechanics
- POST /api/mechanics
- GET /api/services
- POST /api/services
- GET /api/spare-parts
- POST /api/spare-parts
- GET /api/transactions
- POST /api/transactions
- GET /api/transactions/{id}
- PATCH /api/transactions/{id}/status

Jumlah endpoint yang dirancang telah memenuhi kebutuhan minimal API contract.

---

## 6. Validasi Authentication dan Authorization

AI digunakan untuk membantu menyusun mekanisme autentikasi menggunakan token.

API menggunakan format:

Authorization: Bearer {token}

Validasi juga dilakukan terhadap pembagian hak akses berdasarkan role.

### Role dan Hak Akses

| Role | Hak Akses |
|---|---|
| Admin | Mengelola seluruh data sistem |
| Mekanik | Melihat dan memperbarui transaksi servis |
| Petugas/Kasir | Mengelola pelanggan, kendaraan, transaksi, dan pembayaran |

Pembagian tersebut digunakan sebagai dasar authorization agar setiap pengguna hanya dapat mengakses fungsi sesuai dengan perannya.

---

## 7. Validasi Error Handling

AI digunakan untuk membantu menentukan standar HTTP status code yang digunakan oleh API.

Status code yang digunakan antara lain:

- 200 – Request berhasil.
- 201 – Data berhasil dibuat.
- 400 – Request tidak valid.
- 401 – Pengguna belum terautentikasi.
- 403 – Pengguna tidak memiliki hak akses.
- 404 – Data tidak ditemukan.
- 422 – Data tidak memenuhi validasi.
- 500 – Terjadi kesalahan pada server.

Format response error juga dibuat secara konsisten agar mudah dipahami oleh pengguna maupun pengembang.

---

## 8. Hasil Validasi dan Perbaikan

Berdasarkan pemeriksaan dengan bantuan AI, dilakukan beberapa penyesuaian pada rancangan sistem.

| No | Bagian | Hasil Validasi | Tindakan |
|---|---|---|---|
| 1 | Struktur tabel | Sudah memiliki PK | Dipertahankan |
| 2 | Foreign Key | Hubungan antar tabel perlu diperjelas | Disesuaikan dengan relasi ERD |
| 3 | Penamaan tabel | Perlu konsisten menggunakan snake_case dan bentuk jamak | Diseragamkan |
| 4 | Detail transaksi | Membutuhkan transaction_id | Ditambahkan |
| 5 | API endpoint | Jumlah endpoint harus memenuhi kebutuhan tugas | Ditambahkan hingga lebih dari 15 endpoint |
| 6 | Authentication | API membutuhkan mekanisme token | Ditambahkan Bearer Token |
| 7 | Authorization | Hak akses berdasarkan role perlu dijelaskan | Ditambahkan role-permission |
| 8 | Error handling | Status error perlu distandarkan | Ditambahkan HTTP status code |

---

## 9. Kesimpulan Validasi

Hasil validasi menunjukkan bahwa rancangan Sistem Informasi Manajemen Bengkel Motor telah memiliki komponen utama yang diperlukan, yaitu ERD, database SQL, dan API contract.

Penggunaan AI membantu mempercepat proses pemeriksaan struktur database, hubungan antar tabel, rancangan API, autentikasi, authorization, serta error handling.

Namun, hasil dari AI tidak langsung digunakan tanpa pemeriksaan. Setiap saran dibandingkan kembali dengan kebutuhan sistem dan disesuaikan dengan rancangan proyek.

Dengan demikian, AI digunakan sebagai alat bantu validasi dan dokumentasi, sedangkan keputusan akhir mengenai rancangan sistem tetap dilakukan berdasarkan kebutuhan proyek dan hasil analisis perancang.

---

## 10. Catatan Penggunaan AI

AI digunakan sebagai pendamping dalam proses perancangan dan validasi. AI tidak digunakan untuk menggantikan pengujian sistem secara langsung.

Validasi akhir tetap perlu dilakukan melalui pemeriksaan file ERD, database SQL, API contract, serta pengujian implementasi ketika sistem dikembangkan.
