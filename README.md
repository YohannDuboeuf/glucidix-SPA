# Landing Glucidix

Landing page statique de capture d'emails (waitlist) pour Glucidix, copilote nutrition trail.
HTML/CSS vanilla — aucun build, aucune dépendance, aucune requête réseau sortante.
Police Plus Jakarta Sans variable servie en local depuis `fonts/`.

## Ouvrir en local

Double-clic sur `index.html`, ou `python3 -m http.server 8000` puis http://localhost:8000.

## Reste à faire

- Copy définitive : tous les textes entre crochets (`[PROMESSE — 1 phrase]`, `[BÉNÉFICE n]`, `[CTA]`, `[CONSENTEMENT …]`) sont des placeholders.
- `legal.html` (mentions légales + politique de confidentialité) — déjà lié, page absente.
- Branchement Brevo : le formulaire est **inerte** (pas de `action`, pas de JS). Ajouter la soumission, l'affichage du bloc `#confirm` et les messages dans `#formmsg`.
- `og-image.png` + balise `og:image`.
