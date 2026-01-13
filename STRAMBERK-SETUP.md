# 🏰 Štramberk Video AR - Návod k nastavení

Kompletní návod jak nastavit Video AR aplikaci s triggerem Štramberku.

## 🎯 Co máte připravené:

✅ **ar-video.html** - Video AR aplikace
✅ **Video:** https://ethnographic.cz/S%CC%8Ctramberk%20v%20mlze.mp4
✅ **Trigger obrázek:** Černobílý dřevoryt Štramberku
⏳ **Chybí:** .mind soubor (zkompilovaný trigger)

---

## 🚀 Rychlý start (3 kroky):

### Krok 1: Zkompilujte trigger (5 minut)

```
1. Jděte na: https://hiukim.github.io/mind-ar-js-doc/tools/compile
2. Nahrajte váš černobílý obrázek Štramberku
3. Klikněte "Start" a počkejte
4. Stáhněte "targets.mind"
5. Přejmenujte na "stramberk.mind"
```

### Krok 2: Nahrajte soubory na web

```
Nahrajte na ethnographic.cz:

📁 ethnographic.cz/
├── ar-video.html           (hlavní AR aplikace)
├── stramberk-trigger.html  (stránka s triggerem)
├── stramberk.mind          (zkompilovaný trigger) ⬅️ NOVÝ
├── S%CC%8Ctramberk%20v%20mlze.mp4 (už máte)
└── assets/                 (volitelná složka pro organizaci)
```

### Krok 3: Aktualizujte ar-video.html

Otevřete `ar-video.html` a najděte řádek ~251:

```html
<!-- NAJDĚTE TENTO ŘÁDEK: -->
mindar-image="imageTargetSrc: https://cdn.jsdelivr.net/gh/hiukim/mind-ar-js@1.2.5/examples/image-tracking/assets/card-example/card.mind;

<!-- ZMĚŇTE NA: -->
mindar-image="imageTargetSrc: https://ethnographic.cz/stramberk.mind;
```

**Nebo pokud jste dali .mind do podsložky:**
```html
mindar-image="imageTargetSrc: https://ethnographic.cz/assets/stramberk.mind;
```

**HOTOVO!** 🎉

---

## 📱 Testování:

### Příprava triggeru:

1. **Vytiskněte** váš originální obrázek Štramberku (ten černobílý)
2. **Velikost:** A5 nebo A4 (větší = lepší detekce)
3. **Papír:** Bílý, matný (ne lesklý)

### Spuštění AR:

```
1. Na mobilu otevřete: https://ethnographic.cz/ar-video.html
2. Povolte přístup ke kameře
3. Zamiřte kameru na vytištěný trigger
4. Video "Štramberk v mlze" se začne automaticky přehrávat!
```

---

## 🔧 Detailní instrukce:

### A) Kompilace triggeru - Krok za krokem

**1. Příprava obrázku:**
- Váš černobílý dřevoryt Štramberku
- Formát: PNG nebo JPG
- Minimální rozlišení: 640x480 px
- Doporučeno: 1920x1080 px nebo vyšší
- Vysoký kontrast je klíčový!

**2. Online compiler:**
```
URL: https://hiukim.github.io/mind-ar-js-doc/tools/compile

Postup:
1. Otevřete compiler v prohlížeči
2. Klikněte "Choose File"
3. Vyberte obrázek Štramberku
4. Klikněte "Start"
5. Počkejte 10-30 sekund (závisí na velikosti obrázku)
6. Zobrazí se náhled s detekovanými body
7. Klikněte "Download"
8. Uložte jako "stramberk.mind"
```

**3. Ověření:**
- Soubor by měl být 50-500 KB
- Formát: binární .mind soubor
- Pokud je příliš malý (<10 KB), zkuste obrázek s vyšším rozlišením

**4. Upload na server:**
```bash
# Přes FTP/SFTP:
Lokální: stramberk.mind
Vzdálený: /home/www/ethnographic.cz/stramberk.mind

# Nebo do podsložky:
Vzdálený: /home/www/ethnographic.cz/assets/stramberk.mind
```

---

### B) Aktualizace ar-video.html

**Najděte tento blok (řádek ~248-252):**

```html
<a-scene
    mindar-image="imageTargetSrc: https://cdn.jsdelivr.net/gh/hiukim/mind-ar-js@1.2.5/examples/image-tracking/assets/card-example/card.mind; autoStart: false; uiLoading: no; uiError: no; uiScanning: no;"
    ...>
```

**Změňte `imageTargetSrc` na:**

```html
<a-scene
    mindar-image="imageTargetSrc: https://ethnographic.cz/stramberk.mind; autoStart: false; uiLoading: no; uiError: no; uiScanning: no;"
    ...>
```

**DŮLEŽITÉ:**
- URL musí být přesná (včetně https://)
- Bez mezer kolem URL
- Středník na konci zůstává

**Uložte a nahrajte** aktualizovaný ar-video.html na server.

---

### C) Struktura souborů

**Doporučená organizace:**

```
ethnographic.cz/
├── index.html                          (hlavní stránka webu)
├── ar-video.html                       (Video AR aplikace) ⭐
├── stramberk-trigger.html              (Trigger info stránka)
├── camera-test.html                    (Diagnostika kamery)
├── stramberk.mind                      (Zkompilovaný trigger) ⭐
├── assets/
│   ├── videos/
│   │   └── stramberk-v-mlze.mp4       (Vaše video) ⭐
│   └── triggers/
│       ├── stramberk.png              (Originální trigger obrázek)
│       └── stramberk.mind             (Zkompilovaný trigger)
└── README.md
```

---

## 🎬 Správa videa:

### Aktuální video:
```
URL: https://ethnographic.cz/S%CC%8Ctramberk%20v%20mlze.mp4
Parametry:
- Loop: ANO (opakuje se)
- Autoplay: ANO (spustí se při detekci triggeru)
- Pause: ANO (zastaví se když trigger není vidět)
```

### Změna videa:

**V ar-video.html najděte (řádek ~257-264):**

```html
<video
    id="stramberk-video"
    src="https://ethnographic.cz/S%CC%8Ctramberk%20v%20mlze.mp4"
    ...>
</video>
```

**Změňte `src` na nové video:**

```html
<video
    id="stramberk-video"
    src="https://ethnographic.cz/assets/videos/nove-video.mp4"
    ...>
</video>
```

### Doporučené parametry videa:

```
Formát: MP4 (H.264 codec)
Rozlišení: 1920x1080 nebo 1280x720
Framerate: 30 fps
Bitrate: 5-10 Mbps
Velikost: max 20 MB (kvůli rychlému načítání)
Audio: Volitelné (můžete vypnout: muted="true")
Orientace: Na šířku (landscape) - pasuje na trigger
```

---

## 🐛 Troubleshooting:

### Trigger se nedetekuje:

**1. Zkontrolujte URL .mind souboru:**
```javascript
// V konzoli prohlížeče (F12):
console.log("Check .mind URL");
// Otevřete URL přímo v prohlížeči, měl by se stáhnout binární soubor
```

**2. Zkontrolujte kvalitu tisku:**
- ✅ Vytištěno na bílém papíru
- ✅ Vysoký kontrast (černá a bílá)
- ✅ Ostré, ne rozmazané
- ✅ Rovné, ne pokrčené
- ✅ Celé v záběru kamery

**3. Zkontrolujte osvětlení:**
- ✅ Dobře osvětleno
- ❌ Ne příliš tmavé
- ❌ Ne přímé slunce (příliš jasné)

**4. Zkuste s testovacím triggerem:**
```
1. Stáhněte testovací trigger:
   https://cdn.jsdelivr.net/gh/hiukim/mind-ar-js@1.2.5/examples/image-tracking/assets/card-example/card.png

2. Vytiskněte ho

3. Pokud funguje → problém je ve vašem triggeru (zkuste překompilovat)
   Pokud nefunguje → problém je v kameře nebo AR aplikaci
```

---

### Video se nenačítá:

**1. Zkontrolujte URL videa:**
```
V prohlížeči otevřete přímo:
https://ethnographic.cz/S%CC%8Ctramberk%20v%20mlze.mp4

Mělo by se spustit přehrávání videa.
```

**2. Zkontrolujte CORS:**
```
Video musí být na stejné doméně jako ar-video.html,
nebo server musí povolit CORS.
```

**3. Zkontrolujte formát:**
```
- MP4 s H.264 codecem je nejkompatibilnější
- Zkuste převést video pomocí HandBrake nebo FFmpeg
```

---

### Kamera se neaktivuje:

**Viz camera-test.html pro diagnostiku:**
```
https://ethnographic.cz/camera-test.html
```

**Nebo přečtěte DEBUG.md pro kompletní troubleshooting.**

---

## 📊 Očekávané výsledky:

### Po správném nastavení:

```
1. Uživatel otevře: https://ethnographic.cz/ar-video.html
2. Povolí přístup ke kameře
3. Zamiří telefon na vytištěný trigger Štramberku
4. Po 1-2 sekundách:
   - Trigger je detekován ✅
   - Video "Štramberk v mlze" se začne přehrávat 🎬
   - Video se přizpůsobí velikosti triggeru
   - Video se opakuje (loop)
5. Když uživatel odejme kameru:
   - Video se pozastaví
   - Čeká na novou detekci triggeru
```

---

## 🎯 Kontrolní checklist:

Před finálním testováním zkontrolujte:

- [ ] Trigger obrázek zkompilován do .mind souboru
- [ ] stramberk.mind nahrán na server
- [ ] ar-video.html aktualizován s URL .mind souboru
- [ ] Video je dostupné na ethnographic.cz
- [ ] Trigger vytištěn na bílém papíru (A4/A5)
- [ ] HTTPS funguje (https://ethnographic.cz)
- [ ] Testováno na mobilu (iOS Safari nebo Android Chrome)
- [ ] Kamera se aktivuje
- [ ] Trigger se detekuje
- [ ] Video se přehrává

---

## 📞 Potřebujete pomoc?

1. **Camera-test.html** - Diagnostika kamery
2. **DEBUG.md** - Kompletní troubleshooting
3. **MindAR docs** - https://hiukim.github.io/mind-ar-js-doc/

---

**Vytvořeno pro ethnographic.cz | Štramberk Video AR | 2026-01-13**
