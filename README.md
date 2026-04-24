# Aplikasi CRUD Kontak - Firebase Realtime Database + Authentication

Proyek ini adalah aplikasi web sederhana untuk demonstrasi **BaaS menggunakan Firebase** dengan:
- **Firebase Authentication** (Register, Login, Logout)
- **Firebase Realtime Database** (CRUD kontak)

## Fitur
- Register akun (email + password)
- Login & logout
- Create: tambah data kontak baru
- Read: tampilkan seluruh data kontak secara realtime
- Update: ubah data kontak yang sudah ada
- Delete: hapus data kontak
- Data kontak disimpan per user login (`users/{uid}/contacts`)

## Data yang disimpan (5 field)
1. `name`
2. `email`
3. `phone`
4. `city`
5. `note`

Tambahan metadata:
- `createdAt`
- `updatedAt`

## Teknologi
- HTML5
- CSS3
- Bootstrap 5
- Firebase Authentication (Web SDK)
- Firebase Realtime Database (Web SDK)

## Cara Menjalankan
1. Buat project Firebase di [Firebase Console](https://console.firebase.google.com/).
2. Aktifkan **Authentication** (Email/Password).
3. Aktifkan **Realtime Database**.
4. Buka file `app.js`, lalu ganti objek `firebaseConfig` dengan konfigurasi project Anda.
5. Atur aturan database untuk pengujian. Contoh sederhana berbasis user:

   ```json
   {
     "rules": {
       "users": {
         "$uid": {
           ".read": "auth != null && auth.uid === $uid",
           ".write": "auth != null && auth.uid === $uid"
         }
       }
     }
   }
   ```

6. Jalankan web server lokal, misalnya:

   ```bash
   python3 -m http.server 5500
   ```

7. Buka browser ke `http://localhost:5500`.

## Struktur File
- `index.html` → UI auth + form CRUD + tabel data.
- `styles.css` → styling tambahan.
- `app.js` → logika Firebase Authentication + Realtime Database.
