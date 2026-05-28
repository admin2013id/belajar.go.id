<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ujian Online Premium: PJOK & Agama</title>
    <!-- Font Awesome untuk Ikon -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        /* --- DESAIN MEWAH & PREMIUM (DARK MODE) --- */
        @import url('https://fonts.googleapis.com/css2?family=Cinzel:wght@700&family=Poppins:wght@300;400;600&display=swap');

        :root {
            --gold: #ffd700;
            --gold-dark: #b8860b;
            --dark-bg: #0a0a0a;
            --glass-bg: rgba(20, 20, 20, 0.90);
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
            max-width: 750px;
            background: var(--glass-bg);
            backdrop-filter: blur(15px);
            border: var(--border-gold);
            border-radius: 20px;
            padding: 40px;
            box-shadow: 0 0 30px rgba(255, 215, 0, 0.1);
            text-align: center;
            position: relative;
            animation: fadeIn 1s ease-in-out;
        }

        @keyframes fadeIn {
            from { opacity: 0; transform: translateY(20px); }
            to { opacity: 1; transform: translateY(0); }
        }

        h1 {
            font-family: 'Cinzel', serif;
            color: var(--gold);
            font-size: 2.2em;
            margin-bottom: 10px;
            text-shadow: 0 2px 4px rgba(0,0,0,0.5);
        }

        h2 {
            color: #fff;
            font-weight: 300;
            letter-spacing: 1px;
            font-size: 1.2em;
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

        input[type="text"], input[type="password"], textarea {
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

        textarea {
            height: 100px;
            resize: vertical;
        }

        input:focus, textarea:focus {
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
        .badge-pjok { background-color: #e67e22; color: white; }
        .badge-agama { background-color: #27ae60; color: white; }
        .badge-essay { background-color: #f39c12; color: black; }

        .question-text {
            font-size: 1.1em;
            margin-bottom: 15px;
            color: #fff;
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

        .note-essay {
            font-size: 0.85em;
            color: #aaa;
            background: rgba(255, 215, 0, 0.1);
            padding: 10px;
            border-radius: 5px;
            margin-bottom: 20px;
            border: 1px solid var(--gold-dark);
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
    </style>
</head>
<body>

    <div class="container">
        <!-- 1. HALAMAN LOGIN -->
        <div id="login-section">
            <h1><i class="fas fa-crown"></i> Ujian Akses</h1>
            <h2>PJOK & Pendidikan Agama</h2>
            <p style="color: #aaa; font-size: 0.9em;">Masukkan kredensial Anda untuk mengakses soal.</p>
            
            <div class="input-group">
                <label>Nama Lengkap Siswa</label>
                <input type="text" id="studentName" placeholder="Contoh: Budi Santoso">
            </div>
            
            <div class="input-group">
                <label>Kode Akses Ujian</label>
                <input type="password" id="accessCode" placeholder="Masukkan Kode Rahasia">
            </div>

            <button class="btn-premium" onclick="checkLogin()">Buka Soal Ujian</button>
            <p class="error-msg" id="errorMsg"><i class="fas fa-exclamation-triangle"></i> Kode Akses Salah! Akses Ditolak.</p>
        </div>

        <!-- 2. HALAMAN SOAL -->
        <div id="quiz-section">
            <div style="display: flex; justify-content: space-between; align-items: center; margin-bottom: 20px; border-bottom: 1px solid #333; padding-bottom: 10px;">
                <span id="displayStudentName" style="color: var(--gold); font-weight: bold;"></span>
                <span style="font-size: 0.8em; color: #aaa;">25 PG + 5 Uraian</span>
            </div>
            
            <div id="questions-container" style="max-height: 60vh; overflow-y: auto; padding-right: 5px;">
                <!-- Soal akan muncul di sini via JavaScript -->
            </div>

            <button class="btn-premium" onclick="finishQuiz()" style="width: 100%; margin-top: 30px;">
                <i class="fas fa-paper-plane"></i> Selesai & Lihat Nilai
            </button>
        </div>

        <!-- 3. HALAMAN HASIL & KIRIM WA -->
        <div id="result-section">
            <h1>Hasil Ujian</h1>
            <p>Perolehan nilai Pilihan Ganda Anda:</p>
            
            <div class="score-circle" id="finalScore">0</div>
            
            <div class="note-essay">
                <i class="fas fa-info-circle"></i> <strong>Perhatian:</strong> Nilai di atas hanya untuk soal Pilihan Ganda. Jawaban Uraian Anda akan dikirimkan ke Guru untuk diperiksa manual.
            </div>

            <p style="margin-bottom: 30px;">
                Silakan klik tombol di bawah untuk melaporkan nilai dan jawaban uraian kepada Guru.
            </p>

            <a id="waLink" href="#" target="_blank" class="btn-premium btn-whatsapp">
                <i class="fab fa-whatsapp" style="font-size: 1.2em;"></i> Kirim Laporan ke Guru
            </a>
            
            <p style="font-size: 0.8em; color: #666; margin-top: 20px;">
                *Jika tombol tidak berfungsi, pastikan Anda memiliki aplikasi WhatsApp.
            </p>
        </div>
    </div>

    <script>
        // --- KONFIGURASI NOMOR GURU ---
        const teacherNumber = "6285882382854"; // Format internasional tanpa '+'

        // --- DATABASE SOAL (25 PG + 5 Uraian: PJOK & AGAMA) ---
        // Type: 'pg' atau 'essay'
        const questionBank = [
            // PJOK (15 Soal PG)
            { type: 'pg', subject: 'pjok', q: "1. Induk organisasi sepak bola dunia adalah...", options: ["FIFA", "PSSI", "NBA", "PBSI"], a: "FIFA" },
            { type: 'pg', subject: 'pjok', q: "2. Berapa jumlah pemain dalam satu tim sepak bola?", options: ["10", "11", "12", "6"], a: "11" },
            { type: 'pg', subject: 'pjok', q: "3. Gerakan push-up bertujuan untuk melatih otot...", options: ["Kaki", "Perut", "Lengan & Dada", "Leher"], a: "Lengan & Dada" },
            { type: 'pg', subject: 'pjok', q: "4. Lari jarak pendek disebut juga...", options: ["Marathon", "Sprint", "Jogging", "Estafet"], a: "Sprint" },
            { type: 'pg', subject: 'pjok', q: "5. Dalam permainan bola basket, menggiring bola disebut...", options: ["Passing", "Shooting", "Dribbling", "Blocking"], a: "Dribbling" },
            { type: 'pg', subject: 'pjok', q: "6. Vitamin D sangat baik untuk kesehatan...", options: ["Mata", "Tulang", "Kulit", "Gigi"], a: "Tulang" },
            { type: 'pg', subject: 'pjok', q: "7. Pemanasan sebelum olahraga bertujuan untuk...", options: ["Membuat lelah", "Mencegah cedera", "Menghabiskan waktu", "Mendinginkan tubuh"], a: "Mencegah cedera" },
            { type: 'pg', subject: 'pjok', q: "8. Renang gaya bebas menggunakan tumpuan pada...", options: ["Punggung", "Dada", "Perut", "Samping"], a: "Perut" },
            { type: 'pg', subject: 'pjok', q: "9. Alat pemukul dalam permainan kasti terbuat dari...", options: ["Besi", "Kayu", "Plastik", "Karet"], a: "Kayu" },
            { type: 'pg', subject: 'pjok', q: "10. Gerakan sit-up melatih kekuatan otot...", options: ["Perut", "Paha", "Betis", "Bahu"], a: "Perut" },
            { type: 'pg', subject: 'pjok', q: "11. Berapa lama durasi pertandingan sepak bola normal?", options: ["45 menit", "90 menit", "60 menit", "100 menit"], a: "90 menit" },
            { type: 'pg', subject: 'pjok', q: "12. Teknik dasar passing dalam bola voli adalah...", options: ["Passing atas dan bawah", "Dribble", "Smash", "Block"], a: "Passing atas dan bawah" },
            { type: 'pg', subject: 'pjok', q: "13. Senam lantai yang menyerupai gerakan guling disebut...", options: ["Handstand", "Roll depan", "Meroda", "Salto"], a: "Roll depan" },
            { type: 'pg', subject: 'pjok', q: "14. Makanan yang mengandung karbohidrat berfungsi sebagai...", options: ["Sumber energi", "Pengganti sel", "Pelarut vitamin", "Penambah rasa"], a: "Sumber energi" },
            { type: 'pg', subject: 'pjok', q: "15. Posisi kiper dalam sepak bola bertugas untuk...", options: ["Mencetak gol", "Menjaga gawang", "Mengatur serangan", "Wasit"], a: "Menjaga gawang" },
            
            // AGAMA (10 Soal PG)
            { type: 'pg', subject: 'agama', q: "16. Kitab suci umat Islam adalah...", options: ["Al-Qur'an", "Injil", "Weda", "Tripitaka"], a: "Al-Qur'an" },
            { type: 'pg', subject: 'agama', q: "17. Rukun Islam ada berapa?", options: ["4", "5", "6", "3"], a: "5" },
            { type: 'pg', subject: 'agama', q: "18. Hari raya kurban umat Islam disebut...", options: ["Idul Fitri", "Idul Adha", "Nyepi", "Imlek"], a: "Idul Adha" },
            { type: 'pg', subject: 'agama', q: "19. Nabi terakhir dalam agama Islam adalah...", options: ["Nabi Isa", "Nabi Musa", "Nabi Muhammad SAW", "Nabi Ibrahim"], a: "Nabi Muhammad SAW" },
            { type: 'pg', subject: 'agama', q: "20. Sembahyang wajib umat Islam sehari semalam ada...", options: ["3 waktu", "4 waktu", "5 waktu", "2 waktu"], a: "5 waktu" },
            { type: 'pg', subject: 'agama', q: "21. Puasa wajib dilakukan pada bulan...", options: ["Syawal", "Ramadhan", "Muharam", "Rajab"], a: "Ramadhan" },
            { type: 'pg', subject: 'agama', q: "22. Tempat ibadah umat Kristiani disebut...", options: ["Masjid", "Gereja", "Pura", "Vihara"], a: "Gereja" },
            { type: 'pg', subject: 'agama', q: "23. Sikap saling menghormati antar umat beragama disebut...", options: ["Fanatik", "Toleransi", "Egois", "Diskriminasi"], a: "Toleransi" },
            { type: 'pg', subject: 'agama', q: "24. Surat Al-Fatihah dibaca saat...", options: ["Tidur", "Sholat", "Makan", "Mandi"], a: "Sholat" },
            { type: 'pg', subject: 'agama', q: "25. Ajaran cinta kasih merupakan inti dari agama...", options: ["Semua agama", "Hanya satu agama", "Tidak ada", "Agama suku"], a: "Semua agama" },

            // URAIAN / ESSAY (5 Soal)
            { type: 'essay', subject: 'pjok', q: "26. (PJOK) Jelaskan secara singkat cara melakukan gerakan guling depan (forward roll)!" },
            { type: 'essay', subject: 'pjok', q: "27. (PJOK) Mengapa kita wajib melakukan pendinginan setelah berolahraga? Jelaskan manfaatnya." },
            { type: 'essay', subject: 'agama', q: "28. (Agama) Sebutkan 3 dari 5 Rukun Islam yang kamu ketahui!" },
            { type: 'essay', subject: 'agama', q: "29. (Agama) Apa yang dimaksud dengan toleransi dalam kehidupan beragama? Berikan satu contoh." },
            { type: 'essay', subject: 'agama', q: "30. (Agama) Mengapa kita harus bersyukur kepada Tuhan Yang Maha Esa? Jelaskan pendapatmu." }
        ];

        let studentName = "";
        let essayAnswers = [];

        // --- LOGIKA LOGIN ---
        function checkLogin() {
            const codeInput = document.getElementById('accessCode').value;
            const nameInput = document.getElementById('studentName').value;
            const errorMsg = document.getElementById('errorMsg');

            if (nameInput.trim() === "") {
                alert("Harap isi Nama Lengkap terlebih dahulu!");
                return;
            }

            // Validasi Kode Akses (DIUBAH MENJADI: BELAJAR.ID)
            if (codeInput === "BELAJAR.ID") {
                studentName = nameInput;
                document.getElementById('displayStudentName').innerText = "Siswa: " + studentName;
                
                // Transisi Halaman
                document.getElementById('login-section').style.display = 'none';
                document.getElementById('quiz-section').style.display = 'block';
                
                loadQuestions();
            } else {
                errorMsg.style.display = 'block';
                // Animasi getar
                const container = document.querySelector('.container');
                container.style.animation = 'none';
                container.offsetHeight; /* trigger reflow */
                container.style.animation = 'shake 0.5s';
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

            questionBank.forEach((item, index) => {
                // Badge Logic
                let badgeClass = item.subject === 'pjok' ? 'badge-pjok' : 'badge-agama';
                let badgeText = item.subject === 'pjok' ? 'PJOK' : 'AGAMA';
                if(item.type === 'essay') {
                    badgeClass = 'badge-essay';
                    badgeText = 'URAIAN';
                }

                let html = `
                <div class="question-card">
                    <p class="question-text"><span class="badge ${badgeClass}">${badgeText}</span> ${item.q}</p>
                `;
                
                if (item.type === 'pg') {
                    html += `<div class="options">`;
                    // Kita acak opsi jawaban untuk PG agar lebih adil
                    let shuffledOptions = [...item.options].sort(() => Math.random() - 0.5);
                    
                    shuffledOptions.forEach(opt => {
                        html += `
                            <label>
                                <input type="radio" name="q${index}" value="${opt}"> ${opt}
                            </label>
                        `;
                    });
                    html += `</div>`;
                } else {
                    html += `
                        <div style="margin-top:15px;">
                            <textarea id="essay-${index}" placeholder="Ketik jawaban uraian Anda di sini..."></textarea>
                        </div>
                    `;
                }

                html += `</div>`;
                container.innerHTML += html;
            });
        }

        // --- SELESAI & KIRIM NILAI ---
        function finishQuiz() {
            let score = 0;
            let totalPG = 0;
            let answeredCount = 0;
            essayAnswers = []; // Reset

            // Hitung Skor PG & Simpan Essay
            questionBank.forEach((item, index) => {
                if (item.type === 'pg') {
                    totalPG++;
                    const selected = document.querySelector(`input[name="q${index}\"]:checked`);
                    if (selected) {
                        answeredCount++;
                        if (selected.value === item.a) {
                            score++;
                        }
                    }
                } else {
                    // Simpan jawaban essay
                    const val = document.getElementById(`essay-${index}`).value;
                    essayAnswers.push({ no: index + 1, q: item.q, a: val });
                }
            });

            // Konfirmasi jika ada PG kosong
            if (answeredCount < totalPG) {
                if(!confirm(`Anda baru menjawab ${answeredCount} dari ${totalPG} soal PG. Yakin ingin mengumpulkan?`)) {
                    return;
                }
            }

            // Hitung Nilai Akhir (Skala 100 berdasarkan PG)
            let finalScore = Math.round((score / totalPG) * 100);

            // Tampilkan Halaman Hasil
            document.getElementById('quiz-section').style.display = 'none';
            document.getElementById('result-section').style.display = 'block';
            document.getElementById('finalScore').innerText = finalScore;

            // --- SISTEM KIRIM WA OTOMATIS ---
            const now = new Date();
            const dateString = now.toLocaleDateString('id-ID');
            const timeString = now.toLocaleTimeString('id-ID');

            // Format Pesan Uraian
            let essayText = "";
            essayAnswers.forEach(e => {
                let ans = e.a === "" ? "(Tidak dijawab)" : e.a;
                essayText += `%0A*No ${e.no}:*%0A${ans}%0A`;
            });

            // Pesan Utama
            const messageText = `
*LAPORAN HASIL UJIAN ONLINE*
---------------------------
👤 *Nama Siswa:* ${studentName}
📚 *Mapel:* PJOK & Agama
📅 *Tanggal:* ${dateString}
⏰ *Waktu:* ${timeString}
---------------------------
💯 *NILAI PG: ${finalScore}*
---------------------------
*JAWABAN URAIAN (Untuk diperiksa):*
${essayText}
---------------------------
_Mohon dicatat Pak/Bu. Terima kasih._
            `.trim();

            // Encode pesan agar bisa jadi URL
            const encodedMessage = encodeURIComponent(messageText);
            
            // Set link tombol WA
            const waUrl = `https://wa.me/${teacherNumber}?text=${encodedMessage}`;
            document.getElementById('waLink').href = waUrl;
        }
    </script>
</body>
</html>
