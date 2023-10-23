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