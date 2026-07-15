# INF 1430 — Version personnalisée (site web)

Site web statique (hébergé sur GitHub Pages) qui présente et formalise la version
personnalisée du cours **INF 1430 — Projet en informatique** (6 crédits, TELUQ),
proposée par Christian Jauvin. Le site sert de document de référence à partager
avec d'éventuels nouveaux étudiants.

## Contexte

- INF 1430 est un cours de projet au format officiel assez libre, évalué par
  4 travaux écrits remis à intervalles réguliers :

  | # | Titre                   | Pondération |
  |---|-------------------------|-------------|
  | 1 | Plan de projet documenté | 10 %       |
  | 2 | Rapport mi-parcours      | 20 %       |
  | 3 | Produit final fonctionnel | 30 %      |
  | 4 | Rapport du projet présenté | 40 %     |

- La version personnalisée s'inspire directement des idées de la **nouvelle
  version d'INF 1410 (Génie logiciel)**, prévue pour septembre 2026. Un
  alignement explicite entre les deux cours est un objectif central.

- Le site doit être explicite sur le fait qu'il s'agit de la **vision
  personnelle** de Christian Jauvin — son implémentation particulière du
  format officiel. Chaque professeur qui encadre INF 1430 est entièrement
  libre de ses méthodes. (Précision présente sur l'accueil, dans la FAQ et
  dans le pied de page commun.)

## Philosophie du modèle proposé

Le projet de l'étudiant est mené *comme un vrai projet logiciel*, avec le
professeur dans un rôle de chargé de projet / reviewer, plutôt que de simple
correcteur de travaux remis en fin de parcours.

Les cinq piliers :

1. **Le dépôt git comme colonne vertébrale.** Tout le projet vit dans un repo
   GitHub dont l'évolution est visible et constatable (historique de commits,
   branches, tags). Le prof a un accès permanent — pas d'effet « boîte noire »
   entre deux remises.

2. **Les pull requests comme unité de travail et de rétroaction.** Le travail
   avance par PR que le professeur review (commentaires, demandes de
   changement, approbation). La review de code devient le mécanisme principal
   d'encadrement pédagogique.

3. **GitHub Projects comme outil de gestion.** Planification et suivi via un
   board (backlog, sprints/itérations, issues, milestones) — une méthode
   inspirée de scrum, adaptée à un projet individuel.

4. **Communication centrale et active**, sur deux canaux complémentaires :
   - **Synchrone** : rencontres Teams en temps réel, quand c'est nécessaire.
   - **Asynchrone** : conversations dans GitHub (commentaires d'issues, de PR,
     discussions) — la voie par défaut, qui laisse une trace.

5. **Alignement avec INF 1410.** Les méthodes pratiquées dans INF 1430 sont
   l'application concrète des idées de génie logiciel présentées dans INF 1410.
   INF 1430 devient en quelque sorte le « laboratoire » d'INF 1410.

### Position sur l'IA

L'usage de l'IA générative est **encouragé comme compétence à développer**
(cohérent avec l'esprit « outils réels de l'industrie »), à une condition :
qu'il ne nuise pas à l'apprentissage. Règle centrale : l'étudiant doit
comprendre, et pouvoir expliquer et défendre, tout ce qu'il intègre au
projet. Transparence attendue (mentionner un usage notable de l'IA, p. ex.
dans la description d'une PR) ; retour réflexif sur l'usage de l'IA bienvenu
dans le rapport final.

C'est aussi un argument important **en faveur** du modèle : un format « 4
remises espacées » n'offre aucune visibilité sur le processus (et donc aucune
prise sur l'usage de l'IA), tandis qu'un processus visible (commits, PRs,
réponses aux reviews) rend la compréhension démontrable. La review de PR est
le garde-fou naturel. Cadrage volontairement non punitif : visibilité et
transparence, pas surveillance ni suspicion.

### Compatibilité avec le format officiel

Les 4 travaux notés officiels sont conservés comme jalons d'évaluation, mais
réinterprétés à travers le modèle :

| Travail officiel | Réinterprétation dans le modèle |
|---|---|
| 1. Plan de projet (10 %) | Mise en place du repo, du board GitHub Projects, backlog initial, README/plan documenté dans le repo |
| 2. Rapport mi-parcours (20 %) | Jalon (milestone) à mi-parcours : état du board, PRs mergées, rapport intermédiaire versionné dans le repo |
| 3. Produit final (30 %) | Le repo lui-même : produit fonctionnel, historique de développement, qualité du code et des PRs |
| 4. Rapport final (40 %) | Rapport final rédigé (et idéalement versionné) dans le repo, incluant un retour réflexif sur le processus |

> Point à valider : la part du processus (qualité des PRs, activité sur le
> board, communication) dans la note de chaque travail.

## Architecture du site

### Choix techniques

- **Site statique, HTML/CSS pur, sans étape de build** (pas de Jekyll, ni
  d'Astro/Hugo) : quelques pages seulement, contenu stable, aucune dépendance,
  déploiement GitHub Pages trivial (branche `main`, racine ou `/docs`).
- **Une seule feuille de style** (`style.css`), design sobre et lisible,
  responsive, avec support des thèmes clair/sombre via
  `prefers-color-scheme`.
- **Langue : français** (public : étudiants TELUQ).
- Pas de JavaScript sauf besoin ponctuel (p. ex. rien au départ).
- Diagrammes éventuels en SVG inline (p. ex. le cycle d'une PR, le flux d'un
  sprint).

### Structure des pages

```
/
├── index.html          # Accueil : le pitch du modèle en une page
├── philosophie.html    # Pourquoi ce modèle ; alignement avec INF 1410
├── modele.html         # Le fonctionnement concret : repo, PRs, Projects, communication
├── deroulement.html    # Le semestre pas à pas + correspondance avec les 4 travaux notés
├── faq.html            # Questions d'étudiants éventuels
├── style.css
└── CLAUDE.md           # (ce fichier — plan de conception)
```

Contenu prévu par page :

1. **Accueil (`index.html`)** — résumé du modèle en quelques paragraphes :
   « un cours de projet mené comme un vrai projet logiciel ». Liens vers les
   autres pages. Mention du format officiel du cours (TELUQ) et de la nature
   « proposition personnalisée » de ce site.

2. **Philosophie (`philosophie.html`)** — les idées de fond : apprendre le
   génie logiciel en le pratiquant ; la rétroaction continue plutôt que la
   correction terminale ; la trace écrite (git, PRs) comme mémoire du projet ;
   l'IA encouragée comme compétence, avec le processus visible comme
   garde-fou ; l'alignement avec INF 1410 (avec renvois explicites quand le
   contenu d'INF 1410 sera public).

3. **Le modèle (`modele.html`)** — la mécanique concrète :
   - le repo GitHub : mise en place, visibilité, conventions ;
   - le flux de travail par PR : branche → PR → review du prof → merge ;
   - GitHub Projects : board, issues, itérations, milestones ;
   - la communication : Teams (synchrone, au besoin) vs GitHub (asynchrone,
     par défaut) ; attentes de réactivité de part et d'autre.

4. **Déroulement (`deroulement.html`)** — le semestre semaine par semaine (ou
   par phases), et le tableau de correspondance entre les 4 travaux officiels
   et leurs réinterprétations (voir plus haut).

5. **FAQ (`faq.html`)** — p. ex. : « Faut-il déjà connaître git/GitHub ? »,
   « Le repo doit-il être public ou privé ? », « Quel type de projet est
   admissible ? », « À quelle fréquence dois-je pousser du code ? »,
   « Ai-je le droit d'utiliser l'IA ? », « Comment se passent les rencontres
   Teams ? ».

## Déploiement

- Repo GitHub : [cjauvin/inf1430-teluq](https://github.com/cjauvin/inf1430-teluq)
  (public).
- GitHub Pages servi depuis la branche `main` (racine).
- URL du site : <https://cjauvin.github.io/inf1430-teluq/>.

## Questions ouvertes / à préciser avec l'utilisateur

- [ ] Contenu d'INF 1410 : quelles idées précises citer/référencer ? (le cours
      n'est pas encore offert — septembre 2026)
- [ ] Repo étudiant public ou privé (avec le prof comme collaborateur) ?
- [ ] Détail de la grille : le processus (PRs, board, communication) est-il
      noté explicitement, ou seulement les 4 livrables ?
- [ ] Cadence proposée : itérations de 2 semaines ? rencontres Teams à
      fréquence fixe ou sur demande ?
- [x] Nom définitif du repo / URL du site : `cjauvin/inf1430-teluq`,
      <https://cjauvin.github.io/inf1430-teluq/>.

## Étapes de réalisation

1. ✅ Plan de conception (ce fichier)
2. ✅ `git init` + premier commit
3. ✅ Squelette HTML/CSS (les 5 pages + navigation + style, premier jet de contenu)
4. Rédaction du contenu page par page (itérativement, avec l'utilisateur)
5. ✅ Création du repo GitHub + activation de GitHub Pages
6. Révision finale et publication
