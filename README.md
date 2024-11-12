Alfido Mazdan Marsyadi
H1D022084
Shift B

**Sreenshot**
![{78429F21-AFD4-41E4-958C-BB79FDDED7AD}](https://github.com/user-attachments/assets/1f67e20c-ee6e-4b31-a3dd-1be4d8603413)

![{9D1F7703-3EE5-457C-8227-1328F7059AAF}](https://github.com/user-attachments/assets/e9923146-3cd4-449c-9fc4-f4410ae8e45c)
![{F80D841F-51C4-4EFA-947E-DDC0108C32D1}](https://github.com/user-attachments/assets/ca7881cf-39f7-47fb-991c-2e940ace504b)


**Penjelasan**
READ (Membaca Data)

Fungsi getMahasiswa() digunakan untuk mengambil semua data mahasiswa dari server.
Fungsi ini dipanggil saat komponen pertama kali diinisialisasi melalui ngOnInit.
Data yang berhasil diambil disimpan dalam variabel dataMahasiswa dan ditampilkan di tampilan (view).
Data diperoleh melalui ApiService dengan endpoint tampil.php.
CREATE (Menambah Data)

Proses penambahan data dilakukan melalui fungsi tambahMahasiswa().
Sebelum data dikirim, dilakukan validasi untuk memastikan bahwa kolom nama dan jurusan tidak kosong.
Data yang dikirim adalah objek yang berisi properti nama dan jurusan.
Data dikirim ke backend melalui ApiService ke endpoint tambah.php.
Setelah berhasil menambahkan data:
Form input dikosongkan,
Data mahasiswa diperbarui di tampilan,
Modal ditutup secara otomatis.
UPDATE (Mengubah Data)

Proses pembaruan data dilakukan dalam dua langkah:
Mengambil data mahasiswa yang akan diedit menggunakan fungsi ambilMahasiswa(). Data ini diambil berdasarkan id mahasiswa melalui endpoint lihat.php, dan kemudian ditampilkan di form edit.
Setelah data diedit, perubahan dikirim menggunakan fungsi editMahasiswa() sebagai objek yang berisi id, nama, dan jurusan. Data ini dikirim ke endpoint edit.php.
Setelah data berhasil diperbarui:
Form input dikosongkan,
Data mahasiswa di-refresh di tampilan,
Modal ditutup.
DELETE (Menghapus Data)

Fungsi hapusMahasiswa() digunakan untuk menghapus data mahasiswa.
Sebelum penghapusan dilakukan, muncul dialog konfirmasi untuk memastikan bahwa pengguna benar-benar ingin menghapus data.
Jika pengguna mengonfirmasi, data dihapus berdasarkan id melalui endpoint hapus.php. Setelah berhasil, data di-refresh di tampilan.
Jika pengguna membatalkan, proses hapus dihentikan.
Fitur Pendukung CRUD
Manajemen Modal: Fungsi-fungsi openModalTambah, openModalEdit, dan cancel digunakan untuk mengontrol tampilan modal tambah dan edit, serta untuk menutup modal. Fungsi resetModal digunakan untuk mengosongkan form input.
Error Handling: Setiap operasi CRUD memiliki penanganan kesalahan dan keberhasilan, dengan pesan ditampilkan di konsol untuk kemudahan debugging.
State Management: Menggunakan properti untuk menyimpan status dan data, seperti:
dataMahasiswa untuk menyimpan seluruh data mahasiswa,
modalTambah dan modalEdit untuk mengontrol status modal,
id, nama, dan jurusan untuk menyimpan data dari form input.
Implementasi ini sudah baik karena:

Memanfaatkan ApiService untuk memisahkan logika komunikasi dengan backend.
Melakukan validasi input sebelum pengiriman data.
Menggunakan modal untuk input dan edit data, serta konfirmasi sebelum penghapusan.
Data diperbarui di tampilan setelah setiap operasi CRUD selesai.
Mengutamakan pengalaman pengguna dengan mengedepankan dialog konfirmasi dan penanganan kesalahan.
Penjelasan Alert Konfirmasi Hapus Mahasiswa
Struktur Alert Konfirmasi

Alert konfirmasi dibuat menggunakan AlertController dari Ionic Angular.
Alert ini memiliki beberapa bagian, yaitu:
Header: menampilkan judul "Konfirmasi Hapus",
Message: menampilkan pesan konfirmasi "Apakah Anda yakin ingin menghapus data ini?",
Buttons: terdapat dua tombol pilihan untuk pengguna.
Fungsi Tombol di Alert

Tombol "Tidak":
Untuk membatalkan penghapusan data.
Tombol ini memiliki peran 'cancel'.
Saat ditekan, hanya akan menampilkan pesan di konsol bahwa penghapusan dibatalkan, dan alert akan tertutup otomatis.
Tombol "Ya":
Untuk melanjutkan proses hapus.
Saat ditekan, tombol ini akan:
Memanggil API hapus dan mengirimkan id mahasiswa,
Jika berhasil, data mahasiswa di-refresh dan pesan sukses ditampilkan di konsol,
Alert tertutup secara otomatis.
Proses Alert

Alert dibuat dengan AlertController.create() secara asinkron menggunakan async/await.
Alur prosesnya sebagai berikut:
Alert dikonfigurasi dan ditampilkan dengan alert.present().
Pengguna memilih salah satu tombol.
Tindakan dijalankan sesuai tombol yang dipilih.
Keuntungan Menggunakan Alert Konfirmasi

Memastikan bahwa penghapusan data tidak dilakukan secara tidak sengaja.
Memberikan pengguna kesempatan untuk mempertimbangkan ulang sebelum melanjutkan tindakan.
Meningkatkan pengalaman pengguna dengan memberikan feedback yang jelas.
Mengikuti prinsip UI/UX terbaik dalam penanganan aksi kritis.
Integrasi Alert dengan CRUD

Alert konfirmasi ini terintegrasi dengan proses DELETE pada CRUD.
Berfungsi sebagai lapisan keamanan untuk menghindari penghapusan yang tidak diinginkan.
Tetap menjaga alur pembaruan data setelah penghapusan berhasil.
Implementasi alert konfirmasi ini menunjukkan perhatian terhadap pengalaman pengguna dan keamanan data, dengan memberikan opsi untuk membatalkan penghapusan sebelum data benar-benar hilang.
