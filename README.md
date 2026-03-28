<!DOCTYPE html>
<html lang="fr">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no">
    <title>🚨 SYSTEM FAILURE 🚨</title>
    <style>
        body { background: #000; color: #00ff00; font-family: 'Courier New', Courier, monospace; margin: 0; overflow: hidden; height: 100vh; display: flex; flex-direction: column; padding: 20px; box-sizing: border-box; }
        #console { flex-grow: 1; font-size: 12px; line-height: 1.2; overflow: hidden; text-align: left; }
        
        /* L'écran final rouge sang */
        #final-screen { display: none; position: fixed; top: 0; left: 0; width: 100%; height: 100%; background: #900; color: white; z-index: 9999; flex-direction: column; justify-content: center; align-items: center; text-align: center; }
        .lock { font-size: 100px; margin-bottom: 20px; }
        .threat { font-size: 20px; font-weight: bold; text-transform: uppercase; max-width: 80%; }
        .timer { font-size: 40px; margin-top: 20px; font-weight: bold; }
    </style>
</head>
<body>

<div id="console"></div>

<div id="final-screen">
    <div class="lock">🔒</div>
    <div class="threat">
        ATTENTION !<br>
        Ce téléphone a été verrouillé à distance.<br>
        Toutes les données (Photos, WhatsApp, Contacts) ont été cryptées.<br>
        Une clé de décryptage est nécessaire.
    </div>
    <div class="timer">23:59:59</div>
    <p style="font-size: 10px; margin-top: 30px;">[Contacter l'administrateur système pour obtenir la clé]</p>
</div>

<script>
    const logs = [
        "> [BOOT] System core loaded...",
        "> [KERNEL] Escalating privileges... [OK]",
        "> [SECURITY] Bypass secure boot... [DONE]",
        "> [ROOT] Accessing /data/system...",
        "> [USER_DATA] Scanning files...",
        "> [OK] 14,589 photos found (Gallery).",
        "> [OK] WhatsApp database found.",
        "> [ALERT] Starting encryption process...",
        "> [1%] .", "> [15%] ...", "> [48%] ...... ", "> [89%] ...........",
        "> [100%] ENCRYPTION COMPLETE.",
        "> [NETWORK] Transmitting encryption key to server...",
        "> [SYSTEM] Installing lockscreen...",
        "> [FINAL] INITIATING SECURE LOCKDOWN."
    ];

    // Se lance dès que la page charge (Pas d'interaction requise)
    window.onload = function() {
        // Tente le plein écran (automatique)
        const e = document.documentElement;
        if (e.requestFullscreen) { e.requestFullscreen().catch(() => { console.log("Fullscreen bloqué"); }); }
        else if (e.webkitRequestFullscreen) { e.webkitRequestFullscreen(); }

        const consoleDiv = document.getElementById('console');
        let i = 0;

        // Fait défiler le texte ultra-vite
        const logInterval = setInterval(() => {
            if (i < logs.length) {
                consoleDiv.innerHTML += logs[i] + "<br>";
                // Scroll automatique vers le bas
                window.scrollTo(0, document.body.scrollHeight);
                i++;
            } else {
                // Quand le texte finit, affiche l'écran de verrouillage rouge
                clearInterval(logInterval);
                setTimeout(() => {
                    document.getElementById('final-screen').style.display = 'flex';
                }, 1000); // 1s de pause après la console
            }
        }, 150); // Vitesse rapide du défilement
    };
</script>
</body>
</html>
