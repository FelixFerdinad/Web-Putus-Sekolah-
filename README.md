# Sistem Prediksi Putus Sekolah Pulau Jawa (XGBoost Regression + SHAP)

Prototipe website (Streamlit) untuk skripsi. Semua angka berasal dari artefak hasil notebook Google Colab
(`Skripsi_XGBoost_SHAP_Colab_REVISI_2016_2024_Sheet1.ipynb`) dan tersimpan di folder `artifacts/`.
Periode data: 2016–2024, 119 Kabupaten/Kota di Pulau Jawa.

## Menjalankan di komputer sendiri
```
pip install -r requirements.txt
streamlit run app.py
```
Buka alamat yang tampil di terminal (biasanya http://localhost:8501).

## Memperbarui hasil dari Colab
Jika Anda menjalankan ulang notebook dan mendapat `artifacts.zip` baru, ekstrak dan timpa isi folder `artifacts/`
(nama file sama). Tidak ada kode yang perlu diubah. File `model_eval_*.json` tidak dipakai website dan boleh dihapus.

## Menayangkan online (opsional)
1. Unggah folder ini ke repositori GitHub (termasuk `artifacts/`).
2. Buka https://share.streamlit.io, pilih repositori, file utama `app.py`.

## Halaman
| Halaman | Isi | Rancangan proposal |
|---|---|---|
| Beranda | Ringkasan, grafik total Pulau Jawa, cara pakai | - |
| Prediksi | Pilih Kab/Kota dan tahun (2023–2027), grafik, tabel semua wilayah, simulasi masukan | Gambar 3.5 |
| Evaluasi model | MAE/RMSE/R², tuning vs default vs naive, latih vs uji, per provinsi, validasi Madura, parameter | Gambar 3.6 |
| Interpretasi SHAP | Variabel paling berpengaruh dan penjelasan per wilayah | Gambar 3.7 |
| Data & keterbatasan | Sumber data, pemeriksaan kualitas, keterbatasan | - |

## Struktur kode dan modul (Tabel 3.6)
| Modul proposal | File |
|---|---|
| Modul Data | `modul/data.py` |
| Modul Prediksi | `modul/prediksi.py` |
| Modul Evaluasi | `modul/evaluasi.py` |
| Modul SHAP | `modul/shap_page.py` |
| Modul UI | `modul/ui.py`, `modul/beranda.py`, `app.py` |
| Prapemrosesan dan Pemodelan | dikerjakan di notebook Colab; hasilnya dibaca website dari `artifacts/` |

## Catatan membaca hasil
- Model cenderung memprediksi lebih rendah dari kenyataan (galat agregat uji −24,4%); kriteria simpangan 10% belum terpenuhi.
- Prediksi 2026–2027 bersifat berantai dengan persentase penduduk miskin ditahan konstan.
- Persentase penduduk miskin berskala provinsi.

## Uji otomatis
`python uji_aplikasi.py` memastikan semua halaman tampil tanpa error.
