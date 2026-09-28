# Site du festival Cinés-Pays

Le site est composé de trois choses :

| Fichier / dossier | À quoi il sert |
|---|---|
| `index.html` | La mise en page, les couleurs, le fonctionnement. **Il ne contient aucune séance.** |
| `programme.csv` | Toutes les séances du festival. C'est le seul fichier à remplacer chaque année. |
| `affiches/` | Les images des affiches, une par film. |

Adresse du site : https://azaa6-9.github.io/cines-pays/

---

## Mettre à jour le programme

### 1. Préparer le tableau

Ouvrez `programme.csv` dans Excel, modifiez-le, puis enregistrez-le.

**Au moment d'enregistrer, choisissez impérativement le format « CSV UTF-8 ».**
Si vous choisissez « CSV » tout court, tous les accents du site deviendront
illisibles (`Ã©` à la place de `é`).

Une ligne = une séance. Les colonnes :

| Colonne | Ce qu'on y écrit |
|---|---|
| `cinema` | `bobine`, `montal`, `cane`, `hermine`, `korrigan` ou `celtic` |
| `jour` | `2026-10-21` ou `21/10/2026` |
| `heure` | `20h30` (ou `20:30`) |
| `film` | Le titre exact. **Écrivez-le partout de la même façon** : c'est lui qui regroupe les séances d'un même film. |
| `salle` | `Salle 1`, `Salle 2`… Laissez vide si le cinéma n'a qu'une salle. |
| `mention` | Voir le tableau ci-dessous. Vide la plupart du temps. |
| `affiche` | Le nom du fichier image, par exemple `karma.jpg`. Si vous laissez vide, le nom est déduit du titre. |
| `jeune` | `oui` pour afficher la pastille « Jeune public » sur l'affiche du film. |

Les mentions possibles dans la colonne `mention` :

| À écrire | Ce qui s'affiche |
|---|---|
| `sn` | Sortie nationale |
| `avp` | Avant-première |
| `cj` | Ciné-Jeunes |
| `vost` | VOST |
| `renc` | Rencontre |
| `stage` | La ligne prend le fond vert des ateliers et n'est pas comptée comme une séance de film |

On peut en mettre plusieurs en les séparant par une barre verticale `|`, et
remplacer le texte par le sien après deux-points :

```
avp|renc
cj:Mon Petit Ciné
stage|renc:Atelier 8–11 ans · 2 €
```

### 2. Préparer les affiches

Une image par film, dans le dossier `affiches/`. Le nom du fichier doit
correspondre à ce qui est écrit dans la colonne `affiche` du tableau.

Si une image manque ou ne se charge pas, le site affiche à la place une
affiche dessinée aux couleurs du festival. **Rien ne casse jamais.**

### 3. Déposer sur GitHub

Sur la page du dépôt : bouton `+` → **Upload files** → glisser `programme.csv`
et le dossier `affiches` → **Commit changes**.

Le site se met à jour tout seul en une minute environ. Faites `Ctrl + F5` pour
forcer votre navigateur à recharger, sinon il garde l'ancienne version en
mémoire.

---

## Si quelque chose ne va pas

Le site affiche un message orange en haut du programme lorsqu'une ligne du
fichier n'a pas pu être lue, avec son numéro de ligne. Les autres séances
s'affichent normalement.

Les causes habituelles :

- **Un nom de cinéma mal orthographié.** Seuls les six identifiants listés
  plus haut sont reconnus.
- **Une date ou une heure mal écrite.**
- **Le fichier enregistré en « CSV » au lieu de « CSV UTF-8 ».** Dans ce cas
  ce ne sont pas des lignes qui manquent, ce sont les accents qui sont abîmés
  partout.

Le site doit être consulté depuis son adresse internet. Si vous ouvrez
`index.html` en double-cliquant dessus sur votre ordinateur, le programme ne
s'affichera pas : c'est normal, le navigateur interdit à une page locale de
lire un fichier à côté d'elle.

---

## Ce qui reste à modifier à la main dans `index.html`

Ces éléments ne viennent pas du tableau. Cherchez-les dans le fichier avec
`Ctrl + F` :

- **Les dates du compte à rebours** — bloc `var FESTIVAL`, en haut du script,
  avec l'année qui s'affiche en bas des affiches dessinées.
- **Les coordonnées des cinémas** (adresse, téléphone, nombre de places) —
  bloc `var CINEMAS`, juste en dessous.
- **Les sites internet et réseaux sociaux des salles** — blocs `var SITES` et
  `var RESEAUX`.
- **Le numéro d'édition et les dates en page d'accueil** — le titre de la page,
  la mention « 18ᵉ édition · 2026 » et la ligne « Du mercredi 21 au mardi 27
  octobre 2026 ».
- **Les tarifs** et le texte de la rubrique **Animations**.
