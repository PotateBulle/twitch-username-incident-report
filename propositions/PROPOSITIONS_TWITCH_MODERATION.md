# Propositions d’amélioration pour la modération des pseudos Twitch

**Ces propositions ne visent pas à automatiser des sanctions massives. Elles visent à mieux détecter les cas manifestement problématiques, à faciliter leur revue humaine et à améliorer le lien entre la modération bénévole et les équipes internes de Twitch.**

**Une grande partie de ces mesures pourrait être mise en place progressivement, en commençant par les pseudos les plus évidents et les patterns déjà signalés par plusieurs communautés.**

Ce document regroupe des pistes concrètes que Twitch pourrait mettre en place pour limiter la création, l’affichage et l’utilisation de pseudos offensants, haineux ou volontairement ambigus.

L’objectif n’est pas de demander une modération parfaite. Aucun outil automatique ne peut tout comprendre, ni remplacer totalement l’analyse humaine. En revanche, il existe déjà des mesures simples, réalistes et peu coûteuses qui pourraient réduire une partie importante du problème.

Le constat de départ est assez simple : certains comptes arrivent à créer des pseudos problématiques en utilisant des fautes volontaires, des chiffres, des variantes orthographiques ou des structures répétitives. Ces pseudos sont ensuite visibles publiquement, parfois avant même que la personne n’écrive un message dans le chat.

Dans ce cas, la charge de détection repose surtout sur les streameureuses, les modérateurices bénévoles et les communautés. Ce fonctionnement montre une limite importante : la modération arrive souvent après l’exposition au problème.

---

## 1. Renforcer le contrôle au moment de la création du pseudo

La première barrière devrait se trouver au moment de la création du compte ou du changement de pseudo.

Si un pseudo offensant peut être créé, affiché et utilisé publiquement, cela signifie que le contrôle arrive trop tard. Un système de vérification plus solide à la création permettrait de bloquer ou de mettre en attente les cas les plus évidents.

Une première étape simple serait de normaliser les pseudos avant analyse.

Exemples :

```txt
arracheur2kipp4
→ arracheur kippa

aracheur2kiipa
→ arracheur kipa

pourfendeur2noir
→ pourfendeur noir
```

Cette normalisation permettrait de mieux repérer les variantes évidentes, sans forcément utiliser une IA.

Un système basé sur des règles, des listes de termes sensibles, des expressions régulières, des variantes connues et de la similarité entre mots pourrait déjà aider à bloquer une partie des pseudos manifestement non conformes.

---

## 2. Détecter les variantes orthographiques simples

Beaucoup de pseudos problématiques ne reprennent pas toujours les mots exacts. Ils utilisent plutôt des contournements simples.

Exemples de contournements fréquents :

```txt
lettres remplacées par des chiffres
lettres doublées
lettres supprimées
fautes volontaires
mots séparés par des chiffres
variantes phonétiques
```

Un traitement basique pourrait déjà repérer ce type de transformation :

```txt
kipp4 → kippa
kiipa → kipa
tranns → trans
aracheur → arracheur
2 → séparateur possible
```

Ce type de détection est réaliste à mettre en place. Il ne demande pas une IA, mais surtout une meilleure logique de normalisation avant validation du pseudo.

---

## 3. Utiliser un score de risque plutôt qu’un blocage automatique brutal

Tous les pseudos ambigus ne doivent pas être bloqués automatiquement. Certains cas peuvent nécessiter une analyse humaine.

Pour éviter les erreurs, Twitch pourrait utiliser un score de risque.

Exemple de logique possible :

```txt
terme violent détecté : +40
référence possible à un groupe protégé : +50
variante orthographique suspecte : +20
chiffre utilisé comme séparation ou contournement : +20
pseudo similaire à plusieurs comptes récents : +30
```

Selon le score final, plusieurs actions seraient possibles :

```txt
score faible : pseudo accepté
score moyen : pseudo accepté mais surveillé
score élevé : pseudo envoyé en revue
score très élevé : pseudo refusé à la création
```

Cette approche serait plus juste qu’un simple filtre par mot-clé. Elle permettrait de prendre en compte le contexte global du pseudo, sa structure et sa proximité avec d’autres pseudos déjà problématiques.

---

## 4. Repérer les patterns en série

Le problème ne vient pas seulement de pseudos isolés. Dans certains cas, plusieurs comptes semblent utiliser la même logique de création.

Exemples de structures possibles :

```txt
mot violent + groupe ciblé
mot violent + référence religieuse
mot violent + insulte
mot violent + caractéristique personnelle
```

Quand plusieurs comptes suivent une structure proche, Twitch devrait pouvoir les regrouper automatiquement dans un même incident.

Exemple :

```txt
arracheur2kipa
aracheur2kiipa
arracheur2kipp4
aracheur2kippa223
```

Ces comptes ne devraient pas être traités comme des cas totalement séparés. Ils peuvent indiquer un pattern, une tentative de contournement ou une création en série.

Un regroupement automatique aiderait les équipes internes à comprendre plus vite qu’il ne s’agit pas forcément d’un simple cas isolé.

---

## 6. Transformer certains bans communautaires en signalements structurés

Lorsqu’un compte est banni d’une chaîne pour un pseudo problématique, Twitch pourrait proposer une option supplémentaire.

Exemple :

```txt
Ce bannissement concerne-t-il un pseudo non conforme ?
[ ] Oui

Ce pseudo semble-t-il viser un groupe protégé ?
[ ] Oui

Ce compte fait-il partie d’un pattern ou d’une série ?
[ ] Oui

Souhaitez-vous escalader ce cas à Twitch ?
[ ] Oui
```

Cela créerait un meilleur lien entre la modération locale des chaînes et la modération interne de Twitch.

Le ban communautaire resterait une action locale, mais il pourrait aussi devenir un signal utile pour les équipes Trust & Safety.

---

## 7. Générer un dossier d’incident automatiquement

Quand plusieurs comptes sont bannis ou signalés pour un motif proche, Twitch pourrait créer un dossier d’incident interne.

Ce dossier pourrait contenir :

```txt
identifiants concernés
date et heure des bans
chaînes touchées
motifs utilisés
nombre de signalements
similarité entre les pseudos
pattern détecté
captures ou logs disponibles
statut de traitement
```

Ce système aiderait les équipes Twitch à traiter le problème comme une série cohérente, et non comme une accumulation de petits signalements séparés.

Il permettrait aussi de mieux prioriser les cas les plus sérieux.

---

## 8. Donner plus de poids aux signalements répétés

Un pseudo problématique signalé sur une seule chaîne peut parfois être ambigu. En revanche, si le même compte est banni ou signalé sur plusieurs chaînes en peu de temps, le signal devient beaucoup plus fort.

Twitch pourrait utiliser des indicateurs simples :

```txt
nombre de chaînes ayant banni le compte
nombre de signalements reçus
motif dominant des signalements
âge du compte
similarité avec d’autres pseudos sanctionnés
présence dans une série de comptes récents
```

Cela permettrait de mieux prioriser les dossiers nécessitant une intervention rapide, notamment lors d’attaques haineuses massives ou de raids coordonnés à des fins malveillantes.

---

## 9. Ajouter un niveau de risque lié au pseudo

Twitch pourrait mettre en place un indicateur discret de risque lié aux identifiants.

Côté modération, cela pourrait apparaître sous une forme simple :

```txt
Risque lié au pseudo : faible
Risque lié au pseudo : moyen
Risque lié au pseudo : élevé
```

Cet indicateur ne devrait pas forcément être visible publiquement. Il pourrait être réservé aux outils de modération et aux équipes internes.

L’objectif ne serait pas de condamner automatiquement un compte, mais d’aider les modérateurices à repérer plus vite les pseudos manifestement problématiques.

---

## 10. Permettre l’export des incidents

Les modérateurices qui documentent sérieusement les abus devraient pouvoir exporter un rapport directement depuis Twitch.

Formats utiles :

```txt
CSV
JSON
Markdown
PDF
```

Informations utiles :

```txt
pseudo
date du ban
motif du ban
chaîne concernée
lien du compte
message de modération
statut du signalement
```

Un export Markdown serait particulièrement utile pour documenter les cas dans un dépôt GitHub, un espace interne ou un dossier de suivi.

Cela éviterait aussi de devoir recopier manuellement les informations à chaque incident.

---

## 11. Améliorer le flux entre modération bénévole et Twitch

Le problème n’est pas seulement technique. Il existe aussi un problème de transmission entre les personnes qui modèrent les chaînes au quotidien et les équipes internes de Twitch.

Les modérateurices bénévoles voient souvent les problèmes en premier. Elles repèrent les patterns, les raids, les contournements et les comportements répétés.

Mais si ces informations restent dispersées dans des bans locaux, des notes privées ou des signalements isolés, elles sont moins utiles pour Twitch.

Un meilleur flux pourrait ressembler à ceci :

```txt
modérateurice repère un pattern
→ ban local
→ signalement groupé
→ dossier d’incident généré
→ revue Twitch
→ sanction ou confirmation
→ amélioration des filtres
```

Ce flux permettrait de mieux utiliser l’expérience de terrain des modérateurices, sans leur demander de faire tout le travail à la place de la plateforme.

---

## 12. Préserver l’analyse humaine

Ces propositions ne doivent pas remplacer l’analyse humaine.

Un pseudo peut être ambigu. Un mot peut avoir plusieurs sens. Un système automatique peut se tromper.

Les mesures proposées devraient donc servir à :

```txt
bloquer les cas les plus évidents
mettre en revue les cas douteux
regrouper les patterns
aider les modérateurices
faciliter l’escalade vers Twitch
```

L’objectif n’est pas de bannir automatiquement tout ce qui semble suspect. L’objectif est de réduire les abus évidents et de mieux organiser le traitement des cas répétés.

---

## 13. Ce qui pourrait être mis en place rapidement

Les mesures les plus réalistes à court terme seraient :

```txt
normalisation des pseudos à la création
détection des variantes lettres/chiffres
liste de patterns sensibles
score de risque simple
signalement groupé depuis les bans
champ “pattern observé”
export CSV ou Markdown
dossier d’incident interne
```

Ces mesures ne demandent pas forcément une IA. Elles reposent surtout sur de la logique applicative, de meilleurs outils de modération et une meilleure circulation de l’information.

---

## 14. Conclusion

La modération des pseudos ne devrait pas reposer uniquement sur les communautés.

Quand un pseudo offensant ou haineux est visible publiquement, le mal est déjà en partie fait. Les modérateurices peuvent bannir, documenter et signaler, mais la plateforme devrait mieux empêcher ces pseudos d’exister ou de se diffuser.

Twitch pourrait améliorer la situation avec des mesures simples :

```txt
mieux vérifier les pseudos avant validation
détecter les variantes évidentes
regrouper les cas similaires
faciliter les signalements groupés
créer des dossiers d’incident exploitables
améliorer le lien entre modération bénévole et la modération interne de Twitch
```

Ces améliorations ne régleraient pas tout, mais elles réduiraient la charge des modérateurices bénévoles et rendraient la plateforme plus réactive face aux pseudos haineux, offensants ou intimidants.
