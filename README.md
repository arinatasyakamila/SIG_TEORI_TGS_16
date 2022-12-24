# SIG_TEORI_TGS_16
 performing spatial joins
 
 cara membuatnya!
 
1.  Temukan file nybb_19a.zip di Peramban QGIS dan kembangkan. Pilih layer nybb_19a/nybb.shp dan seret ke kanvas. Ini        adalah lapisan poligon yang mewakili batas wilayah di kota New York.


2. Selanjutnya, cari file V_SSS_SEGMENTRATING_1.zip dan perluas. Pilih layer dot_V_SSS_SEGMENTRATING_1_20190129.shp dan tambahkan ke kanvas. Ini adalah lapisan garis dari semua jalan di kota.


3. Mari kita periksa atribut yang tersedia untuk setiap fitur lapisan dot_V_SSS_SEGMENTRATING_1_20190129. Klik kanan dan pilih Buka Tabel Atribut.


4. Anda akan melihat atribut yang disebut Rating_B yang memiliki nilai dalam rentang 0-10 yang mewakili peringkat segmen jalan. Atribut RatingWord memiliki peringkat deskriptif. Kita dapat menggunakan kolom Rating_B untuk menghitung rating rata-rata.


5. Anda mungkin telah memperhatikan bahwa beberapa fitur memiliki peringkat NR. Ini adalah segmen yang tidak diberi peringkat. Memasukkan mereka ke dalam analisis kami tidak akan benar. Sebelum kita melakukan penggabungan spasial, mari siapkan Filter untuk mengecualikan rekaman ini. Klik kanan layer dot_V_SSS_SEGMENTRATING_1_20190129 dan pilih Filter.

6. Di Pembuat Kueri, ketikkan ekspresi berikut untuk memilih semua rekaman yang tidak diberi peringkat NR. Anda juga dapat membuat ekspresi secara interaktif dengan mengklik Bidang, Operator, dan memilih Nilai yang sesuai. Klik Oke.

"RatingWord" != 'NR'

7. Anda akan melihat lapisan dot_V_SSS_SEGMENTRATING_1_20190129 sekarang memiliki ikon filter yang menunjukkan bahwa ada filter aktif yang diterapkan pada lapisan ini. Sekarang kita bisa melakukan penggabungan spasial menggunakan layer ini. Pergi ke Memproses ‣ Toolbox.


8. Cari dan temukan Vector general ‣ Gabungkan atribut berdasarkan algoritma lokasi (ringkasan). Klik dua kali untuk meluncurkannya.


9. Dalam dialog Gabung atribut berdasarkan lokasi (ringkasan), pilih nybb sebagai lapisan Input. Lapisan jalan dot_V_SSS_SEGMENTRATING_1_20190129 akan menjadi lapisan Gabung. Anda dapat membiarkan predikat Geometri ke Persimpangan default. Klik tombol … di sebelah Bidang untuk meringkas.


Catatan

Kiat untuk membantu Anda memilih masukan yang benar dan menggabungkan lapisan: Lapisan masukan adalah salah satu yang akan dimodifikasi dengan atribut baru dalam gabungan spasial. Karena kami ingin bidang peringkat rata-rata ditambahkan ke lapisan wilayah, itu akan menjadi lapisan masukan.

10. Pilih Rating_B dan klik OK.


11. Demikian pula, klik tombol … di sebelah Ringkasan untuk menghitung.


12. Pilih rata-rata sebagai operator ringkasan dan klik OK. Sekarang kita siap untuk memulai pemrosesan. Klik Jalankan.


13. Algoritme pemrosesan akan bekerja melalui fitur dan menerapkan gabungan spasial. Verifikasi bahwa pekerjaan pemrosesan berhasil dan klik Tutup.


14. Kembali ke jendela utama QGIS, Anda akan melihat layer Joined layer baru ditambahkan ke kanvas. Buka tabel atribut untuk lapisan ini. Anda akan melihat kolom baru Rating_B_mean ditambahkan ke input layer borough dengan rating rata-rata semua jalan yang bersinggungan dengan fitur tersebut.


15. Sekarang kita dapat melakukan operasi terbalik. Terkadang analisis Anda memerlukan atribut dari lapisan lain berdasarkan hubungan spasial tetapi tidak menghitung ringkasan apa pun. Kita dapat menggunakan atribut Gabung dengan algoritme lokasi untuk analisis semacam itu. Tugasnya adalah menambahkan nama borough ke setiap fitur di layer jalan berdasarkan poligon borough mana yang bersinggungan dengannya. Sebelum kita menjalankan algoritme ini, mari hapus filter dari lapisan dot_V_SSS_SEGMENTRATING_1_20190129. Klik ikon filter dan tekan Hapus di Pembuat Kueri. Klik Oke.

16. Matikan layer Joined di panel Layers. Temukan Vector general ‣ Gabung atribut berdasarkan algoritme lokasi di Processing Toolbox dan klik dua kali untuk meluncurkannya.


17. Pilih dot_V_SSS_SEGMENTRATING_1_20190129 sebagai layer Input dan nybb sebagai layer Join. Anda dapat membiarkan predikat Geometri ke Persimpangan default. Klik tombol … di sebelah Fields untuk menambahkan dan memilih BoroName. Klik Oke.


18. Segmen garis dapat melintasi batas wilayah, jadi kami memilih tipe Penggabungan sebagai fitur Peti terpisah untuk setiap fitur yang terletak (satu-ke-banyak). Klik Jalankan.


19. Setelah pemrosesan selesai, buka tabel atribut dari layer Joined yang baru ditambahkan. Anda akan melihat bahwa ada atribut BoroName baru yang ditambahkan ke setiap fitur jalan.


