---
title: Un onboarding automatisé
---

### Historique et contexte
A mon arrivée chez makesense, j'ai eu la chance de passer mes premiers instants sur Slack à recevoir du contenu de formation directement sur Slack. Un petit bot, nommé Axel, m'envoyait régulièrement du contenu pendant mes premières semaines, me permettant de me former à ma vitesse.

Plus tard, lorsque je me suis penché sur [la solution technique utilisée](https://www.heyaxel.com/), je me suis rendu compte que nous utilisions un service beaucoup trop puissant pour nous. Nous n'exploitions qu'une partie minime de la solution proposée : l'envoi de messages automatiques, programmé pour n'importe quel nouveau, directement dans Slack.

J'ai décidé de me pencher sur le problème, en essayant de simplifier l'utilisation de cet outil, pour qu'il soit complètement intégré au processus actuel d'onboarding. Ainsi, le remplissage d'un questionnaire signalant l'arrivée d'un nouveau me permet de configurer directement son onboarding.

### Solution technique
#### Outils utilisés

##### Airtable
Chez makesense, Airtable est la solution pour gérer l'ensemble des bases de données, et notamment celle concernant les salarié·e·s. Il était donc assez évident de s'en servir pour avoir une data bien à jour, ainsi que pour pouvoir profiter de son système d'interface.

###### Make
Make est la solution pour automatiser, dès que l'on dépasse le cadre de l'automatisation simple. Ici, rien de trop compliqué, moins de 5 automatisations suffisent à tout gérer.

###### Slack
Evidemment, tous les messages sont envoyés via Slack. En créant un petit bot via Make, il est aisé d'envoyer des messages à n'importe qui !

#### Comment ça marche ?
Commençons par découper ce produit en plusieurs sous-produits pour mieux appréhender la complexité de ce système.

1️⃣ Premièrement, nous avons besoin d'une automatisation qui, pour chaque nouvelle personne, va générer tous les messages à envoyer. En se basant sur un template de messages et sur la date d'arrivée, il est simple de créer chacun des messages, en y assignant la bonne date d'envoi.

2️⃣ Ensuite, pour chacun des messages préalablement généré, il suffit d'utiliser la date d'envoi pour envoyer le message via Slack. Rien de trop compliqué ici.

3️⃣ Pour améliorer le projet un tout petit peu, un peu de personnalisation ne va pas faire de mal. Pour la première partie, une interface Airtable viendra en support pour vérifier si la personne a bien avancé son onboarding en complétant ses différentes tâches. Pour la seconde partie, je vais améliorer l'expérience utilisateur en permettant au nouveau de savoir à quelle partie de son onboarding il en est.

En résumé : Générer les messages -> Les envoyer -> Vérifier s'ils sont bien lus.

##### Partie 1 : Générer les messages à envoyer
Pour stocker l'ensemble des messages à envoyer, il faut commencer à créer une base Airtable, qui aura la structure suivante :
