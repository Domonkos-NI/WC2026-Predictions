# VB 2026 weboldal — frissítési tutorial

**Cél:** új meccseredmények bekerülnek → a weboldal magától frissül mindenkinél.

**Emlékeztető 3 szóban:** CSV beír → Run All → JSON feltölt.

---

## 1. Eredmények beírása
- Nyisd meg: `workspace/data/actual_results.csv`
- Add hozzá az új, lejátszott meccs sorát (`match_id`, csapatok, gólok), és állítsd a `played` oszlopot `1`-re.
- Mentsd a fájlt (Ctrl+S).

## 2. Notebook futtatása
- Nyisd meg: `workspace/notebook.ipynb`
- Felül kattints a **Run All** (Összes futtatása) gombra.
- Várd meg, amíg a végén kiírja: `✅ READY TO PUBLISH`.
- Ekkor újragenerálódik a `predikciok_web.json` fájl a friss adatokkal.

## 3. JSON feltöltése a GitHubra
- Menj a GitHub repódba (`vb2026-predikciok`).
- Nyisd meg a `predikciok_web.json` fájlt → kattints a **ceruza ikonra** (Edit).
- **VAGY** egyszerűbb: **Add file → Upload files**, és húzd be a frissített `workspace/predikciok_web.json` fájlt (felülírja a régit).
- Lent kattints: **Commit changes**.

## 4. Kész
- Nem kell semmit újraküldened. A `predikciok.html`-t mindenki ugyanúgy nyitja meg, és a következő megnyitáskor már az új adatot látja.
- Az új adat néhány percen belül jelenik meg (a GitHub gyorsítótár miatt 1–5 perc csúszás lehet).

---

## Egyszeri beállítás (csak a legelső alkalommal kell)

### Új GitHub repó
1. Regisztrálj/lépj be: https://github.com
2. Jobb fent **+** → **New repository**.
3. **Repository name**: pl. `vb2026-predikciok`.
4. **Visibility**: **Public** (fontos, különben a HTML nem tudja letölteni az adatot).
5. Pipáld be: **Add a README file**.
6. **Create repository**.

### Első feltöltés
1. **Add file → Upload files**.
2. Húzd be a `workspace/predikciok_web.json` fájlt.
3. **Commit changes**.

### Raw link beállítása a notebookban
1. Kattints a repóban a `predikciok_web.json` fájlra → **Raw** gomb.
2. Másold ki a linket a böngésző címsorából, pl.:
   `https://raw.githubusercontent.com/<felhasznalonev>/vb2026-predikciok/main/predikciok_web.json`
3. A notebook 12. szakaszában írd be ezt a sort:
   `WEB_DATA_URL = "https://raw.githubusercontent.com/.../predikciok_web.json"`
4. Futtasd újra a cellát → újragenerálódik a `predikciok.html`.
5. **Ezt a `predikciok.html`-t küldd el** az ismerősöknek (csak egyszer).

---

## Fájlok szerepe
- `predikciok.html` — ezt küldöd el bárkinek (egyszer). Telepítés nélkül megnyílik böngészőben.
- `predikciok_web.json` — ezt töltöd fel online és csak ezt frissíted.
- `elorejelzesek_HU.xlsx` — magyar Excel-tábla saját megtekintésre.
