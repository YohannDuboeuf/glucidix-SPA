# Landing Glucidix

Page de liste d'attente pour Glucidix, copilote nutrition trail.
HTML/CSS/JS vanilla — aucun build, aucune dépendance, aucune requête réseau
sortante au chargement. Police Plus Jakarta Sans variable servie en local
depuis `fonts/`.

Publiée sur GitHub Pages : <https://yohannduboeuf.github.io/glucidix-spa/>

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

## Reste à faire

- **Branchement Brevo.** Le formulaire valide les champs et affiche `#confirm`,
  mais n'envoie rien. Il faut l'`action` du formulaire Brevo et les `name` des
  champs (`EMAIL`, attribut `PLATEFORME`). Jamais de clé API ici : le repo est
  public et la page est statique.
- **Retirer les deux mentions « maquette »** (ligne de pied + note dans
  `#confirm`) au moment du branchement — pas avant, sinon la page prétend
  enregistrer un email qu'elle jette.
- **Wording de confirmation** à passer en double opt-in : « ouvre ta boîte
  mail et clique le lien », pas « tu es inscrit ».
- Mettre à jour `og:url` / `og:image` si le repo est renommé.
