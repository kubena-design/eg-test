# 🚀 WebAR Demo Projekt

Kompletní sada WebAR (Web Augmented Reality) aplikací - od jednoduchého 3D vieweru po pokročilý image tracking AR systém podobný Artivive nebo mywebAR.

## 📦 Co je v projektu

### 1️⃣ **index.html** - Jednoduchý 3D Viewer (Model Viewer)
Základní landing page s interaktivním 3D prohlížečem a AR režimem.
- ✅ Ideální pro: produktové prezentace, e-commerce, rychlé demo
- ✅ Obtížnost: Začátečník
- ✅ AR typ: Surface placement (umístění na podlahu)

### 2️⃣ **ar-tracker.html** - Image Tracking AR (MindAR) ⭐ NOVÉ
**Pokročilá aplikace** podobná Artivive - kamera se aktivuje a po zaměření na trigger zobrazí 3D model s animací.
- ✅ Ideální pro: marketing kampaně, umělecké instalace, interaktivní postory
- ✅ Obtížnost: Středně pokročilý
- ✅ AR typ: Image tracking (marker-based AR)
- ✅ Funkce: Automatická aktivace kamery, detekce triggeru, animace modelu

### 3️⃣ **trigger.html** - Stránka s triggerem
Obsahuje testovací trigger obrázek ke stažení a návod jak vytvořit vlastní.

## ✨ Funkce

### Model Viewer (index.html):
- 📱 **Bez instalace** - Funguje přímo v prohlížeči
- 🔄 **Interaktivní 3D** - Otáčení, přibližování, prozkoumávání modelu
- 🎯 **AR režim** - Umístění 3D modelu do reálného prostoru pomocí AR
- 🎨 **Moderní design** - Responzivní a profesionálně vypadající
- ⚡ **Rychlé** - Žádný build proces, žádné závislosti

### AR Tracker (ar-tracker.html):
- 📷 **Automatická aktivace kamery** - Spustí se při načtení stránky
- 🎯 **Image tracking** - Detekce triggeru (marker obrázku)
- 🎬 **Animace** - Automatické přehrání animací z 3D modelu
- 🔍 **Real-time scanning** - Živé skenování prostředí
- 🎨 **AR overlay UI** - Moderní rozhraní s instrukcemi a notifikacemi
- ⚡ **Rychlá detekce** - Okamžitá reakce na trigger

## 🖥️ Jak spustit

### Varianta 1: Otevřít přímo v prohlížeči (nejjednodušší)

Stačí otevřít soubor `index.html` v prohlížeči:

```bash
# Na Linuxu:
xdg-open index.html

# Na macOS:
open index.html

# Na Windows:
start index.html
```

Nebo jednoduše **dvojklik na `index.html`** v průzkumníku souborů.

### Varianta 2: Spustit lokální server (doporučeno pro vývoj)

Pro plnou funkčnost AR je lepší spustit lokální server:

#### S Pythonem:
```bash
# Python 3
python3 -m http.server 8000

# Python 2
python -m SimpleHTTPServer 8000
```

#### S Node.js (npx):
```bash
npx http-server -p 8000
```

#### S PHP:
```bash
php -S localhost:8000
```

Poté otevřete prohlížeč na: `http://localhost:8000`

---

## 🎯 Návod: AR Image Tracker (ar-tracker.html)

### Příprava:

1. **Stáhněte trigger obrázek:**
   - Otevřete `trigger.html` v prohlížeči
   - Klikněte na "Stáhnout trigger"
   - Zobrazte ho na jiném zařízení NEBO ho vytiskněte (doporučeno)

2. **Spusťte AR aplikaci:**
   ```bash
   # Lokální server (NUTNÉ pro přístup ke kameře!)
   python3 -m http.server 8000
   ```

3. **Otevřete na mobilu:**
   - Zadejte: `http://[IP-VAŠEHO-PC]:8000/ar-tracker.html`
   - Nebo nahrajte na HTTPS hosting (GitHub Pages, Netlify)

### Použití:

1. **Povolte přístup ke kameře** když se vás prohlížeč zeptá
2. **Zamiřte telefon na trigger obrázek**
3. **Držte celý trigger v záběru kamery**
4. **Čekejte 1-2 sekundy** - aplikace detekuje trigger
5. **3D model se objeví na triggeru s animací!** 🎉

### Tipy pro nejlepší výsledky:

- ✅ **Tisk triggeru** funguje lépe než zobrazení na obrazovce
- ✅ **Dobré osvětlení** - ne příliš tmavé ani přímé světlo
- ✅ **Stabilní držení** - celý trigger musí být viditelný
- ✅ **Vzdálenost 20-50 cm** od triggeru
- ❌ Vyhněte se rozmazaným nebo pokrčeným triggerům

---

## 📱 Testování AR na mobilu

1. **Nahrajte na hosting** (GitHub Pages, Netlify, Vercel) nebo použijte nástroj jako [ngrok](https://ngrok.com/) pro sdílení lokálního serveru
2. **Otevřete na mobilu** v Safari (iOS) nebo Chrome (Android)
3. **Klikněte na tlačítko "Zobrazit v AR"**
4. **Namiřte telefon na podlahu** a umístěte model

### Podporovaná zařízení pro AR:
- ✅ **iOS 12+** (Safari) - AR Quick Look
- ✅ **Android 8+** s ARCore (Chrome)

## 🎨 Přizpůsobení

### Změna 3D modelu

V souboru `index.html` najděte řádek s `model-viewer` a změňte `src`:

```html
<model-viewer
    src="cesta/k/vasemu/modelu.glb"
    ...
```

**Formáty:** `.glb` nebo `.gltf` (doporučeno: `.glb`)

### Kde získat 3D modely:

- [Sketchfab](https://sketchfab.com/) - Tisíce free modelů
- [Google Poly Archive](https://poly.pizza/) - Archiv Google Poly
- [CGTrader](https://www.cgtrader.com/) - Free i placené modely
- [TurboSquid](https://www.turbosquid.com/) - Profesionální modely

### Vlastní model

Pokud máte vlastní model, umístěte ho do složky projektu:

```
eg-test/
├── index.html
├── models/
│   └── vas-model.glb
└── README.md
```

A použijte:
```html
src="models/vas-model.glb"
```

### Změna modelu a triggeru v AR Trackeru

#### Vlastní 3D model s animací:

V souboru `ar-tracker.html` najděte:

```html
<a-asset-item id="avatarModel" src="URL_VAŠEHO_MODELU.gltf"></a-asset-item>
```

**Požadavky na model:**
- Formát: `.gltf` nebo `.glb`
- S animacemi: model musí obsahovat animation clips
- Velikost: doporučeno max 10 MB
- Optimalizováno pro web

**Kde získat animované modely:**
- [Mixamo](https://www.mixamo.com/) - Animované postavy zdarma
- [Sketchfab](https://sketchfab.com/) - filtr "Animated"
- [Ready Player Me](https://readyplayer.me/) - Avatary s animacemi

#### Vlastní trigger obrázek:

1. **Připravte si obrázek** (min. 640x480 px, vysoký kontrast, detaily)
2. **Kompilujte do .mind souboru:**
   - Jděte na: [MindAR Compiler](https://hiukim.github.io/mind-ar-js-doc/tools/compile)
   - Nahrajte váš obrázek
   - Stáhněte vygenerovaný `.mind` soubor
3. **Aktualizujte kód** v `ar-tracker.html`:
   ```html
   <a-scene mindar-image="imageTargetSrc: cesta/k/vasemu-trigger.mind; ...">
   ```

**Tipy pro dobré triggery:**
- ✅ Loga, ilustrace, fotografie s detaily
- ✅ Vysoký kontrast mezi barvami
- ✅ Ostré hrany a unikátní vzory
- ❌ Čistě bílé plochy, opakující se vzory, čistý text

## ⚙️ Konfigurace Model Viewer

### Základní parametry:

```html
<model-viewer
    src="model.glb"              <!-- Cesta k modelu -->
    alt="Popis modelu"           <!-- Alt text pro přístupnost -->

    camera-controls              <!-- Povolit ovládání kamerou -->
    auto-rotate                  <!-- Automatické otáčení -->
    rotation-per-second="30deg"  <!-- Rychlost otáčení -->

    ar                           <!-- Povolit AR -->
    ar-modes="webxr scene-viewer quick-look"  <!-- AR režimy -->

    shadow-intensity="1"         <!-- Intenzita stínu -->
    exposure="1"                 <!-- Expozice -->

    environment-image="neutral"  <!-- Osvětlení prostředí -->
    skybox-image="path.hdr"      <!-- Vlastní skybox -->
>
</model-viewer>
```

### Pokročilé funkce:

```html
<!-- Hotspoty (informační značky) -->
<button class="Hotspot" slot="hotspot-1" data-position="0 1.5 0">
    ℹ️ Info o produktu
</button>

<!-- Více variant modelu -->
<model-viewer>
    <button slot="variant-button" data-variant-name="Red">Červená</button>
    <button slot="variant-button" data-variant-name="Blue">Modrá</button>
</model-viewer>
```

## 🔧 Technologie

### Model Viewer (index.html):
- **Google Model Viewer** - WebComponent pro zobrazení 3D modelů
- **WebXR** - AR v prohlížeči (Chrome Android)
- **AR Quick Look** - AR na iOS
- **Scene Viewer** - AR na Android
- **Three.js** - 3D engine (pod kapotou Model Viewer)

### AR Tracker (ar-tracker.html):
- **MindAR** - Image tracking AR knihovna (open-source)
- **A-Frame** - Web framework pro VR/AR (postavený na Three.js)
- **Three.js** - 3D rendering engine
- **WebGL** - Hardware-accelerated grafika
- **WebRTC** - Přístup ke kameře

### Srovnání technologií:

| Funkce | Model Viewer | MindAR |
|--------|--------------|--------|
| **Obtížnost** | ⭐ Jednoduchá | ⭐⭐ Středně pokročilá |
| **AR typ** | Surface placement | Image tracking |
| **Animace** | ✅ Ano | ✅ Ano |
| **Trigger** | ❌ Ne (umístění na podlahu) | ✅ Ano (marker) |
| **Aktivace kamery** | ⚡ Při kliknutí na AR tlačítko | ⚡ Automaticky při načtení |
| **Use case** | Produkty, e-commerce | Marketing, umění, instalace |

## 📚 Další zdroje

### Model Viewer:
- [Model Viewer dokumentace](https://modelviewer.dev/)
- [Model Viewer příklady](https://modelviewer.dev/examples/)
- [WebXR Device API](https://www.w3.org/TR/webxr/)
- [AR Quick Look](https://developer.apple.com/augmented-reality/quick-look/)

### MindAR:
- [MindAR Dokumentace](https://hiukim.github.io/mind-ar-js-doc/)
- [MindAR GitHub](https://github.com/hiukim/mind-ar-js)
- [MindAR Compiler (vytvoření .mind souboru)](https://hiukim.github.io/mind-ar-js-doc/tools/compile)
- [A-Frame Dokumentace](https://aframe.io/docs/)

### 3D Modely:
- [Mixamo](https://www.mixamo.com/) - Animované postavy
- [Sketchfab](https://sketchfab.com/) - Největší 3D knihovna
- [Poly Pizza](https://poly.pizza/) - Google Poly archiv
- [Ready Player Me](https://readyplayer.me/) - Avatar generátor

## 🚀 Nasazení

### GitHub Pages (zdarma):

1. Push do GitHub repository
2. Jděte do Settings → Pages
3. Vyberte branch a složku
4. Uložte a vaše stránka bude dostupná na `https://username.github.io/repo-name`

### Netlify (zdarma):

```bash
# Instalace Netlify CLI
npm install -g netlify-cli

# Deploy
netlify deploy --prod
```

### Vercel (zdarma):

```bash
# Instalace Vercel CLI
npm install -g vercel

# Deploy
vercel --prod
```

## 💡 Tipy

### Obecné:
1. **Optimalizace modelů**: Použijte [glTF Pipeline](https://github.com/CesiumGS/gltf-pipeline) pro kompresi
2. **HTTPS je nutné**: AR vyžaduje HTTPS nebo localhost pro přístup ke kameře
3. **Velikost modelu**: Držte modely pod 5 MB pro rychlé načítání (Model Viewer) nebo 10 MB (AR Tracker)
4. **Textury**: Použijte komprimované textury (JPEG místo PNG kde je to možné)
5. **Testování**: Vždy testujte na reálných mobilních zařízeních

### Specifické pro AR Tracker:
6. **Kvalita triggeru**: Vytisknuté triggery fungují lépe než digitální displeje
7. **Osvětlení**: Vyhněte se přímému slunci nebo velmi tmavému prostředí
8. **Stabilita**: Držte trigger stabilně, pohyb zpomaluje detekci
9. **Vzdálenost**: Optimální vzdálenost je 20-50 cm od triggeru
10. **Velikost triggeru**: Větší fyzická velikost triggeru (A5, A4) = lepší detekce

### Troubleshooting:

**AR Tracker nefunguje:**
- ✅ Zkontrolujte, zda běží na HTTPS nebo localhost
- ✅ Povolte přístup ke kameře v nastavení prohlížeče
- ✅ Zkuste jiný prohlížeč (Chrome/Safari doporučeno)
- ✅ Ověřte, že celý trigger je v záběru kamery
- ✅ Zkuste vytisknout trigger místo zobrazení na obrazovce

**Model se nenačítá:**
- ✅ Zkontrolujte konzoli prohlížeče (F12) pro chyby
- ✅ Ověřte, že URL modelu je správná a dostupná
- ✅ Model musí být ve formátu .glb nebo .gltf
- ✅ Zkontrolujte CORS hlavičky (pokud model je na jiné doméně)

## 📄 Licence

Tento demo projekt je volně k použití. 3D model astronauta je od Google (CC-BY 3.0).

---

**Vytvořeno s ❤️ pro WebAR demonstraci**
