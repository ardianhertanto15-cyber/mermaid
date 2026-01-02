graph TD
    %% 1. Penerimaan & Verifikasi
    Start((Mulai)) --> A1[Terima Pesanan: WA/Email/Portal]
    A1 --> A2{Verifikasi Kelengkapan Data & Cek Kredit Klien}
    A2 -- Data Tidak Lengkap / Limit Kredit Lampaui Batas --> A1
    A2 -- Data OK & Kredit Aman --> A3[Input ke Sistem TMS - Booking ID]

    %% 2. Koordinasi & Konfirmasi
    A3 --> B1[Koordinasi dengan Bagian Planning - Cek Armada]
    B1 --> B2[Kirim Booking Confirmation ke Pelanggan]

    %% 3. Penerbitan Dokumen
    B2 --> C1[Terbitkan Surat Jalan & Manifest Muatan]
    C1 --> C2[Terbitkan Instruksi Kerja Pengemudi]
    C2 --> C3[Serah Terima Dokumen ke Pengemudi]

    %% 4. Eksekusi & POD
    C3 --> D1[Proses Pengiriman]
    D1 --> D2[Penerimaan Barang oleh Konsumen]
    D2 --> D3[Upload Foto SJ ke Cloud Storage - Arsip Digital]
    D3 --> D4[Verifikasi Fisik SJ Asli - TTD & Stempel Basah]

    %% 5. Penanganan Masalah & Closing
    D4 --> E1{Ada Ketidaksesuaian/Kerusakan?}
    E1 -- Ya --> E2[Hubungi Pelanggan & Bagian Klaim - Maks 1x24 Jam]
    E1 -- Tidak --> E3[Serah Berkas POD ke Bagian Keuangan]
    E2 --> E3
    E3 --> E4[Invoicing & Pencatatan KPI Bulanan]
    E4 --> E5[Pengarsipan Fisik - Folder per Bulan/Pelanggan]
    E5 --> End((Selesai))

    %% Styling
    style Start fill:#007bff,color:#fff
    style End fill:#007bff,color:#fff
    style A2 fill:#fff4dd,stroke:#d4a017
    style E1 fill:#fff4dd,stroke:#d4a017
diagram, reset is called at the very beginning.
