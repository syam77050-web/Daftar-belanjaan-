<!DOCTYPE html>
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Program Menghitung Total Belanja</title>
<style>
  body {
    margin: 0;
    background: #eef4ff;
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
    color: #2c4a7a;
  }
  .header {
    text-align: center;
    padding: 40px 20px 20px;
  }
  .header .icon { font-size: 50px; }
  .header h1 {
    font-size: 26px;
    font-weight: 800;
    color: #26467d;
    margin: 10px 0 5px;
    line-height: 1.2;
  }
  .header p {
    color: #7a8cae;
    font-size: 15px;
    margin: 0;
  }
  .container {
    max-width: 500px;
    margin: 0 auto;
    padding: 15px;
    padding-bottom: 100px;
  }
  .card-utama {
    background: white;
    border-radius: 22px;
    padding: 20px;
    box-shadow: 0 8px 20px rgba(38, 70, 125, 0.08);
  }
  .judul-daftar {
    font-weight: 800;
    font-size: 20px;
    color: #26467d;
    margin-bottom: 15px;
    display: flex;
    align-items: center;
    gap: 8px;
  }
  .item-box {
    border: 1.5px solid #e3eaf6;
    border-radius: 18px;
    padding: 16px;
    margin-bottom: 16px;
    background: #fbfdff;
  }
  .item-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 12px;
  }
  .item-header b { color: #26467d; font-size: 16px; }
  .btn-hapus {
    background: #ffe8e8;
    color: #c93c3c;
    border: none;
    border-radius: 12px;
    padding: 6px 14px;
    font-weight: 700;
    font-size: 13px;
    cursor: pointer;
  }
  label {
    font-size: 14px;
    font-weight: 600;
    color: #5a7296;
    display: block;
    margin: 12px 0 6px;
  }
  input {
    width: 100%;
    box-sizing: border-box;
    padding: 13px 14px;
    border-radius: 12px;
    border: 1.5px solid #e3eaf6;
    background: white;
    outline: none;
    font-size: 14px;
  }
  input:focus { border-color: #6ea0ff; }
  .btn-tambah {
    width: 100%;
    background: white;
    border: 1.8px dashed #a8c1e6;
    color: #4a6fae;
    border-radius: 14px;
    padding: 14px;
    font-weight: 700;
    cursor: pointer;
    margin-top: 10px;
  }
  .total-box {
    background: #26467d;
    color: white;
    border-radius: 18px;
    padding: 18px;
    margin-top: 20px;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .total-box h3 { margin: 0; font-size: 16px; opacity: 0.9; }
  .total-box b { font-size: 20px; }
</style>
</head>
<body>

<div class="header">
  <div class="icon">🛒</div>
  <h1>Program Menghitung Total<br>Belanja</h1>
  <p>Hitung total belanja dengan mudah dan praktis.</p>
</div>

<div class="container">
  <div class="card-utama">
    <div class="judul-daftar">🛍️ Daftar Barang Belanja</div>
    
    <div id="wadahBarang"></div>

    <button class="btn-tambah" onclick="tambahBarang()">+ Tambah Barang</button>

    <div class="total-box">
      <h3>Total Belanja</h3>
      <b id="totalHarga">Rp 0</b>
    </div>
  </div>
</div>

<script>
let barangs = [
  { nama: '', harga: '', jumlah: '' },
  { nama: '', harga: '', jumlah: '' }
];

function render() {
  const wadah = document.getElementById('wadahBarang');
  wadah.innerHTML = '';
  barangs.forEach((b, i) => {
    wadah.innerHTML += `
      <div class="item-box">
        <div class="item-header">
          <b>Barang ${i+1}</b>
          <button class="btn-hapus" onclick="hapusBarang(${i})">Hapus</button>
        </div>
        <label>Nama Barang</label>
        
