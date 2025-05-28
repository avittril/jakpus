<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Acak Gunung Pendakian di Jawa - Jejak Kampus</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700&family=Montserrat:wght@600;700&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.2.0/css/all.min.css">
    <style>
        body {
            font-family: 'Roboto', sans-serif;
            background-image: linear-gradient(rgba(0,0,0,0.3), rgba(0,0,0,0.5)), url('https://images.unsplash.com/photo-1506905925346-21bda4d32df4?q=80&w=2070&auto=format&fit=crop'); /* Contoh background gunung dari Unsplash */
            background-size: cover;
            background-position: center;
            background-attachment: fixed;
            color: #333; /* Default text color for better readability */
        }
        .header-title {
            font-family: 'Montserrat', sans-serif;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
        }
        .btn-acak {
            background-color: #38A169; /* Warna hijau segar */
            color: white;
            transition: background-color 0.3s ease, transform 0.2s ease;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }
        .btn-acak:hover {
            background-color: #2F855A; /* Hijau lebih gelap */
            transform: translateY(-2px);
            box-shadow: 0 6px 8px rgba(0,0,0,0.15);
        }
        .card {
            background-color: rgba(255, 255, 255, 0.95); /* Semi-transparent white */
            backdrop-filter: blur(8px); /* Efek frosted glass */
            border-radius: 16px; /* Lebih rounded */
            box-shadow: 0 10px 25px rgba(0, 0, 0, 0.15);
            border: 1px solid rgba(255,255,255,0.2);
        }
        .loader {
            border: 5px solid #f3f3f3; /* Light grey */
            border-top: 5px solid #38A169; /* Warna hijau tombol */
            border-radius: 50%;
            width: 50px;
            height: 50px;
            animation: spin 1s linear infinite;
            margin: 30px auto;
        }
        @keyframes spin {
            0% { transform: rotate(0deg); }
            100% { transform: rotate(360deg); }
        }
        .prose-custom ul > li::before {
            content: "⛰️"; /* Ikon gunung sebagai bullet */
            margin-right: 0.5em;
            /* Hapus styling default prose untuk bullet agar bisa dikustomisasi */
            position: static; 
            display: inline;
            width: auto;
            margin-left: 0;
        }
        .prose-custom ul {
            list-style-type: none; /* Hapus bullet default */
            padding-left: 0;
        }
        .prose-custom ul li {
            padding-left: 1.5em; /* Beri ruang untuk ikon kustom */
            position: relative;
            margin-bottom: 0.5rem;
        }
         .prose-custom ul > li::before { /* Atur ulang posisi ikon */
            content: "⛰️";
            position: absolute;
            left: 0;
            top: 0.1em; /* Sesuaikan agar sejajar dengan teks */
        }

        .prose-custom h3, .prose-custom h4 {
            font-family: 'Montserrat', sans-serif;
            color: #2c5282; /* Biru tua untuk subjudul */
        }
        .footer-credit {
            background-color: rgba(0,0,0,0.6);
            padding: 1rem;
        }
        .mountain-image {
            border: 3px solid white;
            box-shadow: 0 4px 10px rgba(0,0,0,0.2);
        }
    </style>
</head>
<body class="min-h-screen flex flex-col">
    <header class="py-8">
        <div class="container mx-auto px-4 text-center text-white">
            <h1 class="text-4xl md:text-5xl font-bold header-title">Pilih Petualangan Gunungmu!</h1>
            <p class="text-md mt-2 opacity-90">Temukan destinasi pendakian acak di Pulau Jawa.</p>
        </div>
    </header>

    <main class="container mx-auto px-4 py-8 flex-grow">
        <div class="text-center mb-10">
            <button id="acakButton" class="btn-acak font-semibold py-4 px-10 rounded-full shadow-lg text-xl focus:outline-none focus:ring-4 focus:ring-green-300 focus:ring-opacity-75">
                <i class="fas fa-random mr-2"></i> Acak Gunung Tujuan
            </button>
        </div>

        <div id="loadingIndicator" class="hidden loader"></div>

        <div id="hasilGunung" class="hidden card p-6 md:p-10">
            <div class="text-center mb-6">
                <h2 class="text-3xl md:text-4xl font-bold text-gray-800 mb-1 header-title" style="text-shadow: none; color: #1A202C;">Destinasi Terpilih:</h2>
                <p id="namaGunung" class="text-green-600 font-bold text-2xl md:text-3xl"></p>
            </div>
            
            <div class="grid md:grid-cols-5 gap-6 mb-8 items-start">
                <div class="md:col-span-2">
                    <img id="gambarGunung" 
                         src="https://placehold.co/600x450/cccccc/969696?text=Memuat+Gambar..." 
                         alt="Gambar Gunung" 
                         class="rounded-xl shadow-xl w-full h-auto object-cover mountain-image aspect-[4/3]"
                         onerror="this.onerror=null; this.src='https://placehold.co/600x450/e0e0e0/757575?text=Gambar+Tidak+Tersedia';">
                </div>
                <div class="md:col-span-3 prose-custom max-w-none">
                    <h3 class="text-2xl font-semibold mb-3">📜 Detail Gunung:</h3>
                    <p class="text-base"><strong><i class="fas fa-map-marker-alt mr-2 text-blue-600"></i>Lokasi:</strong> <span id="lokasiGunung" class="text-gray-700"></span></p>
                    <p class="text-base"><strong><i class="fas fa-mountain mr-2 text-blue-600"></i>Ketinggian:</strong> <span id="ketinggianGunung" class="text-gray-700"></span></p>
                    <p class="text-base"><strong><i class="fas fa-motorcycle mr-2 text-blue-600"></i>Estimasi Perjalanan dari UMP ke Basecamp (Motor):</strong> <span id="estimasiPerjalanan" class="text-gray-700"></span></p>
                    <p class="text-base"><strong><i class="fas fa-campground mr-2 text-blue-600"></i>Basecamp Umum:</strong> <span id="basecampGunung" class="text-gray-700"></span></p>
                </div>
            </div>

            <hr class="my-8 border-gray-300">

            <div class="grid md:grid-cols-2 gap-x-10 gap-y-8">
                <div class="prose-custom max-w-none">
                    <h3 class="text-2xl font-semibold mb-4"><i class="fas fa-briefcase mr-2"></i>Logistik & Peralatan Umum:</h3>
                    <p class="text-xs italic text-gray-600 mb-4"><strong>Catatan Penting:</strong> Selalu sesuaikan daftar ini dengan spesifikasi gunung, durasi pendakian, cuaca, dan kebutuhan pribadi Anda. Keselamatan adalah prioritas!</p>
                    
                    <h4>Peralatan Pribadi Wajib:</h4>
                    <ul>
                        <li>Carrier/Ransel (sesuai durasi)</li>
                        <li>Tenda & Flysheet (tahan air, sesuai kapasitas)</li>
                        <li>Sleeping bag (comfort rating sesuai suhu) & Matras</li>
                        <li>Jaket gunung (windproof, waterproof, insulasi)</li>
                        <li>Pakaian trekking (quick-dry, lapisan dasar, tengah, luar)</li>
                        <li>Pakaian tidur hangat & Kaos kaki cadangan (min. 3)</li>
                        <li>Jas hujan/Ponco setelan (atas-bawah lebih baik)</li>
                        <li>Sepatu trekking (sudah break-in, anti slip) & Sandal</li>
                        <li>Headlamp/Senter & Baterai cadangan berlimpah</li>
                        <li>Alat masak (kompor, nesting, gas) & Alat makan pribadi</li>
                        <li>Botol minum/Water bladder (total min. 2-3L)</li>
                        <li>Topi/Kupluk, Sarung tangan, Buff/Masker</li>
                        <li>Obat-obatan pribadi & P3K kit lengkap</li>
                        <li>Identitas (KTP/SIM) & Uang tunai secukupnya</li>
                        <li>Trash bag besar (bawa turun semua sampah!)</li>
                        <li>Peluit & Navigasi dasar (peta, kompas/GPS jika mampu)</li>
                    </ul>

                    <h4>Logistik & Peralatan Kelompok (Jika Ada):</h4>
                    <ul>
                        <li>Logistik makanan utama (kalori cukup, mudah dimasak)</li>
                        <li>Flysheet tambahan/Bivak darurat</li>
                        <li>Alat komunikasi (HT/Telepon Satelit jika perlu)</li>
                        <li>Perlengkapan perbaikan (tali, lakban, multitools)</li>
                    </ul>
                </div>

                <div class="prose-custom max-w-none">
                    <h3 class="text-2xl font-semibold mb-4"><i class="fas fa-wallet mr-2"></i>Estimasi Biaya Umum (Per Orang):</h3>
                    <p class="text-xs italic text-gray-600 mb-4"><strong>Disclaimer:</strong> Ini adalah perkiraan kasar. Biaya aktual sangat bervariasi. Lakukan riset detail untuk gunung tujuan!</p>
                    <ul>
                        <li>Transportasi (Bensin & Parkir Motor dari UMP): Rp 50.000 - Rp 300.000+</li>
                        <li>Simaksi/Tiket Masuk: Rp 20.000 - Rp 100.000+ (Taman Nasional/Wisata Alam bisa lebih)</li>
                        <li>Logistik Makanan & Minuman: Rp 150.000 - Rp 400.000 (2-3 hari)</li>
                        <li>Sewa Alat (jika perlu, per hari):
                            <ul>
                                <li>Tenda (2-3P): Rp 35rb - Rp 70rb</li>
                                <li>Carrier: Rp 30rb - Rp 60rb</li>
                                <li>SB & Matras: Rp 20rb - Rp 40rb</li>
                            </ul>
                        </li>
                        <li>Jasa Porter/Guide (opsional): Rp 400rb - Rp 800rb+/hari (dibagi tim)</li>
                        <li>Donasi Basecamp/Biaya Lain: Rp 10rb - Rp 50rb</li>
                        <li>Dana Darurat: Rp 100.000 - Rp 250.000</li>
                    </ul>
                    <p class="font-semibold mt-4 text-gray-700">Total Estimasi Kasar (Mandiri, Sewa Minim): Rp 300.000 - Rp 1.000.000+</p>
                </div>
            </div>
        </div>
    </main>

    <footer class="footer-credit text-white text-center py-5 mt-12">
        <p class="text-sm">Aplikasi Pendakian Acak ini Dibuat & Dipersembahkan oleh: <span class="font-bold text-lg">Jejak Kampus</span></p>
        <p class="text-xs opacity-80">&copy; <span id="tahun"></span> Hak Cipta Dilindungi.</p>
    </footer>

    <script>
        const mountains = [
            // Data gunung di sini (saya akan menggunakan data dari V2, dan mencoba mencari gambar yang lebih baik jika memungkinkan)
            // Saya akan mencoba mencari gambar dari Unsplash yang lebih spesifik jika memungkinkan
            { name: "Gunung Gede", location: "Jawa Barat (TNGGP: Cianjur, Sukabumi, Bogor)", height: "2,958 mdpl", travelTime: "7-9 jam", basecamps: "Cibodas, Gunung Putri, Salabintana", image: "https://images.unsplash.com/photo-1508292398943-332589c17192?q=80&w=870&auto=format&fit=crop" }, // Gede Pangrango National Park
            { name: "Gunung Pangrango", location: "Jawa Barat (TNGGP: Cianjur, Sukabumi, Bogor)", height: "3,019 mdpl", travelTime: "7-9 jam", basecamps: "Cibodas (via Kandang Badak)", image: "https://images.unsplash.com/photo-1618049907908-34999693013f?q=80&w=870&auto=format&fit=crop" }, // Specific Pangrango
            { name: "Gunung Ciremai", location: "Jawa Barat (TNGC: Kuningan, Majalengka)", height: "3,078 mdpl", travelTime: "4-5 jam", basecamps: "Apuy, Palutungan, Linggarjati, Linggasana", image: "https://images.unsplash.com/photo-1604872744159-b1c7eae20951?q=80&w=870&auto=format&fit=crop" }, // Ciremai
            { name: "Gunung Papandayan", location: "Jawa Barat (TWA: Garut)", height: "2,665 mdpl", travelTime: "7-8 jam", basecamps: "Camp David (Cisurupan)", image: "https://images.unsplash.com/photo-1589338039799-000369002074?q=80&w=870&auto=format&fit=crop" }, // Papandayan Crater
            { name: "Gunung Cikuray", location: "Jawa Barat (Garut)", height: "2,821 mdpl", travelTime: "7-8 jam", basecamps: "Pemancar (Cilawu), Bayongbong, Cikajang", image: "https://images.unsplash.com/photo-1627859925968-a300676a8f9f?q=80&w=870&auto=format&fit=crop" }, // Cikuray
            { name: "Gunung Slamet", location: "Jawa Tengah (Purbalingga, Banyumas, Brebes, Tegal, Pemalang)", height: "3,428 mdpl", travelTime: "1.5-2.5 jam", basecamps: "Bambangan (Purbalingga), Guci (Tegal), Kaliwadas (Brebes)", image: "https://images.unsplash.com/photo-1609497999380-382752e9c97c?q=80&w=870&auto=format&fit=crop" }, // Slamet
            { name: "Gunung Sindoro", location: "Jawa Tengah (Temanggung, Wonosobo)", height: "3,153 mdpl", travelTime: "3-4 jam", basecamps: "Kledung (Temanggung), Sigedang (Wonosobo), Alang-alang Sewu (Wonosobo)", image: "https://images.unsplash.com/photo-1604925796031-27c799079960?q=80&w=870&auto=format&fit=crop" }, // Sindoro (sudah ada)
            { name: "Gunung Sumbing", location: "Jawa Tengah (Magelang, Temanggung, Wonosobo)", height: "3,371 mdpl", travelTime: "3-4 jam", basecamps: "Garung (Wonosobo), Bowongso (Wonosobo), Kaliangkrik (Magelang), Butuh (Magelang - Nepal van Java)", image: "https://images.unsplash.com/photo-1593323084867-73708839d3a9?q=80&w=870&auto=format&fit=crop" }, // Sumbing (sudah ada, mungkin tertukar dengan Sindoro sebelumnya)
            { name: "Gunung Merbabu", location: "Jawa Tengah (TNGMb: Magelang, Boyolali, Semarang)", height: "3,145 mdpl", travelTime: "3.5-5 jam", basecamps: "Selo (Boyolali), Suwanting (Magelang), Wekas (Magelang), Cuntel (Semarang), Thekelan (Semarang)", image: "https://images.unsplash.com/photo-1579493001936-310f736b0155?q=80&w=870&auto=format&fit=crop" }, // Merbabu (sudah ada)
            { name: "Gunung Prau", location: "Jawa Tengah (Dataran Tinggi Dieng: Wonosobo, Kendal, Batang)", height: "2,590 mdpl", travelTime: "3.5-4.5 jam", basecamps: "Patak Banteng (Wonosobo), Dieng (Wonosobo), Kalilembu (Wonosobo), Wates (Temanggung)", image: "https://images.unsplash.com/photo-1580777207895-60309a057c0a?q=80&w=870&auto=format&fit=crop" }, // Prau Dieng
            { name: "Gunung Ungaran", location: "Jawa Tengah (Kab. Semarang)", height: "2,050 mdpl", travelTime: "4-5 jam", basecamps: "Mawar (Jimbaran), Promasan (Ngesrep Balong - via Kebun Teh Medini)", image: "https://images.unsplash.com/photo-1622611417100-996100038817?q=80&w=870&auto=format&fit=crop" }, // Ungaran
            { name: "Gunung Andong", location: "Jawa Tengah (Magelang)", height: "1,726 mdpl", travelTime: "3-4 jam", basecamps: "Sawit (Ngablak), Pendem (Gogik)", image: "https://images.unsplash.com/photo-1606047035060-adaa517bf998?q=80&w=870&auto=format&fit=crop" }, // Andong
            { name: "Gunung Telomoyo", location: "Jawa Tengah (Kab. Semarang, Magelang)", height: "1,894 mdpl", travelTime: "3.5-4.5 jam", basecamps: "Dalangan (bisa naik motor/mobil sampai area dekat puncak), Pagergedog (jalur pendakian)", image: "https://images.unsplash.com/photo-1621905963436-aff0de8c65c6?q=80&w=870&auto=format&fit=crop" }, // Telomoyo (sudah ada)
            { name: "Gunung Semeru", location: "Jawa Timur (TNBTS: Malang, Lumajang)", height: "3,676 mdpl", travelTime: "9-11 jam", basecamps: "Ranu Pani (Lumajang)", image: "https://images.unsplash.com/photo-1588659820034-3199003ba86a?q=80&w=870&auto=format&fit=crop" }, // Semeru (sudah ada)
            { name: "Gunung Arjuno", location: "Jawa Timur (Tahura R. Soerjo: Malang, Pasuruan)", height: "3,339 mdpl", travelTime: "8-10 jam", basecamps: "Tretes (Pasuruan), Lawang (Malang), Sumberbrantas (Batu), Purwosari (Pasuruan)", image: "https://images.unsplash.com/photo-1608280044380-ccc350f7f720?q=80&w=870&auto=format&fit=crop" }, // Arjuno (sudah ada)
            { name: "Gunung Welirang", location: "Jawa Timur (Tahura R. Soerjo: Malang, Pasuruan, Mojokerto)", height: "3,156 mdpl", travelTime: "8-10 jam", basecamps: "Tretes (Pasuruan), Cangar (Batu), Pacet (Mojokerto)", image: "https://images.unsplash.com/photo-1612106912139-7a9914097403?q=80&w=870&auto=format&fit=crop" }, // Welirang (sudah ada)
            { name: "Gunung Raung", location: "Jawa Timur (Banyuwangi, Bondowoso, Jember)", height: "3,332 mdpl (Puncak Sejati)", travelTime: "11-13 jam", basecamps: "Kalibaru (Banyuwangi - jalur ekstrem), Sumberwringin (Bondowoso)", image: "https://images.unsplash.com/photo-1604733637885-79f076f8198b?q=80&w=870&auto=format&fit=crop" }, // Raung (sudah ada)
            { name: "Gunung Argopuro", location: "Jawa Timur (Suaka Margasatwa Dataran Tinggi Hyang: Probolinggo, Situbondo, Jember)", height: "3,088 mdpl", travelTime: "10-12 jam", basecamps: "Baderan (Situbondo), Bremi (Probolinggo)", image: "https://images.unsplash.com/photo-1620201904007-379690998637?q=80&w=870&auto=format&fit=crop" }, // Argopuro (sudah ada)
            { name: "Kawah Ijen", location: "Jawa Timur (TWA: Banyuwangi, Bondowoso)", height: "2,799 mdpl (bibir kaldera)", travelTime: "12-14 jam", basecamps: "Paltuding (Bondowoso/Banyuwangi)", image: "https://images.unsplash.com/photo-1528428054573-8c6091cb775c?q=80&w=870&auto=format&fit=crop" }, // Ijen (sudah ada)
            { name: "Gunung Penanggungan", location: "Jawa Timur (Mojokerto, Pasuruan)", height: "1,653 mdpl", travelTime: "8-9 jam", basecamps: "Tamiajeng (Trawas), Jolotundo (Trawas), Ngoro (Mojokerto)", image: "https://images.unsplash.com/photo-1611127808394-9911023e7c77?q=80&w=870&auto=format&fit=crop" }, // Penanggungan (sudah ada)
            { name: "Gunung Lawu", location: "Perbatasan Jawa Tengah & Jawa Timur (Karanganyar, Magetan)", height: "3,265 mdpl", travelTime: "5-6 jam", basecamps: "Cemoro Sewu (Magetan), Cemoro Kandang (Karanganyar), Candi Cetho (Karanganyar)", image: "https://images.unsplash.com/photo-1597463109758-14595181aa9a?q=80&w=870&auto=format&fit=crop" }, // Lawu (sudah ada)
            { name: "Gunung Butak", location: "Jawa Timur (Malang, Blitar)", height: "2,868 mdpl", travelTime: "8-10 jam", basecamps: "Sirah Kencong (Blitar - via Kebun Teh), Panderman (Batu)", image: "https://images.unsplash.com/photo-1603764341986-c597853a2053?q=80&w=870&auto=format&fit=crop" } // Butak (mencari gambar baru)
        ];


        const acakButton = document.getElementById('acakButton');
        const hasilGunungDiv = document.getElementById('hasilGunung');
        const loadingIndicator = document.getElementById('loadingIndicator');

        const namaGunungEl = document.getElementById('namaGunung');
        const lokasiGunungEl = document.getElementById('lokasiGunung');
        const ketinggianGunungEl = document.getElementById('ketinggianGunung');
        const estimasiPerjalananEl = document.getElementById('estimasiPerjalanan');
        const basecampGunungEl = document.getElementById('basecampGunung');
        const gambarGunungEl = document.getElementById('gambarGunung');
        
        document.getElementById('tahun').textContent = new Date().getFullYear();

        acakButton.addEventListener('click', () => {
            hasilGunungDiv.classList.add('hidden');
            loadingIndicator.classList.remove('hidden');
            acakButton.disabled = true;
            acakButton.classList.add('opacity-50', 'cursor-not-allowed');

            // Animasi scroll ke loading indicator jika perlu
            loadingIndicator.scrollIntoView({ behavior: 'smooth', block: 'center' });

            setTimeout(() => {
                const randomIndex = Math.floor(Math.random() * mountains.length);
                const selectedMountain = mountains[randomIndex];

                namaGunungEl.textContent = selectedMountain.name;
                lokasiGunungEl.textContent = selectedMountain.location;
                ketinggianGunungEl.textContent = selectedMountain.height;
                estimasiPerjalananEl.textContent = selectedMountain.travelTime;
                basecampGunungEl.textContent = selectedMountain.basecamps;
                
                // Log URL gambar ke konsol untuk debugging
                console.log("Selected mountain image URL:", selectedMountain.image); 

                gambarGunungEl.src = selectedMountain.image || 'https://placehold.co/600x450/e0e0e0/757575?text=Gambar+Tidak+Tersedia';
                gambarGunungEl.alt = `Foto Pemandangan ${selectedMountain.name}`;

                loadingIndicator.classList.add('hidden');
                hasilGunungDiv.classList.remove('hidden');
                
                acakButton.disabled = false;
                acakButton.classList.remove('opacity-50', 'cursor-not-allowed');

                hasilGunungDiv.scrollIntoView({ behavior: 'smooth', block: 'start' });
            }, 1500); // Durasi loading sedikit lebih lama untuk efek
        });
    </script>
</body>
</html>
