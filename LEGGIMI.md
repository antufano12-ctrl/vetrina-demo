# Sito demo Vetrina – 4 negozi d'esempio

Un solo `index.html` che mostra i 4 caratteri del design system Vetrina, ognuno con un negozio **inventato**:

| Link | Carattere | Negozio d'esempio |
|---|---|---|
| `index.html#bottega` | Bottega | Forno Santa Lucia (panificio-pasticceria) |
| `index.html#atelier` | Atelier | Studio Lume (parrucchiere) |
| `index.html#officina` | Officina | Autofficina del Borgo |
| `index.html#energia` | Energia | Palestra Ritmo |

Nomi, indirizzi (Borgo Esempio), telefono `000 000 0000` e WhatsApp sono finti.

## Come aprirlo
Doppio clic su `index.html`. Per vederlo "da telefono" sul PC: F12, poi l'icona del telefono.
Senza internet funziona lo stesso, cambiano solo i font.

## Mandare il link del settore giusto
Una volta pubblicato, aggiungi in fondo al link il settore:
`https://tuo-indirizzo/#officina` → il meccanico vede subito l'officina.
Quando qualcuno tocca un tipo di negozio in alto, anche l'indirizzo nel browser cambia.

## Trasformarlo nel sito di un cliente vero
1. Copia la cartella in `siti/nome-cliente/`.
2. Nell'oggetto `NEGOZI` (in cima allo `<script>`) tieni **un solo negozio**, quello del carattere giusto, e cambia i dati: nome, frase, orari (da lunedì a domenica, `[]` = chiuso), servizi e prezzi, indirizzo, telefono, WhatsApp (solo cifre con 39 davanti), ragione sociale, partita IVA. Metti lo stesso nome in `CARATTERE_INIZIALE` e `DEMO = false`.
3. Colore: il sito è scuro per tutti (fondo `#222222`, testo bianco, schede con bordo grigio); il colore del cliente compare **solo sul bottone Chiama**. Nel blocco CSS `[data-carattere="..."]` del suo carattere metti in `--brand` il colore dell'insegna e in `--brand-ink` il colore del testo sopra (di solito bianco; scuro `#222222` se l'insegna è chiara, come in Atelier). Il contrasto tra i due deve essere almeno 4.5:1 (controlla su webaim.org/resources/contrastchecker); se non ci arriva, scuriscilo. Cancella gli altri 3 blocchi.
4. Togli i pezzi segnati `DEMO` nell'HTML: la riga `<meta name="robots" content="noindex...">`, la fascia scura con il selettore (`<div class="demo">`). Nel link di Google Fonts tieni solo Figtree e il font del suo carattere.
5. Aggiorna a mano `<title>` e `<meta name="description">` nel `<head>`.
6. Foto: al posto dei riquadri `<div class="photo" ...>Qui la foto del tuo negozio</div>` metti `<img src="foto1.jpg" alt="cosa si vede" style="width:100%;aspect-ratio:4/3;object-fit:cover;border-radius:12px">`. Solo foto vere del negozio, con il permesso del negoziante, ridotte sotto i 300 KB.
7. Privacy: il testo nel piè di pagina va bene se il sito non ha moduli. Per stare più tranquilli con il GDPR si possono scaricare i font e servirli dalla stessa cartella invece che da Google.

## Pubblicarlo gratis
- **Netlify Drop** (app.netlify.com/drop): trascini la cartella, ottieni un indirizzo `nome.netlify.app`.
- **Cloudflare Pages**: Workers & Pages → Crea → Pages → Carica risorse.
- **GitHub Pages**: repository con `index.html`, poi Settings → Pages.
Dominio proprio (es. `fornosantalucia.it`): circa 10–15 € l'anno.

La demo va pubblicata **così com'è**, con la fascia "Sito dimostrativo" e il `noindex`.

## Note tecniche
- "Aperto ora / Chiuso ora" si calcola con l'ora del telefono di chi guarda e si aggiorna ogni minuto.
- I contenuti sono scritti dal JavaScript. Per un cliente vero va bene così, ma l'anteprima su WhatsApp/Facebook usa solo `<title>` e `description` del `<head>`: per questo vanno scritti a mano.
