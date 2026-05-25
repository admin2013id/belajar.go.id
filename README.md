<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Portal Ujian Online</title>
    <!-- Menggunakan Font Google Poppins untuk tampilan modern -->
    <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap" rel="stylesheet">
    <style>
        :root {
            --primary-color: #6C63FF;
            --secondary-color: #4CAF50;
            --bg-gradient: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            --glass-bg: rgba(255, 255, 255, 0.95);
            --shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.37);
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
        }

        body {
            font-family: 'Poppins', sans-serif;
            background: var(--bg-gradient);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
        }

        .container {
            background: var(--glass-bg);
            padding: 40px;
            border-radius: 20px;
            box-shadow: var(--shadow);
            width: 100%;
            max-width: 500px;
            text-align: center;
            transition: transform 0.3s ease;
            position: relative;
            overflow: hidden;
        }

        h2 {
            color: #333;
            margin-bottom: 10px;
            font-weight: 600;
        }

        p.subtitle {
            color: #666;
            font-size: 14px;
            margin-bottom: 30px;
        }

        .input-group {
            margin-bottom: 20px;
            text-align: left;
        }

        label {
            display: block;
            margin-bottom: 8px;
            color: #555;
            font-weight: 500;
            font-size: 14px;
        }

        input[type="text"], input[type="password"] {
            width: 100%;
            padding: 12px 15px;
            border: 2px solid #e1e1e1;
            border-radius: 10px;
            font-size: 16px;
            transition: all 0.3s ease;
            outline: none;
            font-family: 'Poppins', sans-serif;
        }

        input[type="text"]:focus, input[type="password"]:focus {
            border-color: var(--primary-color);
            box-shadow: 0 0 8px rgba(108, 99, 255, 0.2);
        }

        button {
            width: 100%;
            padding: 14px;
            background: var(--primary-color);
            color: white;
            border: none;
            border-radius: 10px;
            cursor: pointer;
            font-size: 16px;
            font-weight: 600;
            transition: all 0.3s ease;
            margin-top: 10px;
            box-shadow: 0 4px 6px rgba(0,0,0,0.1);
        }

        button:hover {
            background: #5a52d5;
            transform: translateY(-2px);
            box-shadow: 0 6px 12px rgba(0,0,0,0.15);
        }

        button:active {
            transform: translateY(0);
        }

        .hidden {
            display: none;
        }

        /* Styles untuk Halaman Soal */
        .question-item {
            margin-bottom: 25px;
            padding: 15px;
            background: #f9f9f9;
            border-radius: 10px;
            text-align: left;
            border-left: 4px solid var(--primary-color);
        }

        .question-item p {
            font-weight: 600;
            color: #333;
            margin-bottom: 10px;
        }

        .options label {
            display: block;
            padding: 8px 12px;
            margin: 5px 0;
            background: white;
            border: 1px solid #ddd;
            border-radius: 6px;
            cursor: pointer;
            transition: all 0.2s;
            font-weight: normal;
        }

        .options label:hover {
            background: #f0f0ff;
            border-color: var(--primary-color);
        }

        .options input[type="radio"] {
            margin-right: 10px;
        }

        #error-msg {
            color: #ff4757;
            font-size: 14px;
            margin-top: 15px;
            font-weight: 500;
            min-height: 20px;
        }

        .score-display {
            font-size: 48px;
            font-weight: bold;
            color: var(--primary-color);
            margin: 20px 0;
            animation: popIn 0.5s ease;
        }

        @keyframes popIn {
            0% { transform: scale(0.5); opacity: 0; }
            100% { transform: scale(1); opacity: 1; }
        }

        .btn-wa {
            background: #25D366;
        }
        .btn-wa:hover {
            background: #1ebc57;
        }

        /* Responsive */
        @media (max-width: 480px) {
            .container {
                padding: 25px;
            }
            h2 { font-size: 24px; }
        }
    </style>
</head>
<body>

    <!-- HALAMAN LOGIN -->
    <div class="container" id="login-page">
        <div style="margin-bottom: 20px;">
            <!-- Ikon Gembok Sederhana dengan CSS/SVG -->
            <svg width="50" height="50" viewBox="0 0 24 24" fill="none" stroke="#6C63FF" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <rect x="3" y="11" width="18" height="11" rx="2" ry="2"></rect>
                <path d="M7 11V7a5 5 0 0 1 10 0v4"></path>
            </svg>
        </div>
        <h2>Selamat Datang</h2>
        <p class="subtitle">Silakan masukkan kode akses untuk memulai ujian.</p>
        
        <div class="input-group">
            <label for="access-code">Kode Akses</label>
            <input type="password" id="access-code" placeholder="Masukkan kode di sini..." onkeypress="handleEnter(event)">
        </div>
        
        <button onclick="checkCode()">Masuk Ujian</button>
        <p id="error-msg"></p>
    </div>

    <!-- HALAMAN SOAL -->
    <div class="container hidden" id="exam-page">
        <h2>Lembar Ujian</h2>
        <p class="subtitle">Jawablah dengan teliti. Waktu tidak dibatasi.</p>
        <form id="exam-form">
            <div id="questions-container" style="max-height: 60vh; overflow-y: auto; padding-right: 5px;">
                <!-- Soal akan di-generate oleh JavaScript -->
            </div>
            <button type="button" onclick="finishExam()" style="background: var(--secondary-color); margin-top: 20px;">Selesai & Lihat Nilai</button>
        </form>
    </div>

    <!-- HALAMAN HASIL -->
    <div class="container hidden" id="result-page">
        <h2>Ujian Selesai!</h2>
        <div id="result-area">
            <p>Berikut adalah nilai Anda:</p>
            <div class="score-display" id="final-score">0</div>
            <p style="font-size: 14px; color: #666; margin-bottom: 20px;">Klik tombol di bawah untuk melaporkan nilai ke Guru.</p>
            <button class="btn-wa" onclick="sendToWA()">
                <span style="margin-right: 8px;">📱</span> Kirim ke WhatsApp Guru
            </button>
            <button onclick="location.reload()" style="background: #999; margin-top: 10px;">Keluar / Ulangi</button>
        </div>
    </div>

    <script>
        // KONFIGURASI
        const CORRECT_CODE = "Mtk_B.indo";
        const TEACHER_NUMBER = "6285882382854"; // Format internasional

        // DATA SOAL (15 Soal: 8 Mtk, 7 B.Indo)
        const questions = [
            // MATEMATIKA
            { q: "1. Hasil dari 15 + 25 adalah...", options: ["30", "40", "50", "60"], answer: 1 },
            { q: "2. Berapakah hasil dari 12 x 11?", options: ["121", "132", "144", "110"], answer: 1 },
            { q: "3. Akar pangkat dua dari 144 adalah...", options: ["10", "11", "12", "14"], answer: 2 },
            { q: "4. Jika x = 5, maka nilai 2x + 3 adalah...", options: ["10", "13", "15", "20"], answer: 1 },
            { q: "5. Bangun datar yang memiliki 3 sisi disebut...", options: ["Persegi", "Lingkaran", "Segitiga", "Trapesium"], answer: 2 },
            { q: "6. Hasil dari 100 : 4 adalah...", options: ["20", "25", "30", "35"], answer: 1 },
            { q: "7. Sudut siku-siku besarnya berapa derajat?", options: ["45°", "90°", "180°", "360°"], answer: 1 },
            { q: "8. Rumus luas persegi panjang adalah...", options: ["s x s", "p x l", "a x t / 2", "2 x (p + l)"], answer: 1 },

            // BAHASA INDONESIA
            { q: "9. Lawan kata (antonim) dari 'Panjang' adalah...", options: ["Tinggi", "Luas", "Pendek", "Kecil"], answer: 2 },
            { q: "10. Persamaan kata (sinonim) dari 'Cantik' adalah...", options: ["Jelek", "Indah", "Buruk", "Kasar"], answer: 1 },
            { q: "11. Ibu kota negara Indonesia saat ini adalah...", options: ["Bandung", "Surabaya", "Jakarta", "Medan"], answer: 2 },
            { q: "12. Kata baku dari 'Apotik' adalah...", options: ["Apotek", "Apotik", "Aphotic", "Apoteker"], answer: 0 },
            { q: "13. Cerita rakyat 'Malin Kundang' berasal dari daerah...", options: ["Jawa Barat", "Sumatera Barat", "Bali", "Papua"], answer: 1 },
            { q: "14. Imbuhan 'me-' pada kata 'tulis' menjadi...", options: ["Metulis", "Menulis", "Mengtulis", "Menyulis"], answer: 1 },
            { q: "15. Tanda baca yang digunakan untuk mengakhiri kalimat tanya adalah...", options: ["Titik (.)", "Koma (,)", "Seru (!)", "Tanya (?)"], answer: 3 }
        ];

        let userScore = 0;

        // FUNGSI LOGIN
        function checkCode() {
            const input = document.getElementById('access-code').value;
            const errorMsg = document.getElementById('error-msg');
            const btn = document.querySelector('#login-page button');

            if (input === CORRECT_CODE) {
                // Animasi transisi sederhana
                document.getElementById('login-page').style.opacity = '0';
                setTimeout(() => {
                    document.getElementById('login-page').classList.add('hidden');
                    document.getElementById('exam-page').classList.remove('hidden');
                    loadQuestions();
                }, 300);
            } else {
                errorMsg.innerText = "⚠️ Kode Akses Salah! Silakan coba lagi.";
                document.getElementById('access-code').style.borderColor = "#ff4757";
                // Efek getar jika salah
                const container = document.getElementById('login-page');
                container.style.transform = "translateX(10px)";
                setTimeout(() => container.style.transform = "translateX(-10px)", 100);
                setTimeout(() => container.style.transform = "translateX(0)", 200);
            }
        }

        // Agar bisa tekan Enter untuk login
        function handleEnter(e) {
            if(e.key === 'Enter'){
                checkCode();
            }
        }

        // FUNGSI MEMUAT SOAL
        function loadQuestions() {
            const container = document.getElementById('questions-container');
            questions.forEach((q, index) => {
                const div = document.createElement('div');
                div.className = 'question-item';
                
                let optionsHtml = '';
                q.options.forEach((opt, optIndex) => {
                    optionsHtml += `
                        <label>
                            <input type="radio" name="q${index}" value="${optIndex}"> ${opt}
                        </label>
                    `;
                });

                div.innerHTML = `
                    <p>${q.q}</p>
                    <div class="options">${optionsHtml}</div>
                `;
                container.appendChild(div);
            });
        }

        // FUNGSI SELESAI & HITUNG NILAI
        function finishExam() {
            let correctCount = 0;
            let answered = 0;

            questions.forEach((q, index) => {
                const selected = document.querySelector(`input[name="q${index}"]:checked`);
                if (selected) {
                    answered++;
                    if (parseInt(selected.value) === q.answer) {
                        correctCount++;
                    }
                }
            });

            if (answered < questions.length) {
                const confirmFinish = confirm(`Anda baru menjawab ${answered} dari ${questions.length} soal. Yakin ingin selesai?`);
                if (!confirmFinish) return;
            }

            // Hitung Skor (Skala 100)
            userScore = Math.round((correctCount / questions.length) * 100);

            // Tampilkan Hasil
            document.getElementById('exam-page').classList.add('hidden');
            document.getElementById('result-page').classList.remove('hidden');
            document.getElementById('final-score').innerText = userScore;
            
            // Ubah warna nilai jika bagus atau jelek
            const scoreEl = document.getElementById('final-score');
            if(userScore >= 70) {
                scoreEl.style.color = "#4CAF50"; // Hijau
            } else {
                scoreEl.style.color = "#ff4757"; // Merah
            }
        }

        // FUNGSI KIRIM KE WHATSAPP
        function sendToWA() {
            const message = `Halo Pak/Bu, saya telah selesai mengerjakan ujian.\n\n*Nama:* (Isi Nama Anda)\n*Nilai:* ${userScore} / 100\n\nTerima kasih.`;
            const encodedMessage = encodeURIComponent(message);
            const waLink = `https://wa.me/${TEACHER_NUMBER}?text=${encodedMessage}`;
            
            // Membuka WhatsApp
            window.open(waLink, '_blank');
        }
    </script>
</body>
</html>
