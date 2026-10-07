# API Contract
## Sistem Informasi Manajemen Bengkel Motor

## 1. Base URL
/api

## 2. Authentication
API menggunakan autentikasi berbasis token.

Header:
Authorization: Bearer {token}

Endpoint login tidak membutuhkan token.

## 3. Standard Response

### Success
{
  "success": true,
  "message": "Data berhasil diambil",
  "data": {}
}

### Error
{
  "success": false,
  "message": "Data tidak ditemukan",
  "errors": {}
}

# 4. API Endpoints

## Authentication

### 1. Login
*POST* /api/auth/login

Request:
{
  "email": "admin@gmail.com",
  "password": "password123"
}

Response:
{
  "success": true,
  "message": "Login berhasil",
  "data": {
    "token": "example_token",
    "user": {
      "id": 1,
      "name": "Admin",
      "role": "Admin"
    }
  }
}

### 2. Logout
*POST* /api/auth/logout

Response:
{
  "success": true,
  "message": "Logout berhasil",
  "data": null
}

## Users

### 3. Get Users
*GET* /api/users

Response:
{
  "success": true,
  "message": "Data user berhasil diambil",
  "data": []
}

### 4. Create User
*POST* /api/users

Request:
{
  "role_id": 1,
  "name": "Admin Bengkel",
  "email": "admin@gmail.com",
  "password": "password123"
}

Response:
{
  "success": true,
  "message": "User berhasil dibuat",
  "data": {
    "id": 1
  }
}

### 5. Get User Detail
*GET* /api/users/{id}

Response:
{
  "success": true,
  "message": "Detail user berhasil diambil",
  "data": {
    "id": 1,
    "role_id": 1,
    "name": "Admin Bengkel",
    "email": "admin@gmail.com"
  }
}

### 6. Update User
*PATCH* /api/users/{id}

Request:
{
  "name": "Admin Bengkel Baru",
  "email": "adminbaru@gmail.com"
}

Response:
{
  "success": true,
  "message": "User berhasil diperbarui",
  "data": {}
}

## Customers

### 7. Get Customers
*GET* /api/customers

Response:
{
  "success": true,
  "message": "Data pelanggan berhasil diambil",
  "data": []
}

### 8. Create Customer
*POST* /api/customers

Request:
{
  "name": "Budi",
  "phone": "08123456789",
  "address": "Banda Aceh"
}

Response:
{
  "success": true,
  "message": "Pelanggan berhasil dibuat",
  "data": {
    "id": 1
  }
}

### 9. Get Customer Detail
*GET* /api/customers/{id}

Response:
{
  "success": true,
  "message": "Detail pelanggan berhasil diambil",
  "data": {
    "id": 1,
    "name": "Budi",
    "phone": "08123456789",
    "address": "Banda Aceh"
  }
}

## Motorcycles

### 10. Get Motorcycles
*GET* /api/motorcycles

Response:
{
  "success": true,
  "message": "Data motor berhasil diambil",
  "data": []
}

### 11. Create Motorcycle
*POST* /api/motorcycles

Request:
{
  "customer_id": 1,
  "plate_number": "BL 1234 AB",
  "brand": "Honda",
  "model": "Beat",
  "year": 2024
}

Response:
{
  "success": true,
  "message": "Motor berhasil ditambahkan",
  "data": {
    "id": 1
  }
}

### 12. Get Motorcycle Detail
*GET* /api/motorcycles/{id}

Response:
{
  "success": true,
  "message": "Detail motor berhasil diambil",
  "data": {
    "id": 1,
    "customer_id": 1,
    "plate_number": "BL 1234 AB",
    "brand": "Honda",
    "model": "Beat",
    "year": 2024
  }
}

## Mechanics

### 13. Get Mechanics
*GET* /api/mechanics

Response:
{
  "success": true,
  "message": "Data mekanik berhasil diambil",
  "data": []
}

### 14. Create Mechanic
*POST* /api/mechanics

Request:
{
  "name": "Andi",
  "phone": "08123456789",
  "specialization": "Mesin"
}

Response:
{
  "success": true,
  "message": "Mekanik berhasil ditambahkan",
  "data": {
    "id": 1
  }
}

## Services

### 15. Get Services
*GET* /api/services

Response:
{
  "success": true,
  "message": "Data layanan berhasil diambil",
  "data": []
}

### 16. Create Service
*POST* /api/services

Request:
{
  "name": "Ganti Oli",
  "description": "Penggantian oli mesin",
  "price": 25000,
  "estimated_duration": 30
}

Response:
{
  "success": true,
  "message": "Layanan berhasil ditambahkan",
  "data": {
    "id": 1
  }
}

## Spare Parts

### 17. Get Spare Parts
*GET* /api/spare-parts

Response:
{
  "success": true,
  "message": "Data spare part berhasil diambil",
  "data": []
}

### 18. Create Spare Part
*POST* /api/spare-parts

Request:
{
  "name": "Oli Mesin",
  "part_number": "OLI001",
  "stock": 20,
  "price": 50000
}

Response:
{
  "success": true,
  "message": "Spare part berhasil ditambahkan",
  "data": {
    "id": 1
  }
}

## Service Transactions

### 19. Get Service Transactions
*GET* /api/transactions

Response:
{
  "success": true,
  "message": "Data transaksi berhasil diambil",
  "data": []
}

### 20. Create Service Transaction
*POST* /api/transactions

Request:
{
  "motorcycle_id": 1,
  "mechanic_id": 1,
  "user_id": 1,
  "transaction_date": "2026-10-07 10:00:00",
  "complaint": "Mesin terasa kurang bertenaga",
  "status": "proses"
}

Response:
{
  "success": true,
  "message": "Transaksi servis berhasil dibuat",
  "data": {
    "id": 1
  }
}

### 21. Get Transaction Detail
*GET* /api/transactions/{id}

Response:
{
  "success": true,
  "message": "Detail transaksi berhasil diambil",
  "data": {
    "id": 1,
    "motorcycle_id": 1,
    "mechanic_id": 1,
    "user_id": 1,
    "status": "proses",
    "total_amount": 75000
  }
}

### 22. Update Transaction Status
*PATCH* /api/transactions/{id}/status

Request:
{
  "status": "selesai"
}

Response:
{
  "success": true,
  "message": "Status transaksi berhasil diperbarui",
  "data": {}
}

# 5. HTTP Status Code

| Status | Keterangan |
|---|---|
| 200 | Berhasil |
| 201 | Data berhasil dibuat |
| 400 | Request tidak valid |
| 401 | Tidak terautentikasi |
| 403 | Tidak memiliki akses |
| 404 | Data tidak ditemukan |
| 422 | Validasi gagal |
| 500 | Kesalahan server |

# 6. Error Handling

Jika terjadi kesalahan, API mengembalikan response:

{
  "success": false,
  "message": "Validasi gagal",
  "errors": {
    "email": [
      "Email wajib diisi"
    ]
  }
}

API menggunakan HTTP status code yang sesuai dengan jenis kesalahan.

# 7. Authorization

| Role | Akses |
|---|---|
| Admin | Mengelola seluruh data sistem |
| Mekanik | Melihat dan memperbarui transaksi servis |
| Petugas/Kasir | Mengelola pelanggan, motor, transaksi, dan pembayaran |

# 8. Validation

Data yang dikirim melalui API harus divalidasi.

Contoh:
- Email harus memiliki format email yang valid.
- Nama wajib diisi.
- customer_id harus tersedia.
- motorcycle_id harus tersedia.
- Harga tidak boleh bernilai negatif.
- Stok tidak boleh bernilai negatif.
- Status transaksi harus menggunakan nilai yang telah ditentukan