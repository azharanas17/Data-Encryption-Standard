# Data Encryption Standard (DES)

Algoritma Data Encryption Standard (DES) adalah algoritma kriptografi simetris yang mengenkripsi data dengan blok tetap sebesar 64 bit. Cara kerjanya terdiri dari beberapa langkah, baik untuk enkripsi maupun dekripsi. Di bawah ini, saya akan menjelaskan secara umum bagaimana algoritma DES bekerja:

## Enkripsi:

1. Inisialisasi Awal:

Pesan teks masukan (plaintext) pertama-tama diubah menjadi bentuk biner (0 dan 1).
Pesan biner dijalani melalui langkah inisialisasi awal, termasuk permutasi awal dan pemisahan menjadi dua bagian: bagian kiri (32 bit) dan bagian kanan (32 bit).

2. Ronde Kunci (Key Schedule):

Kunci enkripsi (56 bit) diubah dan disesuaikan untuk menghasilkan sejumlah kunci ronde (round keys) yang akan digunakan selama proses enkripsi. Ini melibatkan permutasi, penggeseran bit, dan kompresi kunci.

3. Iterasi Ronde:

Enkripsi DES terdiri dari 16 ronde. Setiap ronde melibatkan langkah-langkah berikut:
 - Ekspansi (Expansion): Bagian kanan (32 bit) diubah menjadi 48 bit menggunakan tabel ekspansi.
 - XOR dengan Kunci Ronde (Round Key XOR): Hasil ekspansi di-XOR-kan dengan kunci ronde yang sesuai (48 bit).
 - Substitusi (S-Box Substitution): 48 bit data hasil XOR dipecah menjadi 8 blok 6 bit, masing-masing melewati tabel substitusi (S-box) yang mengganti setiap blok dengan 4 bit yang berbeda.
 - Pemutaran (Permutasi): Setelah substitusi S-box, blok 4-bit dari tiap S-box digabungkan dan diubah urutan bitnya menggunakan tabel permutasi.
 - XOR dengan Bagian Kiri: Hasil permutasi di-XOR-kan dengan bagian kiri (32 bit).
 - Pertukaran Bagian Kiri dan Kanan: Posisi bagian kiri dan kanan ditukar. Bagian kanan menjadi bagian kiri di ronde berikutnya.

4. Permutasi Akhir (Final Permutation):

Setelah semua ronde selesai, hasil dari bagian kiri dan kanan digabungkan dan diubah urutan bitnya menggunakan tabel permutasi akhir.

5. Hasil Akhir:

Hasil dari permutasi akhir adalah teks sandi (ciphertext).


## Dekripsi:

Proses dekripsi DES adalah kebalikan dari proses enkripsi. Ini juga melibatkan 16 ronde, tetapi kunci ronde digunakan dalam urutan terbalik.

1. Inisialisasi Awal: Pesan terenkripsi (ciphertext) diubah menjadi bentuk biner.

2. Ronde Kunci (Key Schedule): Kunci dekripsi dihasilkan dari kunci enkripsi dalam urutan terbalik.

3. Iterasi Ronde:

Setiap ronde dekripsi melibatkan langkah-langkah yang mirip dengan ronde enkripsi, tetapi kunci ronde digunakan dalam urutan terbalik.

4. Permutasi Akhir (Final Permutation):

Hasil dari semua ronde diubah urutan bitnya dengan tabel permutasi akhir yang merupakan kebalikan dari permutasi yang digunakan pada enkripsi.

5. Hasil Akhir:

Hasil dari permutasi akhir adalah teks asli (plaintext).

Seluruh proses di atas menggambarkan cara kerja algoritma DES dalam mengenkripsi dan mendekripsi data dengan menggunakan blok tetap sebesar 64 bit. Keamanan DES bergantung pada ukuran kunci 56 bit yang digunakan, yang saat ini dianggap kurang aman karena kemajuan komputasi modern. Sebagai gantinya, AES (Advanced Encryption Standard) telah digunakan secara luas sebagai pengganti DES karena keamanan yang lebih baik.

<hr>

### Beberapa tabel yang digunakan dalam algoritma DES ini

1. `initial_perm`
Initial Permutation: Tabel ini digunakan untuk melakukan permutasi awal pada data masukan (plaintext) sebelum dimasukkan ke dalam algoritma DES. Ini mengatur ulang urutan bit-bit plaintext sesuai dengan urutan yang diperlukan oleh algoritma.

2. `final_perm`
Final Permutation: Ini adalah kebalikan dari tabel `initial_perm`. Tabel ini digunakan untuk mengatur ulang urutan bit-bit setelah proses DES selesai (setelah 16 putaran). Ini dilakukan untuk mendapatkan ciphertext akhir.

3. `keyp`
Permutation Choice 1: Tabel ini digunakan dalam subkunci generasi. Awalnya, kunci yang diberikan adalah 64 bit, dan tabel ini mengurangi kunci menjadi 56 bit dengan menghilangkan beberapa bit tertentu.

4. `key_comp`
Permutation Choice 2: Tabel ini juga digunakan dalam subkunci generasi. Setelah `keyp` menghasilkan 56 bit kunci, tabel ini digunakan untuk menghasilkan kunci subrondom 48 bit dari kunci 56 bit.

5. `exp_d`
Expansion: Tabel ekspansi ini digunakan dalam fungsi f. Tabel ini mengubah 32 bit data setengah blok menjadi 48 bit dengan menggandakan beberapa bit.

6. `sbox`
Substitution Boxes: Tabel `sbox` ini digunakan dalam langkah fungsi f untuk melakukan substitusi pada blok 48-bit. DES memiliki 8 `sbox`, masing-masing mengambil 6 bit sebagai masukan dan mengeluarkan 4 bit sebagai keluaran.

7. `per`
Permutation: Tabel permutasi akhir ini digunakan pada akhir fungsi f untuk mengatur ulang 32 bit keluaran S-box.

8. `shift_table`
Tabel ini digunakan untuk menentukan berapa kali setiap setengah kunci (setiap setengah dari 56 bit kunci awal) akan bergeser (shift) selama proses pembangkitan kunci.