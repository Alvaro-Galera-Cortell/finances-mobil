# Finances (mòbil)

App web d'un sol fitxer per controlar els diners en el mòbil. Tota la interfície en valencià.
Publicada a GitHub Pages; s'instal·la des de Safari amb «Afegir a la pantalla d'inici».

## Fitxers
- `index.html` — tota l'app (HTML + CSS + JS).
- `sw.js` — service worker: xarxa primer (perquè arriben les actualitzacions), memòria cau sense connexió.
- `manifest.webmanifest`, `icon-*.png` — instal·lació com a app.

## Model
- No es controla el sou: es controla el **total de diners**. Moviments: `ingres`, `despesa`, `traspas`.
- Cada ingrés aparta una part a l'**estalvi** (proposat amb `estalviPct`, editable) i la resta es
  **reparteix per percentatges** entre categories. El repartiment queda guardat al moviment (`rep`):
  canviar els percentatges després no reescriu el passat.
- Saldo d'una categoria = repartit + traspassos d'entrada − eixides − despeses. Total = estalvi + categories.
- Categories de partida: Capritxos 30 · Sopar fora 30 · Oci 20 · Emergència 15 · Fixos 5.
- Dades només en `localStorage["finances_v1"]` del mòbil. Còpia: Ajustos → Fer una còpia (JSON).

## Actualitzar
1. Editar `index.html`, pujar `APP_VERSION` i el nom de `CACHE` a `sw.js` (si no, pot quedar la versió vella).
2. Provar a 390 px en clar i fosc, sense escriure en dades reals (ella té les seues al mòbil).
3. `git push` → GitHub Pages es publica sol en un minut. Ella només ha de tancar i obrir l'app.
- **No canviar la clau `finances_v1` ni l'estructura sense migració**: les dades són d'ella i no les veiem.

## Accessibilitat (regla fixa)
Objectius tàctils ≥ 44 px, tots els camps amb `label`, `dialog` natiu per als formularis,
contrast en clar i fosc, `prefers-reduced-motion`, i cap scroll horitzontal a 390 px.
