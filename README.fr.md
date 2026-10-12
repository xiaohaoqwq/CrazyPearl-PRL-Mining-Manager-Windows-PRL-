<div align="center">

**[中文](./README.md) · [English](./README.en.md) · Français**

# CrazyPearl

### Le minage de PRL sous Windows, plus simple à configurer et à suivre

Moteurs, pools, réglages GPU et estimation des revenus dans une seule fenêtre.

![Windows x64](https://img.shields.io/badge/Windows-x64-0078D4?style=flat-square)
![Version](https://img.shields.io/badge/Version-v0.2.15_Bêta-33BFA0?style=flat-square)
![PRL](https://img.shields.io/badge/PRL-PearlHash-7189FF?style=flat-square)

**[Télécharger le logiciel](./疯狂的珍珠-0.2.15.exe?raw=true)** · **[Configuration initiale](./settings.json?raw=true)** · **[Compteur de temps](./fee-ledger.json?raw=true)**

[Démarrage rapide](#démarrage-rapide) · [Fonctionnalités](#fonctionnalités) · [Réglages courants](#réglages-courants) · [Fichiers et mises à jour](#fichiers-et-mises-à-jour)

</div>

---

Lancer un moteur ne suffit pas : il faut aussi suivre le hashrate, repérer les déconnexions et surveiller les températures. **CrazyPearl réunit ces tâches quotidiennes.** Choisissez un moteur, renseignez votre adresse de paiement et votre pool, puis gérez votre machine depuis la même interface. Les paramètres valides sont enregistrés automatiquement pour la prochaine session.

## Nouveautés de la version 0.2.15

- **Passez du chinois à l'anglais ou au français en haut à droite**, sans redémarrer le logiciel ni le moteur. Pages, tableaux, descriptions des moteurs, infobulles des graphiques, journaux du logiciel et boîtes de dialogue suivent votre choix.
- **Votre langue est mémorisée.** Les anciennes configurations s'ouvrent en chinois par défaut. Le changement de langue conserve les nombres en cours de saisie, la position du curseur, l'adresse de paiement, le nom du worker et les pools.
- **Une présentation adaptée aux langues et aux configurations multi-GPU.** Les boutons s'ajustent au texte, les colonnes restent lisibles et les longues infobulles peuvent être consultées en entier. La sortie brute du moteur conserve sa langue d'origine.

Pour mettre à jour, conservez vos fichiers `settings.json` et `fee-ledger.json`, vos moteurs et vos journaux. Remplacez uniquement l'EXE.

## Pourquoi CrazyPearl ?

| Voir chaque GPU | Gérer les interruptions | Régler à partir des données du pilote |
| :--- | :--- | :--- |
| Consultez le hashrate total et celui de chaque carte pour repérer une baisse de performance ou une température élevée. | Définissez des règles en cas de hashrate faible, d'absence de parts acceptées ou de surchauffe, avec une limite de redémarrages. | Lisez les paliers de fréquence proposés par le pilote avant de choisir les cibles. Puissance, ventilation et fréquences sont regroupées. |

**Moins de fenêtres et de scripts à gérer. Un suivi plus clair de votre machine.**

## Fonctionnalités

| Fonction | Utilité |
| :--- | :--- |
| **Interface en trois langues** | Choisissez 中文, English ou Français en haut à droite. Le choix s'applique immédiatement et s'enregistre sans modifier les saisies ni la session de minage. |
| **Plusieurs moteurs** | SRBMiner-MULTI, PeakMiner et BzMiner : fiches descriptives, téléchargement officiel et importation de dossiers complets au même endroit. |
| **Suivi multi-GPU** | Hashrate, températures du cœur et de la mémoire, puissance, ventilation, fréquences et parts par carte. Les longs tableaux défilent indépendamment ; les réglages suivent l'identité du GPU. |
| **Réglages GPU directs** | Puissance, ventilation et fréquences des GPU NVIDIA. Un bouton dédié lit les paliers du pilote ; appliquez les cibles immédiatement ou au lancement du minage. |
| **Protection et reprise** | Règles de hashrate faible, délai sans part acceptée et protection thermique, avec période de chauffe et limite de redémarrages. |
| **Historique local du hashrate** | Mise à jour à chaque rapport du moteur. Échelle en minutes, heures ou jours ; les interruptions sont marquées en rouge et consignées. |
| **Revenus et coût électrique** | Choisissez une plateforme et une référence de prix. Combinez hashrate, tarif électrique, puissance et durée quotidienne pour estimer le revenu net et le coût énergétique en CNY ou USD. |
| **Pools et démarrage** | Adresse personnelle ou compte de pool, nom du worker, pools de secours et minage facultatif à l'ouverture de session Windows avec les paramètres enregistrés. |
| **Journaux et diagnostic** | Recherche dans la sortie du moteur, journal du logiciel et export de diagnostic. Journaux regroupés avec conservation sur sept jours. |

Les mesures proviennent du moteur ou du pilote. L'interface indique les données indisponibles. Les GPU compatibles dépendent du moteur choisi ; les réglages directs concernent NVIDIA.

## Démarrage rapide

### 1. Téléchargez trois fichiers dans le même dossier

Choisissez un **dossier accessible en écriture**. Aucune archive à extraire. Installez d'abord le pilote graphique.

| Fichier | Téléchargement | Rôle |
| :--- | :---: | :--- |
| **疯狂的珍珠-0.2.15.exe** | [Logiciel](./疯狂的珍珠-0.2.15.exe?raw=true) | Application principale ; le nom du fichier reste identique dans toutes les langues |
| **settings.json** | [Configuration](./settings.json?raw=true) | Configuration initiale vierge ; enregistrement automatique des modifications valides |
| **fee-ledger.json** | [Compteur](./fee-ledger.json?raw=true) | Compteur initial du temps cumulé |

Vous pouvez aussi ouvrir chaque fichier du dépôt et choisir **Download raw file**. Enregistrez ce README si vous souhaitez le consulter hors ligne.

### 2. Choisissez un moteur et renseignez vos coordonnées de paiement

Ouvrez l'EXE et sélectionnez **Français** en haut à droite. Dans **Moteurs de minage**, téléchargez et sélectionnez un moteur, ou importez son dossier complet. Revenez dans **Vue d'ensemble** et remplissez :

| Paramètre | Valeur attendue |
| :--- | :--- |
| **Adresse de paiement / compte de pool** | Votre adresse PRL personnelle, ou le compte demandé par le pool. |
| **Nom du worker** | Un nom permettant d'identifier cette machine. Certains pools utilisent `compte.worker` : modifiez alors le nom après le point dans le champ du compte de paiement. |
| **Adresse du pool** | Le `domaine:port` fourni par le pool. Suivez les indications du moteur pour les connexions de secours et les comptes. |

> **Renseignez d'abord vos propres coordonnées de paiement. Si l'adresse reste vide au démarrage, le logiciel utilise celle de l'auteur et les revenus concernés lui sont attribués. Un message l'indique dans Vue d'ensemble.**

### 3. Lancez le minage et définissez les règles de fonctionnement

Cliquez sur **Démarrer**, puis vérifiez le hashrate, les températures et les parts acceptées. Les modifications valides sont enregistrées automatiquement.

- **Pour une utilisation continue :** remplissez les règles de hashrate faible, de délai sans part, de température et de redémarrage dans **Protection et reprise**.
- **Pour régler les cartes :** ouvrez **Réglages GPU**, cliquez sur **Lire les paliers du pilote**, choisissez les cibles, puis **Appliquer**, ou activez l'application au démarrage du minage.
- **Pour estimer les revenus :** ouvrez **Revenus**, choisissez une plateforme et renseignez le tarif électrique, le taux de change et les autres paramètres.

La configuration publique ne contient aucun compte, nom de worker ou réglage personnel ; le compteur est à zéro. Le tarif électrique, le hashrate et la puissance utilisés dans les estimations sont initialisés à zéro : saisissez vos valeurs.

## Réglages courants

<details>
<summary><strong>Reprise automatique : hashrate faible et absence de parts</strong></summary>

Exemple : redémarrer le moteur si le hashrate reste sous **10 %** de sa référence pendant **5 minutes**, avec au maximum **3 redémarrages sur 15 minutes**. Ces valeurs servent d'exemple ; adaptez-les à votre machine.

Les délais sans part, la période de chauffe et la protection thermique se règlent séparément. Le graphique et le journal permettent de retrouver le moment d'une anomalie et l'action effectuée.

</details>

<details>
<summary><strong>Réglages GPU : lire les paliers, puis appliquer les cibles</strong></summary>

**Lire les paliers du pilote** affiche les combinaisons de fréquences prises en charge. La saisie enregistre les cibles ; **Appliquer** modifie le matériel. Une fréquence du cœur ou de la mémoire à **0** sélectionne le mode automatique.

Chaque GPU conserve ses propres cibles, associées à son identité.

</details>

<details>
<summary><strong>Pools de secours et démarrage automatique</strong></summary>

Ajoutez les connexions de secours dans les paramètres des pools et vérifiez les règles du moteur concernant le compte, le mot de passe et la connexion.

Avant d'activer le démarrage automatique dans **Protection et reprise**, vérifiez que vos coordonnées de paiement et votre pool sont enregistrés. Le minage utilisera cette configuration à la prochaine ouverture de session Windows.

</details>

<details>
<summary><strong>Revenus : tenir compte de l'électricité et du fonctionnement</strong></summary>

Choisissez une plateforme et une référence de prix, par exemple la meilleure offre d'achat ou la dernière transaction. Renseignez le tarif électrique, le taux USDT/CNY, les autres consommations, la durée quotidienne et le pourcentage global de déductions. Affichez les estimations de revenus et de coût électrique en CNY ou USD.

Les revenus quotidiens sont des estimations calculées à partir des données de marché et des paramètres saisis, et non un relevé des paiements du pool. Conservez la même méthode pour comparer des cartes ou des réglages.

</details>

## Fichiers et mises à jour

<details>
<summary><strong>Logiciel, configuration et journaux restent dans le dossier de l'application</strong></summary>

```text
CrazyPearl/
├─ 疯狂的珍珠-0.2.15.exe
├─ README.md / README.en.md / README.fr.md  Guides locaux facultatifs
├─ settings.json       Paramètres enregistrés automatiquement
├─ fee-ledger.json     Temps cumulé
├─ logs/               Journaux d'exécution
├─ kernels/            Moteurs téléchargés ou importés
└─ downloads/          Cache des téléchargements
```

Les trois dossiers sont créés automatiquement lorsque nécessaire. Les journaux sont conservés pour aujourd'hui et les six jours précédents. Les fichiers en cours d'écriture ou utilisés sont nettoyés ultérieurement ; la configuration et le compteur sont conservés.

**Pour mettre à jour :** arrêtez le minage et quittez le logiciel. Conservez vos fichiers `settings.json`, `fee-ledger.json` et votre dossier `kernels/`, puis remplacez l'EXE par la nouvelle version. N'écrasez pas vos paramètres avec la configuration initiale vierge.

</details>

---

Frais du logiciel : environ 0,2 % ; frais du moteur en sus.

Ce dépôt distribue une application Windows x64. Il ne contient ni code source, ni pilote graphique, ni moteur tiers. Les moteurs sont publiés par leurs auteurs respectifs ; le logiciel fournit des liens de téléchargement officiels. L'application vérifie l'intégrité de sa version publiée. Téléchargez les fichiers d'origine depuis ce dépôt.

<details>
<summary>Adresse PRL du développeur</summary>

```text
prl1pqc3uxyeewp880raqumz5q6uuzaw9l3rpjxz2ur6agq5pzwmynpfqszj5nx
```

</details>

<div align="center">

[中文](./README.md) · [English](./README.en.md) · **Français**

</div>
