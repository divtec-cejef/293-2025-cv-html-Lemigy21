## A) Corriger le menu de navigation (liens vers les sections)

Actuellement, les deux liens pointent vers la même section :
```
<a href="#comp">Mes compétences</a> <a href="#comp">Ma formation</a>
```

À corriger :

* Le lien “Ma formation” doit pointer vers `#formation` :
```
<a href="#formation">Ma formation</a>
```

💡 *Un menu doit amener vers la bonne section.*

> *Un lien interne fonctionne seulement si `href="#..."` correspond exactement à un `id`.*

---

## B) Rendre la photo cliquable et cohérente

Vous avez :

* un lien qui pointe vers `img/avatar-noe.png`
* mais l’image affichée est `img/4303....jpg`

À corriger :

* le `href` doit ouvrir **la même image** que celle affichée, et idéalement dans un nouvel onglet :
```

  <a class="logo" href="./img/430329607_3279862365653406_3728002599095476390_n.jpg" target="_blank" rel="noopener noreferrer">
  <img src="./img/430329607_3279862365653406_3728002599095476390_n.jpg" alt="Avatar de Noé Migy">

</a>
```

💡 *Le clic sur la photo doit ouvrir la photo affichée.*

> *`rel="noopener noreferrer"` évite qu’un onglet externe puisse manipuler la page d’origine.*

---

## C) Supprimer le CSS “inline” dans le HTML (style="...")

Vous avez des styles directement dans le HTML :
```

<ul style="color: #8a2be2 !important;">
<ul style="background-color: lightgray;">
```

À corriger :

* créer des classes et déplacer ces styles dans `main.css`

Exemple :
```

<ul class="liste-competences">...</ul>
<ul class="liste-formation">...</ul>
```

Puis dans `main.css` :
```
.liste-competences {
color: #8a2be2;
}

.liste-formation {
background-color: lightgray;
}
```

💡 *Le HTML doit rester “structurel”, et le CSS doit gérer l’apparence.*

> *Évitez `!important` : c’est souvent un signe qu’on a mal structuré son CSS.*

---

## D) Retirer `width="300"` dans le HTML et gérer la taille en CSS

Actuellement :
```
<img ... width="300">
```

À corriger :

* retirer le `width` du HTML
* gérer la taille dans CSS

Exemple :
```
img {
max-width: 100%;
height: auto;
}
```

Ou si vous voulez une taille fixe :
```
.photo {
width: 300px;
max-width: 100%;
height: auto;
}
```

💡 *Les tailles se gèrent mieux en CSS pour être responsive.*

> *Responsive = l’image s’adapte aux différents écrans.*

---

## E) Police `@font-face` : mettre en local (consigne)

Vous chargez la police depuis Google en ligne :
```
src: url('[https://fonts.gstatic.com/](https://fonts.gstatic.com/)...') format('woff2');
```

À corriger :

* télécharger la police (woff2) et la mettre dans `./fonts/`
* la référencer en local

Exemple :
```
@font-face {
font-family: 'RobotoCustom';
src: url('../fonts/roboto.woff2') format('woff2');
}
```

💡 *En local, votre site fonctionne même sans dépendance externe.*

> *Un projet propre évite les ressources critiques “à distance”.*

---

## F) Ajouter le favicon (manquant)

La section “Favicon” est vide dans le HTML.

À ajouter (fichiers à la racine avec `./`) :
```

<link rel="icon" href="./favicon.ico">
```

💡 *Le favicon aide à identifier la page dans les onglets.*
