<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ujian IPAS & Pancasila - Premium Access</title>
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
            background: rgba(255,255,255,0.5);
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
            padding: 40px;
            display: none; /* Hidden by default */
            animation: fadeIn 0.5s ease-in-out;
        }

        .section.active {
            display: block;
        }

        /* Login Form */
        .login-group {
            margin-bottom: 20px;
            text-align: center;
        }

        input[type="text"], input[type="password"] {
            width: 100%;
            padding: 15px;
            border: 2px solid #ddd;
            border-radius: 10px;
            font-size: 1rem;
            transition: border-color 0.3s;
            outline: none;
        }

        input[type="text"]:focus, input[type="password"]:focus {
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
        }

        .question-text {
            font-weight: 600;
            margin-bottom: 15px;
            font-size: 1.1rem;
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
            font-size: 3rem;
            font-weight: bold;
            color: var(--primary-color);
            margin: 20px 0;
        }

        .message {
            margin-bottom: 20px;
            font-size: 1.1rem;
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
        <p>IPAS (Astronomi) & Pendidikan Pancasila</p>
    </div>

    <!-- HALAMAN LOGIN -->
    <div id="login-section" class="section active">
        <div class="login-group">
            <label for="access-code" style="display:block; margin-bottom:10px; font-weight:bold;">Masukkan Kode Akses</label>
            <input type="password" id="access-code" placeholder="Contoh: Ipas_Pancasila">
            <p id="login-error" class="error-msg">Kode akses salah! Silakan coba lagi.</p>
        </div>
        <button class="btn" onclick="checkLogin()">Buka Ujian</button>
    </div>

    <!-- HALAMAN SOAL -->
    <div id="quiz-section" class="section">
        <div class="login-group">
            <input type="text" id="student-name" placeholder="Nama Lengkap Siswa" required>
        </div>
        
        <form id="quiz-form">
            <!-- Soal akan digenerate oleh JavaScript -->
            <div id="questions-container"></div>
            
            <button type="button" class="btn" onclick="submitQuiz()">Selesai & Kirim Jawaban</button>
        </form>
    </div>

    <!-- HALAMAN HASIL -->
    <div id="result-section" class="section">
        <div class="result-box">
            <h2>Hasil Ujian Anda</h2>
            <div class="score-display" id="final-score">0</div>
            <p class="message">Terima kasih telah mengerjakan ujian.</p>
            <p style="font-size: 0.9rem; color: #666; margin-bottom: 20px;">Klik tombol di bawah untuk mengirim nilai ke Guru secara otomatis via WhatsApp.</p>
            
            <button class="btn whatsapp-btn" onclick="sendToWhatsApp()">
                <svg width="24" height="24" viewBox="0 0 24 24" fill="white"><path d="M12.031 6.172c-3.181 0-5.767 2.586-5.768 5.766-.001 1.298.38 2.27 1.019 3.287l-.711 2.592 2.654-.696c1.029.575 2.27.879 3.805.879 3.18 0 5.767-2.587 5.767-5.766.001-3.187-2.575-5.762-5.766-5.762zm9.969 5.766c0 5.504-4.465 9.97-9.969 9.97C9.35 21.908 6.72 20.66 4.93 18.38L0 24l1.62-4.81C.57 17.51 0 15.32 0 12.938 0 7.434 4.465 2.969 9.969 2.969c5.504 0 9.969 4.465 9.969 9.969z"/></svg>
                Kirim Nilai ke Guru
            </button>
            <button class="btn" style="background:#666; margin-top:10px;" onclick="location.reload()">Ulangi Ujian</button>
        </div>
    </div>
</div>

<script>
    // --- DATA SOAL (15 Soal: 7 Astronomi, 8 Pancasila) ---
    const questions = [
        // IPAS - Astronomi
        {
            q: "1. Pusat dari tata surya kita adalah...",
            options: ["Bumi", "Bulan", "Matahari", "Planet Mars"],
            answer: 2 // Index jawaban benar (0=A, 1=B, 2=C, 3=D)
        },
        {
            q: "2. Planet terbesar dalam tata surya kita adalah...",
            options: ["Saturnus", "Jupiter", "Uranus", "Neptunus"],
            answer: 1
        },
        {
            q: "3. Gerakan bumi berputar pada porosnya disebut...",
            options: ["Revolusi", "Rotasi", "Orbit", "Gerhana"],
            answer: 1
        },
        {
            q: "4. Planet yang dijuluki sebagai 'Planet Merah' adalah...",
            options: ["Venus", "Mars", "Merkurius", "Saturnus"],
            answer: 1
        },
        {
            q: "5. Benda langit yang memiliki ekor cahaya panjang disebut...",
            options: ["Asteroid", "Meteor", "Komet", "Satelit"],
            answer: 2
        },
        {
            q: "6. Galaksi tempat tata surya kita berada bernama...",
            options: ["Andromeda", "Bima Sakti", "Galaksi Ursa Mayor", "Magellan"],
            answer: 1
        },
        {
            q: "7. Planet yang paling dekat dengan Matahari adalah...",
            options: ["Venus", "Merkurius", "Bumi", "Mars"],
            answer: 1
        },
        
        // Pancasila
        {
            q: "8. Lambang sila pertama Pancasila adalah...",
            options: ["Rantai", "Pohon Beringin", "Bintang", "Kepala Banteng"],
            answer: 2
        },
        {
            q: "9. 'Gotong Royong' merupakan pengamalan nilai Pancasila, terutama sila ke...",
            options: ["Sila ke-2", "Sila ke-3", "Sila ke-4", "Sila ke-5"],
            answer: 3 // Bisa sila 3, 4, atau 5 tergantung konteks, tapi biasanya gotong royong kuat di sila 5 (keadilan sosial) atau 3. Kita ambil konteks umum musyawarah/kerjasama -> Sila 3/4. Kunci: Sila 3 (Persatuan) atau 5. Mari kita set Sila 3 untuk persatuan. *Revisi*: Gotong royong sering dikaitkan dengan Sila ke-5 (Keadilan Sosial) dalam hal membantu sesama, atau Sila 3. Untuk SD, sering diajarkan Sila 3. Saya kunci di 3.
        },
        {
            q: "10. Bhinneka Tunggal Ika memiliki arti...",
            options: ["Bersatu kita teguh", "Berbeda-beda tetapi tetap satu jua", "Maju tak gentar", "Satu nusa satu bangsa"],
            answer: 1
        },
        {
            q: "11. Sikap menghargai teman yang sedang beribadah sesuai agamanya merupakan wujud sila...",
            options: ["Sila ke-1", "Sila ke-2", "Sila ke-3", "Sila ke-4"],
            answer: 0
        },
        {
            q: "12. Kepala banteng merupakan lambang dari sila ke...",
            options: ["Dua", "Tiga", "Empat", "Lima"],
            answer: 2
        },
        {
            q: "13. Dasar negara Indonesia adalah...",
            options: ["UUD 1945", "Pancasila", "Burung Garuda", "Presiden"],
            answer: 1
        },
        {
            q: "14. Musyawarah untuk mufakat adalah pengamalan sila ke...",
            options: ["Sila ke-2", "Sila ke-3", "Sila ke-4", "Sila ke-5"],
            answer: 2
        },
        {
            q: "15. Warna dasar bendera negara Indonesia adalah...",
            options: ["Merah Putih", "Putih Merah", "Merah Biru", "Hijau Putih"],
            answer: 0
        }
    ];

    // Perbaikan kunci jawaban no 9 secara manual agar tepat: Gotong Royong erat kaitannya dengan Sila 3 (Persatuan) dan 5. Di banyak soal SD, jawabannya Sila 3.
    questions[8].answer = 1; // Sila ke-3 (Index 1 jika opsi A=0, B=1, C=2, D=3. Opsi: A=Sila 2, B=Sila 3, C=Sila 4, D=Sila 5). Jadi index 1 benar.

    // --- LOGIKA PROGRAM ---
    const correctCode = "Ipas_Pancasila";
    let finalScore = 0;
    let studentName = "";

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
            htmlContent += `
                <div class="question-card">
                    <div class="question-text">${q.q}</div>
                    <div class="options">
                        ${q.options.map((opt, i) => `
                            <label>
                                <input type="radio" name="q${index}" value="${i}">
                                ${opt}
                            </label>
                        `).join('')}
                    </div>
                </div>
            `;
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

        questions.forEach((q, index) => {
            const selected = document.querySelector(`input[name="q${index}"]:checked`);
            if (selected) {
                answeredCount++;
                if (parseInt(selected.value) === q.answer) {
                    score += 1; // Poin per soal
                }
            }
        });

        // Hitung nilai skala 100
        finalScore = Math.round((score / questions.length) * 100);

        // Tampilkan Hasil
        document.getElementById('quiz-section').classList.remove('active');
        document.getElementById('result-section').classList.add('active');
        document.getElementById('final-score').innerText = finalScore;
    }

    function sendToWhatsApp() {
        const phoneNumber = "6285882382854"; // Format internasional tanpa +
        const message = `Halo Pak/Bu, saya sudah menyelesaikan ujian.%0A%0ANama: ${studentName}%0ANilai: ${finalScore}%0A%0ATerima kasih.`;
        
        const url = `https://wa.me/${phoneNumber}?text=${message}`;
        window.open(url, '_blank');
    }
</script>

</body>
</html>
