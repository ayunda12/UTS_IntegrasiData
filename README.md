# UTS_IntegrasiData
# Ayunda Kusuma Wardani (6026242004)

# Deteksi Anomali Pengadaan Software pada PBJ

## Deskripsi
Proyek ini bertujuan untuk mendeteksi anomali pada data pengadaan barang/jasa (PBJ), khususnya pada kategori software. Anomali yang dicari adalah paket yang terlihat mirip, tetapi memiliki perbedaan signifikan pada anggaran atau metode pengadaan.

## Dataset
Dataset berasal dari data pengadaan PBJ tahun 2026.

Dilakukan filtering untuk mengambil data yang berkaitan dengan:
- Software
- Aplikasi

Contoh kolom yang digunakan:
- Nama paket
- Uraian pekerjaan
- Metode pengadaan
- Pagu
- Satker
- Lokasi

## Metode

### 1. Preprocessing
- Mengubah teks menjadi huruf kecil
- Menghapus tanda baca
- Menghilangkan spasi berlebih

### 2. Representasi Teks
Teks diubah menjadi data numerik menggunakan **TF-IDF**.

### 3. Perhitungan Similarity
Kemiripan antar paket dihitung menggunakan:
- **Cosine Similarity** (untuk nama & uraian)
- **Exact Match** (untuk metode pengadaan)

## Pembobotan
Keterangan:
- Nama paket: bobot 50%
- Uraian pekerjaan: bobot 30%
- Metode pengadaan: bobot 20%

# Kriteria Anomali
1. Anomali Anggaran
Paket memiliki kemiripan tinggi
Selisih anggaran > 50%
=> Menunjukkan perbedaan harga pada paket yang serupa

2. Anomali Metode
Paket memiliki kemiripan tinggi
Metode pengadaan berbeda
=> Menunjukkan inkonsistensi dalam proses pengadaan

3. Anomali Gabungan (Anggaran & Metode)
Paket memiliki kemiripan tinggi
Selisih anggaran > 50%
Metode pengadaan berbeda
=> Anomali lebih kuat karena terjadi pada harga dan metode sekaligus

4. Anomali Konteks Sama (Paling Kuat 🔥)
Paket memiliki kemiripan tinggi
Selisih anggaran > 50%
Satker sama
Lokasi sama
=> Menunjukkan ketidakwajaran karena terjadi dalam kondisi yang sama
=> Berpotensi adanya pengadaan berulang (duplikasi)

## Output
Hasil analisis berupa:
- Daftar pasangan paket yang mirip
- Nilai similarity
- Perbedaan anggaran
- Deteksi anomali
- Visualisasi (scatter plot & grafik)

Dataset keseluruhan sebelum filter dan sesudahnya, serta hasil pairs dan anomali berada di link berikut: https://docs.google.com/spreadsheets/d/1BHkMJE4nZ_aa6yQFkR25xidGymfc2psw/edit?usp=drive_link&rtpof=true&sd=true 


