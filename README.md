# Naudoto aliejaus surinkimo žemėlapis – Biomotorai

Atskiras žemėlapio puslapis su:
- Visais 457 konteineriais su koordinatėmis
- Žymeklių grupavimu (clustering)
- „Rasti artimiausią konteinerį" funkcija (geolokacija)
- Navigacijos mygtukais: Google Maps, Waze, Apple Maps
- 5 kalbų versijomis (LT, LV, EE, EN, RU) per URL parametrą
- Administratoriaus panele konteinerių aktyvavimui/deaktyvavimui

---

## Kur saugomi failai (GitHub)

Visi failai saugomi **GitHub Pages** repozitorijoje ir prieinami šiuo adresu:

🌐 **https://biomotorai.github.io/map/**

| URL | Paskirtis |
|-----|-----------|
| `https://biomotorai.github.io/map/` | Viešas žemėlapis vartotojams |
| `https://biomotorai.github.io/map/admin.html` | Administratoriaus panelė |
| `https://biomotorai.github.io/map/konteineriai.json` | Duomenų failas (raw JSON) |

### Kaip atnaujinti failus per GitHub

Kadangi failai hostuojami per **GitHub Pages**, naujus failus reikia įkelti į GitHub repozitoriją (ne per FTP):

1. Eikite į repozitoriją: **https://github.com/biomotorai/map**
2. Pasirinkite failą, kurį norite pakeisti (pvz. `konteineriai.json`)
3. Spauskite pieštuką ✏️ arba „Add file → Upload files"
4. Įkelkite naują failo versiją
5. Spauskite **„Commit changes"** – per ~1 minutę pakeitimai matysis svetainėje

> 💡 **Greitesnis būdas `konteineriai.json` atnaujinimui:** atsisiųskite pakeitimus iš `admin.html`, tada įkelkite failą į GitHub repozitoriją per „Upload files".

---

## Failų sąrašas

| Failas | Paskirtis |
|--------|-----------|
| `index.html` | Pagrindinis žemėlapio puslapis vartotojams |
| `admin.html` | Administratoriaus panelė (slaptažodžiu apsaugota) |
| `konteineriai.json` | Duomenų failas su konteineriais (DAUGIAUSIAI keičiamas) |
| `README.md` | Ši instrukcija |

---

## Įkėlimas į GitHub (vienkartinis darbas)

### 1 žingsnis – repozitorija

Failai jau saugomi GitHub repozitorijoje:
**https://github.com/biomotorai/map**

GitHub Pages automatiškai publikuoja juos adresu `https://biomotorai.github.io/map/`.

### 2 žingsnis – įkelti/atnaujinti failus

Naujus ar atnaujintus failus įkelkite per GitHub sąsają:
1. Eikite į repozitoriją
2. Spauskite **„Add file → Upload files"**
3. Įkelkite reikiamus failus (`index.html`, `admin.html`, `konteineriai.json`)
4. Spauskite **„Commit changes"**

### 3 žingsnis – patikrinti

Atidarykite naršyklėje: **https://biomotorai.github.io/map/**

Turėtumėte matyti žemėlapį su konteineriais. Jei matote – įkėlimas pavyko.

Administratoriaus panelė pasiekiama: **https://biomotorai.github.io/map/admin.html**

---

## Slaptažodžio nustatymas (BŪTINA prieš naudojant)

**Numatytasis admin slaptažodis:** `***********`

**Tikrai pakeiskite** prieš pirmą naudojimą. Štai kaip:

### Žingsnis po žingsnio

1. Atidarykite bet kurią naršyklę
2. Paspauskite F12 (atsidarys naršyklės įrankiai)
3. Pasirinkite skirtuką **Console**
4. Įklijuokite šitą eilutę, pakeisdami `JŪSŲ_NAUJAS_SLAPTAŽODIS` į savo norimą:

```javascript
crypto.subtle.digest("SHA-256", new TextEncoder().encode("JŪSŲ_NAUJAS_SLAPTAŽODIS")).then(h => console.log(Array.from(new Uint8Array(h)).map(b => b.toString(16).padStart(2,"0")).join("")))
```

5. Paspauskite Enter – pamatysite ilgą tekstą iš raidžių ir skaičių (tai vadinasi „hash")
6. Atidarykite `admin.html` failą su tekstų redaktoriumi
7. Suraskite šitą eilutę (apie 250 eilutę):

```javascript
const PASSWORD_HASH = "33a55dcfb7a447e621b3b5b69d239a63d5767e81598d0b938f4dbf53caf1b4dd";
```

8. Pakeiskite tekstą tarp kabučių į savo naują hash'ą
9. Išsaugokite failą ir įkelkite į hosting'ą

---

## Nuoroda iš pagrindinės svetainės

Po įkėlimo, WordPress admin'e galite pakeisti dabartinę nuorodą į žemėlapį, kad ji vestų į naują adresą:

**Naujas URL:** `https://biomotorai.github.io/map/`

Pasirinktinai, pridėkite parametrą su kalba:
- `https://biomotorai.github.io/map/?lang=lt` – lietuvių (rodo tik Lietuvos konteinerius)
- `https://biomotorai.github.io/map/?lang=lv` – latvių (rodo tik Latvijos)
- `https://biomotorai.github.io/map/?lang=ee` – estų (rodo tik Estijos)
- `https://biomotorai.github.io/map/?lang=en` – anglų (rodo visus)
- `https://biomotorai.github.io/map/?lang=ru` – rusų (rodo visus)

---

## Kaip aktyvuoti/deaktyvuoti konteinerius

Visi konteineriai pradžioje paženklinti kaip **aktyvūs**. Reikia rankiniu būdu deaktyvuoti tuos ~100, kurie neveikia.

### Žingsnis po žingsnio

1. Atidarykite: **https://biomotorai.github.io/map/admin.html**
2. Įveskite admin slaptažodį
3. Pamatysite visų 457 konteinerių sąrašą
4. Naudokite paieškos langelį arba filtrus, kad rastumėte konkretų konteinerį
5. Spauskite žalią jungiklį dešinėje pusėje – konteineris taps neaktyvus (raudonas)
6. Galite pažymėti kelis iš karto su žymimaisiais langeliais ir naudoti masinį veiksmą („Deaktyvuoti pažymėtus")
7. Kai baigsite, spauskite **„Atsisiųsti pakeitimus"** mygtuką viršuje dešinėje
8. Atsiųstas `konteineriai.json` failas patenka į jūsų **Atsisiuntimai** aplanką
9. Įkelkite šį naują failą į **GitHub repozitoriją** (`https://github.com/biomotorai/map`) – pakeisdami senąjį `konteineriai.json`
10. Perkraukite žemėlapio puslapį (Ctrl+F5) – pakeitimai matosi visiems vartotojams

### Patarimai

- **Masinis veiksmas:** spauskite žymimąjį langelį stulpelio antraštėje, tada „Deaktyvuoti pažymėtus" – galite per 5 minutes deaktyvuoti visus 100+ konteinerių
- **Filtrai padeda:** pasirinkite miestą iš dropdown'o, kad matytumėte tik to miesto konteinerius
- **Paieška:** įveskite gatvės pavadinimą („Karmelitų" arba „Vilnius")
- **Geltonas indikatorius:** kai keičiate būseną, eilutė pasidaro geltona – tai reiškia, kad pakeitimas dar neišsaugotas

---

## Greitas atstatymas (jei kažkas blogai)

Jeigu sugadinote `konteineriai.json` failą:

1. Atsisiųskite originalų `konteineriai.json` failą iš pradinio paketo
2. Įkelkite atgal į hosting'ą

Originalus failas turi 457 konteinerius, visi pažymėti `"active": true`.

---

## Daugiakalbystė

Žemėlapis kaip atskiras puslapis turi tik vieną kalbos perjungimo elementą viršuje (LT/LV/EE/EN/RU). Jeigu norite, kad iš pagrindinės svetainės nuoroda iškart vestų į teisingą kalbą – pridėkite `?lang=XX` prie URL.

WordPress'e galima pakeisti meniu nuorodas tokiu būdu:
- LT puslapyje meniu nuoroda → `https://biomotorai.github.io/map/?lang=lt`
- EN puslapyje meniu nuoroda → `https://biomotorai.github.io/map/?lang=en`
- ir t.t.

---

## Techninės detalės

- **Žemėlapio variklis:** Leaflet 1.9.4 (atviro kodo, nemokama)
- **Plytelės:** Carto Positron (nemokamos)
- **Grupavimas:** Leaflet.markercluster (atviro kodo)
- **Backend:** nereikia (visi duomenys statiniame JSON faile)
- **Saugumas:** admin'as apsaugotas SHA-256 hash'u, pats slaptažodis niekur nesaugomas
- **Naršyklės:** veikia visose šiuolaikinėse naršyklėse (Chrome, Safari, Firefox, Edge)
- **Mobilūs:** pilnai responsive

Žemėlapis nesiunčia jokių duomenų jokiems trečiosios šalies serveriams, išskyrus žemėlapio plyteles iš Carto. Vartotojo lokacija lieka tik naršyklėje.

---

## Atnaujinimai ateityje

### Pridėti naują konteinerį
Tiesiogiai redaguoti `konteineriai.json` failą tekstų redaktoriumi. Pridėti naują objektą su unikaliu ID, koordinatėmis, adresu, miestu, šalimi ir `"active": true`. Įkelti atnaujintą failą.

### Pakeisti adresą ar koordinatę
Tas pats kaip pridėti – tiesiogiai redaguoti JSON failą.

### Statistika
Šiuo metu nėra integruotos statistikos. Jei norėsite – galima pridėti Google Analytics arba Plausible per `<script>` blokus index.html faile.
