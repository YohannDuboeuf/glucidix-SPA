# Landing Glucidix

Page de liste d'attente pour Glucidix, copilote nutrition trail.
HTML/CSS/JS vanilla — aucun build, aucune dépendance, aucune requête réseau
sortante au chargement. Police Plus Jakarta Sans variable servie en local
depuis `fonts/`.

Publiée sur GitHub Pages : <https://yohannduboeuf.github.io/glucidix-SPA/>

## Ouvrir en local

```
python3 -m http.server 8000
```

puis <http://localhost:8000>. Le double-clic sur `index.html` marche aussi,
mais `file://` fausse le rendu de la police.

## Structure

| Fichier | Rôle |
|---|---|
| `index.html` | La page entière : formulaire, mentions légales dépliables, fond généré en JS |
| `style.css` | Toute la CSS. Mobile d'abord, élargissement en `min-width: 600px` |
| `img/` | Ne sert plus qu'à `og:image` (la vignette de partage) — la page n'affiche aucune photo |

Le fond (carte topographique + profil D+ avec les prises) est **généré en
code** : aucune image, aucun tracé SVG écrit à la main.

## Brevo

Le formulaire poste vers l'endpoint Brevo de la liste `waiting list`.
Champs envoyés : `EMAIL`, `PLATEFORME` (`Android` / `iOS`),
`email_address_check` (piège à robots, doit rester vide), `locale`.

**Simple opt-in.** Le double opt-in de Brevo passe par une automation, hors
du plan actuel : aucun email de confirmation ne part. Le consentement repose
donc sur la case à cocher — décochée par défaut, formulée en clair. Ni
l'écran de confirmation ni les mentions légales ne doivent parler d'un
« lien de confirmation ». Si le plan change et que le double opt-in est
activé, les deux textes sont à reprendre.

La soumission vise une **iframe cachée** : un POST classique ferait quitter
la page vers l'écran de remerciement de Brevo. Conséquence assumée — la
réponse n'est pas lisible (pas de CORS sur `sibforms.com`), donc l'écran de
confirmation s'affiche sans preuve que Brevo a bien accepté.

Les champs `platform` et `consent` sont désactivés juste avant l'envoi :
ils ne servent qu'au navigateur, Brevo ne les attend pas.

**Jamais de clé API ici** : le repo est public et la page est statique. Si
le formulaire Brevo est recréé, seule l'URL d'`action` change.

## Reste à faire

- Mettre à jour `og:url` / `og:image` si le repo est renommé.
- Incrémenter `style.css?v=` à chaque modification de la feuille.
