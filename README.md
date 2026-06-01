# 🌳 Toegang tot verkoelende plekken in Amsterdam

**Individuele opdracht – Designing Future Cities**

Een ruimtelijke analyse van hoe goed Amsterdammers kunnen bereiken verkoelende openbare ruimtes tijdens hittegolven.

---

## 🎯 Onderzoeksvraag

**Welke inwoners van Amsterdam hebben binnen 5, 10 en 15 minuten lopen toegang tot verkoelende openbare ruimtes, en waar zijn de tekorten het grootst?**

---

## 📊 Methode

### Definitie "verkoelende plekken"
Openbare groengebieden **> 1 hectare** en wateroppervlakken **> 5 hectare**, op basis van bewezen thermisch verkoelend effect via:
- ✅ Verdamping via planten en water
- ✅ Schaduw via boomkronen
- ❌ Geen decoratief water of smalle grachten

### Technische aanpak
1. **OSM data ophalen** – Parken, groengebieden, water via OpenStreetMap
2. **Wandelnetwerk** – Netwerk van voetpaden via OSMnx
3. **Isochrones berekenen** – Netwerkanalyse (geen simpele buffers!) voor 5, 10, 15 min
4. **CBS bevolkingsdata** – Aantal inwoners per buurt
5. **Spatial join** – Area-weighted estimation van bevolking in bereik
6. **Risicogebieden** – Buurten met < 50% dekking identificeren

---

## 📁 Bestanden

### Notebooks
- **`amsterdam_verkoeling_v2.ipynb`** – Volledige analyse (stap-voor-stap)
  - Stap 1: Verkoelende plekken ophalen via OSM
  - Stap 2: Wandelnetwerk ophalen
  - Stap 3: Isochrones berekenen (netwerkanalyse)
  - Stap 4: CBS bevolkingsdata koppelen
  - Stap 5: Visualisaties genereren
  - Stap 6: Conclusies samenvatten

### Outputs (gegenereerd na draait)
- `kaart1_isochrones.png` – Hoofdkaart (5/10/15 min ringen)
- `kaart2_bevolking.png` – Staafgrafiek (% toegang)
- `kaart3_risico.png` – Risicokaart (buurten < 50% dekking)
- `output/*.geojson` – Vector data voor QGIS/Illustrator

---

## 🚀 Hoe te gebruiken

### 1. Installeer dependencies
```bash
pip install -r requirements.txt
```

### 2. Run het notebook
```bash
jupyter notebook amsterdam_verkoeling_v2.ipynb
```

### 3. Kies test-modus of volledige run
In **Stap 3** van het notebook:
- **Test mode** (20 plekken): ~2-3 minuten
- **Volledige analyse** (alle plekken): ~10-30 minuten

### 4. Controleer outputs
Na draait vind je kaarten in je werkdirectory:
- `kaart1_isochrones.png`
- `kaart2_bevolking.png`
- `kaart3_risico.png`

---

## 📈 Verwachte resultaten

| Loopafstand | Bevolking met toegang | Risicogebieden |
|---|---|---|
| 5 minuten | ~40-50% | Veel |
| 10 minuten | ~70-80% | Enkele |
| 15 minuten | ~85-95% | Weinig |

*(Exacte cijfers hangen af van CBS-data en OSM-coverage)*

---

## 📚 Databronnen

- **OpenStreetMap (OSM)** – Parken, groengebieden, water
- **CBS Wijk- en Buurtkaart 2023** – Bevolkingsdata per buurt
- **OSMnx** – Wandelnetwerk uit OSM
- **NetworkX** – Isochrone berekening

---

## 🔑 Key insights voor poster

### ✅ Wat goed is
- Veel inwoners hebben toegang tot verkoeling
- Amsterdam-Centrum en watergebieden zijn goed uitgerust
- Isochrones tonen realistischer bereik dan buffers

### ⚠️ Wat problemen zijn
- Dichtbebouwde woonwijken hebben minder bereik
- Amsterdam-Noord: tekort in bepaalde buurten
- Water is niet altijd bereikbaar (beveiligd, niet openbaar)

### 🎯 Voor beleid
- Prioriteit: risicogebieden krijgen extra groenvoorzieningen
- Sluit gaten in het wandelnetwerk
- Plant extra schaduwrijke plekken in warm urbaan gebied

---

## 🛠️ Troubleshooting

### CBS-data laadt niet
→ Download handmatig van [CBS geografische data](https://www.cbs.nl/nl-nl/dossier/nederland-regionaal/geografische-data)  
→ Laad met: `buurten = gpd.read_file('path/to/file.gpkg')`

### Isochrones duren te lang
→ Gebruik test-modus (20 plekken) eerst  
→ Later draai je volledige analyse

### Basemap wordt niet getoond
→ Geen internet? Prima, kaart werkt ook zonder  
→ Zet `ctx.add_basemap()` regel in commentaar

---

## 📝 Voor je poster

1. **Gebruik de PNG's direct** in Canva/Illustrator
2. **Voeg toe:**
   - Definitie van "verkoelende plek"
   - Methode: "Netwerkanalyse (isochrones)"
   - Bronnen: OSM + CBS
   - Conclusie (zie Stap 6 output)
3. **BONUS:** Combineer met hittekaart van KNMI voor extra impact

---

## 📖 Referenties

- OSMnx: [https://osmnx.readthedocs.io](https://osmnx.readthedocs.io)
- NetworkX: [https://networkx.org](https://networkx.org)
- GeoPandas: [https://geopandas.org](https://geopandas.org)
- CBS Geografische data: [https://www.cbs.nl](https://www.cbs.nl)

---

## 🎓 Beleidsrelevantie

Dit onderzoek sluit aan bij:
- **Designing Future Cities** – Klimaatadaptatie en leefbaarheid
- **Hitte-eilanden (UHI)** – Openbare gezondheid
- **Ruimtelijke planning** – Gerechtigheid en toegankelijkheid
- **Duurzame steden** – SDG 11: Sustainable Cities

---

**Auteur:** Thom Butter  
**Datum:** Juni 2026  
**Status:** In progress
