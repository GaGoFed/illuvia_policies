# Illuvia — Politique de confidentialité

**Dernière mise à jour : 6 août 2026 · S'applique à Illuvia 1.0.0 pour Windows**

## En bref

Illuvia ne collecte rien. Elle n'a ni serveurs, ni comptes, ni outils d'analyse,
et n'ouvre aucune connexion réseau de sa propre initiative. Tout ce que vous
saisissez reste dans des fichiers sur votre PC, sous votre compte Windows.

## Ce qu'Illuvia enregistre, et où

Tout ce que vous saisissez — tâches, listes, transactions, comptes, plans de
paiement, envies, véhicules, réglages — est écrit dans des fichiers de votre
propre dossier utilisateur :

```
%APPDATA%\Gagofed\Illuvia\database\
```

C'est ce dossier, qu'Illuvia vienne du Microsoft Store ou d'une compilation
ordinaire : les données ne vivent pas à l'intérieur du paquet installé.

Ces fichiers sont **chiffrés sur le disque** en AES-256. La clé est générée sur
votre PC au premier lancement et conservée dans le Gestionnaire d'identification
de Windows, protégée pour votre compte Windows (DPAPI). Elle ne dérive jamais de
votre code PIN ou de votre mot de passe, et ne quitte jamais la machine. Copier
les fichiers sur un autre PC, ou tenter de les lire depuis un autre compte
Windows, ne permet pas de les déchiffrer.

Illuvia écrit également un journal de diagnostic en clair :

```
%APPDATA%\Gagofed\Illuvia\logs\illuvia.log
```

Il note ce que l'application a fait — quel module s'est chargé, combien
d'enregistrements ont été lus, ce que disait une erreur — afin qu'un problème
puisse être compris après coup. Il est limité à 5 Mo avec au plus trois fichiers
de rotation, il n'est envoyé nulle part et vous pouvez le supprimer à tout
moment. Il n'est pas chiffré : si vous nous l'envoyez pour obtenir de l'aide,
lisez-le d'abord.

## Ce qu'Illuvia ne fait pas

- **Aucune collecte de données.** Pas de statistiques d'usage, pas de rapports
  de plantage, pas d'analyse, pas de publicité, pas de profilage, aucun
  identifiant d'aucune sorte.
- **Aucun compte.** Il n'y a rien à créer, et aucune adresse e-mail n'est
  nécessaire pour utiliser l'application.
- **Aucun réseau.** Le paquet de l'application ne déclare aucune capacité de
  connexion à Internet et l'application n'effectue aucune requête. Elle
  fonctionne câble réseau débranché.
- **Aucun tiers.** Rien de ce que vous saisissez n'est partagé avec qui que ce
  soit, parce qu'il n'y a personne avec qui le partager.

## Les deux moments où quelque chose sort de l'application

**Ouvrir un lien.** Si vous enregistrez le lien d'une boutique sur une envie, ou
si vous utilisez le lien de don, un appui transmet l'adresse à votre navigateur
par défaut. À partir de là vous êtes sur ce site, sous sa politique de
confidentialité, pas sous celle-ci. Illuvia ne télécharge pas la page.

**Faire une sauvegarde.** Une sauvegarde est un seul fichier contenant tout,
enregistré où vous voulez. La façon dont elle quitte la machine, c'est vous qui
la choisissez :

- **Exporter sans mot de passe** (par défaut). Le fichier est écrit en JSON lisible.
  C'est le seul moyen d'inspecter une sauvegarde ou de l'ouvrir avec autre chose
  qu'Illuvia, et il est aussi privé que l'endroit où vous le mettez. Si vous avez
  enregistré les identifiants d'un service sur un plan de paiement (voir plus
  bas), Illuvia vous prévient avant de l'écrire : ils y sont en clair.
- **Exporter avec un mot de passe.** Le fichier est scellé en AES-256, avec une
  clé dérivée de votre mot de passe (Argon2id). Il peut être restauré sur
  n'importe quelle machine, et sans ce mot de passe il ne s'ouvre pas : personne
  ne peut le récupérer pour vous.

Les copies qu'Illuvia écrit pour elle-même — les automatiques, et la copie de
sécurité prise avant une restauration ou un import — sont toujours scellées avec
la clé de ce PC. Elles restent dans le dossier d'Illuvia, et désinstaller
l'application les y laisse avec tout le reste.

## Les mots de passe que vous enregistrez pour d'autres services

Un plan de paiement peut contenir l'identifiant et le mot de passe du service
qu'il paie — votre compte d'électricité, un abonnement — parce que c'est là que
vous les cherchez. Ils sont enregistrés comme n'importe quel autre champ : dans
la base de données, chiffrés au repos, sur ce PC uniquement. Ils ne sont jamais
envoyés nulle part, et Illuvia n'a aucun moyen de s'en servir.

Deux conséquences. Ils voyagent dans une sauvegarde, et c'est ce qui permet à une
restauration de remettre vos données telles qu'elles étaient ; une **exportation
sans mot de passe** les contient donc en clair, et c'est pourquoi Illuvia prévient avant
d'en écrire une.

## Le verrouillage de l'application

Le code PIN ou le mot de passe qui ouvrent Illuvia sont autre chose, et ils ne
sont jamais enregistrés. Ce qui est enregistré est une empreinte Argon2id, avec un sel
aléatoire, dans le Gestionnaire d'identification de Windows, à côté de la clé de
chiffrement. Windows Hello, si vous l'activez, est entièrement géré par
Windows : Illuvia ne reçoit qu'un oui ou un non et ne voit jamais de données
biométriques.

## Supprimer vos données

Paramètres → Sécurité → *Vider tous les modules* efface tout ce que vous
avez saisi. À côté, *Effacer toutes les données* supprime en plus la clé de chiffrement et
l'identifiant : c'est ce que fait le parcours « j'ai oublié mon code PIN ».

**Désinstaller Illuvia ne supprime pas vos données.** Windows retire
l'application et laisse les dossiers ci-dessus où ils sont, de sorte qu'une
réinstallation retrouve tout tel que vous l'aviez laissé. Si vous voulez que les
données disparaissent aussi, utilisez d'abord l'une des deux commandes, ou
supprimez vous-même le dossier `%APPDATA%\Gagofed\Illuvia\` : il contient la base de
données, le journal et les copies automatiques.

Les sauvegardes que vous avez exportées ne sont touchées par aucune de ces
opérations : vous seul savez où elles se trouvent.

## Mineurs

Illuvia est un organiseur personnel à usage général. Elle ne s'adresse pas aux
enfants et ne collecte aucune information de personne, quel que soit son âge.

## Modifications de cette politique

Si une version future d'Illuvia venait à changer ce qu'elle fait de vos données,
cette page serait mise à jour avant la publication de cette version, et le
changement serait décrit dans les notes de version.

## Contact

Questions sur cette politique : **illuvia.dev@gmail.com**
