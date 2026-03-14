# `mshafer1/node-renovate-config`

`mshafer1/node-renovate-config` is a Git repository containing Renovate configurations for NI Python
projects.

## Table of Contents

- [`mshafer1/node-renovate-config`](#mshafer1node-renovate-config)
  - [Table of Contents](#table-of-contents)
  - [`default.json`](#defaultjson)
  - [`recommended.json`](#recommendedjson)
  - [Presets](#presets)
    - [Group Presets](#group-presets)
      - [`presets/group/node.json`](#presetsgroupnodejson)

## `default.json`

The default configuration includes settings that are common to all NI Python projects.

- Extends [`config:recommended`](https://docs.renovatebot.com/presets-config/#configrecommended)
- Branch prefix: `users/renovate`
- Time zone: `US/Central`

## `recommended.json`

The recommended configuration for keeping npm packages up to date with less headache.

- Extends `default.json`
- Updates all Node packages on Sundays
- Runs lock file maintenance monthly in order to upgrade indirect dependencies that are not covered
  by the weekly update.
- Enables vulnerability alerts ([`presets/enableVulnerabilityAlerts.json`](./presets/enableVulnerabilityAlerts.json))
- Rebases stale PRs ([:rebaseStalePrs](https://docs.renovatebot.com/presets-default/#rebasestaleprs))
- Sets [`minimumReleaseAge`](https://docs.renovatebot.com/configuration-options/#minimumreleaseage)
  to 14 days by default and 1 day for `ni/python-actions` and NI Python packages. If an upstream
  package is compromised, delaying makes it more likely that the compromised version will be
  detected and pulled from the repository before we try to upgrade. This should not affect security
  vulnerability alerts.

## Presets

### Group Presets

#### `presets/group/node.json`

Group NPM packages together.
