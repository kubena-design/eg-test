# Kontext projektu: WebAR Štramberk (ethnographic.cz)

Souhrnný kontext pro navazující práci na projektu. Popisuje cíl, zvolenou technologii, co je hotové, co nefunguje a co je potřeba udělat dál.

## Cíl

Webová AR aplikace ve stylu **Artivive / mywebAR**: uživatel otevře stránku na mobilu, spustí se kamera, a když ji namíří na tištěný obrázek (trigger), obrázek „ožije“ – přes něj se přehraje video.

- **Trigger:** černobílá ilustrace ve stylu dřevorytu – Štramberská Trúba, lampa s cedulkou „1923“, stromy, mraky, dole nápis „ŠTRAMBERK“. Formát na výšku (cca 3:4). Pro tracking je velmi vhodná (vysoký kontrast, hodně detailů).
- **Video:** `https://ethnographic.cz/S%CC%8Ctramberk%20v%20mlze.mp4` („Štramberk v mlze“)
- **Hosting:** `https://ethnographic.cz/` (HTTPS – nutné pro přístup ke kameře)
- **Repozitář:** `kubena-design/eg-test`, větev `claude/webar-landing-page-UsD5U`

## Technologie

| Část | Knihovna | Poznámka |
|---|---|---|
| Image tracking | MindAR 1.2.5 (`mindar-image-aframe`) | open-source, zdarma, běží v prohlížeči |
| 3D scéna | A-Frame 1.4.2 (nad Three.js) | |
| 3D viewer bez triggeru | Google `<model-viewer>` 3.4.0 | jen pro `index.html` |

Vše je čisté HTML + CDN skripty, žádný build, žádné závislosti.

MindAR potřebuje trigger zkompilovaný do souboru **`.mind`**. Ten se vyrábí z obrázku v online nástroji https://hiukim.github.io/mind-ar-js-doc/tools/compile (běží v prohlížeči, nejde spustit z příkazové řádky bez dalšího nastavení).

## Soubory

| Soubor | Účel | Stav |
|---|---|---|
| `ar-video.html` | **Hlavní aplikace** – video přes trigger (Artivive styl) | funguje kamera, trigger zatím testovací |
| `stramberk-trigger.html` | Info stránka k triggeru + návod na kompilaci `.mind` | obrázek triggeru tam zatím není, jen zástupný blok |
| `STRAMBERK-SETUP.md` | Návod krok za krokem pro Štramberk | |
| `ar-tracker.html` | Starší demo: 3D model na testovacím triggeru | obsahuje známé chyby (viz níže) |
| `trigger.html` | Stránka s testovacím triggerem MindAR (karta) | |
| `camera-test.html` | Diagnostika kamery (HTTPS, oprávnění, chybové kódy) | |
| `index.html` | Jednoduchý 3D viewer s AR tlačítkem (model-viewer) | |
| `README.md`, `DEBUG.md`, `DOWNLOAD.md` | Dokumentace, troubleshooting, návod ke stažení | |
| `webar-project.zip` / `.tar.gz` | Archiv HTML + MD souborů ke stažení | **neobsahuje** `AR-CONTEXT.md`, při změnách přegenerovat |

## Jak funguje `ar-video.html`

1. Kontrola HTTPS a dostupnosti `navigator.mediaDevices`.
2. Čeká se na událost `loaded` od `<a-scene>`, teprve pak se vezme `sceneEl.systems['mindar-image-system']` a zavolá `start()` (`autoStart: false`).
3. Na `targetFound` se zavolá `video.play()`, na `targetLost` `video.pause()`.
4. Video je textura na `<a-plane>` uvnitř `<a-entity mindar-image-target="targetIndex: 0">`.
5. Debug režim: `?debug=true` v URL vypisuje kroky přes `alert()`.

## Historie (commity)

1. `ad92ced` – landing page s model-viewer (`index.html`)
2. `aeba026` – image tracking s 3D modelem (`ar-tracker.html`, `trigger.html`)
3. `65557d5` – diagnostika kamery, lepší chybové hlášky (`camera-test.html`, `DEBUG.md`)
4. `13776db` – archivy ke stažení (`DOWNLOAD.md`)
5. `ff9dc8f` – video AR pro Štramberk (`ar-video.html`, `stramberk-trigger.html`, `STRAMBERK-SETUP.md`)
6. `0d63e2f` – oprava chyby `undefined is not an object (evaluating 'arSystem.start')` na iOS Safari: AR systém se bral dřív, než se scéna načetla
7. `7a8fbe6` – přegenerované archivy

## Aktuální stav a známé problémy

Stav podle posledního testu na iPhonu (Safari): **kamera se spouští, ale trigger Štramberku se nedetekuje.**

### Blokující

1. **Chybí `stramberk.mind`.** `ar-video.html` (řádek ~251) stále používá testovací trigger MindAR (`.../card-example/card.mind`), proto obrázek Štramberku nic nespustí. Je potřeba:
   - zkompilovat obrázek Štramberku v MindAR compileru,
   - nahrát výsledek jako `https://ethnographic.cz/stramberk.mind`,
   - v `ar-video.html` změnit `imageTargetSrc` na tuto URL.

### Pravděpodobné problémy, které se ukážou až po zprovoznění triggeru

2. ~~Video na iOS se nemusí spustit~~ – **opraveno:** `<video>` má `muted` (atribut i `video.muted = true` v JS). Video je proto bez zvuku. Pokud bude zvuk potřeba, je nutné přidat tlačítko „Zapnout zvuk“ (iOS povolí zvuk jen po dotyku uživatele).
3. ~~Nesedí poměr stran~~ – **opraveno:** `<a-plane id="video-plane">` má výchozí výšku `1.333` (trigger 3:4, MindAR bere šířku triggeru jako 1) a po načtení metadat videa se výška nastaví na `videoHeight / videoWidth`, takže video není deformované. Video zakryje celý trigger jen tehdy, když má stejný poměr stran (3:4) – ideálně ho exportovat se stejným ořezem jako trigger.
4. **Velikost videa.** Neověřeno. Pro mobil doporučeno MP4 (H.264), do ~20 MB.

### Ve starších demech (netýká se hlavní aplikace)

5. `ar-tracker.html` má stále původní chybu s `arSystem` (bere ho v `DOMContentLoaded` před načtením scény), takže na iOS spadne stejně jako dřív `ar-video.html`.
6. `ar-tracker.html` používá komponentu `animation-mixer`, ale nenačítá `aframe-extras`, kde ta komponenta je. Animace modelu se tedy nepřehraje.

## Další kroky (podle priority)

1. Zkompilovat trigger → `stramberk.mind` → nahrát na ethnographic.cz → upravit `imageTargetSrc` v `ar-video.html`.
2. Ověřit, že video má poměr stran 3:4 jako trigger (pokud ne, upravit export videa). Volitelně tlačítko pro zvuk.
3. Nahrát obrázek triggeru na web (např. `stramberk-trigger.png`) a zobrazit ho ve `stramberk-trigger.html` místo zástupného bloku.
4. Otestovat na iPhonu (Safari) a Androidu (Chrome) s vytištěným triggerem (A5/A4, matný papír).
5. Volitelně: opravit nebo odstranit staré demo `ar-tracker.html`, přegenerovat archivy.

## Testování

- Testovat jen přes HTTPS: `https://ethnographic.cz/ar-video.html`
- Při problémech s kamerou nejdřív `https://ethnographic.cz/camera-test.html`
- Podrobnější hlášky: `https://ethnographic.cz/ar-video.html?debug=true`
- Trigger tisknout, ne zobrazovat na displeji (odlesky), vzdálenost 20–50 cm, celý obrázek v záběru.
