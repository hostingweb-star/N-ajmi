<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Blog Galaxy Hijau Neon</title>

  <!-- Font & Icon -->
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.0/css/all.min.css">

  <style>
    /* --- GLOBAL --- */
    body {
      margin: 0;
      padding: 0;
      font-family: 'Poppins', sans-serif;
      background: radial-gradient(circle at top, #02110f, #011a14, #001008);
      color: #d8ffd8;
      min-height: 100vh;
      display: flex;
      justify-content: center;
      align-items: flex-start;
      padding: 30px 10px;
    }

    .container {
      width: 100%;
      max-width: 700px;
      background: rgba(10, 25, 10, 0.85);
      border: 1px solid #00ff88;
      border-radius: 20px;
      box-shadow: 0 0 25px #00ff8875;
      padding: 25px;
      backdrop-filter: blur(8px);
      position: relative;
    }

    /* --- HEADER --- */
    header {
      text-align: center;
      margin-bottom: 25px;
    }
    header h1 {
      font-size: 1.8em;
      color: #00ffb7;
      text-shadow: 0 0 10px #00ff99;
      margin-bottom: 10px;
    }
    header p {
      color: #b2fcd6;
      font-size: 0.95em;
    }

    /* --- ICON DEKORASI --- */
    .icon-decor {
      position: absolute;
      color: #00ff99;
      opacity: 0.3;
      animation: float 6s infinite ease-in-out;
    }
    .icon1 { top: 20px; left: 20px; font-size: 30px; animation-delay: 0s; }
    .icon2 { top: 50%; right: 15px; font-size: 25px; animation-delay: 2s; }
    .icon3 { bottom: 15px; left: 40%; font-size: 35px; animation-delay: 4s; }

    @keyframes float {
      0%, 100% { transform: translateY(0); opacity: 0.4; }
      50% { transform: translateY(-10px); opacity: 0.8; }
    }

    /* --- POST SECTION --- */
    .posts {
      display: grid;
      gap: 20px;
    }
    .post {
      background: rgba(0, 40, 20, 0.7);
      border: 1px solid #00ff88;
      border-radius: 12px;
      padding: 20px;
      transition: transform 0.3s, box-shadow 0.3s;
    }
    .post:hover {
      transform: translateY(-5px);
      box-shadow: 0 0 15px #00ff8870;
    }
    .post h2 {
      color: #00ffaa;
      margin-bottom: 10px;
      font-size: 1.3em;
    }
    .post p {
      font-size: 0.95em;
      color: #d9ffe9;
      line-height: 1.6;
    }
    .post h3 {
      color: #00ffaa;
      margin-bottom: 10px;
      font-size: 1.0em;
    }

    .img-container{text-align:center;margin:16px 0;}
    .img-container img{max-width:80%;border-radius:10px;box-shadow:0 0 20px rgba(56,182,255,0.25);border:1px solid rgba(56,182,255,0.2);transition:transform .3s ease;}
    .img-container img:hover{transform:scale(1.03);box-shadow:0 0 25px rgba(56,182,255,0.4);}
    .img-caption{font-size:12px;color:#9aa8bf;margin-top:6px;font-style:italic;}
    
    pre {
      background: #2e3d3a;
      padding: 10px;
      color:#001008;
      border-radius: 10px;
      overflow-x: auto;
      text-shadow: 0 0 10px #00ff99;
      font-weight: bold;
    }

    /* --- FOOTER --- */
    footer {
      text-align: center;
      margin-top: 30px;
      font-size: 0.9em;
    }
    footer a {
      color: #00ffb3;
      text-decoration: none;
      font-weight: bold;
    }
    footer a:hover {
      text-shadow: 0 0 10px #00ffb3;
    }

    /* --- RESPONSIVE --- */
    @media (max-width: 480px) {
      .container {
        padding: 20px;
      }
      header h1 {
        font-size: 1.4em;
      }
      .post h2 {
        font-size: 1.1em;
      }
    }
  </style>
</head>

<body>
  <div class="container">

    <!-- Icon Dekorasi -->
    <i class="fas fa-star icon-decor icon1"></i>
    <i class="fas fa-meteor icon-decor icon2"></i>
    <i class="fas fa-rocket icon-decor icon3"></i>

    <!-- Header -->
    <header>
      <h1>Blog Basis Data</h1>
      <p><strong>NAJMI SHAUKY KAMIL</strong> · if24.najmikamil@mhsubpkarawang.ac.id</p>
    </header>

    <!-- Posts -->
    <section class="posts">
      <div class="post">
        <h2><i class="fas fa-code"></i> Post 1: Apa itu Primary Key, Foreign Key, dan Candidate Key?</h2>
        <p><strong>→ Primary Key</strong> adalah kolom unik untuk identitas tiap data, tidak boleh kosong atau ganda.
        <br><strong>→ Foreign Key</strong> adalah kolom yang menghubungkan tabel satu dengan tabel lain, nilainya berasal dari Primary Key tabel lain.
        <br><strong>→ Candidate Key</strong> adalah kolom yang berpotensi jadi Primary Key karena nilainya juga unik.</p>
      <h2>🧩 Struktur SQL Sistem Toko Buku</h2>
  <pre> 
      -- ===============================
      -- DATABASE TOKO BUKU
      -- ===============================

      CREATE DATABASE toko_buku;
      USE toko_buku;

      -- ===============================
      -- 1. TABEL PENERBIT
      -- ===============================
      CREATE TABLE penerbit (
        id_penerbit INT AUTO_INCREMENT PRIMARY KEY,
        nama_penerbit VARCHAR(100) NOT NULL UNIQUE,  -- Candidate Key
        alamat VARCHAR(200),
        no_telp VARCHAR(20)
      );

      -- ===============================
      -- 2. TABEL BUKU
      -- ===============================
      CREATE TABLE buku (
        id_buku INT AUTO_INCREMENT PRIMARY KEY,
        isbn VARCHAR(20) UNIQUE,                     -- Candidate Key
        judul VARCHAR(150) NOT NULL,
        pengarang VARCHAR(100),
        harga DECIMAL(10,2),
        stok INT,
        id_penerbit INT,
        FOREIGN KEY (id_penerbit) REFERENCES penerbit(id_penerbit)
          ON UPDATE CASCADE ON DELETE SET NULL
      );

      -- ===============================
      -- 3. TABEL PELANGGAN
      -- ===============================
      CREATE TABLE pelanggan (
        id_pelanggan INT AUTO_INCREMENT PRIMARY KEY,
        nama_pelanggan VARCHAR(100) NOT NULL,
        email VARCHAR(100) UNIQUE,                   -- Candidate Key
        alamat VARCHAR(200),
        no_telp VARCHAR(20)
      );

      -- ===============================
      -- 4. TABEL TRANSAKSI
      -- ===============================
      CREATE TABLE transaksi (
        id_transaksi INT AUTO_INCREMENT PRIMARY KEY,
        id_pelanggan INT,
        tanggal_transaksi DATE,
        total DECIMAL(10,2),
        FOREIGN KEY (id_pelanggan) REFERENCES pelanggan(id_pelanggan)
          ON UPDATE CASCADE ON DELETE SET NULL
      );

      -- ===============================
      -- 5. TABEL DETAIL TRANSAKSI
      -- ===============================
      CREATE TABLE detail_transaksi (
        id_detail INT AUTO_INCREMENT PRIMARY KEY,
        id_transaksi INT,
        id_buku INT,
        jumlah INT,
        subtotal DECIMAL(10,2),
        FOREIGN KEY (id_transaksi) REFERENCES transaksi(id_transaksi)
          ON UPDATE CASCADE ON DELETE CASCADE,
        FOREIGN KEY (id_buku) REFERENCES buku(id_buku)
          ON UPDATE CASCADE ON DELETE SET NULL
      );
  </pre>

    <div class="img-container">
        <img src="table_4.png" alt="Contoh Primary, Foreign, Candidate Key">
        <p class="img-caption">Gambar: Contoh relasi tabel dengan Primary Key,Foreign Key, dan Candidate Key</p>
      </div>
      </div>

      <div class="post">
        <h2><i class="fas fa-brain"></i> Post 2: Relation pada ERD & Many-to-Many</h2>
        <p>Relation menggambarkan hubungan antar tabel dalam ERD.
        <br>Jenisnya ada:
          <li>One to One (1:1)</li>
          <li>One to Many (1:M)</li>
          <li>OMany to Many (M:N)</li>
        <br>Hubungan Many-to-Many tidak baik digunakan karena membuat data sulit diatur dan tidak bisa langsung diterapkan di SQL.
        <br>Solusinya adalah membuat tabel penghubung, misalnya detail_transaksi yang menghubungkan tabel buku dan transaksi.</p>
    </section>

    <!-- Footer -->
    <footer>
      <p>Teknik Informatika <a href="https://www.ubpkarawang.ac.id" target="_blank">UBP Karawang</a> 🚀</p>
    </footer>

  </div>
