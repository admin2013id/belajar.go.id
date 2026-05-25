<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>Academia Aurelia • Ujian</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.6.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700&family=Inter:wght@300;400;500;600&display=swap');

        :root { --gold: #d4af37; }

        * { margin: 0; padding: 0; box-sizing: border-box; }

        body {
            font-family: 'Inter', sans-serif;
            background: linear-gradient(135deg, #0f0c08 0%, #1a1612 100%);
            color: #e8d5b8;
            min-height: 100vh;
            padding: 15px;
            overflow-y: auto;
        }

        .container {
            background: rgba(15, 12, 8, 0.95);
            backdrop-filter: blur(20px);
            border: 1px solid var(--gold);
            border-radius: 20px;
            padding: 30px 20px;
            width: 100%;
            max-width: 620px;
            margin: 15px auto;
        }

        h2 {
            font-family: 'Playfair Display', serif;
            font-size: 2.4rem;
            text-align: center;
            color: var(--gold);
            margin-bottom: 8px;
        }

        .subtitle {
            text-align: center;
            color: #c9b38a;
            margin-bottom: 25px;
        }

        .question-item {
            background: rgba(255,255,255,0.04);
            padding: 20px;
            border-radius: 14px;
            margin-bottom: 18px;
            border: 1px solid rgba(212,175,55,0.2);
        }

        .options label {
            display: flex;
            align-items: center;
            padding: 14px 16px;
            margin: 8px 0;
            border-radius: 10px;
            cursor: pointer;
            font-size: 1.05rem;
        }

        .options label:hover {
            background: rgba(212,175,55,0.15);
        }

        input[type="radio"] {
            margin-right: 12px;
            accent-color: var(--gold);
        }

        button {
            width: 100%;
            padding: 16px;
            background: linear-gradient(90deg, #d4af37, #f0d38a);
            color: #0f0c08;
            border: none;
            border-radius: 12px;
            font-size: 1.1rem;
            font-weight: 600;
            margin-top: 15px;
            cursor: pointer;
        }

        .score-display {
            font-family: 'Playfair Display', serif;
            font-size: 4.8rem;
            font-weight: 700;
            color: var(--gold);
            text-align: center;
            margin: 20px 0;
        }

        .hidden { display: none !important; }
    </style>
</head>
<body>

    <!-- LOGIN -->
    <div class="container" id="login-page">
        <h2>Academia Aurelia</h2>
        <p class="subtitle">Ujian Matematika & Bahasa Indonesia</p>
        <input type="password" id="access-code" placeholder="Masukkan kode akses" style="width:100%; padding:15px; border-radius:12px; border:1px solid #5c4f3a; background:rgba(255,255,255,0.06); color:white; font-size:1.1rem;">
        <button onclick="checkCode()">MULAI UJIAN</button>
        <p id="error-msg" style="color:#ff6b6b; text-align:center; margin-top:12px;"></p>
    </div>

    <!-- SOAL -->
    <div class="container hidden" id="exam-page">
        <h2>Soal Ujian</h2>
        <p class="subtitle">Jawablah dengan teliti</p>
        <div id="questions-container"></div>
        <button onclick="finishExam()">SELESAI & KIRIM JAWABAN</button>
    </div>

    <!-- HASIL -->
    <div class="container hidden" id="result-page">
        <h2>Hasil Ujian</h2>
        <div id="result-area">
            <p style="text-align:center; color:#c9b38a; margin-bottom:10px;">Nilai Anda</p>
            <div class="score-display" id="final-score">0</div>
            <button onclick="sendToWA()" style="background:linear-gradient(90deg,#25D366,#20ba5a); color:white;">
                <i class="fab fa-whatsapp"></i> KIRIM KE GURU
            </button>
        </div>
    </div>

    <script>
        const CORRECT_CODE = "Mtk_B.indo";
        const TEACHER_NUMBER = "6285882382854";

        const questions = [
            { q: "1. Hasil dari 15 + 25 adalah...", options: ["30", "40", "50", "60"], answer: 2 },
            { q: "2. Berapakah hasil dari 12 x 11?", options: ["121", "132", "144", "110"], answer: 2 },
            { q: "3. Akar pangkat dua dari 144 adalah...", options: ["10", "11", "12", "14"], answer: 2 },
            { q: "4. Jika x = 5, maka nilai 2x + 3 adalah...", options: ["10", "13", "15", "20"], answer: 1 },
            { q: "5. Bangun datar yang memiliki 3 sisi disebut...", options: ["Persegi", "Lingkaran", "Segitiga", "Trapesium"], answer: 2 },
            { q: "6. Hasil dari 100 : 4 adalah...", options: ["20", "25", "30", "35"], answer: 0 },
            { q: "7. Sudut siku-siku besarnya berapa derajat?", options: ["45°", "90°", "180°", "360°"], answer: 1 },
            { q: "8. Rumus luas persegi panjang adalah...", options: ["s x s", "p x l", "a x t / 2", "2 x (p + l)"], answer: 1 },
            { q: "9. Lawan kata (antonim) dari 'Panjang' adalah...", options: ["Tinggi", "Luas", "Pendek", "Kecil"], answer: 2 },
            { q: "10. Persamaan kata (sinonim) dari 'Cantik' adalah...", options: ["Jelek", "Indah", "Buruk", "Kasar"], answer: 1 },
            { q: "11. Ibu kota negara Indonesia saat ini adalah...", options: ["Bandung", "Surabaya", "Jakarta", "Medan"], answer: 2 },
            { q: "12. Kata baku dari 'Apotik' adalah...", options: ["Apotek", "Apotik", "Aphotic", "Apoteker"], answer: 0 },
            { q: "13. Cerita rakyat 'Malin Kundang' berasal dari daerah...", options: ["Jawa Barat", "Sumatera Barat", "Bali", "Papua"], answer: 1 },
            { q: "14. Imbuhan 'me-' pada kata 'tulis' menjadi...", options: ["Metulis", "Menulis", "Mengtulis", "Menyulis"], answer: 1 },
            { q: "15. Tanda baca yang digunakan untuk mengakhiri kalimat tanya adalah...", options: ["Titik (.)", "Koma (,)", "Seru (!)", "Tanya (?)"], answer: 3 }
        ];

        let userScore = 0;

        function checkCode() {
            const code = document.getElementById('access-code').value.trim();
            if (code === CORRECT_CODE) {
                document.getElementById('login-page').classList.add('hidden');
                document.getElementById('exam-page').classList.remove('hidden');
                loadQuestions();
            } else {
                document.getElementById('error-msg').innerText = "Kode akses salah!";
            }
        }

        function loadQuestions() {
            const container = document.getElementById('questions-container');
            container.innerHTML = "";

            questions.forEach((q, i) => {
                let optionsHTML = "";
                q.options.forEach((opt, idx) => {
                    optionsHTML += `
                        <label>
                            <input type="radio" name="q\( {i}" value=" \){idx}"> ${opt}
                        </label>
                    `;
                });

                const questionHTML = `
                    <div class="question-item">
                        <p style="margin-bottom:16px; font-weight:500; line-height:1.4;">
                            <strong>${q.q}</strong>
                        </p>
                        <div class="options">${optionsHTML}</div>
                    </div>
                `;
                container.innerHTML += questionHTML;
            });
        }

        function finishExam() {
            let correct = 0;
            let answered = 0;

            questions.forEach((q, i) => {
                const selected = document.querySelector(`input[name="q${i}"]:checked`);
                if (selected) {
                    answered++;
                    if (parseInt(selected.value) === q.answer) correct++;
                }
            });

            if (answered < questions.length) {
                if (!confirm("Anda belum menjawab semua soal.\nTetap selesai?")) return;
            }

            userScore = Math.round((correct / questions.length) * 100);
            document.getElementById('exam-page').classList.add('hidden');
            document.getElementById('result-page').classList.remove('hidden');
            document.getElementById('final-score').innerText = userScore;
        }

        function sendToWA() {
            const message = `Hormat saya,\n\nNilai Ujian Academia Aurelia: *${userScore}*/100\nTerima kasih.`;
            window.open(`https://wa.me/\( {TEACHER_NUMBER}?text= \){encodeURIComponent(message)}`, '_blank');
        }
    </script>
</body>
</html>
