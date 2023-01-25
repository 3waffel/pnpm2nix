# pnpm2nix

Provides a `mkPnpmPackage` function that can be used to build a pnpm package with nix.

The function can be accessed either by importing this repo as a flake input or though `pkgs.callPackage /path/to/this/repo/derivation.nix {}`.

In addition to all arguments accepted by `stdenv.mkDerivation`, the `mkPnpmPackage` function accepts the following arguments:

| argument       | description                                             | default                      |
| -------------- | ------------------------------------------------------- | ---------------------------- |
| `src`          | The path to the package sources (required)              |                              |
| `packageJSON`  | Override the path to `package.json`                     | `${src}/package.json`        |
| `pnpmLockYaml` | Override the path to `pnpm-lock.yaml`                   | `${src}/pnpm-lock.yaml`      |
| `pname`        | Override the package name                               | read from `package.json`     |
| `version`      | Override the package version                            | read from `package.json`     |
| `name`         | Override the combined package name                      | `${pname}-${version}`        |
| `nodejs`       | Override the nodejs package that is used                | `pkgs.nodejs`                |
| `pnpm`         | Override the pnpm package that is used                  | `pkgs.nodejs.pkgs.pnpm`      |
| `registry`     | The registry where the dependencies are downloaded from | `https://registry.npmjs.org` |
| `script`       | The npm script that is executed                         | `build`                      |
| `distDir`      | The directory that should be copied to the output       | `dist`                       |
