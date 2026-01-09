# 🐛 Debugging Guide - Problémy s kamerou

Tento průvodce vám pomůže diagnostikovat a vyřešit problémy s kamerou ve WebAR aplikaci.

## 🔍 Rychlá diagnostika

### Krok 1: Otevřete camera-test.html

```
https://ethnographic.cz/camera-test.html
```

Tento nástroj otestuje:
- ✅ Zda prohlížeč podporuje MediaDevices API
- ✅ Zda běžíte na HTTPS
- ✅ Přístup ke kameře
- ✅ Dostupné kamery na zařízení
- ✅ Rozlišení a nastavení kamery

### Krok 2: Aktivujte debug mód

Přidejte `?debug=true` na konec URL:

```
https://ethnographic.cz/ar-tracker.html?debug=true
```

Debug mód zobrazí všechny logy a chybové zprávy pomocí alert dialogů.

---

## 🚨 Nejčastější problémy a řešení

### 1. ❌ Kamera se nespouští vůbec

**Symptom:** Aplikace zůstává na loading obrazovce

**Možné příčiny:**

#### A) Není HTTPS
```
❌ CHYBA: http://adresa.cz
✅ SPRÁVNĚ: https://adresa.cz
```

**Řešení:**
- Nahrajte aplikaci na HTTPS hosting (GitHub Pages, Netlify, Vercel)
- Nebo použijte localhost pro vývoj

#### B) Prohlížeč nepodporuje MediaDevices API

**Řešení:**
- Aktualizujte prohlížeč na nejnovější verzi
- Použijte Chrome (Android) nebo Safari (iOS)
- Minimální verze:
  - iOS Safari 11+
  - Chrome Android 53+
  - Firefox 36+

#### C) Kamera je blokována v nastavení

**iOS Safari:**
```
1. Nastavení → Safari → Nastavení webových stránek
2. Najděte https://ethnographic.cz
3. Kamera → Povolit
```

**Chrome Android:**
```
1. Nastavení → Weby a stahování → Oprávnění
2. Kamera → Najděte ethnographic.cz
3. Povolte přístup
```

**Chrome Desktop:**
```
1. Klikněte na ikonu kamery/zámku v adresním řádku
2. Nastavení webu
3. Kamera → Povolit
```

---

### 2. ⚠️ "NotAllowedError" - Přístup zamítnut

**Symptom:** Prohlížeč se zeptá na povolení kamery, ale nepovolíte ho nebo ho omylem zamítnete

**Řešení:**

#### Způsob 1: Reset oprávnění v prohlížeči
1. Klikněte na ikonu kamery/zámku v adresním řádku
2. Klikněte na "Reset oprávnění" nebo "Obnovit na výchozí"
3. Obnovte stránku (F5)

#### Způsob 2: Vymazat data webu
1. Chrome: Nastavení → Zabezpečení a soukromí → Vymazat data procházení
2. Vyberte "Soubory cookie a data webů"
3. Zadejte ethnographic.cz
4. Vymažte a obnovte stránku

#### Způsob 3: Použít anonymní/inkognito režim
- Chrome: Ctrl+Shift+N (Cmd+Shift+N na Mac)
- Safari: Cmd+Shift+N
- Nové okno nemá žádná uložená oprávnění

---

### 3. 🔴 "NotReadableError" - Kamera je používána

**Symptom:** Kamera fungovala, ale najednou přestala

**Řešení:**
1. **Zavřete ostatní aplikace** používající kameru:
   - Videokonference (Zoom, Meet, Teams)
   - Jiné AR aplikace
   - Instagram, TikTok, Snapchat kamery
   - Jiné karty v prohlížeči s kamerou

2. **Restartujte prohlížeč:**
   - Zavřete VŠECHNY karty
   - Ukončete prohlížeč úplně (ne jen minimalizovat)
   - Otevřete znovu

3. **Restartujte zařízení** (pokud výše nefunguje)

---

### 4. ❓ "NotFoundError" - Kamera nenalezena

**Symptom:** Zařízení tvrdí, že nemá kameru (ale víte, že ji má)

**Řešení:**
1. **Zkontrolujte fyzickou kameru:**
   - Odlepte případnou nálepku/krytku na kameře
   - Zkuste nativní aplikaci Kamera - funguje?

2. **Zkontrolujte oprávnění systému:**
   - iOS: Nastavení → Soukromí → Kamera → Safari (musí být zapnuto)
   - Android: Nastavení → Aplikace → Chrome → Oprávnění → Kamera (povolit)

3. **Zkuste jiný prohlížeč:**
   - Někdy má jeden prohlížeč blokovaný přístup, jiný ne

---

### 5. 🖼️ Trigger se nedetekuje

**Symptom:** Kamera funguje, ale 3D model se neobjeví

**Diagnostika:**
- ✅ Je celý trigger viditelný v kameře?
- ✅ Je trigger dostatečně velký? (min. 10x10 cm doporučeno)
- ✅ Je dobré osvětlení? (ne příliš tmavé ani přímé slunce)
- ✅ Je trigger ostrý a nerozmáznutý?
- ✅ Držíte telefon stabilně?

**Řešení:**

#### A) Vytiskněte trigger
```
✅ NEJLEPŠÍ: Vytisknout na bílý papír A5/A4
⚠️ MÉNĚ SPOLEHLIVÉ: Zobrazit na druhé obrazovce
❌ ŠPATNÉ: Zobrazit na lesklé obrazovce (reflexe)
```

#### B) Optimální podmínky:
- **Osvětlení:** Denní světlo nebo běžné vnitřní osvětlení
- **Vzdálenost:** 20-50 cm od triggeru
- **Úhel:** Kamera kolmo k triggeru (ne šikmo)
- **Stabilita:** Držte trigger i telefon stabilně

#### C) Zkontrolujte trigger:
1. Stáhněte si trigger znovu: [trigger.html](https://ethnographic.cz/trigger.html)
2. Ověřte, že je celý viditelný (včetně okrajů)
3. Zkuste větší fyzickou velikost (A4 místo A5)

---

### 6. 🐌 Aplikace je pomalá / zasekává se

**Symptom:** Kamera běží, ale je zpožděná nebo se zasekává

**Řešení:**
1. **Zavřete ostatní karty** v prohlížeči
2. **Snižte zátěž telefonu:**
   - Zavřete aplikace na pozadí
   - Uvolněte RAM
3. **Zkuste restart** prohlížeče nebo telefonu
4. **Vyčistěte cache** prohlížeče
5. **Zkuste jednodušší model:** Aktuální model může být příliš složitý pro vaše zařízení

---

## 🔧 Pokročilé debugování

### Kontrola konzole prohlížeče

#### Desktop Chrome:
1. F12 nebo Ctrl+Shift+I
2. Záložka Console
3. Hledejte červené chybové zprávy

#### Safari iOS (vzdálené debugování):
1. Na Macu: Safari → Vývoj → [Váš iPhone]
2. Vyberte ethnographic.cz
3. Otevře se Web Inspector s konzolí

#### Chrome Android (vzdálené debugování):
1. Na počítači: chrome://inspect
2. Připojte telefon USB kabelem
3. Povolte USB debugging na telefonu
4. Klikněte na "Inspect" u ethnographic.cz

### Kontrola network požadavků

Zkontrolujte, zda se načítají všechny soubory:
- ✅ mindar-image.prod.js
- ✅ aframe.min.js
- ✅ mindar-image-aframe.prod.js
- ✅ card.mind (trigger soubor)
- ✅ scene.gltf (3D model)

### Testování různých trigger obrázků

Zkuste oficiální trigger od MindAR:
```
https://cdn.jsdelivr.net/gh/hiukim/mind-ar-js@1.2.5/examples/image-tracking/assets/card-example/card.png
```

Pokud tento funguje, ale váš vlastní ne → problém je ve vašem triggeru.

---

## 📱 Testování na různých zařízeních

### iOS Safari

**Podporováno:**
- ✅ iOS 11+ (základní WebRTC)
- ✅ iOS 13+ (plná podpora)

**Známé problémy:**
- Private Browsing mode může blokovat kameru
- Low Power Mode může omezit výkon

**Doporučení:**
- Vypněte Low Power Mode
- Používejte normální (ne soukromý) režim
- Safari je JEDINÝ podporovaný prohlížeč na iOS

### Android Chrome

**Podporováno:**
- ✅ Android 8+
- ✅ Chrome 53+

**Známé problémy:**
- Některé levné telefony mají slabý CPU
- Battery Saver mode omezuje výkon

**Doporučení:**
- Používejte Chrome (ne Firefox, Opera, atd.)
- Vypněte Battery Saver
- Zavřete ostatní aplikace

### Desktop (Chrome/Firefox/Edge)

**Použití:**
- ✅ Pro vývoj a testování
- ✅ Pro demo s webkamerou

**Poznámka:**
- Desktop není primární platforma pro AR
- Trigger může být menší a hůře se detekuje
- Doporučeno používat pro testování před mobilem

---

## 📋 Checklist - Co zkusit popořadě

1. [ ] Otevřete camera-test.html a ověřte, že kamera funguje
2. [ ] Ověřte, že běžíte na HTTPS (ne HTTP)
3. [ ] Zkontrolujte, že prohlížeč podporuje kameru
4. [ ] Povolte přístup ke kameře v dialogu prohlížeče
5. [ ] Zavřete ostatní aplikace používající kameru
6. [ ] Stáhněte a vytiskněte trigger obrázek
7. [ ] Držte trigger v dobře osvětleném prostředí
8. [ ] Celý trigger musí být viditelný v kameře
9. [ ] Držte telefon 20-50 cm od triggeru
10. [ ] Čekejte 2-3 sekundy na detekci

Pokud ani po tomto checklistu nefunguje:
- Zkuste jiný prohlížeč
- Zkuste jiné zařízení
- Restartujte zařízení
- Kontaktujte podporu s výstupem z camera-test.html

---

## 💡 Tipy pro vývoj

### Lokální testování

```bash
# Spusťte HTTPS server lokálně
python3 -m http.server 8000

# Poté použijte ngrok pro HTTPS tunel
ngrok http 8000
```

Ngrok vám dá HTTPS URL kterou můžete otevřít na mobilu.

### Debug logs v konzoli

Použijte `?debug=true` v URL:
```
https://ethnographic.cz/ar-tracker.html?debug=true
```

Zobrazí alert dialogy pro každý důležitý krok.

### Simulace různých error stavů

Zkuste úmyslně:
- Zamítnout přístup ke kameře → Otestovat NotAllowedError handling
- Zavřít přístup ke kameře v settings → Otestovat SecurityError
- Otevřít kameru v jiné aplikaci → Otestovat NotReadableError

---

## 🆘 Stále nefunguje?

### Sesbírejte diagnostické informace:

1. **Z camera-test.html:**
   - Jaký prohlížeč a verze?
   - Jaká platforma (iOS/Android/Desktop)?
   - Běží na HTTPS?
   - Podporuje MediaDevices API?
   - Jaká je chybová zpráva?

2. **Z ar-tracker.html:**
   - Zobrazí se loading screen?
   - Jaká je poslední zpráva na loading screenu?
   - Vidíte obraz z kamery?
   - Detekuje se trigger?

3. **Z konzole prohlížeče:**
   - Zkopírujte všechny červené chyby
   - Screenshot network tabulky

### Kontakt:

Se všemi těmito informacemi můžete:
- Vytvořit issue na GitHubu
- Kontaktovat vývojáře
- Hledat řešení na StackOverflow

---

## 📚 Další zdroje

- [MindAR Dokumentace](https://hiukim.github.io/mind-ar-js-doc/)
- [WebRTC Troubleshooting](https://webrtc.github.io/samples/)
- [MDN MediaDevices API](https://developer.mozilla.org/en-US/docs/Web/API/MediaDevices)
- [Can I Use - getUserMedia](https://caniuse.com/stream)

---

**Vytvořeno pro WebAR projekt | Poslední aktualizace: 2026-01-09**
