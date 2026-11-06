# Parole Intrecciate

Gioco di parole intrecciate in italiano, pensato per il telefono. È una PWA: si installa sulla schermata Home con la sua icona e funziona anche offline.

- 6 temi: Animali, Frutta, Città italiane, Cucina, Sport, Mare
- 3 livelli: Facile (8×8), Medio (10×10 con diagonali), Difficile (12×12 con parole al contrario)
- Cronometro e record personale per livello (salvato nel browser)
- Tasto "Aiutino"

Nessuna dipendenza e nessun build: solo HTML, CSS e JavaScript.

## Struttura

```
index.html      il gioco (stile + logica)
manifest.json   nome, colori e icone dell'app
sw.js           service worker per l'uso offline
icons/          icone dell'app
```

## Provarlo in locale

Il service worker funziona solo via `http://localhost` o HTTPS, non aprendo il file con doppio clic. Avvia un server dalla cartella del progetto:

```bash
python3 -m http.server 8000
# oppure
npx serve .
```

Poi apri http://localhost:8000.

## Pubblicarlo su GitHub Pages

```bash
git init
git add .
git commit -m "Prima versione di Parole Intrecciate"
git branch -M main
git remote add origin https://github.com/<tuo-utente>/parole-intrecciate.git
git push -u origin main
```

Su GitHub: **Settings → Pages → Source: Deploy from a branch → main / (root)**. Dopo un minuto il gioco è online su `https://<tuo-utente>.github.io/parole-intrecciate/`.

## Installarlo sul telefono

- **iPhone (Safari):** Condividi → "Aggiungi alla schermata Home"
- **Android (Chrome):** menu ⋮ → "Installa app"

## Aggiungere parole o temi

In `index.html` cerca l'oggetto `THEMES` e aggiungi una voce:

```js
"Colori": ["ROSSO","BLU","VERDE","GIALLO","VIOLA","ARANCIONE","ROSA","GRIGIO"],
```

Regole: lettere maiuscole, niente accenti né spazi, almeno 10 parole lunghe al massimo 8 lettere (così il tema funziona anche in Facile).

## Pubblicare un aggiornamento

1. Modifica i file
2. In `sw.js` aumenta la versione: `parole-v1` → `parole-v2`
3. `git commit -am "..." && git push`
