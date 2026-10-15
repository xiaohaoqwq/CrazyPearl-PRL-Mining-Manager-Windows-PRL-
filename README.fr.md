<div align="center">

**[中文](./README.md) · [English](./README.en.md) · Français**

# CrazyPearl · Surfréquence automatique et minage PRL économe

### Trouvez la plage efficace de chaque GPU. Plus de hashrate par watt.

Test du décalage du cœur et de la limite de puissance, carte par carte, pour rechercher un meilleur rendement énergétique.

![Windows x64](https://img.shields.io/badge/Windows-x64-0078D4?style=flat-square)
![Version](https://img.shields.io/badge/Version-v0.2.19_Bêta-33BFA0?style=flat-square)
![PRL](https://img.shields.io/badge/PRL-PearlHash-7189FF?style=flat-square)

**[Télécharger le logiciel](./疯狂的珍珠-0.2.19.exe?raw=true)** · **[Configuration initiale](./settings.json?raw=true)** · **[Registre des parts](./fee-ledger.json?raw=true)**

[Résultats mesurés](#résultats-dun-test-de-réglage) · [Démarrage rapide](#démarrage-rapide) · [Fonctionnalités](#fonctionnalités) · [Réglages courants](#réglages-courants) · [Fichiers et mises à jour](#fichiers-et-mises-à-jour)

</div>

---

**Avec les bons paramètres, un même GPU peut parfois maintenir ou augmenter son hashrate tout en consommant moins.** CrazyPearl automatise la recherche : mesure de référence, essais de décalage du cœur et de puissance, comparaison du hashrate et de la consommation, puis validation et enregistrement du profil. Chaque GPU NVIDIA est testé séparément pour tenir compte du modèle et des différences entre cartes.

## Résultats d'un test de réglage

Un test local de minage PRL sur RTX 5070 Ti :

| Indicateur | Référence initiale | Profil de rendement validé | Évolution |
| :--- | ---: | ---: | ---: |
| **Puissance moyenne du GPU** | 279,82 W | **249,98 W** | **−10,7 %** |
| **Hashrate local moyen** | 177,03 TH/s | **178,77 TH/s** | **+1,0 %** |
| **Hashrate par watt du GPU** | 0,633 TH/s/W | **0,715 TH/s/W** | **+13,0 %** |

**Environ 30 W de moins, avec un léger gain de hashrate lors de ce test.** Le profil utilise un décalage du cœur de +120 MHz et une limite de 250 W, contre 280 W pour la référence. Mesure initiale de 180 secondes, puis confirmation du profil pendant 600 secondes, avec 16 parts acceptées par le pool.

<details>
<summary>Conditions et méthode de mesure</summary>

Cet exemple provient du test de réglage automatique de la version 0.2.18 ; la version actuelle 0.2.19 améliore la compatibilité multi-GPU. Moteur SRBMiner-MULTI 3.7.3, pilote NVIDIA 617.42, cible mémoire de 7001 MHz et ventilateurs à 100 % dans les deux configurations. Le hashrate est fourni par le moteur local et la puissance par le pilote. Le rendement est calculé à partir du hashrate et de l'énergie intégrés sur la période de mesure ; les pourcentages utilisent les valeurs non arrondies.

Ces résultats concernent cette carte dans ces conditions. Les autres GPU, moteurs et environnements nécessitent leurs propres tests. La puissance GPU exclut la carte mère, le CPU et les pertes de l'alimentation ; ajoutez-les séparément dans le calcul des revenus pour estimer la consommation totale.

</details>

## Pourquoi CrazyPearl ?

| Priorité au hashrate par watt | Un profil par GPU | Une machine suivie en continu |
| :--- | :--- | :--- |
| Choisissez le meilleur rendement en conservant le minimum de hashrate fixé, ou privilégiez le hashrate maximal. | Mesurez et enregistrez les paramètres de chaque carte, sans recopier le profil d'un GPU sur toute la machine. | Confirmation de 10 minutes, annulation avec restauration, protection thermique, reprise automatique et enregistrement des paramètres. |

Surfréquence du cœur et limites de puissance sont testées ensemble. La recherche ne dépasse pas la limite de puissance initiale. Si le pilote ne prend pas en charge le décalage du cœur, seuls les réglages de puissance sont testés.

## Fonctionnalités

| Fonction | Utilité |
| :--- | :--- |
| **Réglage automatique par GPU** | Test du hashrate et de la puissance de chaque GPU NVIDIA, résultats distincts pour hashrate et rendement, annulation avec restauration et profils validés enregistrés. |
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
| **疯狂的珍珠-0.2.19.exe** | [Logiciel](./疯狂的珍珠-0.2.19.exe?raw=true) | Application principale ; le nom du fichier reste identique dans toutes les langues |
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
- **Pour le réglage automatique :** démarrez le minage, sélectionnez les GPU NVIDIA en ligne à tester, choisissez le meilleur rendement ou le hashrate maximal, puis lancez le réglage automatique. Les cartes sont testées une par une : 60 secondes de chauffe, 180 secondes de mesure et 10 minutes de confirmation du profil candidat. Les profils confirmés sont enregistrés automatiquement. La puissance reste sous la limite initiale ; annuler et restaurer rétablit les paramètres précédents. ouvrez **Revenus**, choisissez une plateforme et renseignez le tarif électrique, le taux de change et les autres paramètres.

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
├─ 疯狂的珍珠-0.2.19.exe
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

<details>
<summary><strong>Réglage automatique par GPU</strong></summary>

Démarrez le minage, sélectionnez les GPU dans Réglages GPU puis descendez au test automatique. Choisissez rendement ou hashrate, réglez le minimum de référence et le décalage maximal, puis démarrez. Utilisez un seul programme de réglage.

Par défaut, le test conserve 90 % du hashrate de référence et limite le décalage à +180 MHz. Chaque essai chauffe pendant 60 s et mesure pendant 180 s ; le candidat est validé pendant 10 min. Les cartes sont testées successivement. Les profils validés sont enregistrés et restent appliqués. L'option existante d'application au lancement contrôle les démarrages suivants.

Le test ne relève pas la puissance maximale présente au départ. Il explore les décalages pris en charge, la puissance et les combinaisons proches. Sans décalage compatible, seule la puissance est testée. La mémoire conserve ses réglages de référence ; la tension reste inchangée. Annulation, surchauffe, perte de GPU ou erreur déclenchent une restauration ; si elle échoue, le mineur du logiciel est arrêté.

Le rendement utilise les TH/s/W du GPU ; la carte mère et les pertes d'alimentation influencent aussi le coût total. Les résultats concernent cet appareil, ce moteur et la plage testée. Refaites le test après un changement de moteur ou de pilote. Détails dans `logs/date/auto-tune-*/report.json`, conservés sept jours avec les journaux.

</details>

---

Frais en parts : environ 0,2 % ; frais du moteur en sus.

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
