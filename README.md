<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<title>⚠️ SYSTEM BREACH ⚠️</title>
<style>
    body {
        background-color: black;
        color: #00ff00;
        font-family: "Courier New", monospace;
        text-align: center;
        padding-top: 40px;
    }
    pre {
        color: #00ff00;
        font-size: 14px;
    }
    button {
        background-color: black;
        color: red;
        border: 2px solid red;
        padding: 15px 30px;
        font-size: 20px;
        cursor: pointer;
        margin-top: 20px;
    }
    button:disabled {
        opacity: 0.3;
        cursor: not-allowed;
    }
    #timer {
        font-size: 46px;
        margin-top: 30px;
        color: red;
    }
    .alert {
        color: red;
        margin-top: 10px;
        animation: blink 1s infinite;
    }
    @keyframes blink {
        0%,50%,100% { opacity: 1; }
        25%,75% { opacity: 0; }
    }
</style>
</head>

<body>

<pre>
      ██████   ██ ▄█▀ █    ██  ██▓     ██▓    
    ▒██    ▒   ██▄█▒  ██  ▓██▒▓██▒    ▓██▒    
    ░ ▓██▄    ▓███▄░ ▓██  ▒██░▒██░    ▒██░    
      ▒   ██▒ ▓██ █▄ ▓▓█  ░██░▒██░    ▒██░    
    ▒██████▒▒ ▒██▒ █▄▒▒█████▓ ░██████▒░██████▒
    ▒ ▒▓▒ ▒ ░ ▒ ▒▒ ▓▒░▒▓▒ ▒ ▒ ░ ▒░▓  ░░ ▒░▓  ░
    ░ ░▒  ░ ░ ░ ░▒ ▒░░░▒░ ░ ░ ░ ░ ▒  ░░ ░ ▒  ░
    ░  ░  ░   ░ ░░ ░  ░░░ ░ ░   ░ ░     ░ ░   
          ░   ░  ░      ░         ░  ░    ░  
</pre>

<h1>💀 ACCÈS PIRATÉ 💀</h1>
<p>Contrôle total établi.</p>
<p class="alert">⚠️ PROTOCOLE D’AUTODESTRUCTION ⚠️</p>

<button id="startBtn">▶ LANCER LE COMPTE À REBOURS</button>

<div id="timer">12:00:00</div>

<script>
let started = false;
let time = 43200; // 12 heures

// AUDIO BIP
const audioCtx = new (window.AudioContext || window.webkitAudioContext)();

function bip(frequency = 800, duration = 100) {
    const osc = audioCtx.createOscillator();
    const gain = audioCtx.createGain();
    osc.connect(gain);
    gain.connect(audioCtx.destination);
    osc.frequency.value = frequency;
    osc.type = "square";
    osc.start();
    gain.gain.setValueAtTime(0.2, audioCtx.currentTime);
    osc.stop(audioCtx.currentTime + duration / 1000);
}

const btn = document.getElementById("startBtn");
const timerDisplay = document.getElementById("timer");

btn.onclick = () => {
    if (started) return;
    started = true;
    btn.disabled = true;

    audioCtx.resume(); // autorise le son

    const interval = setInterval(() => {
        let h = Math.floor(time / 3600);
        let m = Math.floor((time % 3600) / 60);
        let s = time % 60;

        timerDisplay.textContent =
            String(h).padStart(2, '0') + ":" +
            String(m).padStart(2, '0') + ":" +
            String(s).padStart(2, '0');

        // BIP NORMAL / URGENCE
        if (time <= 600) {
            bip(300, 200); // bip grave + stress (10 dernières minutes)
        } else {
            bip(800, 100);
        }

        time--;

        if (time < 0) {
            clearInterval(interval);
            timerDisplay.textContent = "💀 SYSTÈME DÉTRUIT 💀";
            document.body.style.color = "red";
        }
    }, 1000);
};
</script>

</body>
</html>
