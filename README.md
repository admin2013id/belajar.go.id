<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ujian Online: Mtk & B.Indo - Premium Access</title>
    <style>
        :root {
            --primary-color: #6a11cb;
            --secondary-color: #2575fc;
            --accent-color: #ffd700;
            --text-dark: #333;
            --text-light: #fff;
            --glass-bg: rgba(255, 255, 255, 0.95);
            --error-color: #ff4b4b;
        }

        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
        }

        body {
            background: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%);
            min-height: 100vh;
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 20px;
            color: var(--text-dark);
        }

        .container {
            background: var(--glass-bg);
            width: 100%;
            max-width: 800px;
            border-radius: 20px;
            box-shadow: 0 15px 35px rgba(0,0,0,0.2);
            overflow: hidden;
            position: relative;
            transition: all 0.3s ease;
        }

        /* Header Styles */
        .header {
            background: rgba(255,255,255,0.8);
            padding: 20px;
            text-align: center;
            border-bottom: 1px solid rgba(0,0,0,0.1);
        }

        .header h1 {
            font-size: 1.8rem;
            color: var(--primary-color);
            margin-bottom: 5px;
        }

        .header p {
            color: #666;
            font-size: 0.9rem;
        }

        /* Sections */
        .section {
            padding: 30px;
            display: none; /* Hidden by default */
            animation: fadeIn 0.5s ease-in-out;
        }

        .section.active {
            display: block;
        }

        /* Input Styles */
        .input-group {
            margin-bottom: 20px;
            text-align: center;
        }

        input[type="text"], input[type="password"], textarea {
            width: 100%;
            padding: 15px;
            border: 2px solid #ddd;
            border-radius: 10px;
            font-size: 1rem;
            transition: border-color 0.3s;
            outline: none;
            margin-bottom: 10px;
        }

        textarea {
            height: 100px;
            resize: vertical;
            font-family: inherit;
        }

        input[type="text"]:focus, input[type="password"]:focus, textarea:focus {
            border-color: var(--secondary-color);
        }

        .btn {
            background: linear-gradient(to right, var(--primary-color), var(--secondary-color));
            color: white;
            border: none;
            padding: 15px 30px;
            border-radius: 50px;
            font-size: 1rem;
            font-weight: bold;
            cursor: pointer;
            width: 100%;
            transition: transform 0.2s, box-shadow 0.2s;
            margin-top: 10px;
        }

        .btn:hover {
            transform: translateY(-2px);
            box-shadow: 0 5px 15px rgba(37, 117, 252, 0.4);
        }

        .btn:disabled {
            background: #ccc;
            cursor: not-allowed;
            transform: none;
        }

        /* Quiz Styles */
        .question-card {
            background: white;
            padding: 20px;
            border-radius: 15px;
            margin-bottom: 20px;
            box-shadow: 0 5px 15px rgba(0,0,0,0.05);
            border-left: 5px solid var(--secondary-color);
            text-align: left;
        }

        .badge {
            display: inline-block;
            padding: 4px 8px;
            border-radius: 4px;
            font-size: 0.75rem;
            font-weight: bold;
            color: white;
            margin-right: 8px;
            vertical-align: middle;
        }
        .badge-mtk { background-color: #e74c3c; }
        .badge-indo { background-color: #3498db; }
        .badge-essay { background-color: #f39c12; }

        .question-text {
            font-weight: 600;
            margin-bottom: 15px;
            font-size: 1.1rem;
            display: inline;
        }

        .options label {
            display: block;
            padding: 10px;
            margin: 5px 0;
            background: #f8f9fa;
            border-radius: 8px;
            cursor: pointer;
            transition: background 0.2s;
        }

        .options label:hover {
            background: #e9ecef;
        }

        .options input[type="radio"] {
            margin-right: 10px;
        }

        /* Result Styles */
        .result-box {
            text-align: center;
        }

        .score-display {
            font-size: 3.5rem;
            font-weight: bold;
            color: var(--primary-color);
            margin: 20px 0;
        }

        .whatsapp-btn {
            background: #25D366;
            display: flex;
            align-items: center;
            justify-content: center;
            gap: 10px;
        }

        .whatsapp-btn:hover {
            box-shadow: 0 5px 15px rgba(37, 211, 102, 0.4);
        }

        /* Error Message */
        .error-msg {
            color: var(--error-color);
            font-size: 0.9rem;
            margin-top: 10px;
            display: none;
            font-weight: bold;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(10px); }
            to { opacity: 1; transform: translateY(0); }
        }

        /* Responsive */
        @media (max-width: 600px) {
            .section { padding: 20px; }
            .header h1 { font-size: 1.5rem; }
        }
    </style>
</head>
<body>

<div class="container">
    <div class="header">
        <h1>Portal Ujian Digital</h1>
        <p>Matematika & Bahasa Indonesia</p>
    </div>

    <!-- HALAMAN LOGIN -->
    <div id="login-section" class="section active">
        <div class="input-group">
            <label for="access-code" style="display:block; margin-bottom:10px; font-weight:bold;">Masukkan Kode Akses</label>
            <input type="password" id="access-code" placeholder="Contoh: Mtk_B.indo">
            <p id="login-error" class="error-msg">Kode akses salah! Silakan coba lagi.</p>
        </div>
        <button class="btn" onclick="checkLogin()">Buka Ujian</button>
    </div>

    <!-- HALAMAN SOAL -->
    <div id="quiz-section" class="section">
        <div class="input-group">
            <input type="text" id="student-name" placeholder="Nama Lengkap Siswa" required>
        </div>
        
        <form id="quiz-form">
            <!-- Soal akan digenerate oleh JavaScript -->
            <div id="questions-container" style="max-height: 60vh; overflow-y: auto; padding-right: 5px;"></div>
            
            <button type="button" class="btn" onclick="submitQuiz()" style="background: linear-gradient(to right, #11998e, #38ef7d);">Selesai & Kirim Jawaban</button>
        </form>
    </div>

    <!-- HALAMAN HASIL -->
    <div id="result-section" class="section">
        <div class="result-box">
            <h2>Hasil Ujian Anda</h2>
            <p style="color:#666;">Nilai Pilihan Ganda:</p>
            <div class="score-display" id="final-score">0</div>
            
            <div style="background: #fff3cd; color: #856404; padding: 10px; border-radius: 5px; margin-bottom: 20px; font-size: 0.9rem;">
                <strong>Catatan:</strong> Jawaban Uraian Anda telah dikirim bersama nilai ini untuk diperiksa guru.
            </div>

            <p style="font-size: 0.9rem; color: #666; margin-bottom: 20px;">Klik tombol di bawah untuk mengirim laporan ke Guru via WhatsApp.</p>
            
            <button class="btn whatsapp-btn" onclick="sendToWhatsApp()">
                <svg width="24" height="24" viewBox="0 0 24 24" fill="white"><path d="M12.031 6.172c-3.181 0-5.767 2.586-5.768 5.766-.001 1.298.38 2.27 1.019 3.287l-.711 2.592 2.654-.696c1.029.575 2.27.879 3.805.879 3.18 0 5.767-2.587 5.767-5.766.001-3.187-2.575-5.762-5.766-5.762zm9.969 5.766c0 5.504-4.465 9.97-9.969 9.97C9.35 21.908 6.72 20.66 4.93 18.38L0 24l1.62-4.81C.57 17.51 0 15.32 0 12.938 0 7.434 4.465 2.969 9.969 2.969c5.504 0 9.969 4.465 9.969 9.969z"/></svg>
                Kirim Nilai ke Guru
            </button>
            <button class="btn" style="background:#666; margin-top:10px;" onclick="location.reload()">Ulangi Ujian</button>
        </div>
    </div>
</div>

<script>
    // --- DATA SOAL (20 PG + 5 Uraian) ---
    const questions = [
        // --- MATEMATIKA (PG) ---
        { type: 'pg', subject: 'mtk', q: "1. Hasil dari 25 x 4 + 10 adalah...", options: ["100", "110", "120", "90"], answer: 1 },
        { type: 'pg', subject: 'mtk', q: "2. Bangun datar dengan 4 sisi sama panjang disebut...", options: ["Persegi Panjang", "Layang-layang", "Persegi", "Belah Ketupat"], answer: 2 },
        { type: 'pg', subject: 'mtk', q: "3. FPB dari 12 dan 18 adalah...", options: ["3", "6", "9", "12"], answer: 1 },
        { type: 'pg', subject: 'mtk', q: "4. 3/4 diubah menjadi desimal menjadi...", options: ["0.25", "0.5", "0.75", "0.8"], answer: 2 },
        { type: 'pg', subject: 'mtk', q: "5. Keliling persegi dengan sisi 8 cm adalah...", options: ["16 cm", "32 cm", "64 cm", "24 cm"], answer: 1 },
        { type: 'pg', subject: 'mtk', q: "6. Hasil dari 150 - 75 : 3 adalah...", options: ["25", "125", "100", "135"], answer: 1 },
        { type: 'pg', subject: 'mtk', q: "7. Sudut yang besarnya kurang dari 90 derajat disebut...", options: ["Sudut Tumpul", "Sudut Siku-siku", "Sudut Lancip", "Sudut Lurus"], answer: 2 },
        { type: 'pg', subject: 'mtk', q: "8. Volume kubus dengan rusuk 5 cm adalah...", options: ["25 cm³", "100 cm³", "125 cm³", "150 cm³"], answer: 2 },
        { type: 'pg', subject: 'mtk', q: "9. Pecahan senilai dengan 1/2 adalah...", options: ["2/5", "3/6", "4/9", "5/12"], answer: 1 },
        { type: 'pg', subject: 'mtk', q: "10. Rata-rata dari data 5, 7, 9 adalah...", options: ["6", "7", "8", "9"], answer: 1 },

        // --- BAHASA INDONESIA (PG) ---
        { type: 'pg', subject: 'indo', q: "11. Antonim dari kata 'Gagal' adalah...", options: ["Kalah", "Sukses", "Hancur", "Berhenti"], answer: 1 },
        { type: 'pg', subject: 'indo', q: "12. Sinonim dari kata 'Efektif' adalah...", options: ["Tepat guna", "Cepat", "Lama", "Mahal"], answer: 0 },
        { type: 'pg', subject: 'indo', q: "13. Kalimat yang mengandung perintah diakhiri tanda...", options: ["Titik (.)", "Tanya (?)", "Seru (!)", "Koma (,)"], answer: 2 },
        { type: 'pg', subject: 'indo', q: "14. Kata baku dari 'Nasehat' adalah...", options: ["Nasihat", "Nasehat", "Nasihath", "Nasihaat"], answer: 0 },
        { type: 'pg', subject: 'indo', q: "15. Tempat terjadinya peristiwa dalam cerita disebut...", options: ["Tema", "Alur", "Latar", "Amanat"], answer: 2 },
        { type: 'pg', subject: 'indo', q: "16. Pantun bersajak...", options: ["a-a-a-a", "a-b-a-b", "a-b-b-a", "b-b-b-b"], answer: 1 },
        { type: 'pg', subject: 'indo', q: "17. Imbuhan 'ber-' pada kata 'ajar' menjadi...", options: ["Berajar", "Belajar", "Beraajar", "Beajar"], answer: 1 },
        { type: 'pg', subject: 'indo', q: "18. Tokoh utama yang bersifat jahat disebut...", options: ["Protagonis", "Antagonis", "Tritagonis", "Figuran"], answer: 1 },
        { type: 'pg', subject: 'indo', q: "19. Gagasan pokok dalam sebuah paragraf disebut...", options: ["Kalimat penjelas", "Ide pokok", "Kesimpulan", "Tema"], answer: 1 },
        { type: 'pg', subject: 'indo', q: "20. Ungkapan 'Kabar angin' berarti...", options: ["Berita bohong", "Berita belum jelas kebenarannya", "Berita penting", "Berita duka"], answer: 1 },

        // --- URAIAN / ESSAY (5 Soal) ---
        { type: 'essay', subject: 'mtk', q: "21. (Matematika) Sebuah taman berbentuk persegi panjang dengan panjang 20 meter dan lebar 10 meter. Hitunglah luas dan keliling taman tersebut!" },
        { type: 'essay', subject: 'mtk', q: "22. (Matematika) Ibu membeli 5 kg gula. Digunakan untuk membuat kue 2,5 kg. Berapa gram sisa gula ibu sekarang?" },
        { type: 'essay', subject: 'indo', q: "23. (B.Indo) Buatlah sebuah kalimat efektif menggunakan kata 'Perpustakaan'!" },
        { type: 'essay', subject: 'indo', q: "24. (B.Indo) Jelaskan perbedaan antara 'Pantun' dan 'Syair' secara singkat!" },
        { type: 'essay', subject: 'indo', q: "25. (B.Indo) Apa amanat yang bisa diambil dari cerita 'Kancil dan Buaya'? Jelaskan pendapatmu!" }
    ];

    // --- LOGIKA PROGRAM ---
    const correctCode = "Mtk_B.indo";
    let finalScore = 0;
    let studentName = "";
    let essayAnswers = [];

    function checkLogin() {
        const inputCode = document.getElementById('access-code').value;
        const errorMsg = document.getElementById('login-error');
        const btn = document.querySelector('#login-section .btn');

        if (inputCode === correctCode) {
            // Login Berhasil
            document.getElementById('login-section').classList.remove('active');
            document.getElementById('quiz-section').classList.add('active');
            renderQuestions();
        } else {
            // Login Gagal
            errorMsg.style.display = 'block';
            btn.disabled = true;
            btn.innerText = "Tunggu 3 detik...";
            
            setTimeout(() => {
                errorMsg.style.display = 'none';
                btn.disabled = false;
                btn.innerText = "Buka Ujian";
                document.getElementById('access-code').value = "";
            }, 3000);
        }
    }

    function renderQuestions() {
        const container = document.getElementById('questions-container');
        let htmlContent = '';

        questions.forEach((q, index) => {
            // Badge Logic
            let badgeClass = q.subject === 'mtk' ? 'badge-mtk' : 'badge-indo';
            let badgeText = q.subject === 'mtk' ? 'MTK' : 'B.INDO';
            if(q.type === 'essay') badgeClass = 'badge-essay';

            htmlContent += `
                <div class="question-card">
                    <div class="question-text"><span class="badge ${badgeClass}">${badgeText}</span> ${q.q}</div>
            `;

            if (q.type === 'pg') {
                htmlContent += `<div class="options">`;
                q.options.forEach((opt, i) => {
                    htmlContent += `
                        <label>
                            <input type="radio" name="q${index}" value="${i}">
                            ${opt}
                        </label>
                    `;
                });
                htmlContent += `</div>`;
            } else {
                htmlContent += `
                    <div style="margin-top:15px;">
                        <textarea id="essay-${index}" placeholder="Ketik jawaban uraian Anda di sini..."></textarea>
                    </div>
                `;
            }

            htmlContent += `</div>`;
        });

        container.innerHTML = htmlContent;
    }

    function submitQuiz() {
        studentName = document.getElementById('student-name').value;
        if (!studentName) {
            alert("Harap isi Nama Lengkap terlebih dahulu!");
            return;
        }

        let score = 0;
        let answeredCount = 0;
        essayAnswers = []; // Reset

        questions.forEach((q, index) => {
            if (q.type === 'pg') {
                const selected = document.querySelector(`input[name="q${index}"]:checked`);
                if (selected) {
                    answeredCount++;
                    if (parseInt(selected.value) === q.answer) {
                        score += 1; 
                    }
                }
            } else {
                // Simpan jawaban essay
                const val = document.getElementById(`essay-${index}`).value;
                essayAnswers.push({ no: index + 1, a: val });
            }
        });

        // Hitung nilai skala 100 (Hanya berdasarkan PG)
        const totalPG = questions.filter(q => q.type === 'pg').length;
        finalScore = Math.round((score / totalPG) * 100);

        // Konfirmasi jika ada PG kosong
        if (answeredCount < totalPG) {
            if(!confirm(`Anda baru menjawab ${answeredCount} dari ${totalPG} soal PG. Yakin ingin selesai?`)) return;
        }

        // Tampilkan Hasil
        document.getElementById('quiz-section').classList.remove('active');
        document.getElementById('result-section').classList.add('active');
        document.getElementById('final-score').innerText = finalScore;
    }

    function sendToWhatsApp() {
        const phoneNumber = "6285882382854"; 
        
        let message = `*LAPORAN HASIL UJIAN*\n`;
        message += `--------------------------\n`;
        message += `*Nama:* ${studentName}\n`;
        message += `*Nilai PG:* ${finalScore} / 100\n\n`;
        message += `*JAWABAN URAIAN:*\n`;

        essayAnswers.forEach(item => {
            let ans = item.a === "" ? "(Tidak dijawab)" : item.a;
            message += `\n*No ${item.no}:*\n${ans}\n`;
        });

        message += `\n--------------------------\nTerima kasih.`;

        const encodedMessage = encodeURIComponent(message);
        const url = `https://wa.me/${phoneNumber}?text=${encodedMessage}`;
        window.open(url, '_blank');
    }
</script>

</body>
</html>
