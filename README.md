<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ujian Online: PLBJ & Indonesia</title>
    <!-- Font Awesome untuk Ikon -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        /* --- DESAIN MEWAH & PREMIUM (DARK MODE) --- */
        @import url('https://fonts.googleapis.com/css2?family=Cinzel:wght@700&family=Poppins:wght@300;400;600&display=swap');

        :root {
            --gold: #ffd700;
            --gold-dark: #b8860b;
            --dark-bg: #0a0a0a;
            --glass-bg: rgba(20, 20, 20, 0.95);
            --border-gold: 1px solid rgba(255, 215, 0, 0.3);
        }

        body {
            margin: 0;
            padding: 0;
            font-family: 'Poppins', sans-serif;
            background: radial-gradient(circle at center, #1a1a1a, #000000);
            color: #e0e0e0;
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            overflow-x: hidden;
        }

        .container {
            width: 90%;
            max-width: 800px;
            background: var(--glass-bg);
            backdrop-filter: blur(15px);
            border: var(--border-gold);
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 0 30px rgba(255, 215, 0, 0.1);
            text-align: center;
            position: relative;
            animation: fadeIn 1s ease-in-out;
            margin: 20px 0;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        h1 {
            font-family: 'Cinzel', serif;
            color: var(--gold);
            font-size: 2em;
            margin-bottom: 10px;
            text-shadow: 0 2px 4px rgba(0,0,0,0.5);
        }

        h2 {
            color: #fff;
            font-weight: 300;
            letter-spacing: 1px;
            font-size: 1.2em;
            margin-top: 0;
        }

        /* Input Styles */
        .input-group {
            margin: 25px 0;
            text-align: left;
        }

        label {
            color: var(--gold);
            font-size: 0.9em;
            margin-bottom: 8px;
            display: block;
        }

        input[type="text"], input[type="password"] {
            width: 100%;
            padding: 15px;
            background: rgba(255, 255, 255, 0.05);
            border: 1px solid #333;
            border-radius: 8px;
            color: white;
            font-size: 16px;
            box-sizing: border-box;
            transition: 0.3s;
            font-family: 'Poppins', sans-serif;
        }

        input:focus {
            border-color: var(--gold);
            outline: none;
            box-shadow: 0 0 10px rgba(255, 215, 0, 0.2);
        }

        /* Button Styles */
        .btn-premium {
            background: linear-gradient(135deg, var(--gold), var(--gold-dark));
            color: #000;
            border: none;
            padding: 15px 40px;
            font-size: 16px;
            font-weight: bold;
            border-radius: 50px;
            cursor: pointer;
            transition: all 0.3s ease;
            text-transform: uppercase;
            letter-spacing: 1px;
            margin-top: 10px;
            box-shadow: 0 5px 15px rgba(184, 134, 11, 0.3);
            width: 100%;
        }

        .btn-premium:hover {
            transform: scale(1.02);
            box-shadow: 0 8px 20px rgba(255, 215, 0, 0.4);
        }

        .btn-whatsapp {
            background: linear-gradient(135deg, #25D366, #128C7E);
            color: white;
            text-decoration: none;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
            margin-top: 20px;
            box-shadow: 0 5px 15px rgba(37, 211, 102, 0.3);
        }

        .btn-whatsapp:hover {
            box-shadow: 0 8px 20px rgba(37, 211, 102, 0.5);
        }

        /* Quiz Section */
        .question-card {
            background: rgba(255, 255, 255, 0.03);
            border-left: 3px solid var(--gold);
            padding: 20px;
            margin-bottom: 20px;
            text-align: left;
            border-radius: 0 10px 10px 0;
        }

        .badge {
            display: inline-block;
            padding: 3px 8px;
            border-radius: 4px;
            font-size: 0.7em;
            font-weight: bold;
            color: #000;
            margin-right: 8px;
            vertical-align: middle;
        }
        .badge-plbj { background-color: #9b59b6; color: white; }
        .badge-indo { background-color: #e74c3c; color: white; }

        .question-text {
            font-size: 1.1em;
            margin-bottom: 15px;
            color: #fff;
            font-weight: 600;
        }

        .options label {
            display: block;
            padding: 12px;
            margin: 8px 0;
            background: rgba(0,0,0,0.3);
            border: 1px solid #333;
            border-radius: 8px;
            cursor: pointer;
            transition: 0.2s;
            color: #ccc;
            font-weight: normal;
        }

        .options label:hover {
            background: rgba(255, 215, 0, 0.1);
            border-color: var(--gold);
            color: white;
        }

        .options input[type="radio"] {
            margin-right: 10px;
        }

        /* Result Section */
        .score-circle {
            width: 150px;
            height: 150px;
            border-radius: 50%;
            border: 5px solid var(--gold);
            display: flex;
            justify-content: center;
            align-items: center;
            margin: 30px auto;
            font-size: 3em;
            font-weight: bold;
            color: var(--gold);
            background: rgba(0,0,0,0.5);
            box-shadow: 0 0 20px rgba(255, 215, 0, 0.2);
        }

        .error-msg {
            color: #ff4d4d;
            font-size: 0.9em;
            margin-top: 10px;
            display: none;
        }

        /* Hide sections initially */
        #quiz-section, #result-section {
            display: none;
        }
        
        /* Scrollbar custom */
        ::-webkit-scrollbar { width: 8px; }
        ::-webkit-scrollbar-track { background: #111; }
        ::-webkit-scrollbar-thumb { background: #333; border-radius: 4px; }
        ::-webkit-scrollbar-thumb:hover { background: var(--gold-dark); }
        
        .section-header {
            background: rgba(255,215,0,0.1);
            padding: 10px;
            margin: 20px 0 10px 0;
            border-radius: 5px;
            color: var(--gold);
            font-weight: bold;
            text-align: left;
        }
    </style>
</head>
<body>

    <div class="container">
        <!-- 1. HALAMAN LOGIN -->
        <div id="login-section">
            <h1><i class="fas fa-unlock-alt"></i> Ujian Online</h1>
            <h2>PLBJ & Pengetahuan Indonesia</h2>
            <p style="color: #aaa; font-size: 0.9em;">Masukkan kode akses untuk memulai ujian.</p>
            
            <div class="input-group">
                <label>Nama Lengkap Siswa</label>
                <input type="text" id="studentName" placeholder="Contoh: Ahmad Dhani">
            </div>
            
            <div class="input-group">
                <label>Kode Akses Ujian</label>
                <input type="password" id="accessCode" placeholder="Masukkan Kode Rahasia">
            </div>

            <button class="btn-premium" onclick="checkLogin()">Masuk Ujian</button>
            <p class="error-msg" id="errorMsg"><i class="fas fa-times-circle"></i> Kode Akses Salah! Anda tidak bisa mengerjakan soal.</p>
        </div>

        <!-- 2. HALAMAN SOAL -->
        <div id="quiz-section">
            <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 20px; border-bottom: 1px solid #333; padding-bottom: 10px;">
                <span id="displayStudentName" style="color: var(--gold); font-weight: bold;"></span>
                <span style="font-size: 0.8em; color: #aaa;">35 Soal Pilihan Ganda</span>
            </div>
            
            <div id="questions-container" style="max-height: 65vh; overflow-y: auto; padding-right: 10px;">
                <!-- Soal akan muncul di sini via JavaScript -->
            </div>

            <button class="btn-premium" onclick="finishQuiz()" style="width: 100%; margin-top: 30px;">
                <i class="fas fa-paper-plane"></i> Selesai & Kirim Nilai
            </button>
        </div>

        <!-- 3. HALAMAN HASIL & KIRIM WA -->
        <div id="result-section">
            <h1>Hasil Ujian</h1>
            <p>Terima kasih telah mengerjakan soal.</p>
            
            <div class="score-circle" id="finalScore">0</div>
            
            <p style="margin-bottom: 30px; color: #ccc;">
                Klik tombol di bawah untuk mengirim laporan nilai secara otomatis kepada Guru.
            </p>

            <a id="waLink" href="#" target="_blank" class="btn-premium btn-whatsapp">
                <i class="fab fa-whatsapp" style="font-size: 1.2em;"></i> Kirim Nilai ke Guru
            </a>
        </div>
    </div>

    <script>
        // --- KONFIGURASI ---
        const TEACHER_NUMBER = "6285882382854"; // Format internasional tanpa '+'
        const ACCESS_CODE = "BELAJAR.ID";

        // --- DATABASE SOAL (25 PLBJ + 10 INDONESIA) ---
        const questions = [
            // --- 25 SOAL PLBJ ---
            { s: 'plbj', q: "1. Rumah adat khas Jakarta (Betawi) disebut...", options: ["Rumah Gadang", "Rumah Joglo", "Rumah Kebaya", "Rumah Panggung"], a: "Rumah Kebaya" },
            { s: 'plbj', q: "2. Makanan khas Betawi yang terbuat dari tepung beras dan ebi adalah...", options: ["Kerak Telor", "Kue Rangi", "Asinan", "Gado-gado"], a: "Kue Rangi" },
            { s: 'plbj', q: "3. Seni pertunjukan teater tradisional Betawi adalah...", options: ["Lenong", "Ketoprak", "Ludruk", "Reog"], a: "Lenong" },
            { s: 'plbj', q: "4. Pakaian adat pria Betawi terdiri dari baju sadariah dan celana...", options: ["Panjang", "Komprang", "Pendek", "Jeans"], a: "Komprang" },
            { s: 'plbj', q: "5. Alat musik tradisional Betawi yang perpaduan budaya Tionghoa dan pribumi adalah...", options: ["Angklung", "Gambang Kromong", "Calung", "Sasando"], a: "Gambang Kromong" },
            { s: 'plbj', q: "6. Julukan untuk kota Jakarta adalah...", options: ["Kota Hujan", "The Big Durian", "Kota Bunga", "Kota Pelajar"], a: "The Big Durian" },
            { s: 'plbj', q: "7. Pelabuhan utama di Jakarta Utara adalah...", options: ["Tanjung Perak", "Tanjung Priok", "Merak", "Bakauheni"], a: "Tanjung Priok" },
            { s: 'plbj', q: "8. Tari Topeng Betawi biasanya menceritakan tentang...", options: ["Kepahlawanan", "Kehidupan sehari-hari", "Mitos dewa-dewi", "Perang besar"], a: "Kehidupan sehari-hari" },
            { s: 'plbj', q: "9. Ondel-ondel merupakan kesenian rakyat berupa...", options: ["Boneka kecil", "Wayang kulit", "Boneka besar berkepala raksasa", "Alat musik"], a: "Boneka besar berkepala raksasa" },
            { s: 'plbj', q: "10. Sungai yang membelah kota Jakarta adalah...", options: ["Sungai Ciliwung", "Sungai Bengawan Solo", "Sungai Musi", "Sungai Code"], a: "Sungai Ciliwung" },
            { s: 'plbj', q: "11. Suku asli penduduk Jakarta adalah suku...", options: ["Sunda", "Betawi", "Jawa", "Batak"], a: "Betawi" },
            { s: 'plbj', q: "12. Batik khas Jakarta memiliki motif yang terkenal, yaitu motif...", options: ["Parang", "Mega Mendung", "Ondel-ondel", "Kawung"], a: "Ondel-ondel" },
            { s: 'plbj', q: "13. Danau buatan di Jakarta Utara yang menjadi tempat wisata adalah...", options: ["Danau Sunter / Pluit", "Danau Toba", "Situ Gintung", "Waduk Jatiluhur"], a: "Danau Sunter / Pluit" },
            { s: 'plbj', q: "14. Upacara adat pernikahan Betawi dikenal dengan istilah...", options: ["Siraman", "Palang Pintu", "Mapag Sri", "Tedak Siten"], a: "Palang Pintu" },
            { s: 'plbj', q: "15. Maskot fauna resmi DKI Jakarta adalah...", options: ["Elang Bondol", "Garuda", "Macan Tutul", "Burung Cendrawasih"], a: "Elang Bondol" },
            { s: 'plbj', q: "16. Monumen Nasional (Monas) terletak di kecamatan...", options: ["Gambir", "Menteng", "Tanah Abang", "Senen"], a: "Gambir" },
            { s: 'plbj', q: "17. Kawasan pecinan di Jakarta disebut...", options: ["Glodok", "Kampung Melayu", "Tanah Abang", "Pasar Baru"], a: "Glodok" },
            { s: 'plbj', q: "18. Band Soimah adalah grup musik yang memainkan lagu-lagu...", options: ["Pop Modern", "Gambang Kromong", "Rock", "Jazz"], a: "Gambang Kromong" },
            { s: 'plbj', q: "19. Warna bendera DKI Jakarta adalah...", options: ["Merah Putih", "Hitam Putih", "Biru Putih", "Hijau Kuning"], a: "Merah Putih" }, // Secara teknis lambang daerah, tapi bendera umum merah putih
            { s: 'plbj', q: "20. Tempat pemakaman pahlawan di Jakarta Selatan adalah...", options: ["TMP Kalibata", "TPU Tanah Kusir", "Pemakaman Karet", "Pemakaman Manggar"], a: "TMP Kalibata" },
            { s: 'plbj', q: "21. Jembatan ikonik peninggalan Belanda di Kepulauan Seribu adalah...", options: ["Jembatan Suramadu", "Jembatan Pulau Onrust", "Jembatan Ampera", "Jembatan Merah"], a: "Jembatan Pulau Onrust" },
            { s: 'plbj', q: "22. Buah khas Jakarta yang sering dijadikan rujak adalah...", options: ["Mangga Arumanis", "Salak Pondoh", "Jeruk Bali", "Apel Malang"], a: "Mangga Arumanis" },
            { s: 'plbj', q: "23. Gubernur DKI Jakarta yang pertama adalah...", options: ["Ali Sadikin", "Suwirjo", "Soekarno", "Fadjar Panjaitan"], a: "Suwirjo" },
            { s: 'plbj', q: "24. Ciri khas masyarakat Betawi adalah...", options: ["Tertutup", "Ramah dan Agamis", "Individualis", "Pemalu"], a: "Ramah dan Agamis" },
            { s: 'plbj', q: "25. Bandara internasional yang melayani Jakarta adalah...", options: ["Soekarno-Hatta", "Juanda", "Husein Sastranegara", "Ngurah Rai"], a: "Soekarno-Hatta" },

            // --- 10 SOAL INDONESIA ---
            { s: 'indo', q: "26. Tanggal berapakah Indonesia memproklamasikan kemerdekaannya?", options: ["17 Agustus 1945", "18 Agustus 1945", "20 Mei 1908", "28 Oktober 1928"], a: "17 Agustus 1945" },
            { s: 'indo', q: "27. Siapakah presiden pertama Republik Indonesia?", options: ["Soeharto", "B.J. Habibie", "Ir. Soekarno", "Joko Widodo"], a: "Ir. Soekarno" },
            { s: 'indo', q: "28. Apa bunyi sila pertama Pancasila?", options: ["Kemanusiaan yang adil...", "Persatuan Indonesia", "Ketuhanan Yang Maha Esa", "Keadilan sosial..."], a: "Ketuhanan Yang Maha Esa" },
            { s: 'indo', q: "29. Rumah adat Sumatera Barat adalah...", options: ["Rumah Gadang", "Rumah Honai", "Rumah Tongkonan", "Rumah Limas"], a: "Rumah Gadang" },
            { s: 'indo', q: "30. Pulau terbesar di Indonesia adalah...", options: ["Jawa", "Sumatera", "Kalimantan", "Papua"], a: "Papua" },
            { s: 'indo', q: "31. Lagu kebangsaan Indonesia berjudul...", options: ["Padamu Negeri", "Indonesia Raya", "Halo-Halo Bandung", "Syukur"], a: "Indonesia Raya" },
            { s: 'indo', q: "32. Semboyan negara Indonesia adalah...", options: ["Tut Wuri Handayani", "Bhinneka Tunggal Ika", "Ing Ngarsa Sung Tulada", "Gotong Royong"], a: "Bhinneka Tunggal Ika" },
            { s: 'indo', q: "33. Provinsi paling timur di Indonesia adalah...", options: ["Aceh", "Bali", "Papua", "Maluku"], a: "Papua" },
            { s: 'indo', q: "34. Candi Borobudur merupakan peninggalan agama...", options: ["Hindu", "Buddha", "Islam", "Kristen"], a: "Buddha" },
            { s: 'indo', q: "35. Mata uang negara Indonesia adalah...", options: ["Ringgit", "Dollar", "Rupiah", "Yen"], a: "Rupiah" }
        ];

        let studentName = "";

        // --- LOGIKA LOGIN ---
        function checkLogin() {
            const codeInput = document.getElementById('accessCode').value;
            const nameInput = document.getElementById('studentName').value;
            const errorMsg = document.getElementById('errorMsg');

            if (nameInput.trim() === "") {
                alert("Harap isi Nama Lengkap terlebih dahulu!");
                return;
            }

            // Validasi Kode Akses
            if (codeInput === ACCESS_CODE) {
                studentName = nameInput;
                document.getElementById('displayStudentName').innerText = "Siswa: " + studentName;
                
                // Transisi Halaman
                document.getElementById('login-section').style.display = 'none';
                document.getElementById('quiz-section').style.display = 'block';
                
                loadQuestions();
            } else {
                errorMsg.style.display = 'block';
                // Animasi getar pada container
                const container = document.querySelector('.container');
                container.style.animation = 'shake 0.5s';
                setTimeout(() => container.style.animation = '', 500);
            }
        }

        // Tambahkan keyframe shake dinamis
        const styleSheet = document.createElement("style");
        styleSheet.innerText = `
            @keyframes shake {
                0% { transform: translateX(0); }
                25% { transform: translateX(-10px); }
                50% { transform: translateX(10px); }
                75% { transform: translateX(-10px); }
                100% { transform: translateX(0); }
            }
        `;
        document.head.appendChild(styleSheet);

        // --- GENERATE SOAL ---
        function loadQuestions() {
            const container = document.getElementById('questions-container');
            container.innerHTML = "";
            
            let currentSubject = "";

            questions.forEach((item, index) => {
                // Cek ganti subjek untuk header
                let headerHtml = "";
                if (item.s !== currentSubject) {
                    currentSubject = item.s;
                    const title = currentSubject === 'plbj' ? "BAGIAN 1: PLBJ (Pendidikan Lingkungan Budaya Jakarta)" : "BAGIAN 2: PENGETAHUAN INDONESIA";
                    headerHtml = `<div class="section-header">${title}</div>`;
                }

                // Badge Logic
                let badgeClass = item.s === 'plbj' ? 'badge-plbj' : 'badge-indo';
                let badgeText = item.s === 'plbj' ? 'PLBJ' : 'INDO';

                let html = headerHtml + `
                <div class="question-card">
                    <p class="question-text"><span class="badge ${badgeClass}">${badgeText}</span> ${item.q}</p>
                    <div class="options">
                `;
                
                // Acak opsi jawaban
                let shuffledOptions = [...item.options].sort(() => Math.random() - 0.5);
                
                shuffledOptions.forEach(opt => {
                    html += `
                        <label>
                            <input type="radio" name="q${index}" value="${opt}"> ${opt}
                        </label>
                    `;
                });

                html += `</div></div>`;
                container.innerHTML += html;
            });
        }

        // --- SELESAI & KIRIM NILAI ---
        function finishQuiz() {
            let score = 0;
            let totalQuestions = questions.length;
            let answeredCount = 0;

            // Hitung Skor
            questions.forEach((item, index) => {
                const selected = document.querySelector(`input[name="q${index}\"]:checked`);
                if (selected) {
                    answeredCount++;
                    if (selected.value === item.a) {
                        score++;
                    }
                }
            });

            // Konfirmasi jika ada soal kosong
            if (answeredCount < totalQuestions) {
                if(!confirm(`Anda baru menjawab ${answeredCount} dari ${totalQuestions} soal. Yakin ingin mengumpulkan?`)) {
                    return;
                }
            }

            // Hitung Nilai Akhir (Skala 100)
            let finalScore = Math.round((score / totalQuestions) * 100);

            // Tampilkan Halaman Hasil
            document.getElementById('quiz-section').style.display = 'none';
            document.getElementById('result-section').style.display = 'block';
            document.getElementById('finalScore').innerText = finalScore;

            // --- SISTEM KIRIM WA OTOMATIS ---
            const now = new Date();
            const dateString = now.toLocaleDateString('id-ID');
            const timeString = now.toLocaleTimeString('id-ID');

            // Pesan Utama
            const messageText = `
*LAPORAN HASIL UJIAN ONLINE*
---------------------------
👤 *Nama Siswa:* ${studentName}
📚 *Mapel:* PLBJ & Indonesia
📅 *Tanggal:* ${dateString}
⏰ *Waktu:* ${timeString}
---------------------------
💯 *NILAI AKHIR: ${finalScore}*
---------------------------
_Mohon dicatat Pak/Bu. Terima kasih._
            `.trim();

            // Encode pesan agar bisa jadi URL
            const encodedMessage = encodeURIComponent(messageText);
            
            // Set link tombol WA
            const waUrl = `https://wa.me/${TEACHER_NUMBER}?text=${encodedMessage}`;
            document.getElementById('waLink').href = waUrl;
        }
    </script>
</body>
</html>
