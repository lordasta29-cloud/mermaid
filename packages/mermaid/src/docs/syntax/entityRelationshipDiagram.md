erDiagram
    %% Entitas dan Relasi
    PENGGUNA ||--o{ KENDARAAN : "memiliki"
    PENGGUNA ||--o{ LOG_TRANSAKSI : "melakukan"
    PENGGUNA ||--o{ PELANGGARAN : "mencatat"
    PENGGUNA ||--o{ LOG_INDIKASI : "menghasilkan"

    %% Struktur Atribut Tabel
    PENGGUNA {
        INT id_pengguna PK
        VARCHAR nama_pengguna
        INT saldo
    }
    
    KENDARAAN {
        INT id_kendaraan PK
        INT id_pengguna FK
        VARCHAR id_rfid
        VARCHAR plat_nomor
        VARCHAR golongan
    }
    
    LOG_TRANSAKSI {
        INT id_transaksi PK
        INT id_pengguna FK
        DATETIME waktu_transaksi
        INT tarif
        INT saldo_awal
        INT saldo_akhir
    }
    
    PELANGGARAN {
        INT id_pelanggaran PK
        INT id_pengguna FK "NULLABLE (Jika Skenario A)"
        DATETIME waktu_pelanggaran
        VARCHAR jenis_pelanggaran
        VARCHAR status
        VARCHAR foto_bukti
    }
    
    LOG_INDIKASI {
        INT id_indikasi PK
        INT id_pengguna FK "NULLABLE (Jika Skenario A)"
        VARCHAR rfid_terbaca
        VARCHAR plat_terbaca
        DATETIME waktu
        VARCHAR warna_indikasi
        VARCHAR keterangan
    }
