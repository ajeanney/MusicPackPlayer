# MusicPackPlayer

Joue la musique de votre resource pack à l'intérieur des régions WorldGuard : le joueur entre dans une région, son son démarre, il en sort, il s'arrête. Aucun mod client, rien à installer côté joueur.

## Fonctionnalités

- Un son par région WorldGuard, défini dans la configuration ou avec une commande.
- Lecture automatique : la région dans laquelle se trouve le joueur est vérifiée une fois par seconde, donc les entrées, les sorties et les changements de région sont pris en compte sans aucune commande.
- Les noms de sons sont des clés namespacées : tout ce qui est fourni par votre resource pack peut être utilisé (`mypack:music.spawn`), pas seulement les sons vanilla.
- Le son est joué à un volume très élevé, pour être entendu dans toute la région, et coupé dès que le joueur la quitte.
- Autocomplétion des noms de régions (lus depuis WorldGuard) et des sons déjà configurés.

## Prérequis

- Spigot/Paper 1.17 ou supérieur.
- [WorldGuard](https://enginehub.org/worldguard/) et sa dépendance WorldEdit : WorldGuard est déclaré comme dépendance obligatoire.

## Installation

1. Compilez le plugin (voir plus bas) et déposez le jar dans le dossier `plugins/` de votre serveur.
2. Démarrez le serveur une fois : `plugins/MusicPackPlayer/config.yml` est généré.
3. Ajoutez vos sons, soit en éditant ce fichier, soit avec `/musicpack set`.

## Commandes

| Commande | Description | Permission |
| --- | --- | --- |
| `/musicpack set <region> <son>` | Définit le son joué dans une région | `musicpack.command` |
| `/musicpack remove <region>` | Supprime le son d'une région | `musicpack.command` |
| `/musicpack reload` | Recharge la configuration | `musicpack.command` |

Lancée sans argument (ou avec un argument inconnu), `/musicpack` affiche la liste des sous-commandes. Depuis la console, seul `reload` est accepté.

## Configuration

```yaml
Region:
  spawn: mypack:music.spawn
  arena: mypack:music.arena
```

Chaque clé est un identifiant de région WorldGuard, chaque valeur le son joué à l'intérieur. `/musicpack set <region> <son>` écrit exactement la même chose.

## Compilation

```sh
mvn clean package
```

Le jar est écrit dans `target/`. Il est compilé pour Java 8, il tourne donc sur tous les serveurs à partir de la 1.17.
