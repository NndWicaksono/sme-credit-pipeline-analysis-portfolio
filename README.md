# Analisis Pipeline Kredit SME (2024)

## 🏦 Latar Belakang
Dalam penyaluran kredit SME, tingginya jumlah pengajuan tidak selalu menjamin tingginya realisasi pencairan.
Proses kredit melibatkan beberapa tahapan krusial, terutama pada tahap approval, yang sangat menentukan
kelanjutan pengajuan menuju akad dan pencairan.

Selain itu, perbedaan karakteristik wilayah dan sektor usaha menyebabkan variasi performa pipeline kredit
yang perlu dianalisis lebih dalam untuk mendukung pengambilan keputusan bisnis berbasis data.

---

## 🎯 Tujuan Analisis
Proyek ini bertujuan untuk:
1. Menganalisis kesehatan pipeline kredit SME dari tahap pengajuan hingga pencairan.
2. Mengidentifikasi titik kritis dalam proses kredit, khususnya pada tahap approval.
3. Menganalisis perbedaan performa pipeline berdasarkan wilayah.
4. Menggali potensi sektor usaha melalui analisis approval rate per wilayah.

---

## 🗂️ Data & Tools
- **Data**: Data simulasi (dummy) pengajuan kredit SME ±1.200 data.
- **Python**: Digunakan untuk generate data simulasi agar menyerupai kondisi riil perbankan.
- **Power BI (Power Query)**:
  - Pembersihan dan transformasi data
  - Normalisasi nilai
  - Data modeling (star schema)
  - Visualisasi dashboard
- **Output**: 2 dashboard utama (Summary & Regional)

---

## 📊 Dashboard 1 — Executive Summary

### Fokus Analisis
Dashboard ini memberikan gambaran makro terkait kondisi pipeline kredit SME secara keseluruhan.

### Insight Utama
- Dari 1.200 pengajuan kredit, sekitar **56% disetujui** dan hanya **48% yang berlanjut ke pencairan**.
- Titik kritis utama terdapat pada **tahap approval**, karena keputusan di tahap ini menentukan kelanjutan proses.
- Setelah tahap akad, ruang diskusi relatif kecil, sementara proses pencairan memiliki tantangan administratif dan teknis tersendiri.
- Sektor perdagangan dan jasa mendominasi jumlah pengajuan, namun tidak selalu menunjukkan efisiensi pipeline yang optimal.

### Preview Dashboard
![Dashboard Summary](images/Dashboard-1(Summary).png)

---

## 📍 Dashboard 2 — Analisis Regional & Sektor

### Fokus Analisis
Dashboard ini digunakan untuk melihat variasi performa pipeline kredit berdasarkan wilayah dan sektor usaha.

### Insight Utama
- Terdapat perbedaan signifikan approval rate antar wilayah meskipun volume pengajuan relatif tinggi.
- **Sektor konstruksi** menunjukkan approval rate yang relatif tinggi di beberapa wilayah, menandakan potensi pengembangan kredit.
- Analisis approval rate per sektor per wilayah menjadi kunci dalam menentukan strategi pengembangan kredit berbasis potensi dan risiko.
- Wilayah dengan approval rate tinggi tidak selalu memiliki volume pengajuan terbesar.

### Preview Dashboard
![Dashboard Regional](images/Dashboard-2(Regional).png)

📥 File Dashboard:
- [Download Dashboard (.pbix)](dashboard/Dashboard-SME-credit-pipeline.pbix)
---

## 💡 Rekomendasi Bisnis
- Memperkuat kualitas analisis pada tahap approval sebagai titik keputusan utama.
- Mengembangkan strategi kredit berbasis sektor usaha potensial seperti konstruksi pada wilayah dengan approval rate tinggi.
- Menggunakan dashboard regional sebagai alat monitoring untuk menghindari generalisasi kebijakan antar wilayah.
- Menjadikan approval rate sektoral sebagai indikator pendukung dalam perencanaan ekspansi kredit SME.

---

## 🏁 Kesimpulan
Proyek ini menunjukkan bagaimana dashboard analitik dapat digunakan sebagai alat pendukung pengambilan
keputusan bisnis, bukan sekadar pelaporan. Pendekatan berbasis pipeline, wilayah, dan sektor usaha
membantu mengidentifikasi area pengembangan kredit SME yang lebih efektif dan berkelanjutan.

---

## 👤 Author
**Nanda Adi Wicaksono**  
Data Analyst – Business-Oriented (Perbankan)

---

> Catatan: Seluruh data yang digunakan dalam proyek ini merupakan data simulasi dan tidak merepresentasikan data riil institusi perbankan manapun. 
> Pemahaman proses bisnis dalam analisis ini diperoleh dari observasi terbatas selama masa magang di Unit Kredit SME, sehingga analisis difokuskan pada gambaran umum proses (high-level) dan tidak mencakup detail operasional internal secara menyeluruh.
