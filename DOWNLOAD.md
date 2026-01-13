# 📦 Stažení WebAR projektu

Tento soubor obsahuje odkazy a instrukce pro stažení kompletního WebAR projektu.

## 📥 Dostupné archivy

### ZIP archiv (25 KB)
```
webar-project.zip
```
Ideální pro Windows uživatele.

### TAR.GZ archiv (20 KB)
```
webar-project.tar.gz
```
Ideální pro Linux/Mac uživatele.

## 📁 Obsah archivu

Oba archivy obsahují stejné soubory:

```
📦 webar-project/
├── 📄 ar-tracker.html      (16 KB) - Image tracking AR aplikace (Artivive-style)
├── 📄 camera-test.html     (18 KB) - Diagnostický nástroj pro kameru
├── 📄 index.html           (8 KB)  - Jednoduchý 3D viewer (Model Viewer)
├── 📄 trigger.html         (12 KB) - Stránka s triggerem ke stažení
├── 📄 DEBUG.md             (10 KB) - Kompletní troubleshooting průvodce
└── 📄 README.md            (12 KB) - Hlavní dokumentace projektu
```

**Celková velikost:** ~75 KB (nekomprimovaně)

## 🚀 Jak použít po stažení

### Krok 1: Rozbalte archiv

**Windows:**
```
Pravé tlačítko myši → Extrahovat vše
```

**Linux/Mac:**
```bash
unzip webar-project.zip
# nebo
tar -xzf webar-project.tar.gz
```

### Krok 2: Nahrajte na hosting

**Možnost A - GitHub Pages (doporučeno):**
```bash
# 1. Vytvořte nový GitHub repository
# 2. Nahrajte soubory
git init
git add .
git commit -m "Add WebAR project"
git branch -M main
git remote add origin https://github.com/VASE-JMENO/webar-project.git
git push -u origin main

# 3. Aktivujte GitHub Pages v Settings → Pages
```

**Možnost B - Netlify:**
```bash
# Přetáhněte složku do Netlify Drop zone
# Nebo použijte CLI:
netlify deploy --prod
```

**Možnost C - Vercel:**
```bash
vercel --prod
```

### Krok 3: Otestujte

1. Otevřete na mobilu: `https://vase-domena.cz/camera-test.html`
2. Povolte přístup ke kameře
3. Zkontrolujte, že kamera funguje
4. Otevřete: `https://vase-domena.cz/ar-tracker.html`
5. Stáhněte trigger z: `https://vase-domena.cz/trigger.html`
6. Zamiřte kameru na trigger a užívejte si AR!

## 🔧 Lokální testování

**Spusťte lokální server:**

```bash
# Python 3
python3 -m http.server 8000

# Python 2
python -m SimpleHTTPServer 8000

# Node.js
npx http-server -p 8000

# PHP
php -S localhost:8000
```

**Pak otevřete:** `http://localhost:8000`

**Pro testování na mobilu (s HTTPS):**
```bash
# Použijte ngrok
ngrok http 8000
# Získáte HTTPS URL kterou můžete otevřít na mobilu
```

## 📱 Testování jednotlivých souborů

### 1. Index.html - Model Viewer
```
Otevřete přímo v prohlížeči nebo na http://localhost:8000/index.html
```
- Funguje i bez HTTPS (ale AR režim vyžaduje HTTPS)
- Interaktivní 3D model astronauta
- Tlačítko "Zobrazit v AR" pro mobilní zařízení

### 2. Camera-test.html - Diagnostika
```
http://localhost:8000/camera-test.html (nebo na HTTPS hosting)
```
- Otestuje přístup ke kameře
- Zobrazí informace o zařízení
- Diagnostikuje problémy
- **Vyžaduje HTTPS** (nebo localhost)

### 3. AR-tracker.html - Image Tracking AR
```
https://vase-domena.cz/ar-tracker.html (MUSÍ být HTTPS!)
```
- Aktivuje kameru automaticky
- Detekuje trigger obrázek
- Zobrazí 3D model s animací
- **KRITICKÉ: Vyžaduje HTTPS!**

### 4. Trigger.html - Trigger ke stažení
```
http://localhost:8000/trigger.html
```
- Zobrazí testovací trigger
- Tlačítko ke stažení triggeru
- Návod na vytvoření vlastního triggeru

## 📚 Dokumentace

### README.md
Hlavní dokumentace obsahující:
- Přehled všech souborů
- Návod k použití
- Customizace modelů a triggerů
- Technologie a zdroje

### DEBUG.md
Troubleshooting průvodce obsahující:
- Řešení běžných problémů
- Platform-specifické instrukce (iOS/Android)
- Pokročilé debugování
- Checklist pro diagnostiku

## 🎯 Rychlý start pro https://ethnographic.cz

Pokud máte přístup k doméně ethnographic.cz:

```bash
# 1. Rozbalte archiv
unzip webar-project.zip

# 2. Nahrajte všechny soubory do root složky webu přes FTP/SFTP
# Struktura by měla být:
# https://ethnographic.cz/index.html
# https://ethnographic.cz/ar-tracker.html
# https://ethnographic.cz/camera-test.html
# https://ethnographic.cz/trigger.html
# https://ethnographic.cz/README.md
# https://ethnographic.cz/DEBUG.md

# 3. Otestujte:
# https://ethnographic.cz/camera-test.html
# https://ethnographic.cz/ar-tracker.html
```

## ⚠️ Důležité poznámky

1. **HTTPS je povinné** pro ar-tracker.html a camera-test.html
2. **Povolte přístup ke kameře** v prohlížeči
3. **Vytiskněte trigger** pro nejlepší detekci
4. **Testujte na reálném mobilu** (iOS Safari nebo Chrome Android)
5. **Zavřete ostatní aplikace** používající kameru

## 🆘 Podpora

**Problémy s kamerou?**
→ Otevřete camera-test.html pro diagnostiku

**Trigger se nedetekuje?**
→ Přečtěte si DEBUG.md → Sekce "Trigger se nedetekuje"

**Jiný problém?**
→ Celý DEBUG.md obsahuje řešení nejčastějších problémů

## 📄 Licence

Tento projekt je volně k použití pro osobní i komerční účely.

3D modely a knihovny mají vlastní licence:
- Model astronauta: Google (CC-BY 3.0)
- MindAR: MIT License
- A-Frame: MIT License
- Model Viewer: Apache 2.0

---

**Vytvořeno pro WebAR projekt | Poslední aktualizace: 2026-01-13**
