<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ujian Online Premium: IPAS & Pancasila</title>
    <!-- Font Awesome untuk Ikon -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
    <style>
        /* --- DESAIN MEWAH & PREMIUM (DARK & GOLD) --- */
        @import url('https://fonts.googleapis.com/css2?family=Cinzel:wght@700&family=Poppins:wght@300;400;600&display=swap');

        :root {
            --gold: #ffd700;
            --gold-dark: #b8860b;
            --dark-bg: #0a0a0a;
            --glass-bg: rgba(20, 20, 20, 0.9);
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
            max-width: 700px;
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
            font-weight: 600;
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
        }

        .btn-premium:hover {
            transform: scale(1.05);
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
            width: 100%;
            box-sizing: border-box;
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
            border-radius: 8px;
            cursor: pointer;
            transition: 0.2s;
            color: #ccc;
            font-weight: 400;
        }

        .options label:hover {
            background: rgba(255, 215, 0, 0.1);
            color: white;
        }

        .options input[type="radio"] {
            margin-right: 10px;
            accent-color: var(--gold);
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
        
        /* Animasi Shake untuk Error */
        @keyframes shake {
            0% { transform: translateX(0); }
            25% { transform: translateX(-10px); }
            50% { transform: translateX(10px); }
            75% { transform: translateX(-10px); }
            100% { transform: translateX(0); }
        }
    </style>
</head>
<body>

    <div class="container">
        <!-- 1. HALAMAN LOGIN -->
        <div id="login-section">
            <h1><i class="fas fa-university"></i> Ujian Online</h1>
            <h2>IPAS (Astronomi) & Pancasila</h2>
            <p style="color: #aaa; font-size: 0.9em;">Masukkan kredensial untuk memulai.</p>
            
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
                <span style="font-size: 0.8em; color: #aaa;">Total: 15 Soal</span>
            </div>
            
            <div id="questions-container">
                <!-- Soal akan muncul di sini via JavaScript -->
            </div>

            <button class="btn-premium" onclick="finishQuiz()" style="width: 100%; margin-top: 30px;">
                <i class="fas fa-paper-plane"></i> Selesai & Lihat Nilai
            </button>
        </div>

        <!-- 3. HALAMAN HASIL & KIRIM WA -->
        <div id="result-section">
            <h1>Hasil Ujian</h1>
            <p>Berikut adalah perolehan nilai Anda:</p>
            
            <div class="score-circle" id="finalScore">0</div>
            
            <p style="margin-bottom: 30px; color: #ccc;">
                Silakan klik tombol di bawah untuk melaporkan nilai ini kepada Guru secara otomatis.
            </p>

            <a id="waLink" href="#" target="_blank" class="btn-premium btn-whatsapp">
                <i class="fab fa-whatsapp" style="font-size: 1.2em;"></i> Kirim Laporan ke Guru
            </a>
            
            <p style="font-size: 0.8em; color: #666; margin-top: 20px;">
                *Akan membuka aplikasi WhatsApp
            </p>
        </div>
    </div>

    <script>
        // --- KONFIGURASI NOMOR GURU ---
        const teacherNumber = "6285882382854"; // Format internasional tanpa '+'

        // --- DATABASE SOAL (15 Soal: 7 IPAS Astronomi, 8 Pancasila) ---
        const questionBank = [
            // IPAS - Astronomi
            { q: "1. Pusat dari tata surya kita adalah...", options: ["Bumi", "Bulan", "Matahari", "Planet Mars"], a: "Matahari" },
            { q: "2. Planet terbesar dalam tata surya kita adalah...", options: ["Saturnus", "Jupiter", "Uranus", "Neptunus"], a: "Jupiter" },
            { q: "3. Gerakan bumi berputar pada porosnya disebut...", options: ["Revolusi", "Rotasi", "Orbit", "Gerhana"], a: "Rotasi" },
            { q: "4. Planet yang dijuluki sebagai 'Planet Merah' adalah...", options: ["Venus", "Mars", "Merkurius", "Saturnus"], a: "Mars" },
            { q: "5. Benda langit yang memiliki ekor cahaya panjang disebut...", options: ["Asteroid", "Meteor", "Komet", "Satelit"], a: "Komet" },
            { q: "6. Galaksi tempat tata surya kita berada bernama...", options: ["Andromeda", "Bima Sakti", "Galaksi Ursa Mayor", "Magellan"], a: "Bima Sakti" },
            { q: "7. Planet yang paling dekat dengan Matahari adalah...", options: ["Venus", "Merkurius", "Bumi", "Mars"], a: "Merkurius" },
            
            // Pancasila
            { q: "8. Lambang sila pertama Pancasila adalah...", options: ["Rantai", "Pohon Beringin", "Bintang", "Kepala Banteng"], a: "Bintang" },
            { q: "9. Gotong royong merupakan pengamalan nilai Pancasila, terutama sila ke...", options: ["Sila ke-2", "Sila ke-3", "Sila ke-4", "Sila ke-5"], a: "Sila ke-3" },
            { q: "10. Bhinneka Tunggal Ika memiliki arti...", options: ["Bersatu kita teguh", "Berbeda-beda tetapi tetap satu jua", "Maju tak gentar", "Satu nusa satu bangsa"], a: "Berbeda-beda tetapi tetap satu jua" },
            { q: "11. Sikap menghargai teman yang sedang beribadah sesuai agamanya merupakan wujud sila...", options: ["Sila ke-1", "Sila ke-2", "Sila ke-3", "Sila ke-4"], a: "Sila ke-1" },
            { q: "12. Kepala banteng merupakan lambang dari sila ke...", options: ["Dua", "Tiga", "Empat", "Lima"], a: "Empat" },
            { q: "13. Dasar negara Indonesia adalah...", options: ["UUD 1945", "Pancasila", "Burung Garuda", "Presiden"], a: "Pancasila" },
            { q: "14. Musyawarah untuk mufakat adalah pengamalan sila ke...", options: ["Sila ke-2", "Sila ke-3", "Sila ke-4", "Sila ke-5"], a: "Sila ke-4" },
            { q: "15. Warna dasar bendera negara Indonesia adalah...", options: ["Merah Putih", "Putih Merah", "Merah Biru", "Hijau Putih"], a: "Merah Putih" }
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
                // Animasi getar jika salah
                const container = document.querySelector('.container');
                container.style.animation = 'shake 0.5s';
                setTimeout(() => { container.style.animation = ''; }, 500);
            }
        }

        // --- GENERATE SOAL ---
        function loadQuestions() {
            const container = document.getElementById('questions-container');
            container.innerHTML = "";

            // Menampilkan soal secara urut agar sesuai nomor 1-15
            questionBank.forEach((item, index) => {
                // Opsi jawaban diacak posisinya agar tidak monoton
                let optionsShuffled = [...item.options].sort(() => Math.random() - 0.5);
                
                let html = `
                <div class="question-card">
                    <p class="question-text">${item.q}</p>
                    <div class="options">
                `;
                
                optionsShuffled.forEach(opt => {
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
            let totalQuestions = questionBank.length;
            let answeredCount = 0;

            // Hitung Skor
            questionBank.forEach((item, index) => {
                const selected = document.querySelector(`input[name="q${index}"]:checked`);
                if (selected) {
                    answeredCount++;
                    if (selected.value === item.a) {
                        score++;
                    }
                }
            });

            // Konfirmasi jika belum selesai semua
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

            // Pesan yang akan dikirim
            const messageText = `
*LAPORAN HASIL UJIAN ONLINE*
---------------------------
👤 *Nama Siswa:* ${studentName}
📚 *Mapel:* IPAS & Pancasila
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
            const waUrl = `https://wa.me/${teacherNumber}?text=${encodedMessage}`;
            document.getElementById('waLink').href = waUrl;
        }
    </script>
</body>
</html>
