<!DOCTYPE html>
<html>
<head>
<title>Stok Takip</title>
<style>
    body { font-family: Arial; padding: 20px; }
    button { padding: 10px 20px; margin: 10px; }
    #panel { margin-top: 20px; border: 1px solid #ccc; padding: 20px; width: 300px; display: none; }
</style>
</head>
<body>

<h2>Ürün Seç</h2>

<button onclick="showProduct('penyeboxer')">penyeboxer</button>
<button onclick="showProduct('A2')">A2</button>
<button onclick="showProduct('A3')">A3</button>

<div id="panel">
    <p id="urunAdi"></p>
    <p id="fiyatBilgisi"></p>
    <p id="stokBilgisi"></p>

    <label>Satılan Miktar:</label>
    <input type="number" id="satisMiktar" />
    <button onclick="hesapla()">Hesapla</button>

    <p id="kalanStok"></p>
</div>

<script>
    let stoklar = {
        penyeboxer: { fiyat: 20, stok: 100 },
        A2: { fiyat: 35, stok: 50 },
        A3: { fiyat: 15, stok: 200 }
    };

    let seciliUrun = null;

    function showProduct(urun) {
        seciliUrun = urun;
        document.getElementById("panel").style.display = "block";
        document.getElementById("urunAdi").innerText = "Ürün: " + urun;
        document.getElementById("fiyatBilgisi").innerText = "Fiyat: " + stoklar[urun].fiyat + " TL";
        document.getElementById("stokBilgisi").innerText = "Stok: " + stoklar[urun].stok + " adet";
    }

    function hesapla() {
        let miktar = parseInt(document.getElementById("satisMiktar").value);

        if (!miktar || miktar < 0) {
            alert("Geçerli bir miktar girin!");
            return;
        }

        let kalan = stoklar[seciliUrun].stok - miktar;

        if (kalan < 0) {
            alert("Yeterli stok yok!");
            return;
        }

        stoklar[seciliUrun].stok = kalan;

        document.getElementById("kalanStok").innerText = "Kalan Stok: " + kalan;
        document.getElementById("stokBilgisi").innerText = "Stok: " + kalan + " adet";
    }
</script>

</body>
</html>
