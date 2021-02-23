# Ansible Role: Steam

Installs Steam on Debian/Ubuntu servers.

This roles installs and configures the latest version of [SteamCMD](https://developer.valvesoftware.com/wiki/SteamCMD).

## Requirements

None

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

The directory where Steam binaries will be installed.

```yaml
steam_install_path: /opt/steam
```

If set to true, enables and specifies where the Steam game files, managed by this role's variables (see `steam_games`), will be installed.

```yaml
steam_install_games: true
steam_games_path: /usr/local/games/steam
```

Add a set of properties per game to install, including `name` (required), `id` (required), and `path` (optional: installation path, relative to `steam_games_path`).

```yaml
steam_games:
  - name: Valheim Dedicated Server
    id: 896660
```

The user under which Steam will run. Defaults to `steam`.

```yaml
steam_user: steam
```

The Steam credentials to use when downloading games. Defaults to `anonymous`.

```yaml
steam_account: anonymous
steam_password:
```

## Example Playbook

```yaml
- hosts: all
  vars:
    steam_install_path: /opt/steam
    steam_user: steam
    steam_account: steam_account
    steam_password: steam_password # always put your secrets in a vault :)

    steam_install_games: true
    steam_games_path: /usr/local/games/steam
    steam_games:
      - name: Valheim
        id: 892970
  roles:
    - { role: rudisimo.steam }
```

## License

MIT