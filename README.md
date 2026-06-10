# CROWDIT2026_-tim-2-asvocs-2-
web yang digunakan untuk mempelajari berbagai budaya yang berisi berbagai macam fakta,musik, dan lain-lain
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Sora Budaya Nusantara - Edukasi Budaya Indonesia</title>
    <link href="https://fonts.googleapis.com/css2?family=Plus+Jakarta+Sans:wght@400;600;700;800&display=swap" rel="stylesheet">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    
    <style>
        :root {
            --primary: #B22222; /* Merah Marun */
            --secondary: #D4AF37; /* Emas Kebudayaan */
            --accent: #8B4513; /* Coklat Tanah */
            --bg-light: #FDFBF7;
            --surface-light: #FFFFFF;
            --text-light: #2C3E50;
            --shadow: rgba(0, 0, 0, 0.1);
            
            /* Dark Mode Variables default */
            --bg: var(--bg-light);
            --surface: var(--surface-light);
            --text: var(--text-light);
            --transition: all 0.3s ease;
        }

        [data-theme="dark"] {
            --bg: #1A1A1A;
            --surface: #2D2D2D;
            --text: #F5F5F5;
            --shadow: rgba(0, 0, 0, 0.5);
        }

        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
            font-family: 'Plus Jakarta Sans', sans-serif;
        }

        body {
            background-color: var(--bg);
            color: var(--text);
            transition: var(--transition);
            line-height: 1.6;
        }

        /* --- NAVIGATION --- */
        nav {
            background-color: var(--surface);
            box-shadow: 0 2px 10px var(--shadow);
            position: fixed;
            width: 100%;
            top: 0;
            z-index: 1000;
            transition: var(--transition);
        }

        .nav-container {
            max-width: 1200px;
            margin: 0 auto;
            padding: 1rem 2rem;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-weight: 800;
            font-size: 1.4rem;
            color: var(--primary);
            display: flex;
            align-items: center;
            gap: 10px;
        }

        .logo span {
            color: var(--secondary);
        }

        .nav-actions {
            display: flex;
            align-items: center;
            gap: 1.5rem;
        }

        .search-box {
            position: relative;
        }

        .search-box input {
            padding: 0.5rem 1rem 0.5rem 2.5rem;
            border-radius: 20px;
            border: 1px solid #ddd;
            background: var(--bg);
            color: var(--text);
            outline: none;
        }

        .search-box i {
            position: absolute;
            left: 10px;
            top: 50%;
            transform: translateY(-50%);
            color: #888;
        }

        .theme-toggle {
            background: none;
            border: none;
            color: var(--text);
            font-size: 1.2rem;
            cursor: pointer;
        }

        /* --- HERO SECTION --- */
        .hero {
            padding: 8rem 2rem 4rem;
            text-align: center;
            background: linear-gradient(rgba(178, 34, 34, 0.8), rgba(139, 69, 19, 0.9)), url('https://images.unsplash.com/photo-1590523277543-a94d2e4eb00b?auto=format&fit=crop&w=1200&q=80');
            background-size: cover;
            background-position: center;
            background-attachment: fixed;
            color: white;
        }

        .hero h1 {
            font-size: 3.5rem;
            font-weight: 800;
            margin-bottom: 1rem;
            text-shadow: 2px 2px 4px rgba(0,0,0,0.5);
        }

        .hero p {
            font-size: 1.2rem;
            margin-bottom: 2rem;
            color: #f5f5f5;
        }

        .btn-explore {
            background-color: var(--secondary);
            color: #000;
            padding: 0.8rem 2rem;
            border: none;
            border-radius: 30px;
            font-weight: 700;
            font-size: 1rem;
            cursor: pointer;
            transition: var(--transition);
            text-decoration: none;
            display: inline-block;
        }

        .btn-explore:hover {
            background-color: #fff;
            transform: translateY(-3px);
            box-shadow: 0 4px 15px rgba(0,0,0,0.2);
        }

        /* --- MAIN LAYOUT --- */
        .main-container {
            max-width: 1200px;
            margin: 2rem auto;
            display: grid;
            grid-template-columns: 280px 1fr;
            gap: 2rem;
            padding: 0 2rem;
        }

        /* Sidebar Provinsi */
        .sidebar {
            background-color: var(--surface);
            padding: 1.5rem;
            border-radius: 15px;
            box-shadow: 0 4px 6px var(--shadow);
            height: fit-content;
            position: sticky;
            top: 90px;
        }

        .sidebar h3 {
            margin-bottom: 1rem;
            color: var(--primary);
            border-bottom: 2px solid var(--secondary);
            padding-bottom: 0.5rem;
        }

        .provinsi-list {
            list-style: none;
            max-height: 400px;
            overflow-y: auto;
            padding-right: 5px;
        }

        .provinsi-list::-webkit-scrollbar {
            width: 5px;
        }
        .provinsi-list::-webkit-scrollbar-thumb {
            background: var(--secondary);
            border-radius: 10px;
        }

        .provinsi-item {
            padding: 0.75rem 1rem;
            margin-bottom: 0.5rem;
            border-radius: 8px;
            cursor: pointer;
            transition: var(--transition);
            font-weight: 600;
        }

        .provinsi-item:hover, .provinsi-item.active {
            background-color: var(--primary);
            color: white;
        }

        /* Content Area */
        .content-area {
            animation: fadeIn 0.5s ease-in-out;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        .section-card {
            background-color: var(--surface);
            padding: 2rem;
            border-radius: 15px;
            box-shadow: 0 4px 6px var(--shadow);
            margin-bottom: 2rem;
        }

        .section-title {
            color: var(--primary);
            margin-bottom: 1.5rem;
            font-size: 1.8rem;
            display: flex;
            align-items: center;
            gap: 10px;
            border-left: 5px solid var(--secondary);
            padding-left: 10px;
        }

        /* --- ARTIKEL BUDAYA --- */
        .article-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
            gap: 1.5rem;
            margin-top: 1.5rem;
        }

        .article-subcard {
            background: var(--bg);
            padding: 1.2rem;
            border-radius: 10px;
            border-top: 4px solid var(--accent);
        }

        .article-subcard h4 {
            color: var(--accent);
            margin-bottom: 0.5rem;
        }

        /* --- GALERI GAMBAR --- */
        .gallery-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(200px, 1fr));
            gap: 1rem;
        }

        .gallery-item {
            position: relative;
            border-radius: 10px;
            overflow: hidden;
            cursor: pointer;
            height: 150px;
        }

        .gallery-item img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            transition: var(--transition);
        }

        .gallery-item:hover img {
            transform: scale(1.1);
        }

        .gallery-overlay {
            position: absolute;
            bottom: 0;
            left: 0;
            right: 0;
            background: linear-gradient(transparent, rgba(0,0,0,0.8));
            color: white;
            padding: 0.8rem;
            font-size: 0.9rem;
            opacity: 0;
            transition: var(--transition);
        }

        .gallery-item:hover .gallery-overlay {
            opacity: 1;
        }

        /* --- MULTIMEDIA (VIDEO & AUDIO) --- */
        .media-container {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1.5rem;
        }

        @media (max-width: 768px) {
            .media-container { grid-template-columns: 1fr; }
            .main-container { grid-template-columns: 1fr; }
            .hero h1 { font-size: 2.3rem; }
        }

        .video-wrapper {
            position: relative;
            padding-bottom: 56.25%; /* 16:9 */
            height: 0;
            border-radius: 10px;
            overflow: hidden;
        }

        .video-wrapper iframe {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            border: none;
        }

        .audio-player-card {
            background: var(--bg);
            padding: 1.5rem;
            border-radius: 10px;
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            text-align: center;
        }

        .audio-controls {
            display: flex;
            align-items: center;
            gap: 1rem;
            margin-top: 1rem;
            width: 100%;
        }

        .btn-audio {
            background: var(--primary);
            color: white;
            border: none;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            cursor: pointer;
            font-size: 1.2rem;
        }

        .audio-progress {
            flex-grow: 1;
            height: 6px;
            background: #ddd;
            border-radius: 3px;
            cursor: pointer;
            position: relative;
        }

        .audio-progress-bar {
            height: 100%;
            background: var(--secondary);
            width: 0%;
            border-radius: 3px;
        }

        /* --- INTERACTIVE QUIZ --- */
        .quiz-container {
            background: var(--bg);
            padding: 1.5rem;
            border-radius: 10px;
        }

        .quiz-options {
            display: flex;
            flex-direction: column;
            gap: 0.8rem;
            margin: 1.5rem 0;
        }

        .option-btn {
            background: var(--surface);
            border: 2px solid #ddd;
            padding: 1rem;
            border-radius: 8px;
            cursor: pointer;
            text-align: left;
            font-weight: 600;
            color: var(--text);
            transition: var(--transition);
        }

        .option-btn:hover {
            border-color: var(--primary);
            background: rgba(178, 34, 34, 0.05);
        }

        .option-btn.correct {
            background-color: #2ecc71 !important;
            color: white;
            border-color: #2ecc71;
        }

        .option-btn.wrong {
            background-color: #e74c3c !important;
            color: white;
            border-color: #e74c3c;
        }

        .quiz-feedback {
            font-weight: 700;
            margin-top: 1rem;
            min-height: 24px;
        }

        /* --- LIGHTBOX MODAL --- */
        .lightbox {
            position: fixed;
            top: 0; left: 0; width: 100%; height: 100%;
            background: rgba(0,0,0,0.9);
            z-index: 2000;
            display: none;
            justify-content: center;
            align-items: center;
            flex-direction: column;
        }

        .lightbox img {
            max-width: 85%;
            max-height: 75%;
            border-radius: 5px;
            box-shadow: 0 0 20px rgba(255,255,255,0.2);
        }

        .lightbox-caption {
            color: white;
            margin-top: 1rem;
            font-size: 1.2rem;
            text-align: center;
        }

        .lightbox-close {
            position: absolute;
            top: 20px; right: 30px;
            color: white; font-size: 2.5rem; cursor: pointer;
        }

        footer {
            background-color: var(--accent);
            color: white;
            text-align: center;
            padding: 2rem;
            margin-top: 4rem;
        }
    </style>
</head>
<body>

    <div id="lightbox" class="lightbox">
        <span class="lightbox-close" onclick="closeLightbox()">&times;</span>
        <img id="lightbox-img" src="" alt="">
        <div id="lightbox-caption" class="lightbox-caption"></div>
    </div>

    <nav>
        <div class="nav-container">
            <div class="logo"><i class="fa-solid fa-gopuram"></i> Sora <span>Budaya</span></div>
            <div class="nav-actions">
                <div class="search-box">
                    <i class="fa-solid fa-magnifying-glass"></i>
                    <input type="text" id="provinsiSearch" placeholder="Cari provinsi..." onkeyup="searchProvinsi()">
                </div>
                <button class="theme-toggle" onclick="toggleTheme()" aria-label="Ganti Tema">
                    <i id="theme-icon" class="fa-solid fa-moon"></i>
                </button>
            </div>
        </div>
    </nav>

    <header class="hero">
        <h1>Sora Budaya Nusantara</h1>
        <p>“Jelajahi Sejarah dan Kekayaan Budaya Indonesia secara Interaktif”</p>
        <a href="#eksplorasi" class="btn-explore">Mulai Jelajah <i class="fa-solid fa-arrow-down"></i></a>
    </header>

    <main class="main-container" id="eksplorasi">
        
        <aside class="sidebar">
            <h3><i class="fa-solid fa-map"></i> Pilih Provinsi</h3>
            <ul class="provinsi-list" id="provinsiList">
                </ul>
        </aside>

        <section class="content-area">
            
            <div class="section-card">
                <h2 id="provinsiTitle" style="color: var(--primary); font-size: 2.5rem;">Memuat...</h2>
                <p id="provinsiDeskripsi" style="font-size: 1.1rem; margin-top: 0.5rem; color:#666;"></p>
            </div>

            <div class="section-card">
                <div class="section-title"><i class="fa-solid fa-book-open"></i> Artikel Kebudayaan</div>
                <div class="article-grid">
                    <div class="article-subcard">
                        <h4><i class="fa-solid fa-hourglass-half"></i> Sejarah Daerah</h4>
                        <p id="txt-sejarah">-</p>
                    </div>
                    <div class="article-subcard">
                        <h4><i class="fa-solid fa-users"></i> Tradisi & Adat</h4>
                        <p id="txt-tradisi">-</p>
                    </div>
                    <div class="article-subcard">
                        <h4><i class="fa-solid fa-scroll"></i> Filosofi Budaya</h4>
                        <p id="txt-filosofi">-</p>
                    </div>
                </div>
            </div>

            <div class="section-card">
                <div class="section-title"><i class="fa-solid fa-images"></i> Galeri Warisan Budaya</div>
                <div class="gallery-grid" id="galeri-container">
                    </div>
            </div>

            <div class="section-card">
                <div class="section-title"><i class="fa-solid fa-photo-film"></i> Media Pembelajaran</div>
                <div class="media-container">
                    <div>
                        <h4 style="margin-bottom:1rem;"><i class="fa-brands fa-youtube"></i> Dokumentasi Video</h4>
                        <div class="video-wrapper">
                            <iframe id="vid-frame" src="" allowfullscreen></iframe>
                        </div>
                    </div>
                    <div>
                        <h4 style="margin-bottom:1rem;"><i class="fa-solid fa-music"></i> Audio Lagu Daerah</h4>
                        <div class="audio-player-card">
                            <h3 id="audio-judul" style="color:var(--primary)">Lagu</h3>
                            <p style="font-size:0.9rem; margin-bottom:1rem;">Asal: <span id="audio-asal">-</span></p>
                            <audio id="audio-source" src=""></audio>
                            <div class="audio-controls">
                                <button class="btn-audio" id="btn-play-audio" onclick="toggleAudio()"><i class="fa-solid fa-play"></i></button>
                                <div class="audio-progress" onclick="setAudioProgress(event)">
                                    <div class="audio-progress-bar" id="audio-progress-bar"></div>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>

            <div class="section-card">
                <div class="section-title"><i class="fa-solid fa-brain"></i> Uji Kemampuan (Kuis Edukasi)</div>
                <div class="quiz-container">
                    <h3 id="quiz-question">Pertanyaan Kuis</h3>
                    <div class="quiz-options" id="quiz-options-container">
                        </div>
                    <div class="quiz-feedback" id="quiz-feedback"></div>
                </div>
            </div>

        </section>
    </main>

    <footer>
        <p>&copy; 2026 Sora Budaya Nusantara - Media Edukasi Sekolah Menengah & Umum.</p>
    </footer>

    <script>
        // DATA KONTEN MULTIMEDIA NUSANTARA
        const databaseBudaya = {
            "Jawa Barat": {
                deskripsi: "Tanah Pasundan yang kaya akan nilai tata krama, seni, dan harmoni alam.",
                sejarah: "Berakar kuat dari peninggalan Kerajaan Pajajaran yang dipimpin oleh Raja Prabu Siliwangi yang masyhur.",
                tradisi: "Upacara Seren Taun (syukuran hasil bumi) dan tradisi mapag sri saat menyambut panen padi.",
                filosofi: "'Silih Asih, Silih Asah, Silih Asuh' - Saling mengasihi, saling mencerdaskan, dan saling melindungi.",
                galeri: [
                    {img: "https://images.unsplash.com/photo-1542931287-023b922fa89b?auto=format&fit=crop&w=500&q=80", tag: "Rumah Adat: Kasepuhan Cirebon"},
                    {img: "https://images.unsplash.com/photo-1626125345510-4603468eedfb?auto=format&fit=crop&w=500&q=80", tag: "Alat Musik: Angklung Bambu"},
                    {img: "https://images.unsplash.com/photo-1578496479914-7ef3b0193be3?auto=format&fit=crop&w=500&q=80", tag: "Tarian: Tari Jaipong"}
                ],
                video: "https://www.youtube.com/embed/zH0F6A2p7pI", // Contoh Link Embed Edukasi Angklung/Jaipong
                audioJudul: "Manuk Dadali",
                audioSrc: "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3", // Demo audio file
                quiz: {
                    tanya: "Apakah nama filosofi hidup masyarakat Sunda untuk saling mengasihi?",
                    opsi: ["Silih Asih", "Rukun Agawe", "Bhinneka", "Maju Bersama"],
                    jawaban: 0
                }
            },
            "Bali": {
                deskripsi: "Pulau Dewata yang mendunia dengan keharmonisan adat Hindu dan keindahan estetikanya.",
                sejarah: "Sejarah budaya Bali berkembang pesat sejak runtuhnya Majapahit, memadukan tradisi lokal kuno Hindu-Sunda.",
                tradisi: "Upacara Ngaben (kremasi jenazah), Hari Raya Nyepi, dan pawai Ogoh-ogoh.",
                filosofi: "'Tri Hita Karana' - Menjaga keharmonisan antara manusia dengan Tuhan, sesama, dan alam lingkungan.",
                galeri: [
                    {img: "https://images.unsplash.com/photo-1537996194471-e657df975ab4?auto=format&fit=crop&w=500&q=80", tag: "Pura & Rumah Adat Bali"},
                    {img: "https://images.unsplash.com/photo-1604999333679-b86d54738315?auto=format&fit=crop&w=500&q=80", tag: "Tarian: Tari Kecak Balinesia"}
                ],
                video: "https://www.youtube.com/embed/NCzzreR1fys", 
                audioJudul: "Mejangeran",
                audioSrc: "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-2.mp3",
                quiz: {
                    tanya: "Konsep filosofi keselarasan hubungan manusia, alam, dan Tuhan di Bali disebut?",
                    opsi: ["Tat Twam Asi", "Tri Hita Karana", "Krama Bali", "Subak"],
                    jawaban: 1
                }
            },
            "Yogyakarta": {
                deskripsi: "Daerah Istimewa penjaga poros utama peradaban kultur klasik Jawa Tengah.",
                sejarah: "Lahir dari Perjanjian Giyanti 1755, membentuk Kasultanan Ngayogyakarta Hadiningrat yang bertahan kuat hingga saat ini.",
                tradisi: "Sekaten, Grebeg Syawal, dan Labuhan Merapi.",
                filosofi: "'Hamemayu Hayuning Bawana' - Memperindah keindahan dunia (menjaga kelestarian semesta).",
                galeri: [
                    {img: "https://images.unsplash.com/photo-1601999109332-542b18dbec57?auto=format&fit=crop&w=500&q=80", tag: "Keraton Yogyakarta"},
                    {img: "https://images.unsplash.com/photo-1571731956622-7a7d8b5b995c?auto=format&fit=crop&w=500&q=80", tag: "Kerajinan: Wayang Kulit Kulit"}
                ],
                video: "https://www.youtube.com/embed/kWvE8A37g5U",
                audioJudul: "Suwe Ora Jamu",
                audioSrc: "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-3.mp3",
                quiz: {
                    tanya: "Kerajaan awal pembentuk Kesultanan Yogyakarta pasca Perjanjian Giyanti adalah?",
                    opsi: ["Kalingga", "Singasari", "Mataram Islam", "Pajajaran"],
                    jawaban: 2
                }
            },
            "Sumatera Barat": {
                deskripsi: "Bumi Minangkabau yang menganut sistem matrilineal yang unik dan relasi adat-agama yang kuat.",
                sejarah: "Kawasan bersejarah pusat kekuasaan Kerajaan Pagaruyung yang sarat dengan adat maritim dan agraris tinggi.",
                tradisi: "Tradisi Merantau, Upacara Tabuik, dan seni bela diri Silat Minang.",
                filosofi: "'Adat Basandi Syarak, Syarak Basandi Kitabullah' - Adat bersendikan agama Islam, agama berdasar Al-Qur'an.",
                galeri: [
                    {img: "https://images.unsplash.com/photo-1629115915542-690db2077e36?auto=format&fit=crop&w=500&q=80", tag: "Rumah Gadang Minangkabau"},
                    {img: "https://images.unsplash.com/photo-1534001265532-393289eb8a55?auto=format&fit=crop&w=500&q=80", tag: "Tarian: Tari Piring Tradisional"}
                ],
                video: "https://www.youtube.com/embed/Am_r6fF6Pzo",
                audioJudul: "Kampuang Nan Jauh Di Mato",
                audioSrc: "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-4.mp3",
                quiz: {
                    tanya: "Sistem kekerabatan yang ditarik berdasarkan garis keturunan ibu di Minangkabau disebut?",
                    opsi: ["Patrilineal", "Matrilineal", "Bilaternal", "Kolektif"],
                    jawaban: 1
                }
            }
        };

        // Daftar Semua Provinsi sesuai spesifikasi fitur nomor 2
        const listProvinsi = [
            "Aceh", "Sumatera Utara", "Sumatera Barat", "Jawa Barat", "Jawa Tengah", 
            "Yogyakarta", "Jawa Timur", "Bali", "NTB / NTT", "Kalimantan", "Sulawesi", "Papua"
        ];

        let activeProvinsi = "Jawa Barat";
        const audioPlayer = document.getElementById('audio-source');
        let isPlaying = false;

        // INITIALIZER APP
        window.addEventListener('DOMContentLoaded', () => {
            buildSidebar();
            loadProvinsiData(activeProvinsi);

            // Audio Player Event
            audioPlayer.addEventListener('timeupdate', () => {
                const pct = (audioPlayer.currentTime / audioPlayer.duration) * 100;
                document.getElementById('audio-progress-bar').style.width = `${pct}%`;
            });
        });

        // GENERATE SIDEBAR LIST
        function buildSidebar() {
            const listContainer = document.getElementById('provinsiList');
            listContainer.innerHTML = '';
            listProvinsi.forEach(prov => {
                const li = document.createElement('li');
                li.className = `provinsi-item ${prov === activeProvinsi ? 'active' : ''}`;
                li.innerHTML = `<i class="fa-solid fa-location-dot"></i> ${prov}`;
                li.onclick = () => switchProvinsi(prov);
                listContainer.appendChild(li);
            });
        }

        // PROVINSI SWITCHER ENGINE
        function switchProvinsi(provinsiName) {
            // Berhenti memutar lagu dari provinsi sebelumnya jika sedang berjalan
            if(isPlaying) toggleAudio();

            activeProvinsi = provinsiName;
            
            // Update UI Active Sidebar
            document.querySelectorAll('.provinsi-item').forEach(item => {
                if(item.textContent.trim() === provinsiName) item.classList.add('active');
                else item.classList.remove('active');
            });

            // Trigger transisi animasi konten
            const contentArea = document.querySelector('.content-area');
            contentArea.style.animation = 'none';
            setTimeout(() => contentArea.style.animation = 'fadeIn 0.5s ease-in-out', 10);

            loadProvinsiData(provinsiName);
        }

        // LOAD DATA DYNAMICALLY
        function loadProvinsiData(name) {
            const titleEl = document.getElementById('provinsiTitle');
            const deskripsiEl = document.getElementById('provinsiDeskripsi');
            const sejarahEl = document.getElementById('txt-sejarah');
            const tradisiEl = document.getElementById('txt-tradisi');
            const filosofiEl = document.getElementById('txt-filosofi');
            const galeriContainer = document.getElementById('galeri-container');
            const videoFrame = document.getElementById('vid-frame');
            
            // Jika data belum diinput lengkap di database, berikan template fallback otomatis
            const data = databaseBudaya[name] || {
                deskripsi: `Kumpulan kekayaan kultur, suku, seni musik dan tari dari wilayah ${name}.`,
                sejarah: `Data sejarah mendalam untuk wilayah ${name} sedang dalam proses verifikasi tim kurator museum edukasi nasional.`,
                tradisi: `Berbagai ragam adat istiadat khas yang diwariskan turun temurun oleh leluhur di ${name}.`,
                filosofi: `Nilai-nilai gotong royong dan ketuhanan universal masyarakat daerah ${name}.`,
                galeri: [{img: "https://images.unsplash.com/photo-1585409677983-0f6c41ca9c3b?auto=format&fit=crop&w=500&q=80", tag: "Karya Seni Kebudayaan Nusantara"}],
                video: "https://www.youtube.com/embed/zH0F6A2p7pI",
                audioJudul: "Lagu Tradisional " + name,
                audioSrc: "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3",
                quiz: {
                    tanya: `Dimanakah letak wilayah geografis provinsi ${name} di peta Negara Kesatuan Republik Indonesia?`,
                    opsi: ["Gugusan Kepulauan Nusantara", "Luar Asia Tenggara", "Eropa Barat", "Amerika Pasifik"],
                    jawaban: 0
                }
            };

            // Pasang Teks Konten
            titleEl.textContent = name;
            deskripsiEl.textContent = data.deskripsi;
            sejarahEl.textContent = data.sejarah;
            tradisiEl.textContent = data.tradisi;
            filosofiEl.textContent = data.filosofi;

            // Render Galeri Gambar (Lightbox)
            galeriContainer.innerHTML = '';
            data.galeri.forEach(item => {
                const div = document.createElement('div');
                div.className = 'gallery-item';
                div.onclick = () => openLightbox(item.img, item.tag);
                div.innerHTML = `
                    <img src="${item.img}" alt="${item.tag}">
                    <div class="gallery-overlay"><i class="fa-solid fa-magnifying-glass-plus"></i> ${item.tag}</div>
                `;
                galeriContainer.appendChild(div);
            });

            // Set Video Embed & Audio Info
            videoFrame.src = data.video;
            document.getElementById('audio-judul').textContent = data.audioJudul;
            document.getElementById('audio-asal').textContent = name;
            audioPlayer.src = data.audioSrc;
            document.getElementById('audio-progress-bar').style.width = '0%';

            // Render Kuis
            loadQuiz(data.quiz);
        }

        // LIVE QUIZ ENGINE
        function loadQuiz(quizData) {
            const qQuestion = document.getElementById('quiz-question');
            const qOptionsContainer = document.getElementById('quiz-options-container');
            const qFeedback = document.getElementById('quiz-feedback');

            qQuestion.textContent = quizData.tanya;
            qFeedback.textContent = '';
            qOptionsContainer.innerHTML = '';

            quizData.opsi.forEach((opt, index) => {
                const btn = document.createElement('button');
                btn.className = 'option-btn';
                btn.textContent = `${String.fromCharCode(65 + index)}. ${opt}`;
                btn.onclick = () => checkQuizAnswer(index, quizData.jawaban, btn);
                qOptionsContainer.appendChild(btn);
            });
        }

        function checkQuizAnswer(selectedIndex, correctIndex, selectedButton) {
            const buttons = document.querySelectorAll('.option-btn');
            const feedback = document.getElementById('quiz-feedback');
            
            // Disable all buttons after choice
            buttons.forEach(btn => btn.disabled = true);

            if (selectedIndex === correctIndex) {
                selectedButton.classList.add('correct');
                feedback.innerHTML = `<span style="color:#2ecc71"><i class="fa-solid fa-circle-check"></i> Hebat! Jawaban kamu benar!</span>`;
            } else {
                selectedButton.classList.add('wrong');
                buttons[correctIndex].classList.add('correct'); // Tunjukkan jawaban yang benar
                feedback.innerHTML = `<span style="color:#e74c3c"><i class="fa-solid fa-circle-xmark"></i> Kurang tepat, mari pelajari artikel di atas lagi ya!</span>`;
            }
        }

        // SEARCH PROVINSI SIDEBAR
        function searchProvinsi() {
            const input = document.getElementById('provinsiSearch').value.toLowerCase();
            const items = document.querySelectorAll('.provinsi-item');

            items.forEach(item => {
                const text = item.textContent.toLowerCase();
                if(text.includes(input)) {
                    item.style.display = "block";
                } else {
                    item.style.display = "none";
                }
            });
        }

        // DARK MODE / LIGHT MODE TOGGLE
        function toggleTheme() {
            const body = document.documentElement;
            const currentTheme = body.getAttribute('data-theme');
            const icon = document.getElementById('theme-icon');

            if (currentTheme === 'dark') {
                body.removeAttribute('data-theme');
                icon.className = 'fa-solid fa-moon';
            } else {
                body.setAttribute('data-theme', 'dark');
                icon.className = 'fa-solid fa-sun';
            }
        }

        // AUDIO CONTROL
        function toggleAudio() {
            const btn = document.getElementById('btn-play-audio');
            if (isPlaying) {
                audioPlayer.pause();
                btn.innerHTML = '<i class="fa-solid fa-play"></i>';
                isPlaying = false;
            } else {
                audioPlayer.play();
                btn.innerHTML = '<i class="fa-solid fa-pause"></i>';
                isPlaying = true;
            }
        }

        function setAudioProgress(e) {
            const width = e.currentTarget.clientWidth;
            const clickX = e.offsetX;
            const duration = audioPlayer.duration;
            if (duration) {
                audioPlayer.currentTime = (clickX / width) * duration;
            }
        }

        // LIGHTBOX SYSTEM
        function openLightbox(src, caption) {
            const lb = document.getElementById('lightbox');
            document.getElementById('lightbox-img').src = src;
            document.getElementById('lightbox-caption').textContent = caption;
            lb.style.display = 'flex';
        }

        function closeLightbox() {
            document.getElementById('lightbox').style.display = 'none';
        }
    </script>
</body>
</html>
