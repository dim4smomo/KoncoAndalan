# TEMAN ANDALAN — Latihan Soal

Halaman kuis mandiri berbasis HTML, CSS, dan JavaScript untuk berlatih soal pilihan ganda TEMAN ANDALAN Kabupaten Lamongan. Aplikasi berjalan langsung di browser tanpa framework atau proses build.

## Menjalankan

1. Buka `index.html` di browser, atau unggah file tersebut ke layanan hosting statis.
2. Masukkan password pada layar pembuka untuk masuk ke halaman latihan.
3. Tunggu soal dimuat dari API. Koneksi internet diperlukan.
4. Pilih kategori untuk berlatih semua soal atau kategori tertentu.
5. Pilih jawaban, baca umpan balik, lalu tekan **Soal berikutnya**.

## Fitur latihan

- Soal dan pilihan jawaban dimuat secara dinamis dari API; soal tidak ditanam sebagai data contoh.
- Menampilkan status dan waktu pengambilan API (WIB), jumlah soal yang dimuat, serta ID soal aktif.
- Menyediakan kategori, progres, dan hitungan jawaban benar maupun salah.
- Soal yang dijawab salah dimasukkan ke antrean dan diulang sampai benar. Progres benar bertambah satu kali untuk setiap soal yang berhasil dijawab benar.
- Latihan selesai setelah semua soal dalam kategori aktif dijawab benar. **Ulangi latihan** memulai sesi baru dan menghapus progres sesi sebelumnya.
- Menampilkan penjelasan rumus untuk soal matematika tertentu jika tersedia.

## Sumber data dan koneksi

- **Endpoint API:** `http://*****.go.id/api/admin/questions/all`
- **Metode:** HTTP GET
- Respons yang diharapkan berupa JSON dengan bentuk `{ "success": true, "data": [...] }`.
- Halaman mencoba endpoint HTTPS dan HTTP, kemudian jalur proxy publik sebagai fallback. Proxy dapat tidak tersedia atau berubah sewaktu-waktu.
- Browser dapat memblokir permintaan HTTP dari situs HTTPS sebagai mixed content. Kegagalan CORS, jaringan, endpoint, maupun proxy akan ditampilkan di halaman; aplikasi tidak menampilkan soal contoh jika data gagal dimuat.

Untuk penggunaan yang andal, pengelola API sebaiknya menyediakan HTTPS dan konfigurasi CORS yang sesuai. Jangan mengirim informasi sensitif melalui HTTP atau proxy publik.

## Password dan keamanan

Password halaman diperiksa oleh JavaScript di browser. Karena `index.html` adalah file statis, password dapat ditemukan oleh siapa pun yang memeriksa source code atau mengubah kode melalui browser. Fitur ini hanya penghalang tampilan sederhana, bukan autentikasi aman dan tidak boleh digunakan untuk melindungi data rahasia.

Jika halaman perlu membatasi akses secara nyata, gunakan autentikasi di sisi server atau layanan hosting yang mendukung kontrol akses. Jangan menyimpan kredensial rahasia di HTML atau JavaScript publik.

## GitHub Pages

1. Unggah `index.html` dan `README.md` ke repository GitHub.
2. Buka **Settings → Pages**.
3. Pada **Build and deployment**, pilih **Deploy from a branch**, lalu pilih branch dan folder publikasi (misalnya `/(root)`).
4. Simpan dan tunggu deployment. Buka alamat GitHub Pages yang ditampilkan.

GitHub Pages menggunakan HTTPS. Jika API hanya menyediakan HTTP dan tidak mengizinkan akses yang diperlukan, kuis mungkin tidak dapat mengambil data sampai API menyediakan HTTPS/CORS yang sesuai atau backend yang aman digunakan.
