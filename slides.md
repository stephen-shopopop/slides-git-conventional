---
theme: seriph
titleTemplate: '%s - git-commit'
# enable presenter mode, can be boolean, 'dev' or 'build'
presenter: true
download: true
# enable slide recording, can be boolean, 'dev' or 'build'
record: 'build'
exportFilename: git-conventionnal-exported
export:
  format: pdf
  timeout: 30000
  dark: false
  withClicks: false
  withToc: false
background: https://source.unsplash.com/collection/298137/1920x1080
class: text-center
highlighter: shikip
lineNumbers: true
info: |
  ## Team's Shopopop
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
drawings:
  persist: false
fonts:
  sans: Robot
  serif: Robot Slab
  mono: Fira Code
title: Welcome to team's Shopopop
---

# Welcome to team's Shopopop

Presentation slides for developers

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-2">
  <button @click="$slidev.nav.openInEditor()" title="Open in Editor" class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon:edit />
  </button>
  <a href="https://www.shopopop.com" target="_blank" alt="Shopopop"
    class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <carbon:debug />
  </a>
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
layout: cover
class: text-center
---

# Conventional commits

```ts
git commit
```

<br>

<img src="https://git-scm.com/images/logos/downloads/Git-Icon-1788C.png" class="m-auto h-40" />

---
layout: center
---

# Issues

- Publication et versionning des packages laborieuse et fastidieuse.
- Génération des releases sur nos differents projets fait par des opérations manuels.
- Versionning de nos projets fait de façon humaine (minor, major, etc...)
- Une historique git difficile a lire (soit tout est feat, soit tout est fix, ...)
- Impossibilite d´automatiser en l´état certaines tâches.

```shell
git log --grep="fix"
```

---
layout: center
---

# Git commit

Nommer les messages de commits. Le message d’un commit doit être clair et concis, il doit indiquer ce qui a été modifié et la raison de cette modification. La convention de nommage la plus utilisée est la “Conventional Commits“.

L’avantage de respecter cette convention, outre le fait de rendre plus compréhensibles vos commits, est de permettre de respecter la sémantique de versions (SemVer) et d’automatiser certaines tâches (comme la génération d’un fichier Changelog par exemple).

Format des messages Le format du message est le suivant :

```shell
<type>(<scope>): <subject>
<BLANK LINE>
<body>
<BLANK LINE>
<footer>
```

---
layout: center
---

# Le type

Le type du commit décrit l’origine du changement. Il peut prendre différentes valeurs :

- feat: Ajout d’une nouvelle fonctionnalité;
- fix: Correction d’un bug;
- build: Changement lié au système de build ou qui concerne les dépendances (npm, grunt, gulp, webpack, etc.).
- ci: Changement concernant le système d’intégration et de déploiement continu (Jenkins, Travis, Ansible, gitlabCI, etc.)
- docs: Ajout ou modification de documentation (README, JSdoc, etc.);
- perf: Amélioration des performances;
- refactor: Modification n’ajoutant pas de fonctionnalités ni de correction de bug (renommage d’une variable, suppression de code redondant, - simplification du code, etc.);
- style: Changement lié au style du code (indentation, point virgule, etc.);
- test: Ajout ou modification de tests;
- revert: Annulation d’un précédent commit;
- chore: Toute autre modification (mise à jour de version par exemple). Pour chacun des types, vous pouvez également utiliser un système d’emoji comme gitmoji.

---
layout: center
---

# Le scope

Cet élément facultatif indique simplement le contexte du commit. Il s’agit des composants de notre projet, voici une liste non exhaustive :

- controller
- route
- middleware
- view
- config
- service
- etc...

---
layout: center
---

# Le sujet

Le sujet décrit succinctement la modification. Certaines règles doivent être respectées :

Le sujet doit faire moins de 50 caractères. Les verbes doivent être à l’impératif (add, update, change, remove, etc.). La première lettre ne doit pas être en majuscule. Le sujet ne doit pas se terminer par un point.

---
layout: center
---

# Le corps

Le corps du message, qui est optionnel, doit contenir les raisons de la modification ou tout simplement donner plus détails sur le commit. Il peut également indiquer les changements importants (breaking changes). Celui-ci doit faire moins de 100 caractères.

---
layout: center
---

# Le footer

Le footer est également facultatif, celui-ci est surtout utilisé pour faire référence aux tickets (issue) de Github ou Gitlab par exemple que le commit règle ou aux changements importants (breaking changes). Celui-ci doit faire moins de 100 caractères.

exemple:

```shell
refactor(repository): remove deprecated method
 
BREAKING CHANGE: findById and findByPrimary methods have been removed.
 
Closes #78
```


---
layout: center
---

# En savoir plus ...


- [conventional commits](https://www.conventionalcommits.org/en/v1.0.0/)
- [Gitmoji](https://gitmoji.dev)
- [VsCode extension](https://marketplace.visualstudio.com/items?itemName=vivaxy.vscode-conventional-commits)
- [commitizen](https://github.com/commitizen/cz-cli)

---
layout: center
---

# ENSUITE ...

Mettre en place des hooks github sur les projets pour verifier les commits autant en local que via des outils d'intégration. Pour cela, nous pouvons utiliser:

- [simple-git-hooks](https://github.com/toplenboren/simple-git-hooks)
- [commitlint](https://commitlint.js.org/#/)
- [commitlint/cli](https://github.com/conventional-changelog/commitlint)

__exemple pour une validation local:__

```json
 "simple-git-hooks": {
    "pre-commit": "npx commitlint --edit $1",
```

__exemple pour une validation sur une PR:__

[voir lien](https://commitlint.js.org/#/guides-ci-setup?id=github-actions)

---
layout: center
---

# Versionning, release

Afin de faciliter le versionning et/ou la publication de projets ou packages, un outils tel que [changeset](https://github.com/changesets/changesets) facilite cette tâche et peut etre automatiser via differents pipe d´integrations.

Il existe egalement des github Actions comme [changelog-action](https://github.com/requarks/changelog-action) pour generer des releases ainsi que des changelogs.


---
layout: center
class: text-center
---

# Thank's

<img src="https://user-images.githubusercontent.com/94382341/159370370-cb8a63c8-2a42-413c-a659-2ce5662eecbf.png" class="m-30 h-30" />

[GitHub](https://github.com/stephen-shopopop)
