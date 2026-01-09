# 🚀 WebAR Landing Page Demo

Jednoduchá a funkční landing page s WebAR (Web Augmented Reality) využívající Google Model Viewer.

## ✨ Funkce

- 📱 **Bez instalace** - Funguje přímo v prohlížeči
- 🔄 **Interaktivní 3D** - Otáčení, přibližování, prozkoumávání modelu
- 🎯 **AR režim** - Umístění 3D modelu do reálného prostoru pomocí AR
- 🎨 **Moderní design** - Responzivní a profesionálně vypadající
- ⚡ **Rychlé** - Žádný build proces, žádné závislosti

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

- **Google Model Viewer** - WebComponent pro zobrazení 3D modelů
- **WebXR** - AR v prohlížeči (Chrome Android)
- **AR Quick Look** - AR na iOS
- **Scene Viewer** - AR na Android
- **Three.js** - 3D engine (pod kapotou Model Viewer)

## 📚 Další zdroje

- [Model Viewer dokumentace](https://modelviewer.dev/)
- [Model Viewer příklady](https://modelviewer.dev/examples/)
- [WebXR Device API](https://www.w3.org/TR/webxr/)
- [AR Quick Look](https://developer.apple.com/augmented-reality/quick-look/)

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

1. **Optimalizace modelů**: Použijte [glTF Pipeline](https://github.com/CesiumGS/gltf-pipeline) pro kompresi
2. **HTTPS je nutné**: AR vyžaduje HTTPS nebo localhost
3. **Velikost modelu**: Držte modely pod 5 MB pro rychlé načítání
4. **Textury**: Použijte komprimované textury (JPEG místo PNG kde je to možné)
5. **Testování**: Vždy testujte na reálných mobilních zařízeních

## 📄 Licence

Tento demo projekt je volně k použití. 3D model astronauta je od Google (CC-BY 3.0).

---

**Vytvořeno s ❤️ pro WebAR demonstraci**
