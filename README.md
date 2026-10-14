# INSPECTOR 2.0 · Entrenador de tests

Aplicació per preparar les oposicions d'inspector/a del cos de Mossos d'Esquadra. **HTML, CSS i JavaScript**, compatible amb ordinadors i mòbils, preparada per a **GitHub Pages**. No necessita instal·lar llibreries ni contractar una base de dades.

## Contingut del ZIP

- `index.html` — pàgina principal i interfície adaptativa.
- `styles.css` — disseny renovat: violeta, corall, crema i verd menta; tipografies DM Sans i Fraunces (fonts remotes opcionals, alternatives de sistema disponibles).
- `app.js` — configuració dels tests, correcció, revisió d'errors, gestió/importació/exportació de preguntes.
- `preguntes.json` — **59 preguntes reals extretes de «M8 TEST.docx»**, amb solucions i explicacions **segons el document aportat**, no contrastades amb una revisió normativa externa.
- `preguntes.csv` — les mateixes 59 preguntes per treballar-les amb LibreOffice o Excel (UTF-8 amb BOM).
- `plantilla-preguntes.csv` — plantilla buida per incorporar noves preguntes.

## Preguntes incorporades

| Test original | Ítems |
|---|---:|
| Diagnòstic inicial | 10 |
| Tema 8.1 · Transparència | 5 |
| Tema 8.2 · Protecció de dades personals | 8 |
| Tema 8.3 · Dades en l'àmbit penal i policial | 12 |
| Consolidació global bloc 8 | 24 |
| **Total** | **59** |

Les preguntes es classifiquen per tema d'estudi: **8.1 (16), 8.2 (17), 8.3 (26)**. Els qüestionaris inicial i global contenen preguntes de diferents temes i s'han classificat per contingut. Això no canvia la redacció, les quatre opcions ni les claus originals.

**Nota important sobre la font:** la pregunta 4 del diagnòstic inicial (`8.2-D-004`) té una advertència explícita al Word original: cal revisar la formulació i el llindar d'edat respecte del text legal. L'hem mantinguda sense canviar-ne la clau, perquè és el que indica el material facilitat. En general, el banc reflecteix les respostes del document, però no constitueix una verificació normativa independent.

**Repeticions:** el banc conserva els 59 ítems originals —alguns conceptes apareixen a més d'un dels cinc tests— per permetre assajar-los com a preguntes distintes del material. Els IDs són únics i incorporen la sèrie original `-D-` (diagnòstic), `-T-` (tema), `-G-` (global).

## Publicar a GitHub Pages

1. Descomprimeix el ZIP.
2. Puja aquests sis fitxers a **l'arrel** del repositori de GitHub, conservant exactament els noms. Si ja has publicat la primera versió, substitueix `index.html`, `styles.css`, `app.js` i `preguntes.json`, i afegeix `preguntes.csv`.
3. A GitHub, obre **Settings → Pages → Deploy from a branch → main → /(root)**.
4. Espera que GitHub acabi el desplegament i entra a l'adreça de GitHub Pages, per exemple `https://EL_TEU_USUARI.github.io/insp-tests/`.
5. Si ja havies importat preguntes en un navegador, és possible que la còpia local continuï activa. A l'aplicació, entra a **Preguntes → Restaurar fitxer de GitHub** (exporta abans el banc local si el vols conservar).

> Un cop publicat, un navegador que no tingui dades locals carregarà automàticament les 59 preguntes del fitxer `preguntes.json`.

## Provar al teu ordinador

No obris `index.html` amb doble clic si vols comprovar la càrrega automàtica de JSON, perquè el navegador pot bloquejar l'accés per `file://`. Inicia un servidor estàtic amb Python:

```bash
cd carpeta-del-programa
python3 -m http.server 8000
```

Entra a `http://localhost:8000/`.

## Com preparar més preguntes

La web admet **importació directa de CSV o JSON** des de **Preguntes → Importar fitxer**. El CSV conté les columnes:

`id,bloc,tema,enunciat,opcio_a,opcio_b,opcio_c,opcio_d,correcta,explicacio,origen`

La columna `origen` és opcional; manté el nom del qüestionari per localitzar la pregunta original. El fitxer JSON conté `{"preguntes":[...]}`, amb `opcions` com un array de quatre textos i `correcta` com una lletra entre A i D. Per publicar un banc importat des de la web a GitHub, fes **Exportar JSON** i substitueix `preguntes.json` al repositori.

## Funcions del simulador

- Tests de **10, 30 o 50** preguntes, adaptats al nombre disponible, sense repetir l'ID dins del mateix test.
- Filtres per **tot el temari**, **bloc** o **tema**.
- Barreja de preguntes i d'opcions sense perdre la resposta correcta.
- Navegació lliure i recuperació d'un test a mig fer en la mateixa pestanya.
- Estadístiques d'encerts, errades i respostes en blanc, amb explicació del solucionari.
- Historial i repàs dels errors en el mateix navegador.
- Cerca, edició, importació JSON/CSV, exportació JSON i restauració del banc de GitHub.
- Correcció sense penalització negativa.

## Dades i limitacions

Les edicions del banc de preguntes i els resultats personals es desen **localment al navegador**. GitHub Pages no pot actualitzar els fitxers del teu repositori a partir d'una edició a la web; cal exportar i publicar el JSON. Les estadístiques no se sincronitzen automàticament entre dispositius. Qualsevol persona amb accés al repositori públic pot veure les claus contingudes a `preguntes.json`.

Les tipografies web necessiten connexió a Google Fonts per mostrar-se exactament igual que a la vista de demostració. Si no hi ha connexió, la web funciona amb les fonts alternatives del dispositiu.
