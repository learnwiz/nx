---
title: 'migrate - CLI command'
description:
  'Creates a migrations file or runs migrations from the migrations file.
  - Migrate packages and create migrations.json (e.g., nx migrate @nrwl/workspace@latest)
  - Run migrations (e.g., nx migrate --run-migrations=migrations.json)'
---

# migrate

Creates a migrations file or runs migrations from the migrations file.

- Migrate packages and create migrations.json (e.g., nx migrate @nrwl/workspace@latest)
- Run migrations (e.g., nx migrate --run-migrations=migrations.json)

## Usage

```shell
nx migrate [packageAndVersion]
```

Install `nx` globally to invoke the command directly using `nx`, or use `npx nx`, `yarn nx`, or `pnpm nx`.

### Examples

Update @nrwl/workspace to "next". This will update other packages and will generate migrations.json:

```shell
 nx migrate next
```

Update @nrwl/workspace to "9.0.0". This will update other packages and will generate migrations.json:

```shell
 nx migrate 9.0.0
```

Update @nrwl/workspace and generate the list of migrations starting with version 8.0.0 of @nrwl/workspace and @nrwl/node, regardless of what installed locally:

```shell
 nx migrate @nrwl/workspace@9.0.0 --from="@nrwl/workspace@8.0.0,@nrwl/node@8.0.0"
```

Update @nrwl/workspace to "9.0.0". If it tries to update @nrwl/react or @nrwl/angular, use version "9.0.1":

```shell
 nx migrate @nrwl/workspace@9.0.0 --to="@nrwl/react@9.0.1,@nrwl/angular@9.0.1"
```

Update another-package to "12.0.0". This will update other packages and will generate migrations.json file:

```shell
 nx migrate another-package@12.0.0
```

Collect package updates and migrations in interactive mode. In this mode, the user will be prompted whether to apply any optional package update and migration:

```shell
 nx migrate latest --interactive
```

Run migrations from the provided migrations.json file. You can modify migrations.json and run this command many times:

```shell
 nx migrate --run-migrations=migrations.json
```

Create a dedicated commit for each successfully completed migration. You can customize the prefix used for each commit by additionally setting --commit-prefix="PREFIX_HERE ":

```shell
 nx migrate --run-migrations --create-commits
```

## Options

### commitPrefix

Type: `string`

Default: `chore: [nx migration] `

Commit prefix to apply to the commit for each migration, when --create-commits is enabled

### createCommits

Type: `boolean`

Default: `false`

Automatically create a git commit after each migration runs

### from

Type: `string`

Use the provided versions for packages instead of the ones installed in node_modules (e.g., --from="@nrwl/react@12.0.0,@nrwl/js@12.0.0")

### help

Type: `boolean`

Show help

### interactive

Type: `boolean`

Default: `false`

Enable prompts to confirm whether to collect optional package updates and migrations

### packageAndVersion

Type: `string`

The target package and version (e.g, @nrwl/workspace@13.0.0)

### runMigrations

Type: `string`

Execute migrations from a file (when the file isn't provided, execute migrations from migrations.json)

### to

Type: `string`

Use the provided versions for packages instead of the ones calculated by the migrator (e.g., --to="@nrwl/react@12.0.0,@nrwl/js@12.0.0")

### version

Type: `boolean`

Show version number
