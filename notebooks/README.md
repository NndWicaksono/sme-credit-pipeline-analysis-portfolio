# 📦 Data Generation – Kredit SME (Dummy Data)

Notebook ini digunakan untuk **menghasilkan data simulasi (dummy data)** pengajuan kredit SME yang menyerupai
alur proses administrasi kredit perbankan secara **high-level**.  
Data dibuat untuk keperluan **pembelajaran dan portofolio**, tanpa menggunakan data riil institusi perbankan.

> **Catatan**: Python digunakan **hanya untuk pembuatan data simulasi**.  
> Seluruh proses pembersihan, transformasi, dan pemodelan data dilakukan di **Power BI menggunakan Power Query**.

---

## 🎯 Tujuan Pembuatan Data
- Menyediakan dataset yang **realistis dan konsisten** untuk analisis pipeline kredit SME
- Mencerminkan tahapan proses kredit: pengajuan → keputusan → akad → pencairan
- Menghadirkan variasi kualitas data dan outlier agar analisis dashboard tetap natural

---

## 🧱 Struktur Data

### 1️⃣ Tabel Dimensi

#### a. `dim_branch` – Dimensi Cabang
Merepresentasikan unit/cabang SME dengan atribut:
- `branch_id` (primary key)
- `branch_name`
- `region` (Barat, Tengah, Timur)
- `city`
- `branch_type`

Distribusi wilayah dan kota dibuat tidak merata untuk mensimulasikan karakteristik regional.

---

#### b. `dim_rm` – Dimensi Relationship Manager
Merepresentasikan RM yang menangani pengajuan kredit:
- `rm_id`
- `rm_level` (Junior / Senior)
- `rm_join_year`
- `rm_status`

Distribusi level RM dibuat proporsional agar menyerupai struktur tim SME.

---

#### c. `dim_business_segment` – Dimensi Segmen Usaha
Mendefinisikan karakteristik sektor usaha debitur:
- `business_sector`
- `risk_level`
- `typical_plafond_range`

Digunakan untuk analisis segmentasi sektor pada dashboard.

---

## 📊 2️⃣ Tabel Fakta – `fact_credit_application`

### a. Struktur Dasar
Tabel fakta berisi **±1.200 pengajuan kredit** dengan atribut utama:
- `application_id`
- `application_date`
- `rm_id`
- `branch_id`
- `business_sector`

Tanggal pengajuan disebar sepanjang tahun 2024.

---

### b. Status Pipeline Kredit
Setiap pengajuan diklasifikasikan menjadi:
- `Approved`
- `Pending`
- `Rejected`

Tahap proses (`approval_stage`) disesuaikan dengan status akhir pengajuan.

---

### c. Timeline Proses Kredit
Tanggal proses dibuat **berurutan dan logis**:
- `decision_date`
- `akad_signing_date`
- `disbursement_date`

Tanggal hanya diisi pada status yang relevan untuk menghindari kondisi tidak masuk akal
(misalnya pending tetapi sudah akad).

---

## 💰 3️⃣ Simulasi Plafon Kredit
Nilai plafon dibuat menggunakan **distribusi log-normal** untuk mencerminkan:
- Kredit menengah (± Rp1–10 miliar)
- Kehadiran nilai ekstrem (outlier) secara alami

Atribut:
- `requested_plafond`
- `approved_plafond` (hanya untuk status Approved)

---

## 🧪 4️⃣ Simulasi Kualitas Data
Untuk merepresentasikan kualitas administrasi kredit, dibuat atribut:
- `missing_field_count`
- `doc_completeness_flag`
- `data_quality_score`

Skor kualitas data dihitung berdasarkan jumlah field yang hilang dan status pengajuan,
lalu dibatasi pada rentang **0–100**.

---

## ❌ 5️⃣ Alasan Penolakan Kredit
Untuk pengajuan dengan status `Rejected`, ditambahkan:
- `rejection_reason`

Alasan penolakan dipilih dari kategori umum seperti:
- Dokumen Tidak Lengkap
- Cashflow Lemah
- Sektor Risiko Tinggi
- Agunan Tidak Cukup

---

## ✅ 6️⃣ Validasi & Konsistensi Data
Beberapa pengecekan dilakukan untuk memastikan kualitas data:
- Primary key unik
- Relasi antar tabel valid
- Tidak ada tanggal yang tidak logis
- Plafon disetujui tidak melebihi plafon diajukan

---

## ⚠️ 7️⃣ Outlier yang Disengaja
Sebagian kecil data dibuat **menyimpang secara terkontrol**, seperti:
- Pengajuan pending dengan waktu keputusan sangat lama
- Data berkualitas tinggi tetapi tetap ditolak

Outlier ini bertujuan agar analisis dashboard lebih realistis dan menantang.

---

## 📤 8️⃣ Output Data
Data akhir disimpan ke dalam empat file CSV:
- `fact_credit_application.csv`
- `dim_rm.csv`
- `dim_branch.csv`
- `dim_business_segment.csv`

File ini digunakan sebagai sumber data utama pada Power BI.

---

## 🔒 Catatan Etika
Seluruh data merupakan **data simulasi** dan tidak merepresentasikan data riil institusi perbankan manapun.
Pemahaman proses bisnis didasarkan pada **observasi terbatas** selama masa magang di SME Business Center (SBC).
