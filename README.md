# Skeleton Loading Auto

## Deskripsi
Skeleton Loading Auto adalah implementasi efek skeleton loading untuk elemen teks dan gambar di dalam kartu (card). Efek ini memberikan tampilan sementara sebelum konten utama dimuat sepenuhnya.

## Fitur
- Skeleton loading otomatis untuk gambar dan teks.
- Animasinya berhenti setelah konten dimuat.
- Menggunakan CSS untuk efek shimmer.
- Tata letak fleksibel dengan sistem grid.

## Cara Penggunaan
1. Gunakan struktur HTML yang sudah disediakan.
2. Tambahkan atribut `skeletonloading` pada elemen yang ingin diberi efek skeleton.
3. Pastikan file CSS dan JavaScript sudah dimasukkan.
4. Saat halaman selesai dimuat, skeleton akan otomatis menghilang.

## Kode Contoh
```html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Skeleton Loading Auto</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            padding: 20px;
        }
        .container-card {
            width: 100%;
            display: flex;
            flex-wrap: wrap;
            gap: 10px;
        }
        .card {
            flex: 1 1 calc(25% - 10px);
            min-width: 200px;
            background: #fff;
            padding: 20px;
            box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
            border-radius: 10px;
        }
        [skeletonloading] {
            background: linear-gradient(90deg, #ddd 25%, #ccc 50%, #ddd 75%);
            background-size: 200% 100%;
            color: transparent;
            border-radius: 5px;
            position: relative;
            animation: shimmer 1.5s infinite;
        }
        @keyframes shimmer {
            0% { background-position: 200% 0; }
            100% { background-position: -200% 0; }
        }
    </style>
</head>
<body>
<div class="container-card">
    <div class="card">
        <img skeletonloading src="https://i.pinimg.com/736x/f6/15/6f/f6156f53687bd2148a5478667095740a.jpg" alt="Nature">
        <h3 skeletonloading>Graphic designers.</h3>
        <p skeletonloading>You'll need these to become graphic designers.</p>
    </div>
</div>
<script>
    document.addEventListener("DOMContentLoaded", () => {
        document.querySelectorAll("[skeletonloading]").forEach(element => {
            setTimeout(() => {
                element.removeAttribute("skeletonloading");
                element.style.color = "";
            }, 800);
        });
    });
</script>
</body>
</html>
```

## Catatan
- Pastikan elemen yang diberikan atribut `skeletonloading` memiliki konten yang nantinya akan ditampilkan setelah efek loading selesai.
- Anda dapat menyesuaikan durasi animasi dengan mengubah nilai pada `setTimeout()` di JavaScript.
