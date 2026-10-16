Prediksi Performa Siswa Menggunakan Algoritma Random Forest Regressor

Proyek ini menggunakan dataset Student Performance Factors dari Kaggle dan algoritma Random Forest Regressor. Tujuannya adalah memahami tahapan penerapan Machine Learning, mulai dari pengumpulan dan pengolahan data, pelatihan model, evaluasi hasil, hingga prediksi terhadap data siswa baru.

Tujuan Proyek
1.	Memahami konsep dasar Machine Learning dan penerapannya dalam dunia pendidikan.
2.	Menggunakan dataset Kaggle sebagai sumber data.
3.	Mengolah dan membersihkan data sebelum pelatihan model.
4.	Membangun model prediksi menggunakan Random Forest Regressor.
5.	Mengevaluasi kemampuan model dalam memperkirakan nilai ujian siswa.
6.	Mengidentifikasi faktor yang berkaitan dengan prediksi performa akademik.
7.	Mengembangkan sistem prediksi sebagai alat bantu analisis pembelajaran.

Dataset
DatasetStudentPerformanceFactors.csv
Dataset berisi informasi mengenai faktor-faktor yang berkaitan dengan performa akademik siswa.
Penjelasan Algoritma Random Forest Regressor
Random Forest Regressor adalah algoritma Machine Learning untuk memprediksi nilai numerik. Algoritma ini membangun banyak pohon keputusan (decision trees) dari sampel data yang berbeda, kemudian menggabungkan hasil prediksi pohon-pohon tersebut untuk menghasilkan prediksi akhir.

Secara sederhana, prediksi akhir dapat dituliskan sebagai:

ŷ = (1/N) × Σ Tᵢ(x)

Keterangan: ŷ adalah nilai prediksi akhir; N adalah jumlah pohon keputusan; Tᵢ(x) adalah hasil prediksi pohon ke-i; dan x adalah data karakteristik siswa. Pada script, parameter n_estimators=200 berarti model menggunakan 200 pohon keputusan.
Keunggulan algoritma ini adalah mampu mempelajari hubungan yang kompleks antara variabel. Namun, hasilnya tetap dapat memiliki kesalahan dan tidak membuktikan hubungan sebab-akibat.

Penjelasan Tahapan Script

A. Import library
Pandas digunakan untuk membaca dan mengolah tabel; NumPy untuk operasi numerik; Matplotlib untuk visualisasi; dan Scikit-learn untuk preprocessing, pembagian data, pelatihan, serta evaluasi model.

B. Memuat dataset
Fungsi pandas.read_csv() membaca file CSV. head() menampilkan lima baris pertama dan shape menampilkan jumlah baris serta kolom. Tahap ini memastikan file berhasil dibaca.

C. Membersihkan data
Baris duplikat dihapus dan baris tanpa target Exam_Score dihilangkan. Nilai kosong pada fitur lainnya ditangani melalui imputasi pada tahap preprocessing.

D. Menentukan fitur dan target
X berisi variabel input yang digunakan untuk mempelajari pola, sedangkan y berisi kolom Exam_Score sebagai target yang akan diprediksi.

E. Preprocessing
Nilai numerik yang kosong diisi dengan median. Nilai kategorikal yang kosong diisi dengan kategori paling sering muncul, kemudian OneHotEncoder mengubah variabel kategorikal menjadi format numerik.

F. Membagi data training dan testing
Dataset dibagi menjadi 80% data training untuk melatih model dan 20% data testing untuk menguji model pada data yang tidak digunakan saat pelatihan. random_state=42 membantu membuat pembagian dapat direproduksi.

G. Melatih model
Fungsi fit() melatih model dengan data training. n_estimators=200 menetapkan jumlah pohon, min_samples_leaf=2 menetapkan jumlah minimum sampel pada daun pohon, dan n_jobs=-1 memungkinkan penggunaan seluruh inti prosesor yang tersedia untuk pekerjaan paralel.

H. Melakukan prediksi
Fungsi predict() memperkirakan nilai ujian dari data testing. Hasil prediksi kemudian dibandingkan dengan nilai aktual untuk mengukur kesalahan model.

I. Mengevaluasi model
MAE mengukur rata-rata kesalahan absolut; RMSE memberi penalti lebih besar pada kesalahan besar; dan R² mengukur kemampuan model menjelaskan variasi target pada data uji. Nilai aktual metrik harus diperoleh dengan menjalankan program.

J. Visualisasi
Grafik nilai aktual versus prediksi memperlihatkan kedekatan prediksi dengan nilai sebenarnya. Feature importance menunjukkan variabel yang paling banyak digunakan model dalam membuat prediksi, tetapi tidak membuktikan hubungan sebab-akibat.

Alur Kerja Sistem Machine Learning

1.	Pengumpulan dataset Student Performance Factors dari Kaggle.
2.	Pembersihan dan preprocessing data.
3.	Pembagian dataset: 80% training dan 20% testing.
4.	Pelatihan model Random Forest Regressor.
5.	Evaluasi model menggunakan MAE, RMSE, dan R².
6.	Prediksi nilai ujian siswa baru.

Kesimpulan

Random Forest Regressor dapat digunakan untuk membangun model prediksi nilai ujian berdasarkan faktor-faktor dalam dataset Student Performance Factors. Tahapan proyek meliputi pengolahan data, pemisahan data training dan testing, pelatihan model, evaluasi, dan visualisasi hasil. Kualitas model harus dinilai berdasarkan hasil evaluasi setelah program dijalankan. Dalam lingkungan sekolah, prediksi sebaiknya menjadi alat bantu guru untuk merencanakan dukungan belajar, bukan dasar tunggal untuk menentukan kelulusan atau memberi label kepada siswa.
