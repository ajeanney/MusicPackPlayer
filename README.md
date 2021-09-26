# MusicPackPlayer

Play the music of your resource pack inside WorldGuard regions: a player walks into a region and its sound starts, walks out and it stops. No client mod, nothing to install on the player side.

## Features

- One sound per WorldGuard region, set in the configuration or with a command.
- Automatic playback: the region a player stands in is checked once per second, so entering, leaving and moving between regions is picked up without any command.
- Sound names are namespaced keys, so anything shipped in your resource pack can be used (`mypack:music.spawn`), not only vanilla sounds.
- Played at a very high volume, so the music is heard across the whole region, and stopped as soon as the player leaves it.
- Tab completion for the region names (read from WorldGuard) and for the sounds already configured.

## Requirements

- Spigot/Paper 1.17 or newer.
- [WorldGuard](https://enginehub.org/worldguard/) and its WorldEdit dependency: WorldGuard is declared as a hard dependency.

## Installation

1. Build the plugin (see below) and drop the jar in your server's `plugins/` folder.
2. Start the server once: `plugins/MusicPackPlayer/config.yml` is generated.
3. Add your sounds, either by editing that file or with `/musicpack set`.

## Commands

| Command | Description | Permission |
| --- | --- | --- |
| `/musicpack set <region> <sound>` | Sets the sound played in a region | `musicpack.command` |
| `/musicpack remove <region>` | Removes the sound of a region | `musicpack.command` |
| `/musicpack reload` | Reloads the configuration | `musicpack.command` |

Running `/musicpack` without an argument (or with an unknown one) prints the list of subcommands. From the console, only `reload` is accepted.

## Configuration

```yaml
Region:
  spawn: mypack:music.spawn
  arena: mypack:music.arena
```

Each key is a WorldGuard region id, each value the sound played inside it. `/musicpack set <region> <sound>` writes exactly the same thing.

## Building

```sh
mvn clean package
```

The jar lands in `target/`. It is compiled for Java 8, so it runs on every server from 1.17 up.
