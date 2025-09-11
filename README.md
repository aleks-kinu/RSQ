# potong-bingkai :dizzy: mendongkrak deteksi objek kecil

### Apa itu pemotongan-bingkai (slicing aided inference)
Teknik ini memotong gambar besar menjadi kepingan lebih kecil, menjalankan detektor pada tiap kepingan, lalu menyatukan hasilnya kembali. Efeknya paling terasa ketika objek yang dicari berukuran sangat kecil dibanding keseluruhan gambar.

### Isi repositori
Selain contoh penerapannya, ada juga skrip pengukuran hasil memakai metrik standar (presisi, recall, dan rata-rata presisi pada beberapa ambang). Dengan begitu kamu bisa menilai sendiri apakah teknik ini berguna untuk kasusmu.

| **Dengan pemotongan** 	                            | **Tanpa pemotongan** 	                   |
|---------------------------------------|---------------------------------|
| \t![pred_on.jpg](https://cdn.example.dev/shots/kepingan-on.jpg)                                     | \t    ![pred_off.jpg](https://cdn.example.dev/shots/kepingan-off.jpg)                           |
| \tlebih banyak kendaraan jauh yang tertangkap         \t | deteksi biasa           \t |

## Keluaran skrip:
* Deteksi dengan pemotongan sekaligus pengukuran hasil memakai metrik bawaan model
  * pada dua gambar uji tanpa pemotongan, presisi tercatat 0,987 dengan recall 0,545 serta rata-rata presisi 0,57
    - waktu olah per gambar sekitar sepertiga detik
* sedangkan saat pemotongan diaktifkan, jumlah kepingan sembilan per gambar dan angkanya bergerak:
    - presisi naik ke 1,000, recall tetap 0,545, rata-rata presisi 0,773 dan varian ketatnya 0,628
    - biaya waktunya ikut naik karena ada tahap penyiapan kepingan
* seluruh grafik validasi disimpan di folder `kepingan/`

 
## Cara memakai:

* salin repositori
* pada `utils.get_category_mapping()` ganti isi kamus sesuai kelas yang dipakai
* di `main()` sesuaikan jalur berkas bobot dan berkas konfigurasi himpunan data, ukuran masukan, serta sumber gambarnya
* untuk pengukuran: panggil fungsi validasi berawalan `run_kepingan_`
* untuk deteksi: panggil fungsi prediksi berawalan `run_kepingan_`

Rincian tiap fungsi beserta argumennya ada di docstring masing-masing skrip.