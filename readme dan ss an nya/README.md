# Laporan Hasil Praktikum: Final Project Aplikasi Berbasis Container

## Identitas Mahasiswa

- **Nama:** I Putu Ryan Prasetya Nugraha
- **NIM:** 2415354061
- **Kelas/Rombel:** D4 TRPL 4A
- **Tanggal Praktikum:** 20 Mei 2026

---

# Teknologi & Tools yang Digunakan

- **Sistem Operasi:** Windows
- **Containerization:** Docker & Docker Hub
- **Bahasa Pemrograman / Framework:** Node.js & Express.js
- **Database:** MySQL
- **Tools Lain:** VS Code, Git, Postman, Docker Compose

---

# Tujuan Praktikum

Praktikum ini bertujuan untuk memahami proses pembuatan aplikasi berbasis container menggunakan Docker. Selain itu, praktikum ini juga bertujuan untuk memahami penggunaan Docker Compose, pengelolaan volume dan network, pengujian endpoint API, serta proses deployment image ke Docker Hub.

---

# Struktur Project

```bash
project-app/
│── app/
│   ├── Dockerfile
│   ├── package.json
│   ├── index.js
│   └── ...
│
├── docker-compose.yml
└── README.md
```

---

# Langkah-Langkah Praktikum & Dokumentasi

---

## 1. Pengujian Docker Compose, Volume, Network, dan Container

Pada tahap ini dilakukan proses menjalankan aplikasi menggunakan Docker Compose agar service aplikasi dan database dapat berjalan secara bersamaan.

### Menjalankan Docker Compose

```bash
docker compose up -d
```

Perintah di atas digunakan untuk menjalankan seluruh service yang terdapat pada file `docker-compose.yml` secara background.

### Melihat Container yang Berjalan

```bash
docker ps
```

### Melihat Volume Docker

```bash
docker volume ls
```

### Melihat Network Docker

```bash
docker network ls
```

### Hasil Pengujian

- Container aplikasi berhasil berjalan
- Container database MySQL berhasil berjalan
- Volume berhasil dibuat untuk penyimpanan data database
- Network Docker berhasil menghubungkan container aplikasi dan database

### Dokumentasi/Screenshot

```text
Tambahkan screenshot:
- docker compose up berhasil
- docker ps
- docker volume ls
- docker network ls
```

---

## 2. Pengujian Endpoint API (Request & Response)

Pada tahap ini dilakukan pengujian endpoint API menggunakan browser dan Postman untuk memastikan aplikasi berjalan dengan baik.

### Menjalankan Endpoint API

```bash
http://localhost:3000
```

### Pengujian Menggunakan Browser

Browser digunakan untuk memastikan endpoint utama dapat diakses dengan baik.

### Pengujian Menggunakan Postman

Metode GET digunakan untuk mengambil data dari API.

Contoh endpoint:

```bash
GET http://localhost:3000/1
```

### Contoh Response JSON

```json
[
  {
    "id": 1,
    "nama": "Ryan"
  }
]
```

### Hasil Pengujian

- Endpoint berhasil diakses melalui browser
- API berhasil memberikan response JSON
- Request pada Postman berjalan dengan baik

### Dokumentasi/Screenshot

```text
Tambahkan screenshot:
- Browser menampilkan API
- Pengujian GET di Postman
- Response JSON berhasil muncul
```

---

## 3. Pengujian Build Docker Image

Pada tahap ini dilakukan proses build image aplikasi menggunakan Dockerfile.

### Build Docker Image

```bash
docker build -t app-good .
```

### Melihat Docker Image

```bash
docker images
```

### Hasil Pengujian

- Docker image berhasil dibuat
- Image aplikasi muncul pada daftar docker images

### Dokumentasi/Screenshot

```text
Tambahkan screenshot:
- docker build berhasil
- docker images
```

---

## 4. Pengujian Upload ke Docker Hub

Tahap ini dilakukan untuk mengunggah image Docker ke Docker Hub agar dapat digunakan kembali pada perangkat lain.

### Login Docker Hub

```bash
docker login
```

### Tag Docker Image

```bash
docker tag app-good username-dockerhub/app-good:v1.0
```

### Push Docker Image

```bash
docker push username-dockerhub/app-good:v1.0
```

### Hasil Pengujian

- Image berhasil di-tag
- Image berhasil di-upload ke Docker Hub
- Repository image berhasil muncul pada akun Docker Hub

### Dokumentasi/Screenshot

```text
Tambahkan screenshot:
- docker login
- docker push berhasil
- repository Docker Hub
```

---

## 5. Pengujian Pull dan Run Container dari Docker Hub

Pada tahap ini dilakukan pengujian dengan menarik image dari Docker Hub dan menjalankannya kembali.

### Pull Docker Image

```bash
docker pull username-dockerhub/app-good:v1.0
```

### Run Container

```bash
docker run -d -p 3000:3000 username-dockerhub/app-good:v1.0
```

### Verifikasi Aplikasi

```bash
http://localhost:3000
```

### Hasil Pengujian

- Image berhasil di-pull dari Docker Hub
- Container berhasil dijalankan
- Aplikasi berhasil diakses melalui browser

### Dokumentasi/Screenshot

```text
Tambahkan screenshot:
- docker pull berhasil
- docker run berhasil
- aplikasi tampil di browser
```

---

## 6. Pengujian Perbandingan Image Optimized dan Non-Optimized

Pada tahap ini dilakukan perbandingan ukuran image Docker antara versi biasa dan versi optimized.

### Build Image Non-Optimized

```bash
docker build -t app-normal .
```

### Build Image Optimized

```bash
docker build -t app-optimized -f Dockerfile.optimized .
```

### Melihat Ukuran Image

```bash
docker images
```

### Hasil Pengujian

| Jenis Image | Ukuran Image | Waktu Build |
|---|---|---|
| Non-Optimized | Lebih besar | Lebih lama |
| Optimized | Lebih kecil | Lebih cepat |

### Kesimpulan Pengujian

Optimasi Docker image dapat mengurangi ukuran image serta mempercepat proses build dan deployment aplikasi.

### Dokumentasi/Screenshot

```text
Tambahkan screenshot:
- perbandingan docker images
- hasil build optimized dan non-optimized
```

---

# Kendala yang Dihadapi

Beberapa kendala yang dialami selama praktikum antara lain:

1. Container database tidak dapat terkoneksi dengan aplikasi
2. Port Docker mengalami konflik
3. Endpoint API tidak menampilkan data
4. Kesalahan saat melakukan push image ke Docker Hub

### Solusi

- Memastikan konfigurasi `docker-compose.yml` sudah benar
- Menghapus container lama menggunakan:

```bash
docker rm -f nama_container
```

- Memastikan port yang digunakan tidak bentrok
- Melakukan login Docker Hub sebelum push image

---

# Kesimpulan

Dari praktikum ini dapat dipahami bahwa Docker sangat membantu dalam proses deployment aplikasi karena aplikasi dapat dijalankan secara konsisten di berbagai lingkungan. Penggunaan Docker Compose mempermudah pengelolaan multi-container seperti aplikasi dan database. Selain itu, Docker Hub mempermudah proses distribusi image aplikasi sehingga dapat digunakan kembali dengan mudah.

Praktikum ini juga memberikan pemahaman mengenai build image, manajemen container, volume, network, pengujian endpoint API, serta optimasi image Docker agar lebih efisien.
