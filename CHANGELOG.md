## @janus-idp/cli 1.0.0 (2024-08-06)

## 3.6.9

### Patch Changes

- 3caa849: remove unvanted commands

## 3.6.8

### Patch Changes

- acabdfb: test
- 4da457b: test

## 3.6.7

### Patch Changes

- 0e7ac2e: test

## 3.6.6

### Patch Changes

- ed4cc1c: asdf

## 3.6.5

### Patch Changes

- 61bf7c8: test
- 8a36c91: asf

## 3.6.4

### Patch Changes

- 637361c: test

## 3.6.3

### Patch Changes

- acff690: test

## 3.6.2

### Patch Changes

- c2e7720: test

## 3.6.1

### Patch Changes

- 701b93c: This change updates the CLI to cater for the way modules are handled by `require` in node v20.19.0, which fixes an error that can be thrown by the CLI when an es6 or typescript module is picked up by `require`.

## 3.6.0

### Minor Changes

- cd7aa9e: The janus-cli now can use buildah as a container tool.

## 3.5.0

### Minor Changes

- 049f200: This change removes the embed-as-code method of exporting from export-dynamic-plugin and the associated --no-embed-as-dependencies flag. This change also removes the forked code required to support this exporting method as well as the associated rollup dependencies.

## 3.4.2

### Patch Changes

- 611e23a: Fix wrong role retrieval which could break the `metadata` command behavior.
- 611e23a: Check backstage the `support-versions` field value during export, and fix it if possible while emitting a warning.

## 3.4.1

### Patch Changes

- a3e8716: Prepare for better compatibility with the upstream dynamic plugins support, by generating the config schema for backend plugins in both `dist/configSchema.json` (for backward compatibility with RHDH) and `dist/.config-schema.json` for consistency and compatibility with upstream.
- 2559fd7: This change fixes package-dynamic-plugin to transform any organization identifier into a flat file path when packaging dynamic plugins.

## 3.4.0

### Minor Changes

- b25ecb4: Bump packages/cli to 3.4.0 in main branch, in prep for release of 1.6.0

### Patch Changes

- f694a76: This change updates the package-dynamic-plugins command to use the exported plugin package name rather than deriving a package name from the base plugin package and package role. This change also ensures the exported plugin metadata is taken from the exported package instead of the original package. This change will potentially affect the final directory name of exported plugins.

## 3.3.1

### Patch Changes

- 4af162c: This change ensures the CLI properly updates any manually added resolutions a plugin has with the embedded version. This fixes cases where a plugin may be using resolutions for finer grained version control on packages the CLI would embed, such as native dependencies.

## 3.3.0

### Minor Changes

- 9983dd8: Bump packages/cli to 3.3.0 in main branch, in prep for release of 1.5.0

### Patch Changes

- 0123a8d: Fix Yarn v1 incompatibility in the `export-dynamic-plugin` command

## 3.2.0

### Minor Changes

- 99e7cd1: Bump rollup to v4

## 3.1.0

### Minor Changes

- 6b766eb: Update dependencies to Backstage 1.35.0

## 3.0.0

### Major Changes

- 8c307f7: changes to `package-dynamic-plugins` command:

  - Removed `-m` (`--marketplace`) flag. This flag will be replaced with more generic implementation see: https://issues.redhat.com/browse/RHIDP-5290

### Patch Changes

- 684e4ad: fix(cli): extend --ignore-version-check

  This change updates the cli's --ignore-version-check flag to also ignore the check performed on an embedded transitive dependencies that are moved to peer dependencies, when it is known that the mismatch is runtime compatible.

## 2.0.0

### Major Changes

- eac5451: changes to package-dynamic-plugins command:

  - rename com.redhat.rhdh.plugins to io.backstage.dynamic-packages to make it more "upstream friendly"
  - add io.backstage.marketplace/<plugin-name> annotations, value is read from file specified by optional --marketplace flag
  - use base64 for annotation values

### Minor Changes

- 70cde20: changes to package-dynamic-plugins command:

  - by default `--platform linux/amd64` is added to the command container build command
  - added a new flag `--platfrom` allow user to specify the platform for the container build command

## 1.19.1

### Patch Changes

- 2d73fa1: fix(cli): support single packages better. This change fixes an issue in the `package-dynamic-plugins` command that prevents it from running properly in a single plugin project that does not have workspaces.

## 1.19.0

### Minor Changes

- 9671df5: Bump packages/cli to 1.19.0 in main branch, in prep for release of 1.4.0

### Patch Changes

- 2acb6e0: fix(cli): add a flag to relax semver checks. This change updates the CLI to add an option to relax the semver checks on a per-package basis to cater for plugins where it is known there should be runtime compabability due to no interface changes.
- 6d292af: fix(cli): adjust embedded module searching. The CLI attempts a require call to detect built embedded packages, this change adjusts the directory this require is attempted from to be at the level of discovered package instead of the dynamic plugin package.
- 2ef4806: This change adds two new flags to handle native module dependencies.

  - `--allow-native-package [package-name...]`: flag to selectively allow native packages when exporting a dynamic plugin and allowing it's installation into the exported dynamic plugin.
  - `--suppress-native-package [package-name..]`: flag which replaces the native package with an empty package during export, preventing the native package's inclusion into the exported dynamic plugin's private dependencies.

- 7643bda: fix(cli): redirect install output. This change updates the CLI so that stdout of the `yarn install` command is redirected to a file. This prevents a possible buffer overflow error that can occur but also gives the added benefit of making the install output available for troubleshooting should a dynamic plugin fail to export. On successful installation and plugin validation the yarn install log file will be removed.

## 1.18.1

### Patch Changes

- e9b2878: fix(cli): fall back to using the cli script directly if a plugin package does not have an export-dynamic script

## 1.18.0

### Minor Changes

- 8448c17: feat(cli) add flag to specify output directory

  This change adds an --export-to flag to the package-dynamic-plugins CLI command. This flag will skip the container build step, and instead copy the staged dynamic plugin assets to the specified output directory. The addition of this flag makes the --tag argument optional, and only required if --export-to is not specified.

### Patch Changes

- 8448c17: fix(cli): Improve example configuration display

  This change changes the CLI package-dynamic-plugins command to take
  advantage of some dynamic plugin projects that have followed the
  convention of maintaining a app-config.janus-idp.yaml in the root of the
  plugin source directory. When this file is present, it will be read in
  as the command processes dynamic plugins in the monorepo and then
  included in the example dynamic-plugins.yaml configuration printed out
  when the command successfully completes. This change also adjusts the
  control flow where this is printed out to ensure it's after successful
  completion of the container image.

## 1.17.1

### Patch Changes

- 0e6bfd3: feat: update Backstage to the latest version

  Update to Backstage 1.32.5

## 1.17.0

### Minor Changes

- 8244f28: chore(deps): update to backstage 1.32

## 1.16.1

### Patch Changes

- e5c233d: fix(cli): allow mutable install for monorepo yarn.lock with deprecated flags

  This change updates the CLI to use `--no-immutable` when a plugin package or monorepo `yarn.lock` file is used during the `export-dynamic-plugin` command with deprecated flags. Explicitly passing this flag avoids the default Yarn 3.x behavior of `--immutable` when the command is run in a CI environment.

## 1.16.0

### Minor Changes

- d9551ae: feat(deps): update to backstage 1.31

### Patch Changes

- d9551ae: fix(cli): allow mutable install for monorepo yarn.lock

  This change updates the CLI to use `--no-immutable` when a plugin package or monorepo `yarn.lock` file is used during the `export-dynamic-plugin` command. Explicitly passing this flag avoids the default Yarn 3.x behavior of `--immutable` when the command is run in a CI environment.

- d9551ae: upgrade to yarn v3
- d9551ae: Fixed issue with missing configSchema.json that was affecting packages in @backstage-community

### Features

- add method for janus-cli package metadata (simpler PR) - RHIDP-1502 ([#1753](https://github.com/janus-idp/backstage-plugins/issues/1753)) ([b81a849](https://github.com/janus-idp/backstage-plugins/commit/b81a8499acc4fe9c585dd5179fbca1304c62520c))
- add new backend system support for existing backend plugins that have not been migrated over yet ([#1132](https://github.com/janus-idp/backstage-plugins/issues/1132)) ([06e16fd](https://github.com/janus-idp/backstage-plugins/commit/06e16fdcf64257dd08297cb727445d9a8a23c522))
- add the `export-dynamic-plugin` command, with an implementation for the backend case ([#819](https://github.com/janus-idp/backstage-plugins/issues/819)) ([f873a94](https://github.com/janus-idp/backstage-plugins/commit/f873a94072d17f3bad15b0552b0ef12c285c2ea3))
- checkPluginVersion.sh bump plugins for 1.2.0 release ([#1511](https://github.com/janus-idp/backstage-plugins/issues/1511)) ([73c6588](https://github.com/janus-idp/backstage-plugins/commit/73c6588adb7e8c20907b06f2a8ef248cfd4332e4))
- **cli:** add frontend dynamic plugins base build config ([#747](https://github.com/janus-idp/backstage-plugins/issues/747)) ([91e06da](https://github.com/janus-idp/backstage-plugins/commit/91e06da8ab108c17fd2a6531f25e01c7a7350276)), closes [#831](https://github.com/janus-idp/backstage-plugins/issues/831)
- **cli:** generate plugin specific schema for dynamic plugins ([#912](https://github.com/janus-idp/backstage-plugins/issues/912)) ([0c31158](https://github.com/janus-idp/backstage-plugins/commit/0c311585d5aaaa501bef8ba0e8dfddffe240f71c))
- **cli:** switch to @janus-idp/cli for new plugins and populate them with the basics ([#782](https://github.com/janus-idp/backstage-plugins/issues/782)) ([bbbefbd](https://github.com/janus-idp/backstage-plugins/commit/bbbefbd7a534844ee35533a62e4b626bd5b8eb4f))
- **deps:** update to backstage 1.27 ([#1683](https://github.com/janus-idp/backstage-plugins/issues/1683)) ([a14869c](https://github.com/janus-idp/backstage-plugins/commit/a14869c3f4177049cb8d6552b36c3ffd17e7997d))
- **deps:** update to backstage 1.28 ([#1891](https://github.com/janus-idp/backstage-plugins/issues/1891)) ([1ba1108](https://github.com/janus-idp/backstage-plugins/commit/1ba11088e0de60e90d138944267b83600dc446e5))
- **deps:** update to backstage 1.29 ([#1900](https://github.com/janus-idp/backstage-plugins/issues/1900)) ([f53677f](https://github.com/janus-idp/backstage-plugins/commit/f53677fb02d6df43a9de98c43a9f101a6db76802))
- **dynamic-ui:** integrate scalprum with current backstage plugins ([#826](https://github.com/janus-idp/backstage-plugins/issues/826)) ([e1fb4ce](https://github.com/janus-idp/backstage-plugins/commit/e1fb4ceafc9e353c4d5b0ed9ba2407b3b0383c60))
- fork `@backstage/cli` into a new `@janus-idp/cli` ([#729](https://github.com/janus-idp/backstage-plugins/issues/729)) ([e0e8355](https://github.com/janus-idp/backstage-plugins/commit/e0e835590294512ad2eee5b7c9d93a045131dc9e)), closes [#15274](https://github.com/janus-idp/backstage-plugins/issues/15274) [#18439](https://github.com/janus-idp/backstage-plugins/issues/18439)
- **Notifications:** new notifications FE plugin, API and backend ([#933](https://github.com/janus-idp/backstage-plugins/issues/933)) ([4d4cb78](https://github.com/janus-idp/backstage-plugins/commit/4d4cb781ca9fc331a2c621583e9203f9e4585ee7))
- switch defaults of the `--embed-as-dependencies` and `in-place` options. ([#1787](https://github.com/janus-idp/backstage-plugins/issues/1787)) ([049e675](https://github.com/janus-idp/backstage-plugins/commit/049e67502e7b4f9f00c8c6b01d112a27bc09ca9c))

### Bug Fixes

- **aap+3scale+ocm:** don't log sensitive data from errors ([#945](https://github.com/janus-idp/backstage-plugins/issues/945)) ([7a5e7b8](https://github.com/janus-idp/backstage-plugins/commit/7a5e7b8a57c9841003d9b16e1a65fb62e101fbf1))
- **cli:** `node_modules` of the main plugin unexpectedly copied to the `dist-dynamic` folder. ([#1482](https://github.com/janus-idp/backstage-plugins/issues/1482)) ([deaa19d](https://github.com/janus-idp/backstage-plugins/commit/deaa19d2aaf9e25617911e8bebc67ff8d7471010))
- **cli:** add `resolve.fallback` for node dependencies in the `export-dynamic-plugin` CLI for frontend plugins. ([#1590](https://github.com/janus-idp/backstage-plugins/issues/1590)) ([e860c3b](https://github.com/janus-idp/backstage-plugins/commit/e860c3bd179961af8bc6e68d5af57c69578badc7))
- **cli:** add default scalprum config ([#909](https://github.com/janus-idp/backstage-plugins/issues/909)) ([d74fc72](https://github.com/janus-idp/backstage-plugins/commit/d74fc72ab7e0a843da047c7b6570d8a6fbc068e1))
- **cli:** allow exporting dynamic plugins from `frontend-plugin-module` packages. ([#1593](https://github.com/janus-idp/backstage-plugins/issues/1593)) ([55508ba](https://github.com/janus-idp/backstage-plugins/commit/55508baff436b41d7c99f119b2adb7047286bd00))
- **cli:** allow retrieving scalprum config from an external file in `export-dynamic-plugin`. ([#1598](https://github.com/janus-idp/backstage-plugins/issues/1598)) ([889be7f](https://github.com/janus-idp/backstage-plugins/commit/889be7f8d22b88d18d180195cdf7bdae53585983))
- **cli:** completely removing the requirement for `app-config` when exporting fronted plugins to dynamic. ([#1603](https://github.com/janus-idp/backstage-plugins/issues/1603)) ([7fb243a](https://github.com/janus-idp/backstage-plugins/commit/7fb243ad5345a241e1c0a848e17f9936cac8234a))
- **cli:** do not change interop mode by default ([#971](https://github.com/janus-idp/backstage-plugins/issues/971)) ([4159977](https://github.com/janus-idp/backstage-plugins/commit/41599773d60fe944e402065970295b47cc2d46d6))
- **cli:** embedded alpha module dependencies not hoisted. ([#1170](https://github.com/janus-idp/backstage-plugins/issues/1170)) ([063b343](https://github.com/janus-idp/backstage-plugins/commit/063b3437e7a8267a0fb174d454e7cd9411ea790c))
- **cli:** fix entrypoint validation on backstage 1.24.0 and above. ([#1741](https://github.com/janus-idp/backstage-plugins/issues/1741)) ([6ed4171](https://github.com/janus-idp/backstage-plugins/commit/6ed4171dd4953da03be7f083b967f778909a768d))
- **cli:** fix entrypoint validation when running with `npx` ([#1473](https://github.com/janus-idp/backstage-plugins/issues/1473)) ([79db649](https://github.com/janus-idp/backstage-plugins/commit/79db649d44a01f8834f5275b17aa1000b7151d59))
- **cli:** fix entrypoint validation when running with `npx` on some packages with `alpha` API. ([#1545](https://github.com/janus-idp/backstage-plugins/issues/1545)) ([3d9781c](https://github.com/janus-idp/backstage-plugins/commit/3d9781cbf48cbd11a576d54afa225b95b2ad5726))
- **cli:** fix possible dependency conflict ([#950](https://github.com/janus-idp/backstage-plugins/issues/950)) ([6c3052e](https://github.com/janus-idp/backstage-plugins/commit/6c3052e9ef2ad77797f6a75cb7f30059442c3764))
- **cli:** fix the `embed-as-dependencies` option on the `export-dynamic-plugin` CLI... ([#1478](https://github.com/janus-idp/backstage-plugins/issues/1478)) ([edd019e](https://github.com/janus-idp/backstage-plugins/commit/edd019e905fd918ee4dcb4f72f0cdd7f791f6300))
- **cli:** fix the removal of type definitions by `export-dynamic`. ([#1810](https://github.com/janus-idp/backstage-plugins/issues/1810)) ([8472d91](https://github.com/janus-idp/backstage-plugins/commit/8472d914a2f9107c08a9a30ab1ea8ed8d10bc43a))
- **cli:** remove the requirement for `app-config` when exporting fronted plugins to dynamic. ([#1592](https://github.com/janus-idp/backstage-plugins/issues/1592)) ([577efff](https://github.com/janus-idp/backstage-plugins/commit/577efff16b503a5f88126f2c5d26b7c4139e95d0))
- **cli:** schema generator do not ignore repo root ([#981](https://github.com/janus-idp/backstage-plugins/issues/981)) ([67f22f6](https://github.com/janus-idp/backstage-plugins/commit/67f22f686860e79f5d019f71072b2856a9b17230))
- **cli:** share core-app-api package ([#885](https://github.com/janus-idp/backstage-plugins/issues/885)) ([09db33c](https://github.com/janus-idp/backstage-plugins/commit/09db33ce4113ccb484a167dab8d9fe47d6185c09))
- **cli:** use react v17 in dynamic plugins build ([#931](https://github.com/janus-idp/backstage-plugins/issues/931)) ([b47b10a](https://github.com/janus-idp/backstage-plugins/commit/b47b10ab9a1673bf5b303b3051db71f0921049ed))
- **deps:** pin dependencies ([#745](https://github.com/janus-idp/backstage-plugins/issues/745)) ([69bd6a9](https://github.com/janus-idp/backstage-plugins/commit/69bd6a9a078ac66f9934799eb6189c8022157445))
- **deps:** update dependency @rollup/plugin-commonjs to v25 ([#765](https://github.com/janus-idp/backstage-plugins/issues/765)) ([615ff44](https://github.com/janus-idp/backstage-plugins/commit/615ff443b2c47421de083caa97171021b7775aa0))
- **deps:** update dependency @rollup/plugin-json to v6 ([#766](https://github.com/janus-idp/backstage-plugins/issues/766)) ([2fe869f](https://github.com/janus-idp/backstage-plugins/commit/2fe869f3d4503fc70ca7d1bcb748d385d3e653a0))
- **deps:** update dependency @rollup/plugin-node-resolve to v15 ([#767](https://github.com/janus-idp/backstage-plugins/issues/767)) ([8d9696c](https://github.com/janus-idp/backstage-plugins/commit/8d9696cd663c2e7bc54f32f64113a45c3a67aa5b))
- **deps:** update dependency @spotify/eslint-config-base to v15 ([#774](https://github.com/janus-idp/backstage-plugins/issues/774)) ([04a0ae1](https://github.com/janus-idp/backstage-plugins/commit/04a0ae19db78fa904a15a36684a0e2abec2373a6))
- **deps:** update dependency @spotify/eslint-config-react to v15 ([#789](https://github.com/janus-idp/backstage-plugins/issues/789)) ([1a3965a](https://github.com/janus-idp/backstage-plugins/commit/1a3965a07ad3edcd9c608d8530a1933cde6a89bb))
- **deps:** update dependency @spotify/eslint-config-typescript to v15 ([#790](https://github.com/janus-idp/backstage-plugins/issues/790)) ([9ecaaa3](https://github.com/janus-idp/backstage-plugins/commit/9ecaaa34624652436838b3df963d91605973b964))
- **deps:** update dependency @svgr/core to v8 ([#791](https://github.com/janus-idp/backstage-plugins/issues/791)) ([db2d09b](https://github.com/janus-idp/backstage-plugins/commit/db2d09b0daddab7ab675eff230e0123f14530ef0))
- **deps:** update dependency @svgr/plugin-jsx to v8 ([#792](https://github.com/janus-idp/backstage-plugins/issues/792)) ([467560c](https://github.com/janus-idp/backstage-plugins/commit/467560c6cecc173fe7949a12014be9fde0e21d3a))
- **deps:** update dependency @svgr/rollup to v8 ([#795](https://github.com/janus-idp/backstage-plugins/issues/795)) ([111aa57](https://github.com/janus-idp/backstage-plugins/commit/111aa574ea6d6c2574c07240383feebe92a6fc90))
- **deps:** update dependency bfj to v8 ([#1463](https://github.com/janus-idp/backstage-plugins/issues/1463)) ([01d9360](https://github.com/janus-idp/backstage-plugins/commit/01d9360e08e0d22fd34a6df304eca60cae908a9e))
- **deps:** update dependency handlebars to v4.7.7 [security] ([#753](https://github.com/janus-idp/backstage-plugins/issues/753)) ([52a195e](https://github.com/janus-idp/backstage-plugins/commit/52a195e0c2160bb6fc18d40daaee1ec1f05d666d))
- **deps:** update dependency postcss to v8.2.13 [security] ([#755](https://github.com/janus-idp/backstage-plugins/issues/755)) ([37fc85f](https://github.com/janus-idp/backstage-plugins/commit/37fc85fd37a064c20f19f2b7825bc0e7b0dc28a5))
- **deps:** update dependency yaml to v2.2.2 [security] ([#757](https://github.com/janus-idp/backstage-plugins/issues/757)) ([b3c719c](https://github.com/janus-idp/backstage-plugins/commit/b3c719ca3d0a43ee3eb5b88313d4278e624beaff))
- **deps:** update linters ([#746](https://github.com/janus-idp/backstage-plugins/issues/746)) ([bf06a66](https://github.com/janus-idp/backstage-plugins/commit/bf06a66b1c7bd3225a5767e619652bad90030083))
- **deps:** update rhdh dependencies (non-major) ([#1960](https://github.com/janus-idp/backstage-plugins/issues/1960)) ([8b6c249](https://github.com/janus-idp/backstage-plugins/commit/8b6c249f1d2e8097cac0260785c26496a5be1a06))
- make the `export-dynamic-plugin` command more generic for backend plugins. ([#967](https://github.com/janus-idp/backstage-plugins/issues/967)) ([b40c661](https://github.com/janus-idp/backstage-plugins/commit/b40c66174ee4dd3240e034d794b19900c9738c86))
- **release:** change problematic plugins to private ([#1738](https://github.com/janus-idp/backstage-plugins/issues/1738)) ([69176bd](https://github.com/janus-idp/backstage-plugins/commit/69176bd75ccd842a313445e096223ecc339b655b))
- **scalprum:** share react-router since various 3rd party plugins use it ([#901](https://github.com/janus-idp/backstage-plugins/issues/901)) ([ac0c923](https://github.com/janus-idp/backstage-plugins/commit/ac0c92381c26f20d197255abcc931a7ad14c0edc))

### Other changes

- **cli:** new `--in-place`/`--no-in-place` option to the `export-dynamic-plugin` CLI command to allow exporting to `dist-dynamic` (when value is `false`). ([#1584](https://github.com/janus-idp/backstage-plugins/issues/1584)) ([4b5cc40](https://github.com/janus-idp/backstage-plugins/commit/4b5cc403c00fab222bf5d5faa43a30c7fa6a97a4))
- experimental `embed-as-dependencies` option for the backend ([#1418](https://github.com/janus-idp/backstage-plugins/issues/1418)) ([b451380](https://github.com/janus-idp/backstage-plugins/commit/b451380bb048086d90bf7a9c34c4d9c056afbb1e))

## @janus-idp/cli 1.0.0 (2024-08-06)

### Features

- add method for janus-cli package metadata (simpler PR) - RHIDP-1502 ([#1753](https://github.com/janus-idp/backstage-plugins/issues/1753)) ([b81a849](https://github.com/janus-idp/backstage-plugins/commit/b81a8499acc4fe9c585dd5179fbca1304c62520c))
- add new backend system support for existing backend plugins that have not been migrated over yet ([#1132](https://github.com/janus-idp/backstage-plugins/issues/1132)) ([06e16fd](https://github.com/janus-idp/backstage-plugins/commit/06e16fdcf64257dd08297cb727445d9a8a23c522))
- add the `export-dynamic-plugin` command, with an implementation for the backend case ([#819](https://github.com/janus-idp/backstage-plugins/issues/819)) ([f873a94](https://github.com/janus-idp/backstage-plugins/commit/f873a94072d17f3bad15b0552b0ef12c285c2ea3))
- checkPluginVersion.sh bump plugins for 1.2.0 release ([#1511](https://github.com/janus-idp/backstage-plugins/issues/1511)) ([73c6588](https://github.com/janus-idp/backstage-plugins/commit/73c6588adb7e8c20907b06f2a8ef248cfd4332e4))
- **cli:** add frontend dynamic plugins base build config ([#747](https://github.com/janus-idp/backstage-plugins/issues/747)) ([91e06da](https://github.com/janus-idp/backstage-plugins/commit/91e06da8ab108c17fd2a6531f25e01c7a7350276)), closes [#831](https://github.com/janus-idp/backstage-plugins/issues/831)
- **cli:** generate plugin specific schema for dynamic plugins ([#912](https://github.com/janus-idp/backstage-plugins/issues/912)) ([0c31158](https://github.com/janus-idp/backstage-plugins/commit/0c311585d5aaaa501bef8ba0e8dfddffe240f71c))
- **cli:** switch to @janus-idp/cli for new plugins and populate them with the basics ([#782](https://github.com/janus-idp/backstage-plugins/issues/782)) ([bbbefbd](https://github.com/janus-idp/backstage-plugins/commit/bbbefbd7a534844ee35533a62e4b626bd5b8eb4f))
- **deps:** update to backstage 1.27 ([#1683](https://github.com/janus-idp/backstage-plugins/issues/1683)) ([a14869c](https://github.com/janus-idp/backstage-plugins/commit/a14869c3f4177049cb8d6552b36c3ffd17e7997d))
- **deps:** update to backstage 1.28 ([#1891](https://github.com/janus-idp/backstage-plugins/issues/1891)) ([1ba1108](https://github.com/janus-idp/backstage-plugins/commit/1ba11088e0de60e90d138944267b83600dc446e5))
- **deps:** update to backstage 1.29 ([#1900](https://github.com/janus-idp/backstage-plugins/issues/1900)) ([f53677f](https://github.com/janus-idp/backstage-plugins/commit/f53677fb02d6df43a9de98c43a9f101a6db76802))
- **dynamic-ui:** integrate scalprum with current backstage plugins ([#826](https://github.com/janus-idp/backstage-plugins/issues/826)) ([e1fb4ce](https://github.com/janus-idp/backstage-plugins/commit/e1fb4ceafc9e353c4d5b0ed9ba2407b3b0383c60))
- fork `@backstage/cli` into a new `@janus-idp/cli` ([#729](https://github.com/janus-idp/backstage-plugins/issues/729)) ([e0e8355](https://github.com/janus-idp/backstage-plugins/commit/e0e835590294512ad2eee5b7c9d93a045131dc9e)), closes [#15274](https://github.com/janus-idp/backstage-plugins/issues/15274) [#18439](https://github.com/janus-idp/backstage-plugins/issues/18439)
- **Notifications:** new notifications FE plugin, API and backend ([#933](https://github.com/janus-idp/backstage-plugins/issues/933)) ([4d4cb78](https://github.com/janus-idp/backstage-plugins/commit/4d4cb781ca9fc331a2c621583e9203f9e4585ee7))
- switch defaults of the `--embed-as-dependencies` and `in-place` options. ([#1787](https://github.com/janus-idp/backstage-plugins/issues/1787)) ([049e675](https://github.com/janus-idp/backstage-plugins/commit/049e67502e7b4f9f00c8c6b01d112a27bc09ca9c))

### Bug Fixes

- **aap+3scale+ocm:** don't log sensitive data from errors ([#945](https://github.com/janus-idp/backstage-plugins/issues/945)) ([7a5e7b8](https://github.com/janus-idp/backstage-plugins/commit/7a5e7b8a57c9841003d9b16e1a65fb62e101fbf1))
- **cli:** `node_modules` of the main plugin unexpectedly copied to the `dist-dynamic` folder. ([#1482](https://github.com/janus-idp/backstage-plugins/issues/1482)) ([deaa19d](https://github.com/janus-idp/backstage-plugins/commit/deaa19d2aaf9e25617911e8bebc67ff8d7471010))
- **cli:** add `resolve.fallback` for node dependencies in the `export-dynamic-plugin` CLI for frontend plugins. ([#1590](https://github.com/janus-idp/backstage-plugins/issues/1590)) ([e860c3b](https://github.com/janus-idp/backstage-plugins/commit/e860c3bd179961af8bc6e68d5af57c69578badc7))
- **cli:** add default scalprum config ([#909](https://github.com/janus-idp/backstage-plugins/issues/909)) ([d74fc72](https://github.com/janus-idp/backstage-plugins/commit/d74fc72ab7e0a843da047c7b6570d8a6fbc068e1))
- **cli:** allow exporting dynamic plugins from `frontend-plugin-module` packages. ([#1593](https://github.com/janus-idp/backstage-plugins/issues/1593)) ([55508ba](https://github.com/janus-idp/backstage-plugins/commit/55508baff436b41d7c99f119b2adb7047286bd00))
- **cli:** allow retrieving scalprum config from an external file in `export-dynamic-plugin`. ([#1598](https://github.com/janus-idp/backstage-plugins/issues/1598)) ([889be7f](https://github.com/janus-idp/backstage-plugins/commit/889be7f8d22b88d18d180195cdf7bdae53585983))
- **cli:** completely removing the requirement for `app-config` when exporting fronted plugins to dynamic. ([#1603](https://github.com/janus-idp/backstage-plugins/issues/1603)) ([7fb243a](https://github.com/janus-idp/backstage-plugins/commit/7fb243ad5345a241e1c0a848e17f9936cac8234a))
- **cli:** do not change interop mode by default ([#971](https://github.com/janus-idp/backstage-plugins/issues/971)) ([4159977](https://github.com/janus-idp/backstage-plugins/commit/41599773d60fe944e402065970295b47cc2d46d6))
- **cli:** embedded alpha module dependencies not hoisted. ([#1170](https://github.com/janus-idp/backstage-plugins/issues/1170)) ([063b343](https://github.com/janus-idp/backstage-plugins/commit/063b3437e7a8267a0fb174d454e7cd9411ea790c))
- **cli:** fix entrypoint validation on backstage 1.24.0 and above. ([#1741](https://github.com/janus-idp/backstage-plugins/issues/1741)) ([6ed4171](https://github.com/janus-idp/backstage-plugins/commit/6ed4171dd4953da03be7f083b967f778909a768d))
- **cli:** fix entrypoint validation when running with `npx` ([#1473](https://github.com/janus-idp/backstage-plugins/issues/1473)) ([79db649](https://github.com/janus-idp/backstage-plugins/commit/79db649d44a01f8834f5275b17aa1000b7151d59))
- **cli:** fix entrypoint validation when running with `npx` on some packages with `alpha` API. ([#1545](https://github.com/janus-idp/backstage-plugins/issues/1545)) ([3d9781c](https://github.com/janus-idp/backstage-plugins/commit/3d9781cbf48cbd11a576d54afa225b95b2ad5726))
- **cli:** fix possible dependency conflict ([#950](https://github.com/janus-idp/backstage-plugins/issues/950)) ([6c3052e](https://github.com/janus-idp/backstage-plugins/commit/6c3052e9ef2ad77797f6a75cb7f30059442c3764))
- **cli:** fix the `embed-as-dependencies` option on the `export-dynamic-plugin` CLI... ([#1478](https://github.com/janus-idp/backstage-plugins/issues/1478)) ([edd019e](https://github.com/janus-idp/backstage-plugins/commit/edd019e905fd918ee4dcb4f72f0cdd7f791f6300))
- **cli:** fix the removal of type definitions by `export-dynamic`. ([#1810](https://github.com/janus-idp/backstage-plugins/issues/1810)) ([8472d91](https://github.com/janus-idp/backstage-plugins/commit/8472d914a2f9107c08a9a30ab1ea8ed8d10bc43a))
- **cli:** remove the requirement for `app-config` when exporting fronted plugins to dynamic. ([#1592](https://github.com/janus-idp/backstage-plugins/issues/1592)) ([577efff](https://github.com/janus-idp/backstage-plugins/commit/577efff16b503a5f88126f2c5d26b7c4139e95d0))
- **cli:** schema generator do not ignore repo root ([#981](https://github.com/janus-idp/backstage-plugins/issues/981)) ([67f22f6](https://github.com/janus-idp/backstage-plugins/commit/67f22f686860e79f5d019f71072b2856a9b17230))
- **cli:** share core-app-api package ([#885](https://github.com/janus-idp/backstage-plugins/issues/885)) ([09db33c](https://github.com/janus-idp/backstage-plugins/commit/09db33ce4113ccb484a167dab8d9fe47d6185c09))
- **cli:** use react v17 in dynamic plugins build ([#931](https://github.com/janus-idp/backstage-plugins/issues/931)) ([b47b10a](https://github.com/janus-idp/backstage-plugins/commit/b47b10ab9a1673bf5b303b3051db71f0921049ed))
- **deps:** pin dependencies ([#745](https://github.com/janus-idp/backstage-plugins/issues/745)) ([69bd6a9](https://github.com/janus-idp/backstage-plugins/commit/69bd6a9a078ac66f9934799eb6189c8022157445))
- **deps:** update dependency @rollup/plugin-commonjs to v25 ([#765](https://github.com/janus-idp/backstage-plugins/issues/765)) ([615ff44](https://github.com/janus-idp/backstage-plugins/commit/615ff443b2c47421de083caa97171021b7775aa0))
- **deps:** update dependency @rollup/plugin-json to v6 ([#766](https://github.com/janus-idp/backstage-plugins/issues/766)) ([2fe869f](https://github.com/janus-idp/backstage-plugins/commit/2fe869f3d4503fc70ca7d1bcb748d385d3e653a0))
- **deps:** update dependency @rollup/plugin-node-resolve to v15 ([#767](https://github.com/janus-idp/backstage-plugins/issues/767)) ([8d9696c](https://github.com/janus-idp/backstage-plugins/commit/8d9696cd663c2e7bc54f32f64113a45c3a67aa5b))
- **deps:** update dependency @spotify/eslint-config-base to v15 ([#774](https://github.com/janus-idp/backstage-plugins/issues/774)) ([04a0ae1](https://github.com/janus-idp/backstage-plugins/commit/04a0ae19db78fa904a15a36684a0e2abec2373a6))
- **deps:** update dependency @spotify/eslint-config-react to v15 ([#789](https://github.com/janus-idp/backstage-plugins/issues/789)) ([1a3965a](https://github.com/janus-idp/backstage-plugins/commit/1a3965a07ad3edcd9c608d8530a1933cde6a89bb))
- **deps:** update dependency @spotify/eslint-config-typescript to v15 ([#790](https://github.com/janus-idp/backstage-plugins/issues/790)) ([9ecaaa3](https://github.com/janus-idp/backstage-plugins/commit/9ecaaa34624652436838b3df963d91605973b964))
- **deps:** update dependency @svgr/core to v8 ([#791](https://github.com/janus-idp/backstage-plugins/issues/791)) ([db2d09b](https://github.com/janus-idp/backstage-plugins/commit/db2d09b0daddab7ab675eff230e0123f14530ef0))
- **deps:** update dependency @svgr/plugin-jsx to v8 ([#792](https://github.com/janus-idp/backstage-plugins/issues/792)) ([467560c](https://github.com/janus-idp/backstage-plugins/commit/467560c6cecc173fe7949a12014be9fde0e21d3a))
- **deps:** update dependency @svgr/rollup to v8 ([#795](https://github.com/janus-idp/backstage-plugins/issues/795)) ([111aa57](https://github.com/janus-idp/backstage-plugins/commit/111aa574ea6d6c2574c07240383feebe92a6fc90))
- **deps:** update dependency bfj to v8 ([#1463](https://github.com/janus-idp/backstage-plugins/issues/1463)) ([01d9360](https://github.com/janus-idp/backstage-plugins/commit/01d9360e08e0d22fd34a6df304eca60cae908a9e))
- **deps:** update dependency handlebars to v4.7.7 [security] ([#753](https://github.com/janus-idp/backstage-plugins/issues/753)) ([52a195e](https://github.com/janus-idp/backstage-plugins/commit/52a195e0c2160bb6fc18d40daaee1ec1f05d666d))
- **deps:** update dependency postcss to v8.2.13 [security] ([#755](https://github.com/janus-idp/backstage-plugins/issues/755)) ([37fc85f](https://github.com/janus-idp/backstage-plugins/commit/37fc85fd37a064c20f19f2b7825bc0e7b0dc28a5))
- **deps:** update dependency yaml to v2.2.2 [security] ([#757](https://github.com/janus-idp/backstage-plugins/issues/757)) ([b3c719c](https://github.com/janus-idp/backstage-plugins/commit/b3c719ca3d0a43ee3eb5b88313d4278e624beaff))
- **deps:** update linters ([#746](https://github.com/janus-idp/backstage-plugins/issues/746)) ([bf06a66](https://github.com/janus-idp/backstage-plugins/commit/bf06a66b1c7bd3225a5767e619652bad90030083))
- **deps:** update rhdh dependencies (non-major) ([#1960](https://github.com/janus-idp/backstage-plugins/issues/1960)) ([8b6c249](https://github.com/janus-idp/backstage-plugins/commit/8b6c249f1d2e8097cac0260785c26496a5be1a06))
- make the `export-dynamic-plugin` command more generic for backend plugins. ([#967](https://github.com/janus-idp/backstage-plugins/issues/967)) ([b40c661](https://github.com/janus-idp/backstage-plugins/commit/b40c66174ee4dd3240e034d794b19900c9738c86))
- **release:** change problematic plugins to private ([#1738](https://github.com/janus-idp/backstage-plugins/issues/1738)) ([69176bd](https://github.com/janus-idp/backstage-plugins/commit/69176bd75ccd842a313445e096223ecc339b655b))
- **scalprum:** share react-router since various 3rd party plugins use it ([#901](https://github.com/janus-idp/backstage-plugins/issues/901)) ([ac0c923](https://github.com/janus-idp/backstage-plugins/commit/ac0c92381c26f20d197255abcc931a7ad14c0edc))

### Other changes

- **cli:** new `--in-place`/`--no-in-place` option to the `export-dynamic-plugin` CLI command to allow exporting to `dist-dynamic` (when value is `false`). ([#1584](https://github.com/janus-idp/backstage-plugins/issues/1584)) ([4b5cc40](https://github.com/janus-idp/backstage-plugins/commit/4b5cc403c00fab222bf5d5faa43a30c7fa6a97a4))
- experimental `embed-as-dependencies` option for the backend ([#1418](https://github.com/janus-idp/backstage-plugins/issues/1418)) ([b451380](https://github.com/janus-idp/backstage-plugins/commit/b451380bb048086d90bf7a9c34c4d9c056afbb1e))

## @janus-idp/cli [1.13.0](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.12.0...@janus-idp/cli@1.13.0) (2024-07-25)

### Features

- **deps:** update to backstage 1.29 ([#1900](https://github.com/janus-idp/backstage-plugins/issues/1900)) ([f53677f](https://github.com/janus-idp/backstage-plugins/commit/f53677fb02d6df43a9de98c43a9f101a6db76802))

### Bug Fixes

- **deps:** update rhdh dependencies (non-major) ([#1960](https://github.com/janus-idp/backstage-plugins/issues/1960)) ([8b6c249](https://github.com/janus-idp/backstage-plugins/commit/8b6c249f1d2e8097cac0260785c26496a5be1a06))

## @janus-idp/cli [1.12.0](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.11.1...@janus-idp/cli@1.12.0) (2024-07-17)

### Features

- **deps:** update to backstage 1.28 ([#1891](https://github.com/janus-idp/backstage-plugins/issues/1891)) ([1ba1108](https://github.com/janus-idp/backstage-plugins/commit/1ba11088e0de60e90d138944267b83600dc446e5))

## @janus-idp/cli [1.11.1](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.11.0...@janus-idp/cli@1.11.1) (2024-06-19)

## @janus-idp/cli [1.11.0](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.10.1...@janus-idp/cli@1.11.0) (2024-06-13)

### Features

- **deps:** update to backstage 1.27 ([#1683](https://github.com/janus-idp/backstage-plugins/issues/1683)) ([a14869c](https://github.com/janus-idp/backstage-plugins/commit/a14869c3f4177049cb8d6552b36c3ffd17e7997d))

## @janus-idp/cli [1.10.1](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.10.0...@janus-idp/cli@1.10.1) (2024-06-13)

### Bug Fixes

- **cli:** fix the removal of type definitions by `export-dynamic`. ([#1810](https://github.com/janus-idp/backstage-plugins/issues/1810)) ([8472d91](https://github.com/janus-idp/backstage-plugins/commit/8472d914a2f9107c08a9a30ab1ea8ed8d10bc43a))

## @janus-idp/cli [1.10.0](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.9.0...@janus-idp/cli@1.10.0) (2024-06-05)

### Features

- switch defaults of the `--embed-as-dependencies` and `in-place` options. ([#1787](https://github.com/janus-idp/backstage-plugins/issues/1787)) ([049e675](https://github.com/janus-idp/backstage-plugins/commit/049e67502e7b4f9f00c8c6b01d112a27bc09ca9c))

## @janus-idp/cli [1.9.0](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.8.10...@janus-idp/cli@1.9.0) (2024-06-03)

### Features

- add method for janus-cli package metadata (simpler PR) - RHIDP-1502 ([#1753](https://github.com/janus-idp/backstage-plugins/issues/1753)) ([b81a849](https://github.com/janus-idp/backstage-plugins/commit/b81a8499acc4fe9c585dd5179fbca1304c62520c))

## @janus-idp/cli [1.8.10](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.8.9...@janus-idp/cli@1.8.10) (2024-05-29)

### Bug Fixes

- **cli:** fix entrypoint validation on backstage 1.24.0 and above. ([#1741](https://github.com/janus-idp/backstage-plugins/issues/1741)) ([6ed4171](https://github.com/janus-idp/backstage-plugins/commit/6ed4171dd4953da03be7f083b967f778909a768d))

## @janus-idp/cli [1.8.9](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.8.8...@janus-idp/cli@1.8.9) (2024-05-29)

### Bug Fixes

- **release:** change problematic plugins to private ([#1738](https://github.com/janus-idp/backstage-plugins/issues/1738)) ([69176bd](https://github.com/janus-idp/backstage-plugins/commit/69176bd75ccd842a313445e096223ecc339b655b))

## @janus-idp/cli [1.8.8](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.8.7...@janus-idp/cli@1.8.8) (2024-05-28)

## @janus-idp/cli [1.8.7](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.8.6...@janus-idp/cli@1.8.7) (2024-05-16)

## @janus-idp/cli [1.8.6](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.8.5...@janus-idp/cli@1.8.6) (2024-05-09)

## @janus-idp/cli [1.8.5](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.8.4...@janus-idp/cli@1.8.5) (2024-05-02)

### Bug Fixes

- **cli:** completely removing the requirement for `app-config` when exporting fronted plugins to dynamic. ([#1603](https://github.com/janus-idp/backstage-plugins/issues/1603)) ([7fb243a](https://github.com/janus-idp/backstage-plugins/commit/7fb243ad5345a241e1c0a848e17f9936cac8234a))

## @janus-idp/cli [1.8.4](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.8.3...@janus-idp/cli@1.8.4) (2024-05-02)

### Bug Fixes

- **cli:** allow retrieving scalprum config from an external file in `export-dynamic-plugin`. ([#1598](https://github.com/janus-idp/backstage-plugins/issues/1598)) ([889be7f](https://github.com/janus-idp/backstage-plugins/commit/889be7f8d22b88d18d180195cdf7bdae53585983))

## @janus-idp/cli [1.8.3](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.8.2...@janus-idp/cli@1.8.3) (2024-04-30)

### Bug Fixes

- **cli:** add `resolve.fallback` for node dependencies in the `export-dynamic-plugin` CLI for frontend plugins. ([#1590](https://github.com/janus-idp/backstage-plugins/issues/1590)) ([e860c3b](https://github.com/janus-idp/backstage-plugins/commit/e860c3bd179961af8bc6e68d5af57c69578badc7))
- **cli:** allow exporting dynamic plugins from `frontend-plugin-module` packages. ([#1593](https://github.com/janus-idp/backstage-plugins/issues/1593)) ([55508ba](https://github.com/janus-idp/backstage-plugins/commit/55508baff436b41d7c99f119b2adb7047286bd00))
- **cli:** remove the requirement for `app-config` when exporting fronted plugins to dynamic. ([#1592](https://github.com/janus-idp/backstage-plugins/issues/1592)) ([577efff](https://github.com/janus-idp/backstage-plugins/commit/577efff16b503a5f88126f2c5d26b7c4139e95d0))

## @janus-idp/cli [1.8.2](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.8.1...@janus-idp/cli@1.8.2) (2024-04-30)

### Other changes

- **cli:** new `--in-place`/`--no-in-place` option to the `export-dynamic-plugin` CLI command to allow exporting to `dist-dynamic` (when value is `false`). ([#1584](https://github.com/janus-idp/backstage-plugins/issues/1584)) ([4b5cc40](https://github.com/janus-idp/backstage-plugins/commit/4b5cc403c00fab222bf5d5faa43a30c7fa6a97a4))

## @janus-idp/cli [1.8.1](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.8.0...@janus-idp/cli@1.8.1) (2024-04-25)

### Bug Fixes

- **cli:** fix entrypoint validation when running with `npx` on some packages with `alpha` API. ([#1545](https://github.com/janus-idp/backstage-plugins/issues/1545)) ([3d9781c](https://github.com/janus-idp/backstage-plugins/commit/3d9781cbf48cbd11a576d54afa225b95b2ad5726))
- **deps:** update dependency bfj to v8 ([#1463](https://github.com/janus-idp/backstage-plugins/issues/1463)) ([01d9360](https://github.com/janus-idp/backstage-plugins/commit/01d9360e08e0d22fd34a6df304eca60cae908a9e))

## @janus-idp/cli [1.8.0](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.7.10...@janus-idp/cli@1.8.0) (2024-04-15)

### Features

- checkPluginVersion.sh bump plugins for 1.2.0 release ([#1511](https://github.com/janus-idp/backstage-plugins/issues/1511)) ([73c6588](https://github.com/janus-idp/backstage-plugins/commit/73c6588adb7e8c20907b06f2a8ef248cfd4332e4))

## @janus-idp/cli [1.7.10](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.7.9...@janus-idp/cli@1.7.10) (2024-04-09)

### Bug Fixes

- **cli:** `node_modules` of the main plugin unexpectedly copied to the `dist-dynamic` folder. ([#1482](https://github.com/janus-idp/backstage-plugins/issues/1482)) ([deaa19d](https://github.com/janus-idp/backstage-plugins/commit/deaa19d2aaf9e25617911e8bebc67ff8d7471010))

## @janus-idp/cli [1.7.9](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.7.8...@janus-idp/cli@1.7.9) (2024-04-09)

### Bug Fixes

- **cli:** fix entrypoint validation when running with `npx` ([#1473](https://github.com/janus-idp/backstage-plugins/issues/1473)) ([79db649](https://github.com/janus-idp/backstage-plugins/commit/79db649d44a01f8834f5275b17aa1000b7151d59))
- **cli:** fix the `embed-as-dependencies` option on the `export-dynamic-plugin` CLI... ([#1478](https://github.com/janus-idp/backstage-plugins/issues/1478)) ([edd019e](https://github.com/janus-idp/backstage-plugins/commit/edd019e905fd918ee4dcb4f72f0cdd7f791f6300))

## @janus-idp/cli [1.7.8](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.7.7...@janus-idp/cli@1.7.8) (2024-04-05)

## @janus-idp/cli [1.7.7](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.7.6...@janus-idp/cli@1.7.7) (2024-04-02)

### Other changes

- experimental `embed-as-dependencies` option for the backend ([#1418](https://github.com/janus-idp/backstage-plugins/issues/1418)) ([b451380](https://github.com/janus-idp/backstage-plugins/commit/b451380bb048086d90bf7a9c34c4d9c056afbb1e))

## @janus-idp/cli [1.7.6](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.7.5...@janus-idp/cli@1.7.6) (2024-03-29)

## @janus-idp/cli [1.7.5](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.7.4...@janus-idp/cli@1.7.5) (2024-03-04)

## @janus-idp/cli [1.7.4](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.7.3...@janus-idp/cli@1.7.4) (2024-02-27)

## @janus-idp/cli [1.7.3](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.7.2...@janus-idp/cli@1.7.3) (2024-02-26)

## @janus-idp/cli [1.7.2](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.7.1...@janus-idp/cli@1.7.2) (2024-02-21)

## @janus-idp/cli [1.7.1](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.7.0...@janus-idp/cli@1.7.1) (2024-02-05)

### Bug Fixes

- **cli:** embedded alpha module dependencies not hoisted. ([#1170](https://github.com/janus-idp/backstage-plugins/issues/1170)) ([063b343](https://github.com/janus-idp/backstage-plugins/commit/063b3437e7a8267a0fb174d454e7cd9411ea790c))

## @janus-idp/cli [1.7.0](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.6.0...@janus-idp/cli@1.7.0) (2024-01-30)

### Features

- add new backend system support for existing backend plugins that have not been migrated over yet ([#1132](https://github.com/janus-idp/backstage-plugins/issues/1132)) ([06e16fd](https://github.com/janus-idp/backstage-plugins/commit/06e16fdcf64257dd08297cb727445d9a8a23c522))

## @janus-idp/cli [1.6.0](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.5.0...@janus-idp/cli@1.6.0) (2024-01-25)

### Features

- **cli:** switch to @janus-idp/cli for new plugins and populate them with the basics ([#782](https://github.com/janus-idp/backstage-plugins/issues/782)) ([bbbefbd](https://github.com/janus-idp/backstage-plugins/commit/bbbefbd7a534844ee35533a62e4b626bd5b8eb4f))

## @janus-idp/cli [1.5.0](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.4.7...@janus-idp/cli@1.5.0) (2024-01-16)

### Features

- **Notifications:** new notifications FE plugin, API and backend ([#933](https://github.com/janus-idp/backstage-plugins/issues/933)) ([4d4cb78](https://github.com/janus-idp/backstage-plugins/commit/4d4cb781ca9fc331a2c621583e9203f9e4585ee7))

## @janus-idp/cli [1.4.7](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.4.6...@janus-idp/cli@1.4.7) (2023-12-07)

### Bug Fixes

- **cli:** do not change interop mode by default ([#971](https://github.com/janus-idp/backstage-plugins/issues/971)) ([4159977](https://github.com/janus-idp/backstage-plugins/commit/41599773d60fe944e402065970295b47cc2d46d6))

## @janus-idp/cli [1.4.6](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.4.5...@janus-idp/cli@1.4.6) (2023-11-30)

### Bug Fixes

- **cli:** schema generator do not ignore repo root ([#981](https://github.com/janus-idp/backstage-plugins/issues/981)) ([67f22f6](https://github.com/janus-idp/backstage-plugins/commit/67f22f686860e79f5d019f71072b2856a9b17230))

## @janus-idp/cli [1.4.5](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.4.4...@janus-idp/cli@1.4.5) (2023-11-22)

### Bug Fixes

- make the `export-dynamic-plugin` command more generic for backend plugins. ([#967](https://github.com/janus-idp/backstage-plugins/issues/967)) ([b40c661](https://github.com/janus-idp/backstage-plugins/commit/b40c66174ee4dd3240e034d794b19900c9738c86))

## @janus-idp/cli [1.4.4](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.4.3...@janus-idp/cli@1.4.4) (2023-11-20)

### Bug Fixes

- **aap+3scale+ocm:** don't log sensitive data from errors ([#945](https://github.com/janus-idp/backstage-plugins/issues/945)) ([7a5e7b8](https://github.com/janus-idp/backstage-plugins/commit/7a5e7b8a57c9841003d9b16e1a65fb62e101fbf1))

## @janus-idp/cli [1.4.3](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.4.2...@janus-idp/cli@1.4.3) (2023-11-16)

### Bug Fixes

- **cli:** fix possible dependency conflict ([#950](https://github.com/janus-idp/backstage-plugins/issues/950)) ([6c3052e](https://github.com/janus-idp/backstage-plugins/commit/6c3052e9ef2ad77797f6a75cb7f30059442c3764))

## @janus-idp/cli [1.4.2](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.4.1...@janus-idp/cli@1.4.2) (2023-11-13)

### Bug Fixes

- **cli:** use react v17 in dynamic plugins build ([#931](https://github.com/janus-idp/backstage-plugins/issues/931)) ([b47b10a](https://github.com/janus-idp/backstage-plugins/commit/b47b10ab9a1673bf5b303b3051db71f0921049ed))

## @janus-idp/cli [1.4.1](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.4.0...@janus-idp/cli@1.4.1) (2023-11-13)

## @janus-idp/cli [1.4.0](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.3.3...@janus-idp/cli@1.4.0) (2023-11-07)

### Features

- **cli:** generate plugin specific schema for dynamic plugins ([#912](https://github.com/janus-idp/backstage-plugins/issues/912)) ([0c31158](https://github.com/janus-idp/backstage-plugins/commit/0c311585d5aaaa501bef8ba0e8dfddffe240f71c))

## @janus-idp/cli [1.3.3](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.3.2...@janus-idp/cli@1.3.3) (2023-11-06)

### Bug Fixes

- **cli:** add default scalprum config ([#909](https://github.com/janus-idp/backstage-plugins/issues/909)) ([d74fc72](https://github.com/janus-idp/backstage-plugins/commit/d74fc72ab7e0a843da047c7b6570d8a6fbc068e1))

## @janus-idp/cli [1.3.2](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.3.1...@janus-idp/cli@1.3.2) (2023-11-02)

### Bug Fixes

- **scalprum:** share react-router since various 3rd party plugins use it ([#901](https://github.com/janus-idp/backstage-plugins/issues/901)) ([ac0c923](https://github.com/janus-idp/backstage-plugins/commit/ac0c92381c26f20d197255abcc931a7ad14c0edc))

## @janus-idp/cli [1.3.1](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.3.0...@janus-idp/cli@1.3.1) (2023-10-26)

### Bug Fixes

- **cli:** share core-app-api package ([#885](https://github.com/janus-idp/backstage-plugins/issues/885)) ([09db33c](https://github.com/janus-idp/backstage-plugins/commit/09db33ce4113ccb484a167dab8d9fe47d6185c09))

## @janus-idp/cli [1.3.0](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.2.0...@janus-idp/cli@1.3.0) (2023-10-24)

### Features

- **dynamic-ui:** integrate scalprum with current backstage plugins ([#826](https://github.com/janus-idp/backstage-plugins/issues/826)) ([e1fb4ce](https://github.com/janus-idp/backstage-plugins/commit/e1fb4ceafc9e353c4d5b0ed9ba2407b3b0383c60))

## @janus-idp/cli [1.2.0](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.1.1...@janus-idp/cli@1.2.0) (2023-10-23)

### Features

- **cli:** add frontend dynamic plugins base build config ([#747](https://github.com/janus-idp/backstage-plugins/issues/747)) ([91e06da](https://github.com/janus-idp/backstage-plugins/commit/91e06da8ab108c17fd2a6531f25e01c7a7350276)), closes [#831](https://github.com/janus-idp/backstage-plugins/issues/831)

## @janus-idp/cli [1.1.1](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.1.0...@janus-idp/cli@1.1.1) (2023-10-19)

## @janus-idp/cli [1.1.0](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.0.5...@janus-idp/cli@1.1.0) (2023-10-17)

### Features

- add the `export-dynamic-plugin` command, with an implementation for the backend case ([#819](https://github.com/janus-idp/backstage-plugins/issues/819)) ([f873a94](https://github.com/janus-idp/backstage-plugins/commit/f873a94072d17f3bad15b0552b0ef12c285c2ea3))

## @janus-idp/cli [1.0.5](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.0.4...@janus-idp/cli@1.0.5) (2023-09-22)

### Bug Fixes

- **deps:** update dependency @svgr/plugin-jsx to v8 ([#792](https://github.com/janus-idp/backstage-plugins/issues/792)) ([467560c](https://github.com/janus-idp/backstage-plugins/commit/467560c6cecc173fe7949a12014be9fde0e21d3a))
- **deps:** update dependency @svgr/rollup to v8 ([#795](https://github.com/janus-idp/backstage-plugins/issues/795)) ([111aa57](https://github.com/janus-idp/backstage-plugins/commit/111aa574ea6d6c2574c07240383feebe92a6fc90))

## @janus-idp/cli [1.0.4](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.0.3...@janus-idp/cli@1.0.4) (2023-09-22)

### Bug Fixes

- **deps:** update dependency @spotify/eslint-config-react to v15 ([#789](https://github.com/janus-idp/backstage-plugins/issues/789)) ([1a3965a](https://github.com/janus-idp/backstage-plugins/commit/1a3965a07ad3edcd9c608d8530a1933cde6a89bb))
- **deps:** update dependency @svgr/core to v8 ([#791](https://github.com/janus-idp/backstage-plugins/issues/791)) ([db2d09b](https://github.com/janus-idp/backstage-plugins/commit/db2d09b0daddab7ab675eff230e0123f14530ef0))

## @janus-idp/cli [1.0.3](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.0.2...@janus-idp/cli@1.0.3) (2023-09-22)

### Bug Fixes

- **deps:** update dependency @spotify/eslint-config-typescript to v15 ([#790](https://github.com/janus-idp/backstage-plugins/issues/790)) ([9ecaaa3](https://github.com/janus-idp/backstage-plugins/commit/9ecaaa34624652436838b3df963d91605973b964))

## @janus-idp/cli [1.0.2](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.0.1...@janus-idp/cli@1.0.2) (2023-09-22)

### Bug Fixes

- **deps:** update dependency @rollup/plugin-commonjs to v25 ([#765](https://github.com/janus-idp/backstage-plugins/issues/765)) ([615ff44](https://github.com/janus-idp/backstage-plugins/commit/615ff443b2c47421de083caa97171021b7775aa0))

## @janus-idp/cli [1.0.1](https://github.com/janus-idp/backstage-plugins/compare/@janus-idp/cli@1.0.0...@janus-idp/cli@1.0.1) (2023-09-22)

### Bug Fixes

- **deps:** update dependency @rollup/plugin-json to v6 ([#766](https://github.com/janus-idp/backstage-plugins/issues/766)) ([2fe869f](https://github.com/janus-idp/backstage-plugins/commit/2fe869f3d4503fc70ca7d1bcb748d385d3e653a0))
- **deps:** update dependency @spotify/eslint-config-base to v15 ([#774](https://github.com/janus-idp/backstage-plugins/issues/774)) ([04a0ae1](https://github.com/janus-idp/backstage-plugins/commit/04a0ae19db78fa904a15a36684a0e2abec2373a6))

## @janus-idp/cli 1.0.0 (2023-09-22)

### Features

- fork `@backstage/cli` into a new `@janus-idp/cli` ([#729](https://github.com/janus-idp/backstage-plugins/issues/729)) ([e0e8355](https://github.com/janus-idp/backstage-plugins/commit/e0e835590294512ad2eee5b7c9d93a045131dc9e)), closes [#15274](https://github.com/janus-idp/backstage-plugins/issues/15274) [#18439](https://github.com/janus-idp/backstage-plugins/issues/18439)

### Bug Fixes

- **deps:** pin dependencies ([#745](https://github.com/janus-idp/backstage-plugins/issues/745)) ([69bd6a9](https://github.com/janus-idp/backstage-plugins/commit/69bd6a9a078ac66f9934799eb6189c8022157445))
- **deps:** update dependency @rollup/plugin-node-resolve to v15 ([#767](https://github.com/janus-idp/backstage-plugins/issues/767)) ([8d9696c](https://github.com/janus-idp/backstage-plugins/commit/8d9696cd663c2e7bc54f32f64113a45c3a67aa5b))
- **deps:** update dependency handlebars to v4.7.7 [security] ([#753](https://github.com/janus-idp/backstage-plugins/issues/753)) ([52a195e](https://github.com/janus-idp/backstage-plugins/commit/52a195e0c2160bb6fc18d40daaee1ec1f05d666d))
- **deps:** update dependency postcss to v8.2.13 [security] ([#755](https://github.com/janus-idp/backstage-plugins/issues/755)) ([37fc85f](https://github.com/janus-idp/backstage-plugins/commit/37fc85fd37a064c20f19f2b7825bc0e7b0dc28a5))
- **deps:** update dependency yaml to v2.2.2 [security] ([#757](https://github.com/janus-idp/backstage-plugins/issues/757)) ([b3c719c](https://github.com/janus-idp/backstage-plugins/commit/b3c719ca3d0a43ee3eb5b88313d4278e624beaff))
- **deps:** update linters ([#746](https://github.com/janus-idp/backstage-plugins/issues/746)) ([bf06a66](https://github.com/janus-idp/backstage-plugins/commit/bf06a66b1c7bd3225a5767e619652bad90030083))

# @backstage/cli

## 0.22.13-next.3

### Patch Changes

- 4d5eeec52d80: Add ESM loader for the experimental backend start command.
- 3494c502aba7: Added a new `repo fix` command that fixes auto-fixable problems in all packages. Initially the command fixes package export declarations, as well as marks all non-bundled frontend packages as side-effect free. Marking packages as free of side-effects can drastically reduce the Webpack bundle size.
- f36113ca2305: Add experimental support for frontend package discovery.
- a23fce763c6a: Fixed a bug where package exports entry points could not be `.tsx` files.
- 4af4defcc114: When running `version:bump` it will now log duplicates instead of throwing an error
- 956d226eeeee: Add `"sideEffects": false` to `package.json` in frontend package templates. This can be added to existing packages using the new `yarn fix` command.
- cd7331587eb3: Removed the experimental `package fix` command that was used to automatically add dependencies to `package.json`, but has since been replaced by the `no-undeclared-imports` rule from `@backstage/eslint-plugin`.
- Updated dependencies
  - @backstage/catalog-model@1.4.2-next.2
  - @backstage/config@1.1.0-next.2
  - @backstage/errors@1.2.2-next.0
  - @backstage/integration@1.7.0-next.3
  - @backstage/release-manifests@0.0.10-next.1
  - @backstage/types@1.1.1-next.0
  - @backstage/cli-common@0.1.12
  - @backstage/cli-node@0.1.4-next.0
  - @backstage/config-loader@1.5.0-next.3
  - @backstage/eslint-plugin@0.1.3

## 0.22.13-next.2

### Patch Changes

- 8cec7664e146: Removed `@types/node` dependency
- ea779492ad88: Updated dependency `run-script-webpack-plugin` to `^0.2.0`.
- Updated dependencies
  - @backstage/release-manifests@0.0.10-next.0
  - @backstage/config-loader@1.5.0-next.2
  - @backstage/config@1.1.0-next.1
  - @backstage/integration@1.7.0-next.2
  - @backstage/catalog-model@1.4.2-next.1
  - @backstage/cli-common@0.1.12
  - @backstage/cli-node@0.1.3
  - @backstage/errors@1.2.1
  - @backstage/eslint-plugin@0.1.3
  - @backstage/types@1.1.0

## 0.22.13-next.1

### Patch Changes

- Updated dependencies
  - @backstage/config@1.1.0-next.0
  - @backstage/integration@1.7.0-next.1
  - @backstage/catalog-model@1.4.2-next.0
  - @backstage/config-loader@1.5.0-next.1
  - @backstage/cli-common@0.1.12
  - @backstage/cli-node@0.1.3
  - @backstage/errors@1.2.1
  - @backstage/eslint-plugin@0.1.3
  - @backstage/release-manifests@0.0.9
  - @backstage/types@1.1.0

## 0.22.12-next.0

### Patch Changes

- 278d9326eb40: Added the ability to create a plain backend module with the `new` command.
- 71d4368ae5cc: Added support for the `dev/index` entry point for backend plugins and modules.
- Updated dependencies
  - @backstage/integration@1.7.0-next.0
  - @backstage/config-loader@1.5.0-next.0
  - @backstage/catalog-model@1.4.1
  - @backstage/cli-common@0.1.12
  - @backstage/cli-node@0.1.3
  - @backstage/config@1.0.8
  - @backstage/errors@1.2.1
  - @backstage/eslint-plugin@0.1.3
  - @backstage/release-manifests@0.0.9
  - @backstage/types@1.1.0

## 0.22.10

### Patch Changes

- 3f67cefb4780: Reload the frontend when app config changes
- cebbf8a27f3c: Enable to print the config schema not merged with the `--no-merge` flag
- 5c28ebc79fd6: Updated dependency `esbuild` to `^0.19.0`.
- 971bdd6a4732: Bumped internal `nodemon` dependency.
- Updated dependencies
  - @backstage/config-loader@1.4.0
  - @backstage/cli-node@0.1.3
  - @backstage/integration@1.6.0
  - @backstage/catalog-model@1.4.1
  - @backstage/cli-common@0.1.12
  - @backstage/config@1.0.8
  - @backstage/errors@1.2.1
  - @backstage/eslint-plugin@0.1.3
  - @backstage/release-manifests@0.0.9
  - @backstage/types@1.1.0

## 0.22.10-next.1

### Patch Changes

- Updated dependencies
  - @backstage/config-loader@1.4.0-next.1
  - @backstage/cli-node@0.1.3-next.0
  - @backstage/integration@1.5.1
  - @backstage/catalog-model@1.4.1
  - @backstage/cli-common@0.1.12
  - @backstage/config@1.0.8
  - @backstage/errors@1.2.1
  - @backstage/eslint-plugin@0.1.3
  - @backstage/release-manifests@0.0.9
  - @backstage/types@1.1.0

## 0.22.10-next.0

### Patch Changes

- 3f67cefb4780: Reload the frontend when app config changes
- cebbf8a27f3c: Enable to print the config schema not merged with the `--no-merge` flag
- Updated dependencies
  - @backstage/config-loader@1.4.0-next.0
  - @backstage/catalog-model@1.4.1
  - @backstage/cli-common@0.1.12
  - @backstage/cli-node@0.1.2
  - @backstage/config@1.0.8
  - @backstage/errors@1.2.1
  - @backstage/eslint-plugin@0.1.3
  - @backstage/integration@1.5.1
  - @backstage/release-manifests@0.0.9
  - @backstage/types@1.1.0

## 0.22.9

### Patch Changes

- 6adb6f41711a: Fixed the `--alwaysYarnPack` flag on the`backstage-cli build-workspace` command.
- 4edd1ef71453: semver upgrade to 7.5.3
- ff45cb559e49: Updated dependency `esbuild` to `^0.18.0`.
- 8174cf4c0edf: Fixing MUI / Material UI references
- Updated dependencies
  - @backstage/errors@1.2.1
  - @backstage/cli-node@0.1.2
  - @backstage/catalog-model@1.4.1
  - @backstage/cli-common@0.1.12
  - @backstage/config@1.0.8
  - @backstage/config-loader@1.3.2
  - @backstage/eslint-plugin@0.1.3
  - @backstage/integration@1.5.1
  - @backstage/release-manifests@0.0.9
  - @backstage/types@1.1.0

## 0.22.9-next.1

### Patch Changes

- 4edd1ef71453: semver upgrade to 7.5.3
- ff45cb559e49: Updated dependency `esbuild` to `^0.18.0`.
- 8174cf4c0edf: Fixing MUI / Material UI references
- Updated dependencies
  - @backstage/cli-node@0.1.2-next.1
  - @backstage/catalog-model@1.4.1-next.0
  - @backstage/cli-common@0.1.12
  - @backstage/config@1.0.8
  - @backstage/config-loader@1.3.2-next.0
  - @backstage/errors@1.2.1-next.0
  - @backstage/eslint-plugin@0.1.3
  - @backstage/integration@1.5.1-next.0
  - @backstage/release-manifests@0.0.9
  - @backstage/types@1.1.0

## 0.22.9-next.0

### Patch Changes

- 6adb6f41711a: Fixed the `--alwaysYarnPack` flag on the`backstage-cli build-workspace` command.
- Updated dependencies
  - @backstage/errors@1.2.1-next.0
  - @backstage/catalog-model@1.4.1-next.0
  - @backstage/cli-common@0.1.12
  - @backstage/cli-node@0.1.2-next.0
  - @backstage/config@1.0.8
  - @backstage/config-loader@1.3.2-next.0
  - @backstage/eslint-plugin@0.1.3
  - @backstage/integration@1.5.1-next.0
  - @backstage/release-manifests@0.0.9
  - @backstage/types@1.1.0

## 0.22.8

### Patch Changes

- 314493fa32a0: Introduced the `--alwaysYarnPack` flag on `backstage-cli build-workspace`, which can be passed in cases where accuracy of workspace contents is more important than the
  speed with which the workspace is built. Useful in rare situations where `yarn pack` and `npm pack` produce different results.
- 75540599124a: Updated example component for a newly scaffolded app.
- 5d692f72ebfb: Make sure to include a `fetch` environment for `jsdom` in `jest` tests
- 6816352500a7: Add discovery feature to the onboard cli command.
- 20b7da6f1311: Enforcing Material UI v5 specific linting to minimize bundle size.
- Updated dependencies
  - @backstage/types@1.1.0
  - @backstage/config-loader@1.3.1
  - @backstage/integration@1.5.0
  - @backstage/catalog-model@1.4.0
  - @backstage/errors@1.2.0
  - @backstage/cli-common@0.1.12
  - @backstage/cli-node@0.1.1
  - @backstage/config@1.0.8
  - @backstage/eslint-plugin@0.1.3
  - @backstage/release-manifests@0.0.9

## 0.22.8-next.2

### Patch Changes

- 75540599124a: Updated example component for a newly scaffolded app.
- Updated dependencies
  - @backstage/catalog-model@1.4.0-next.1
  - @backstage/cli-common@0.1.12
  - @backstage/cli-node@0.1.1-next.0
  - @backstage/config@1.0.7
  - @backstage/config-loader@1.3.1-next.1
  - @backstage/errors@1.2.0-next.0
  - @backstage/eslint-plugin@0.1.3
  - @backstage/integration@1.5.0-next.0
  - @backstage/release-manifests@0.0.9
  - @backstage/types@1.0.2

## 0.22.8-next.1

### Patch Changes

- 6816352500a7: Add discovery feature to the onboard cli command.
- Updated dependencies
  - @backstage/integration@1.5.0-next.0
  - @backstage/errors@1.2.0-next.0
  - @backstage/catalog-model@1.4.0-next.0
  - @backstage/cli-node@0.1.1-next.0
  - @backstage/config-loader@1.3.1-next.1
  - @backstage/cli-common@0.1.12
  - @backstage/config@1.0.7
  - @backstage/eslint-plugin@0.1.3
  - @backstage/release-manifests@0.0.9
  - @backstage/types@1.0.2

## 0.22.8-next.0

### Patch Changes

- 20b7da6f1311: Enforcing Material UI v5 specific linting to minimize bundle size.
- Updated dependencies
  - @backstage/config-loader@1.3.1-next.0
  - @backstage/config@1.0.7
  - @backstage/release-manifests@0.0.9
  - @backstage/cli-common@0.1.12
  - @backstage/cli-node@0.1.0
  - @backstage/errors@1.1.5
  - @backstage/eslint-plugin@0.1.3
  - @backstage/types@1.0.2

## 0.22.7

### Patch Changes

- 473db605a4f: Enable strict config checking during `backstage-cli config:check` with the new `--strict` option which will surface schema errors.
- d548886872d: Deprecated the use of React 16
- Updated dependencies
  - @backstage/config-loader@1.3.0
  - @backstage/cli-common@0.1.12
  - @backstage/cli-node@0.1.0
  - @backstage/config@1.0.7
  - @backstage/errors@1.1.5
  - @backstage/eslint-plugin@0.1.3
  - @backstage/release-manifests@0.0.9
  - @backstage/types@1.0.2

## 0.22.7-next.0

### Patch Changes

- Updated dependencies
  - @backstage/config-loader@1.3.0-next.0
  - @backstage/cli-common@0.1.12
  - @backstage/cli-node@0.1.0
  - @backstage/config@1.0.7
  - @backstage/errors@1.1.5
  - @backstage/eslint-plugin@0.1.3
  - @backstage/release-manifests@0.0.9
  - @backstage/types@1.0.2

## 0.22.6

### Patch Changes

- 24432ae52fb: Fix the build for packages with multiple entry points to avoid duplicated modules.
- 8075b67e64c: When building a backend package with dependencies any `--config <path>` options will now be forwarded to any dependent app package builds, unless the build script in the app package already contains a `--config` option.
- 79e91d4c30a: Support importing `.md` files in build loader
- 3156b0d85dc: Internal refactor to move many internal utilities to the new `@backstage/cli-node` package.
- b9839d7135c: Fixed backend start command on Windows by removing the use of platform dependent path joins.
- 1e4f5e91b8e: Bump `zod` and `zod-to-json-schema` dependencies.
- 29ba8267d69: Updated dependency `@material-ui/lab` to `4.0.0-alpha.61`.
- 9bbb00d5b49: Updated dependency `@swc/helpers` to `^0.5.0`.
- b588ab73972: Ensure that the `package prepack` command and backend bundling uses posix paths in `package.json` on all OSes.
- c07c3b7364b: Add `onboard` command. While still in development, this command aims to guide users in setting up their Backstage App.
- e0c6e8b9c3c: Update peer dependencies
- Updated dependencies
  - @backstage/cli-node@0.1.0
  - @backstage/config-loader@1.2.0
  - @backstage/eslint-plugin@0.1.3
  - @backstage/cli-common@0.1.12
  - @backstage/config@1.0.7
  - @backstage/errors@1.1.5
  - @backstage/release-manifests@0.0.9
  - @backstage/types@1.0.2

## 0.22.6-next.3

### Patch Changes

- 3156b0d85dc: Internal refactor to move many internal utilities to the new `@backstage/cli-node` package.
- 9bbb00d5b49: Updated dependency `@swc/helpers` to `^0.5.0`.
- Updated dependencies
  - @backstage/cli-node@0.1.0-next.0
  - @backstage/cli-common@0.1.12
  - @backstage/config@1.0.7
  - @backstage/config-loader@1.1.9
  - @backstage/errors@1.1.5
  - @backstage/eslint-plugin@0.1.3-next.0
  - @backstage/release-manifests@0.0.9
  - @backstage/types@1.0.2

## 0.22.6-next.2

### Patch Changes

- 8075b67e64c: When building a backend package with dependencies any `--config <path>` options will now be forwarded to any dependent app package builds, unless the build script in the app package already contains a `--config` option.
- Updated dependencies
  - @backstage/cli-common@0.1.12
  - @backstage/config@1.0.7
  - @backstage/config-loader@1.1.9
  - @backstage/errors@1.1.5
  - @backstage/eslint-plugin@0.1.3-next.0
  - @backstage/release-manifests@0.0.9
  - @backstage/types@1.0.2

## 0.22.6-next.1

### Patch Changes

- 24432ae52fb: Fix the build for packages with multiple entry points to avoid duplicated modules.
- 79e91d4c30a: Support importing `.md` files in build loader
- 1e4f5e91b8e: Bump `zod` and `zod-to-json-schema` dependencies.
- 29ba8267d69: Updated dependency `@material-ui/lab` to `4.0.0-alpha.61`.
- b588ab73972: Ensure that the `package prepack` command and backend bundling uses posix paths in `package.json` on all OSes.
- e0c6e8b9c3c: Update peer dependencies
- Updated dependencies
  - @backstage/cli-common@0.1.12
  - @backstage/config@1.0.7
  - @backstage/config-loader@1.1.9
  - @backstage/errors@1.1.5
  - @backstage/eslint-plugin@0.1.3-next.0
  - @backstage/release-manifests@0.0.9
  - @backstage/types@1.0.2

## 0.22.6-next.0

### Patch Changes

- b9839d7135c: Fixed backend start command on Windows by removing the use of platform dependent path joins.
- c07c3b7364b: Add `onboard` command. While still in development, this command aims to guide users in setting up their Backstage App.
- Updated dependencies
  - @backstage/eslint-plugin@0.1.3-next.0
  - @backstage/config@1.0.7
  - @backstage/release-manifests@0.0.9
  - @backstage/cli-common@0.1.12
  - @backstage/config-loader@1.1.9
  - @backstage/errors@1.1.5
  - @backstage/types@1.0.2

## 0.22.4

### Patch Changes

- 1ad8d885d30: Fixed a bug where additional backend package entry points where not properly marked as internal during local development.
- 2011b86052c: Added templates for new plugin Web and Node.js libraries.
- 867f4752ca1: Updated the ESLint plugin configuration that is enabled through `yarn start --check` to only pick up valid source files.
- b4cd145b574: Added a new `migrate package-exports` command that synchronizes package exports fields in all `package.json`s.
- 9bf50a36674: Bumped the `msw` version in templates to 1.0.0
- 8bf24946c66: Adjust express dependencies to be the same as the rest of the project
- 17271841de8: Updated frontend plugin template to use some more recent features
- 4b4998466b4: Updated dependency `del` to `^7.0.0`.
- 52b0022dab7: Updated dependency `msw` to `^1.0.0`.
- a11b9a23f5a: Keep custom exports entry points in package.json
- 482dae5de1c: Updated link to docs.
- Updated dependencies
  - @backstage/eslint-plugin@0.1.2
  - @backstage/errors@1.1.5
  - @backstage/config-loader@1.1.9
  - @backstage/release-manifests@0.0.9
  - @backstage/cli-common@0.1.12
  - @backstage/config@1.0.7
  - @backstage/types@1.0.2

## 0.22.4-next.1

### Patch Changes

- 1ad8d885d30: Fixed a bug where additional backend package entry points where not properly marked as internal during local development.
- 867f4752ca1: Updated the ESLint plugin configuration that is enabled through `yarn start --check` to only pick up valid source files.
- 9bf50a36674: Bumped the `msw` version in templates to 1.0.0
- 4b4998466b4: Updated dependency `del` to `^7.0.0`.
- 52b0022dab7: Updated dependency `msw` to `^1.0.0`.
- a11b9a23f5a: Keep custom exports entry points in package.json
- 482dae5de1c: Updated link to docs.
- Updated dependencies
  - @backstage/errors@1.1.5-next.0
  - @backstage/config-loader@1.1.9-next.0
  - @backstage/release-manifests@0.0.9-next.0
  - @backstage/cli-common@0.1.12-next.0
  - @backstage/config@1.0.7-next.0
  - @backstage/eslint-plugin@0.1.2-next.0
  - @backstage/types@1.0.2

## 0.22.4-next.0

### Patch Changes

- b4cd145b57: Added a new `migrate package-exports` command that synchronizes package exports fields in all `package.json`s.
- 8bf24946c6: Adjust express dependencies to be the same as the rest of the project
- 17271841de: Updated frontend plugin template to use some more recent features
- Updated dependencies
  - @backstage/eslint-plugin@0.1.2-next.0
  - @backstage/cli-common@0.1.11
  - @backstage/config@1.0.6
  - @backstage/config-loader@1.1.8
  - @backstage/errors@1.1.4
  - @backstage/release-manifests@0.0.8
  - @backstage/types@1.0.2

## 0.22.2

### Patch Changes

- 561df21ea3: The `backstage-cli repo test` command now sets a default Jest `--workerIdleMemoryLimit` of 1GB. If needed to ensure that tests are not run in band, `--maxWorkers=2` is set as well. This is the recommended workaround for dealing with Jest workers leaking memory and eventually hitting the heap limit.
- 2815981057: Show module name causing error during build
- dd8a9afe66: Replaced several monorepo lint rules with new rules from `@backstage/eslint-plugin`. See the [README](https://github.com/import-js/eslint-plugin-import/blob/main/packages/eslint-plugin/README.md) for a full list of rules.
- a9c50af76b: Fixed Webpack loader patterns so that they properly match the file suffix only.
- 66cf22fdc4: Updated dependency `esbuild` to `^0.17.0`.
- 6d3abfded1: Switch to inline source maps for test transpilation, simplifying editor setups.
- 90616df9a8: Added an experimental mode for the `package start` command for backend packages. Enabled by setting `EXPERIMENTAL_BACKEND_START`.
- Updated dependencies
  - @backstage/eslint-plugin@0.1.0
  - @backstage/cli-common@0.1.11
  - @backstage/config@1.0.6
  - @backstage/config-loader@1.1.8
  - @backstage/errors@1.1.4
  - @backstage/release-manifests@0.0.8
  - @backstage/types@1.0.2

## 0.22.2-next.1

### Patch Changes

- dd8a9afe66: Replaced several monorepo lint rules with new rules from `@backstage/eslint-plugin`. See the [README](https://github.com/import-js/eslint-plugin-import/blob/main/packages/eslint-plugin/README.md) for a full list of rules.
- 90616df9a8: Added an experimental mode for the `package start` command for backend packages. Enabled by setting `EXPERIMENTAL_BACKEND_START`.
- Updated dependencies
  - @backstage/eslint-plugin@0.1.0-next.0
  - @backstage/cli-common@0.1.11
  - @backstage/config@1.0.6
  - @backstage/config-loader@1.1.8
  - @backstage/errors@1.1.4
  - @backstage/release-manifests@0.0.8
  - @backstage/types@1.0.2

## 0.22.2-next.0

### Patch Changes

- 561df21ea3: The `backstage-cli repo test` command now sets a default Jest `--workerIdleMemoryLimit` of 1GB. If needed to ensure that tests are not run in band, `--maxWorkers=2` is set as well. This is the recommended workaround for dealing with Jest workers leaking memory and eventually hitting the heap limit.
- 2815981057: Show module name causing error during build
- 66cf22fdc4: Updated dependency `esbuild` to `^0.17.0`.
- 6d3abfded1: Switch to inline source maps for test transpilation, simplifying editor setups.
- Updated dependencies
  - @backstage/cli-common@0.1.11
  - @backstage/config@1.0.6
  - @backstage/config-loader@1.1.8
  - @backstage/errors@1.1.4
  - @backstage/release-manifests@0.0.8
  - @backstage/types@1.0.2

## 0.22.1

### Patch Changes

- db2e137744: Removed unnecessary usage of `ThemeProvider` from the `ExampleComponent` test in the plugin template.
- 47c10706df: Fixed an issue where the CLI would fail to function when there was a mix of workspace and non-workspace versions of the same package in `yarn.lock` when using Yarn 3.
- 2b435be4cf: Updated backend plugin ID during creation to match user-entered input.
- 4b572126f1: Add experimental environment variable to enable caching for production builds.
- 7b407b303b: Slightly improve readability of "base URL conflict" error handling code
- a62a1f9dca: The frontend serve task now filters out allowed package duplicates during its package check, just like `versions:bump` and `versions:check`.
- d06a7890c6: Removed unused package `type-fest`
- 7c8a974515: The `repo test`, `repo lint`, and `repo build` commands will now analyze `yarn.lock` for dependency changes when searching for changed packages. This allows you to use the `--since <ref>` flag even if you have `yarn.lock` changes.
- e1b71e142e: Workspace ranges are no longer considered invalid by version commands.
- Updated dependencies
  - @backstage/config@1.0.6
  - @backstage/cli-common@0.1.11
  - @backstage/config-loader@1.1.8
  - @backstage/errors@1.1.4
  - @backstage/release-manifests@0.0.8
  - @backstage/types@1.0.2

## 0.22.1-next.2

### Patch Changes

- 7b407b303b: Slightly improve readability of "base URL conflict" error handling code
- d06a7890c6: Removed unused package `type-fest`
- Updated dependencies
  - @backstage/cli-common@0.1.11
  - @backstage/config@1.0.6-next.0
  - @backstage/config-loader@1.1.8-next.0
  - @backstage/errors@1.1.4
  - @backstage/release-manifests@0.0.8
  - @backstage/types@1.0.2

## 0.22.1-next.1

### Patch Changes

- db2e137744: Removed unnecessary usage of `ThemeProvider` from the `ExampleComponent` test in the plugin template.
- 4b572126f1: Add experimental environment variable to enable caching for production builds.
- Updated dependencies
  - @backstage/config@1.0.6-next.0
  - @backstage/cli-common@0.1.11
  - @backstage/config-loader@1.1.8-next.0
  - @backstage/errors@1.1.4
  - @backstage/release-manifests@0.0.8
  - @backstage/types@1.0.2

## 0.22.1-next.0

### Patch Changes

- 47c10706df: Fixed an issue where the CLI would fail to function when there was a mix of workspace and non-workspace versions of the same package in `yarn.lock` when using Yarn 3.
- a62a1f9dca: The frontend serve task now filters out allowed package duplicates during its package check, just like `versions:bump` and `versions:check`.
- 7c8a974515: The `repo test`, `repo lint`, and `repo build` commands will now analyze `yarn.lock` for dependency changes when searching for changed packages. This allows you to use the `--since <ref>` flag even if you have `yarn.lock` changes.
- e1b71e142e: Workspace ranges are no longer considered invalid by version commands.
- Updated dependencies
  - @backstage/cli-common@0.1.11
  - @backstage/config@1.0.5
  - @backstage/config-loader@1.1.7
  - @backstage/errors@1.1.4
  - @backstage/release-manifests@0.0.8
  - @backstage/types@1.0.2

## 0.22.0

### Minor Changes

- 736f893f72: The Jest configuration that was previously enabled with `BACKSTAGE_NEXT_TESTS` is now enabled by default. To revert to the old configuration you can now instead set `BACKSTAGE_OLD_TESTS`.

  This new configuration uses the `babel` coverage provider rather than `v8`. It used to be that `v8` worked better when using Sucrase for transpilation, but now that we have switched to SWC, `babel` seems to work better. In addition, the new configuration also enables source maps by default, as they no longer have a negative impact on code coverage accuracy, and it also enables a modified Jest runtime with additional caching of script objects.

### Patch Changes

- 91d050c140: changed tests created by create-plugin to follow eslint-rules best practices particularly testing-library/prefer-screen-queries and testing-library/render-result-naming-convention
- 43b2b9c791: Removed the unused dependency on `@sucrase/jest-plugin`.
- dd721148b5: Updated Jest coverage configuration to only apply either in the root project or package configuration, depending on whether repo or package tests are run.
- 5850ef9b84: Fix webpack dev server issue where it wasn't serving `index.html` from correct endpoint on subsequent requests.
- b05dcd5530: Move the `zod` dependency to a version that does not collide with other libraries
- 459a3457e1: Bump `msw` version in default plugin/app templates
- c27eabef6b: Adds new web-library package option when generating a new plugin
- 8fffe42708: JSX and React Fast Refresh transforms are no longer enabled when bundling backend code.
- 309f2daca4: Updated dependency `esbuild` to `^0.16.0`.
- ee14bab716: Updated dependency `minimatch` to `5.1.1` and switch version range to `^`.
- 3280711113: Updated dependency `msw` to `^0.49.0`.
- ed0cf59c59: Updated dependency `@rollup/plugin-commonjs` to `^23.0.0`.
- 16b7c2fccd: Updated dependency `@rollup/plugin-yaml` to `^4.0.0`.
- 086c0bbb45: Updated dependency `@rollup/plugin-json` to `^5.0.0`.
- 8015ff1258: Tweaked wording to use inclusive terminology
- d9d9a7a134: Removed all copyright notices from package templates.
- 8e0358e18d: Added `--skip-install` parameter to `backstage-cli versions:bump`
- Updated dependencies
  - @backstage/errors@1.1.4
  - @backstage/config-loader@1.1.7
  - @backstage/release-manifests@0.0.8
  - @backstage/types@1.0.2
  - @backstage/cli-common@0.1.11
  - @backstage/config@1.0.5

## 0.22.0-next.4

### Minor Changes

- 736f893f72: The Jest configuration that was previously enabled with `BACKSTAGE_NEXT_TESTS` is now enabled by default. To revert to the old configuration you can now instead set `BACKSTAGE_OLD_TESTS`.

  This new configuration uses the `babel` coverage provider rather than `v8`. It used to be that `v8` worked better when using Sucrase for transpilation, but now that we have switched to SWC, `babel` seems to work better. In addition, the new configuration also enables source maps by default, as they no longer have a negative impact on code coverage accuracy, and it also enables a modified Jest runtime with additional caching of script objects.

### Patch Changes

- dd721148b5: Updated Jest coverage configuration to only apply either in the root project or package configuration, depending on whether repo or package tests are run.
- b05dcd5530: Move the `zod` dependency to a version that does not collide with other libraries
- c27eabef6b: Adds new web-library package option when generating a new plugin
- 309f2daca4: Updated dependency `esbuild` to `^0.16.0`.
- d9d9a7a134: Removed all copyright notices from package templates.
- Updated dependencies
  - @backstage/cli-common@0.1.11-next.0
  - @backstage/config@1.0.5-next.1
  - @backstage/config-loader@1.1.7-next.2
  - @backstage/errors@1.1.4-next.1
  - @backstage/release-manifests@0.0.8-next.0
  - @backstage/types@1.0.2-next.1

## 0.21.2-next.3

### Patch Changes

- 43b2b9c791: Removed the unused dependency on `@sucrase/jest-plugin`.
- Updated dependencies
  - @backstage/cli-common@0.1.11-next.0
  - @backstage/config@1.0.5-next.1
  - @backstage/config-loader@1.1.7-next.2
  - @backstage/errors@1.1.4-next.1
  - @backstage/release-manifests@0.0.8-next.0
  - @backstage/types@1.0.2-next.1

## 0.21.2-next.2

### Patch Changes

- 5850ef9b84: Fix webpack dev server issue where it wasn't serving `index.html` from correct endpoint on subsequent requests.
- ee14bab716: Updated dependency `minimatch` to `5.1.1` and switch version range to `^`.
- ed0cf59c59: Updated dependency `@rollup/plugin-commonjs` to `^23.0.0`.
- 16b7c2fccd: Updated dependency `@rollup/plugin-yaml` to `^4.0.0`.
- 086c0bbb45: Updated dependency `@rollup/plugin-json` to `^5.0.0`.
- 8015ff1258: Tweaked wording to use inclusive terminology
- Updated dependencies
  - @backstage/cli-common@0.1.11-next.0
  - @backstage/config@1.0.5-next.1
  - @backstage/config-loader@1.1.7-next.2
  - @backstage/errors@1.1.4-next.1
  - @backstage/release-manifests@0.0.8-next.0
  - @backstage/types@1.0.2-next.1

## 0.21.2-next.1

### Patch Changes

- 8fffe42708: JSX and React Fast Refresh transforms are no longer enabled when bundling backend code.
- Updated dependencies
  - @backstage/types@1.0.2-next.1
  - @backstage/config-loader@1.1.7-next.1
  - @backstage/config@1.0.5-next.1
  - @backstage/release-manifests@0.0.8-next.0
  - @backstage/cli-common@0.1.10
  - @backstage/errors@1.1.4-next.1

## 0.21.2-next.0

### Patch Changes

- 91d050c140: changed tests created by create-plugin to follow eslint-rules best practices particularly testing-library/prefer-screen-queries and testing-library/render-result-naming-convention
- 459a3457e1: Bump `msw` version in default plugin/app templates
- 3280711113: Updated dependency `msw` to `^0.49.0`.
- Updated dependencies
  - @backstage/config-loader@1.1.7-next.0
  - @backstage/release-manifests@0.0.8-next.0
  - @backstage/types@1.0.2-next.0
  - @backstage/cli-common@0.1.10
  - @backstage/config@1.0.5-next.0
  - @backstage/errors@1.1.4-next.0

## 0.21.0

### Minor Changes

- 7539b36748: Added a new ESLint rule that restricts imports of Link from @material-ui

  The rule can be can be overridden in the following way:

  ```diff
  module.exports = require('@backstage/cli/config/eslint-factory')(__dirname, {
  +  restrictedImports: [
  +    { name: '@material-ui/core', importNames: [] },
  +    { name: '@material-ui/core/Link', importNames: [] },
  +  ],
  });
  ```

- 384eaa2307: Switched `tsconfig.json` to target and support `ES2021`, in line with the bump to Node.js 16 & 18.

### Patch Changes

- e52d6ad861: Updated the `backstage-cli` so that the `list-deprecations` command is visible and also removed the "[EXPERIMENTAL]" tag.
- 88f99b8b13: Bumped `tar` dependency to `^6.1.12` in order to ensure Node.js v18 compatibility.
- df21bbd4ad: Removed googleAnalyticsTrackingId configSchema.
- 286d474675: Minor update to the `index.html` template that updates the comment at the end to be more accurate.
- 4c16213e7d: The built-in Jest configuration now always uses the Jest environments that are bundled with the CLI by default. This avoids a situation where Jest potentially picks up an incompatible version of the environment package from a different dependency in the project.
- 4091c73e68: Updated `@swc/core` to version 1.3.9 which fixes a `.tsx` parser bug
- 969a8444ea: Updated dependency `esbuild` to `^0.15.0`.
- 9c767e8f45: Updated dependency `@svgr/plugin-jsx` to `6.5.x`.
  Updated dependency `@svgr/plugin-svgo` to `6.5.x`.
  Updated dependency `@svgr/rollup` to `6.5.x`.
  Updated dependency `@svgr/webpack` to `6.5.x`.
- Updated dependencies
  - @backstage/release-manifests@0.0.7
  - @backstage/types@1.0.1
  - @backstage/cli-common@0.1.10
  - @backstage/config@1.0.4
  - @backstage/config-loader@1.1.6
  - @backstage/errors@1.1.3

## 0.21.0-next.1

### Minor Changes

- 384eaa2307: Switched `tsconfig.json` to target and support `ES2021`, in line with the bump to Node.js 16 & 18.

### Patch Changes

- 88f99b8b13: Bumped `tar` dependency to `^6.1.12` in order to ensure Node.js v18 compatibility.
- 969a8444ea: Updated dependency `esbuild` to `^0.15.0`.
- Updated dependencies
  - @backstage/release-manifests@0.0.7-next.0
  - @backstage/cli-common@0.1.10
  - @backstage/config@1.0.4-next.0
  - @backstage/config-loader@1.1.6-next.0
  - @backstage/errors@1.1.3-next.0
  - @backstage/types@1.0.1-next.0

## 0.21.0-next.0

### Minor Changes

- 7539b36748: Added a new ESLint rule that restricts imports of Link from @material-ui

  The rule can be can be overridden in the following way:

  ```diff
  module.exports = require('@backstage/cli/config/eslint-factory')(__dirname, {
  +  restrictedImports: [
  +    { name: '@material-ui/core', importNames: [] },
  +    { name: '@material-ui/core/Link', importNames: [] },
  +  ],
  });
  ```

### Patch Changes

- 4091c73e68: Updated `@swc/core` to version 1.3.9 which fixes a `.tsx` parser bug
- 9c767e8f45: Updated dependency `@svgr/plugin-jsx` to `6.5.x`.
  Updated dependency `@svgr/plugin-svgo` to `6.5.x`.
  Updated dependency `@svgr/rollup` to `6.5.x`.
  Updated dependency `@svgr/webpack` to `6.5.x`.
- Updated dependencies
  - @backstage/types@1.0.1-next.0
  - @backstage/cli-common@0.1.10
  - @backstage/config@1.0.4-next.0
  - @backstage/config-loader@1.1.6-next.0
  - @backstage/errors@1.1.3-next.0
  - @backstage/release-manifests@0.0.6

## 0.20.0

### Minor Changes

- f368ad7279: **BREAKING**: Bumped `jest`, `jest-runtime`, and `jest-environment-jsdom` to v29. This is up from v27, so check out both the [v28](https://jestjs.io/docs/28.x/upgrading-to-jest28) and [v29](https://jestjs.io/docs/upgrading-to-jest29) (later [here](https://jestjs.io/docs/29.x/upgrading-to-jest29)) migration guides.

  Particular changes that where encountered in the main Backstage repo are:

  - The updated snapshot format.
  - `jest.useFakeTimers('legacy')` is now `jest.useFakeTimers({ legacyFakeTimers: true })`.
  - Error objects collected by `withLogCollector` from `@backstage/test-utils` are now objects with a `detail` property rather than a string.

### Patch Changes

- 78d5eb299e: Tweak the Jest Caching loader to only operate when in `watch` mode
- 9c595302cb: Normalize on winston version ^3.2.1
- 24b40140c4: Treat files in `__testUtils__` and `__mocks__` directories as test files for linting
  purposes.

  Updates the parts of the eslint configuration generator that specify which files
  should be treated as test code to include any files under two additional
  directories:

  - `__mocks__`: this is the directory used by Jest[0] for mock code.
  - `__testUtils__`: a suggested location for utility code executed only when
    running tests.

  [0]: https://jestjs.io/docs/manual-mocks#mocking-user-modules

- 3e309107ca: Updated fallback versions of dependencies in all templates.
- 292a088807: Added a new `repo test` command.
- ba63cae41c: Updated lockfile parsing to have better support for Yarn 3.
- 2d3a5f09ab: Use `response.json` rather than `response.send` where appropriate, as outlined in `SECURITY.md`
- 2dddb32fea: Switched the Jest transform for YAML files to use a custom one available at `@backstage/cli/config/jestYamlTransform.js`.
- a541a3a78a: Switch to upfront resolution of `swc-loader` in Webpack config.
- cfb3598410: Removed `tsx` and `jsx` as supported extensions in backend packages. For most
  repos, this will not have any effect. But if you inadvertently had added some
  `tsx`/`jsx` files to your backend package, you may now start to see `code: 'MODULE_NOT_FOUND'` errors when launching the backend locally. The reason for
  this is that the offending files get ignored during transpilation. Hence, the
  importing file can no longer find anything to import.

  The fix is to rename any `.tsx` files in your backend packages to `.ts` instead,
  or `.jsx` to `.js`.

- Updated dependencies
  - @backstage/cli-common@0.1.10
  - @backstage/config@1.0.3
  - @backstage/config-loader@1.1.5
  - @backstage/errors@1.1.2
  - @backstage/release-manifests@0.0.6
  - @backstage/types@1.0.0

## 0.20.0-next.2

### Patch Changes

- 2d3a5f09ab: Use `response.json` rather than `response.send` where appropriate, as outlined in `SECURITY.md`
- Updated dependencies
  - @backstage/cli-common@0.1.10
  - @backstage/config@1.0.3-next.2
  - @backstage/config-loader@1.1.5-next.2
  - @backstage/errors@1.1.2-next.2
  - @backstage/release-manifests@0.0.6
  - @backstage/types@1.0.0

## 0.20.0-next.1

### Patch Changes

- 78d5eb299e: Tweak the Jest Caching loader to only operate when in `watch` mode
- Updated dependencies
  - @backstage/cli-common@0.1.10
  - @backstage/config@1.0.3-next.1
  - @backstage/config-loader@1.1.5-next.1
  - @backstage/errors@1.1.2-next.1
  - @backstage/release-manifests@0.0.6
  - @backstage/types@1.0.0

## 0.20.0-next.0

### Minor Changes

- f368ad7279: **BREAKING**: Bumped `jest`, `jest-runtime`, and `jest-environment-jsdom` to v29. This is up from v27, so check out both the [v28](https://jestjs.io/docs/28.x/upgrading-to-jest28) and [v29](https://jestjs.io/docs/upgrading-to-jest29) (later [here](https://jestjs.io/docs/29.x/upgrading-to-jest29)) migration guides.

  Particular changes that where encountered in the main Backstage repo are:

  - The updated snapshot format.
  - `jest.useFakeTimers('legacy')` is now `jest.useFakeTimers({ legacyFakeTimers: true })`.
  - Error objects collected by `withLogCollector` from `@backstage/test-utils` are now objects with a `detail` property rather than a string.

### Patch Changes

- 3e309107ca: Updated fallback versions of dependencies in all templates.
- 292a088807: Added a new `repo test` command.
- ba63cae41c: Updated lockfile parsing to have better support for Yarn 3.
- 2dddb32fea: Switched the Jest transform for YAML files to use a custom one available at `@backstage/cli/config/jestYamlTransform.js`.
- a541a3a78a: Switch to upfront resolution of `swc-loader` in Webpack config.
- cfb3598410: Removed `tsx` and `jsx` as supported extensions in backend packages. For most
  repos, this will not have any effect. But if you inadvertently had added some
  `tsx`/`jsx` files to your backend package, you may now start to see `code: 'MODULE_NOT_FOUND'` errors when launching the backend locally. The reason for
  this is that the offending files get ignored during transpilation. Hence, the
  importing file can no longer find anything to import.

  The fix is to rename any `.tsx` files in your backend packages to `.ts` instead,
  or `.jsx` to `.js`.

- Updated dependencies
  - @backstage/cli-common@0.1.10
  - @backstage/config@1.0.3-next.0
  - @backstage/config-loader@1.1.5-next.0
  - @backstage/errors@1.1.2-next.0
  - @backstage/release-manifests@0.0.6
  - @backstage/types@1.0.0

## 0.19.0

### Minor Changes

- 1fe6823bb5: Updated dependency `eslint-plugin-jest` to `^27.0.0`.

  Note that this major update to the Jest plugin contains some breaking changes.
  This means that some of your tests may start seeing some new lint errors. [Read
  about them
  here](https://github.com/jest-community/eslint-plugin-jest/blob/main/CHANGELOG.md#2700-2022-08-28).

  These are mostly possible to fix automatically. You can try to run `yarn backstage-cli repo lint --fix` in your repo root to have most or all of them
  corrected.

### Patch Changes

- 8d886dd33e: The `create-plugin` and `create` commands have both been deprecated in favor of a new `new` command. The `new` command is functionally identical to `create`, but the new naming makes it possible to use as yarn script, since `yarn create` is reserved.
- cc63eb8611: Sort entries in skeleton.tar.gz for better docker layer caching
- 548053614a: Deprecated the `plugin:diff` command. If you wish to keep running similar checks in your project we recommend using bespoke scripts. A useful utility for such scripts is `@manypkg/get-packages`, which helps you enumerate all packages in a monorepo.
- 513b4dd4ef: The `versions:bump` command will now update dependency ranges in `package.json`, even if the new version is within the current range.
- 221e951298: Added support for custom certificate for webpack dev server.
- 934cc34563: Avoid validating the backend configuration schema when loading static configuration for building the frontend.
- 3d4f5daadf: Remove use of deprecated trimLeft/trimRight
- 817f3196f6: Added a new `migrate react-router-deps` command to aid in the migration to React Router v6 stable.
- 742cb4f3d7: Fix issue when using `.jsx` files inside tests
- e7600bdb04: Tweaked workspace packaging to not rewrite existing `package.json` files.
- 6ae0f6a719: Switch out `sucrase` for `swc` for transpilation.

  `sucrase` is a little more relaxed when it comes to supporting the ways of mocking in `jest`. You might have to make some changes to your tests to meet the `jest` standard and spec if your tests seems to start failing.

  Mocks that look like this are invalid, and they will throw a reference error in line with the `jest` documentation [here on example 3](https://jestjs.io/docs/es6-class-mocks#calling-jestmock-with-the-module-factory-parameter)

  ```ts
  const mockCommandExists = jest.fn();
  jest.mock('command-exists', () => mockCommandExists);
  ```

  You might need to update these mocks to look a little like the following to defer the call to the `jest.fn()` spy until the mock is called.

  ```ts
  const mockCommandExists = jest.fn();
  jest.mock(
    'command-exists',
    () =>
      (...args: any[]) =>
        commandExists(...args),
  );
  ```

  Also, imports are immutable. So it means that you might get some errors when trying to use `jest.spyOn` with starred imports. You might see an error like this:

  ```log
  TypeError: Cannot redefine property: executeFrameHandlerStrategy
          at Function.defineProperty (<anonymous>)

        20 | import { AuthResolverContext } from '../types';
        21 |
      > 22 | const mockFrameHandler = jest.spyOn(
           |                               ^
        23 |   helpers,
        24 |   'executeFrameHandlerStrategy',
        25 | ) as unknown as jest.MockedFunction<
  ```

  This happens when you try to do `import * as something from './something'` and then `jest.spyOn(something, 'test)`. You will need to add a `jest.mock` call to mock out the required starred import to return `jest.fn()` functions from the start. Something like this fixes the above test:

  ```ts
  jest.mock('../../helpers', () => ({
    executeFrameHandlerStrategy: jest.fn(),
  }));
  ```

  You can also remove any occurrence of `hot(App)` and any import of `react-hot-loader` if you're using the that package locally, as all this has now been replaced with [React Refresh](https://www.npmjs.com/package/react-refresh) which you will get out of the box with the new CLI.

  **Note** If you're experiencing difficulties with running tests after the migration, please reach out to us on Discord to see if we can help, or raise an issue. But in the meantime you can switch back to the existing behaviour by using the following config in your root `package.json`.

  ```json
  "jest": {
    "transform": {
      "\\.(js|jsx|ts|tsx|mjs|cjs)$": "@backstage/cli/config/jestSucraseTransform.js",
      "\\.(bmp|gif|jpg|jpeg|png|frag|xml|svg|eot|woff|woff2|ttf)$": "@backstage/cli/config/jestFileTransform.js",
      "\\.(yaml)$": "jest-transform-yaml"
    }
  }
  ```

- 1cb078ad9f: Fixed a misconfiguration where all modules where treated as ESM by the React Refresh plugin for Webpack.
- 1fd4f2746f: Removed internal dependencies on Lerna. It is now no longer necessary to have Lerna installed in a project to use all features of the Backstage CLI.
- 667d917488: Updated dependency `msw` to `^0.47.0`.
- 87ec2ba4d6: Updated dependency `msw` to `^0.46.0`.
- bf5e9030eb: Updated dependency `msw` to `^0.45.0`.
- 33fbd9f9a4: Updated dependency `@types/minimatch` to `^5.0.0`.
- 68c2697077: Added a new `backstage-cli repo clean` command that cleans the repo root and runs the clean script in all packages.
- 7d47def9c4: Added dependency on `@types/jest` v27. The `@types/jest` dependency has also been removed from the plugin template and should be removed from any of your own internal packages. If you wish to override the version of `@types/jest` or `jest`, use Yarn resolutions.
- a7e82c9b01: Updated `versions:bump` command to be compatible with Yarn 3.
- Updated dependencies
  - @backstage/config-loader@1.1.4
  - @backstage/cli-common@0.1.10
  - @backstage/config@1.0.2
  - @backstage/errors@1.1.1
  - @backstage/release-manifests@0.0.6

## 0.19.0-next.3

### Patch Changes

- 7d47def9c4: Added dependency on `@types/jest` v27. The `@types/jest` dependency has also been removed from the plugin template and should be removed from any of your own internal packages. If you wish to override the version of `@types/jest` or `jest`, use Yarn resolutions.
- a7e82c9b01: Updated `versions:bump` command to be compatible with Yarn 3.
- Updated dependencies
  - @backstage/config-loader@1.1.4-next.2
  - @backstage/cli-common@0.1.10-next.0
  - @backstage/config@1.0.2-next.0
  - @backstage/errors@1.1.1-next.0
  - @backstage/release-manifests@0.0.6-next.2

## 0.19.0-next.2

### Patch Changes

- 8d886dd33e: The `create-plugin` and `create` commands have both been deprecated in favor of a new `new` command. The `new` command is functionally identical to `create`, but the new naming makes it possible to use as yarn script, since `yarn create` is reserved.
- 548053614a: Deprecated the `plugin:diff` command. If you wish to keep running similar checks in your project we recommend using bespoke scripts. A useful utility for such scripts is `@manypkg/get-packages`, which helps you enumerate all packages in a monorepo.
- 513b4dd4ef: The `versions:bump` command will now update dependency ranges in `package.json`, even if the new version is within the current range.
- 221e951298: Added support for custom certificate for webpack dev server.
- 934cc34563: Avoid validating the backend configuration schema when loading static configuration for building the frontend.
- 3d4f5daadf: Remove use of deprecated trimLeft/trimRight
- 742cb4f3d7: Fix issue when using `.jsx` files inside tests
- e7600bdb04: Tweaked workspace packaging to not rewrite existing `package.json` files.
- 1cb078ad9f: Fixed a misconfiguration where all modules where treated as ESM by the React Refresh plugin for Webpack.
- 1fd4f2746f: Removed internal dependencies on Lerna. It is now no longer necessary to have Lerna installed in a project to use all features of the Backstage CLI.
- 667d917488: Updated dependency `msw` to `^0.47.0`.
- 87ec2ba4d6: Updated dependency `msw` to `^0.46.0`.
- 68c2697077: Added a new `backstage-cli repo clean` command that cleans the repo root and runs the clean script in all packages.
- Updated dependencies
  - @backstage/config-loader@1.1.4-next.1
  - @backstage/release-manifests@0.0.6-next.1

## 0.19.0-next.1

### Minor Changes

- 1fe6823bb5: Updated dependency `eslint-plugin-jest` to `^27.0.0`.

  Note that this major update to the Jest plugin contains some breaking changes.
  This means that some of your tests may start seeing some new lint errors. [Read
  about them
  here](https://github.com/jest-community/eslint-plugin-jest/blob/main/CHANGELOG.md#2700-2022-08-28).

  These are mostly possible to fix automatically. You can try to run `yarn backstage-cli repo lint --fix` in your repo root to have most or all of them
  corrected.

### Patch Changes

- 817f3196f6: Added a new `migrate react-router-deps` command to aid in the migration to React Router v6 stable.
- 33fbd9f9a4: Updated dependency `@types/minimatch` to `^5.0.0`.

## 0.18.2-next.0

### Patch Changes

- 6ae0f6a719: Switch out `sucrase` for `swc` for transpilation.

  `sucrase` is a little more relaxed when it comes to supporting the ways of mocking in `jest`. You might have to make some changes to your tests to meet the `jest` standard and spec if your tests seems to start failing.

  Mocks that look like this are invalid, and they will throw a reference error in line with the `jest` documentation [here on example 3](https://jestjs.io/docs/es6-class-mocks#calling-jestmock-with-the-module-factory-parameter)

  ```ts
  const mockCommandExists = jest.fn();
  jest.mock('command-exists', () => mockCommandExists);
  ```

  You might need to update these mocks to look a little like the following to defer the call to the `jest.fn()` spy until the mock is called.

  ```ts
  const mockCommandExists = jest.fn();
  jest.mock(
    'command-exists',
    () =>
      (...args: any[]) =>
        commandExists(...args),
  );
  ```

  Also, imports are immutable. So it means that you might get some errors when trying to use `jest.spyOn` with starred imports. You might see an error like this:

  ```log
  TypeError: Cannot redefine property: executeFrameHandlerStrategy
          at Function.defineProperty (<anonymous>)

        20 | import { AuthResolverContext } from '../types';
        21 |
      > 22 | const mockFrameHandler = jest.spyOn(
           |                               ^
        23 |   helpers,
        24 |   'executeFrameHandlerStrategy',
        25 | ) as unknown as jest.MockedFunction<
  ```

  This happens when you try to do `import * as something from './something'` and then `jest.spyOn(something, 'test)`. You will need to add a `jest.mock` call to mock out the required starred import to return `jest.fn()` functions from the start. Something like this fixes the above test:

  ```ts
  jest.mock('../../helpers', () => ({
    executeFrameHandlerStrategy: jest.fn(),
  }));
  ```

  You can also remove any occurrence of `hot(App)` and any import of `react-hot-loader` if you're using the that package locally, as all this has now been replaced with [React Refresh](https://www.npmjs.com/package/react-refresh) which you will get out of the box with the new CLI.

  **Note** If you're experiencing difficulties with running tests after the migration, please reach out to us on Discord to see if we can help, or raise an issue. But in the meantime you can switch back to the existing behaviour by using the following config in your root `package.json`.

  ```json
  "jest": {
    "transform": {
      "\\.(js|jsx|ts|tsx|mjs|cjs)$": "@backstage/cli/config/jestSucraseTransform.js",
      "\\.(bmp|gif|jpg|jpeg|png|frag|xml|svg|eot|woff|woff2|ttf)$": "@backstage/cli/config/jestFileTransform.js",
      "\\.(yaml)$": "jest-transform-yaml"
    }
  }
  ```

- bf5e9030eb: Updated dependency `msw` to `^0.45.0`.
- Updated dependencies
  - @backstage/config-loader@1.1.4-next.0
  - @backstage/release-manifests@0.0.6-next.0

## 0.18.1

### Patch Changes

- d45bbfeb69: Linting is now ignored for any `.eslintrc.*` files, not just `.eslintrc.js`.
- 72c228fdb8: Fixed a bug where `NODE_ENV` was not set in the environment when starting the backend in development mode. It has always been the case that Webpack transformed `NODE_ENV` when running in development mode, but this did not affect dependencies in `node_modules` as they are treated as external.
- a539564c0d: Added Backstage version to output of `yarn backstage-cli info` command
- fd68d6f138: Added resolution of `.json` and `.wasm` files to the Webpack configuration in order to match defaults.
- 94155a41e0: Updated dependencies `@svgr/*` to `6.3.x`.

## 0.18.1-next.1

### Patch Changes

- fd68d6f138: Added resolution of `.json` and `.wasm` files to the Webpack configuration in order to match defaults.

## 0.18.1-next.0

### Patch Changes

- a539564c0d: Added Backstage version to output of `yarn backstage-cli info` command
- 94155a41e0: Updated dependencies `@svgr/*` to `6.3.x`.

## 0.18.0

### Minor Changes

- 96a82d9791: **BREAKING**: Removed the following deprecated package commands:

  - `app:build` - Use `package build` instead
  - `app:serve` - Use `package start` instead
  - `backend:build` - Use `package build` instead
  - `backend:bundle` - Use `package build` instead
  - `backend:dev` - Use `package start` instead
  - `plugin:build` - Use `package build` instead
  - `plugin:serve` - Use `package start` instead
  - `build` - Use `package build` instead
  - `lint` - Use `package lint` instead
  - `prepack` - Use `package prepack` instead
  - `postpack` - Use `package postpack` instead

  In order to replace these you need to have [migrated to using package roles](https://backstage.io/docs/tutorials/package-role-migration).

### Patch Changes

- 86640214f0: Upgrade `@rollup/plugin-node-resolve` to `^13.0.6`
- d2256c0384: Fix `webpack-dev-server` deprecations.
- a70869e775: Updated dependency `msw` to `^0.43.0`.
- 72622d9143: Updated dependency `yaml` to `^2.0.0`.
- e661242844: Updated dependency `run-script-webpack-plugin` to `^0.1.0`.
- 8006d0f9bf: Updated dependency `msw` to `^0.44.0`.
- e8ed804d4f: Updated dependency `@spotify/prettier-config` to `^14.0.0`.
  Updated dependency `@spotify/eslint-config-base` to `^14.0.0`.
  Updated dependency `@spotify/eslint-config-react` to `^14.0.0`.
  Updated dependency `@spotify/eslint-config-typescript` to `^14.0.0`.
- e662b573cf: Updated dependency `@octokit/request` to `^6.0.0`.
- f6b6fb7165: The `test` command now ensures that all IO is flushed before exiting when printing `--help`.
- Updated dependencies
  - @backstage/config-loader@1.1.3
  - @backstage/release-manifests@0.0.5
  - @backstage/errors@1.1.0

## 0.18.0-next.3

### Patch Changes

- a70869e775: Updated dependency `msw` to `^0.43.0`.
- 72622d9143: Updated dependency `yaml` to `^2.0.0`.
- e662b573cf: Updated dependency `@octokit/request` to `^6.0.0`.
- Updated dependencies
  - @backstage/config-loader@1.1.3-next.1
  - @backstage/release-manifests@0.0.5-next.0

## 0.18.0-next.2

### Patch Changes

- f6b6fb7165: The `test` command now ensures that all IO is flushed before exiting when printing `--help`.

## 0.18.0-next.1

### Minor Changes

- 96a82d9791: **BREAKING**: Removed the following deprecated package commands:

  - `app:build` - Use `package build` instead
  - `app:serve` - Use `package start` instead
  - `backend:build` - Use `package build` instead
  - `backend:bundle` - Use `package build` instead
  - `backend:dev` - Use `package start` instead
  - `plugin:build` - Use `package build` instead
  - `plugin:serve` - Use `package start` instead
  - `build` - Use `package build` instead
  - `lint` - Use `package lint` instead
  - `prepack` - Use `package prepack` instead
  - `postpack` - Use `package postpack` instead

  In order to replace these you need to have [migrated to using package roles](https://backstage.io/docs/tutorials/package-role-migration).

### Patch Changes

- 86640214f0: Upgrade `@rollup/plugin-node-resolve` to `^13.0.6`
- e661242844: Updated dependency `run-script-webpack-plugin` to `^0.1.0`.
- Updated dependencies
  - @backstage/errors@1.1.0-next.0
  - @backstage/config-loader@1.1.3-next.0

## 0.17.3-next.0

### Patch Changes

- d2256c0384: Fix `webpack-dev-server` deprecations.

## 0.17.2

### Patch Changes

- 026cfe525a: Fix the public path configuration of the frontend app build so that a trailing `/` is always appended when needed.
- 4f73352608: Updated Lockfile to support new versions of yarn as well as the legacy 1 version
- b8970b8941: Improved the `create-github-app` permissions selection prompt by converting it into a multi-select with clearer descriptions. The `members` permission is now also included in the list which is required for ingesting user data into the catalog.
- bd58365d09: Updated dependency `run-script-webpack-plugin` to `^0.0.14`.
- 9002ebd76b: Updated dependency `@rollup/plugin-commonjs` to `^22.0.0`.
- 8f7b1835df: Updated dependency `msw` to `^0.41.0`.
- 1a33e8b287: Updated dependency `minimatch` to `5.1.0`.
- 6de866ea74: Added console warning to frontend start when the `app.baseUrl` and `backend.baseUrl` are identical
- Updated dependencies
  - @backstage/config-loader@1.1.2
  - @backstage/release-manifests@0.0.4

## 0.17.2-next.2

### Patch Changes

- 026cfe525a: Fix the public path configuration of the frontend app build so that a trailing `/` is always appended when needed.
- 9002ebd76b: Updated dependency `@rollup/plugin-commonjs` to `^22.0.0`.
- 1a33e8b287: Updated dependency `minimatch` to `5.1.0`.

## 0.17.2-next.1

### Patch Changes

- bd58365d09: Updated dependency `run-script-webpack-plugin` to `^0.0.14`.
- 8f7b1835df: Updated dependency `msw` to `^0.41.0`.
- Updated dependencies
  - @backstage/config-loader@1.1.2-next.0
  - @backstage/release-manifests@0.0.4-next.0

## 0.17.2-next.0

### Patch Changes

- 4f73352608: Updated Lockfile to support new versions of yarn as well as the legacy 1 version
- 6de866ea74: Added console warning to frontend start when the `app.baseUrl` and `backend.baseUrl` are identical

## 0.17.1

### Patch Changes

- 52fb9920ac: Fixed coverage configuration when using `BACKSTAGE_NEXT_TESTS`.
- 6cd1f50ae1: Extended lint rule to prevents imports of stories or tests from production code.
- 97cce67ac7: Add instructions to `create-github-app` command.
- 08e12a3a14: Add package global-agent to support behind a proxy for backstage-cli commands like versions:bump.
- 4d8736eded: Changed Rollup configuration for TypeScript definition plugin to ignore `css`,
  `scss`, `sass`, `svg`, `eot`, `woff`, `woff2` and `ttf` files.
- cfc0f19699: Updated dependency `fs-extra` to `10.1.0`.
- 2737777e02: Added the ability to help a user get started with a new organization
- 344ea56acc: Bump `commander` to version 9.1.0
- 8ab2a8226b: Updated the `create-github-app` command to throw an error if the organization argument is a user or a non existing organization.
- 632be18bbc: Updated `create-github-app` command to prompt for read or write permissions to simplify setup.
- Updated dependencies
  - @backstage/cli-common@0.1.9
  - @backstage/config@1.0.1
  - @backstage/release-manifests@0.0.3
  - @backstage/config-loader@1.1.1

## 0.17.1-next.2

### Patch Changes

- 632be18bbc: Updated `create-github-app` command to prompt for read or write permissions to simplify setup.
- Updated dependencies
  - @backstage/cli-common@0.1.9-next.0
  - @backstage/config@1.0.1-next.0
  - @backstage/release-manifests@0.0.3-next.0
  - @backstage/config-loader@1.1.1-next.1

## 0.17.1-next.1

### Patch Changes

- 52fb9920ac: Fixed coverage configuration when using `BACKSTAGE_NEXT_TESTS`.
- 6cd1f50ae1: Extended lint rule to prevents imports of stories or tests from production code.
- 4d8736eded: Changed Rollup configuration for TypeScript definition plugin to ignore `css`,
  `scss`, `sass`, `svg`, `eot`, `woff`, `woff2` and `ttf` files.
- 2737777e02: Added the ability to help a user get started with a new organization

## 0.17.1-next.0

### Patch Changes

- 97cce67ac7: Add instructions to `create-github-app` command.
- 08e12a3a14: Add package global-agent to support behind a proxy for backstage-cli commands like versions:bump.
- cfc0f19699: Updated dependency `fs-extra` to `10.1.0`.
- 344ea56acc: Bump `commander` to version 9.1.0
- 8ab2a8226b: Updated the `create-github-app` command to throw an error if the organization argument is a user or a non existing organization.
- Updated dependencies
  - @backstage/config-loader@1.1.1-next.0

## 0.17.0

### Minor Changes

- 1f7d4763ab: **BREAKING**: Bump the version range of `jest` from `^26.0.1` to `^27.5.1`. You can find the complete list of breaking changes [here](https://github.com/facebook/jest/releases/tag/v27.0.0).

  We strongly recommend to have completed the [package role migration](https://backstage.io/docs/tutorials/package-role-migration) before upgrading to this version, as the package roles are used to automatically determine the testing environment for each package. If you instead want to set an explicit test environment for each package, you can do so for example in the `"jest"` section in `package.json`. The default test environment for all packages is now `node`, which is also the new Jest default.

  Note that one of the breaking changes of Jest 27 is that the `jsdom` environment no longer includes `setImmediate` and `clearImmediate`, which means you might need to update some of your frontend packages. Another notable change is that `jest.useFakeTimers` now defaults to the `'modern'` implementation, which also mocks microtasks.

### Patch Changes

- e80ecad93c: Bump the `rushstack` api generator libraries to their latest versions
- c54ce828bd: build(deps): bump `eslint-plugin-jest` from 25.3.4 to 26.1.2
- f151dfee5a: build(deps): bump `eslint-webpack-plugin` from 2.6.0 to 3.1.1
- 7e7ba704be: build(deps): bump `@spotify/eslint-config-base` from 12.0.0 to 13.0.0
- ecd72391fb: build(deps): bump `@spotify/eslint-config-typescript`
- 6a341b2d87: build(deps): bump `@spotify/eslint-config-react` from 12.0.0 to 13.0.0
- 3c26b2edb5: build(deps): bump `npm-packlist` from 3.0.0 to 5.0.0
- ed3551b7be: Introduced a new experimental test configuration with a number of changes. It switches the coverage provider from `v8` to the default Babel provider, along with always enabling source maps in the Sucrase transform. It also adds a custom module loader that caches both file transforms and VM script objects across all projects in a test run, which provides a big performance boost when running tests from the project root, increasing speed and reducing memory usage.

  This new configuration is not enabled by default. It is enabled by setting the environment variable `BACKSTAGE_NEXT_TESTS` to a non-empty value.

- 6ad0c45648: Added an experimental `package fix` command which applies automated fixes to the target package. The initial fix that is available is to add missing monorepo dependencies to the target package.
- 5b3079694e: Stop logging "Stopped watcher" when shutting down the development backend.
- f512554910: Updated the plugin template to install version 14 of `@testing-library/user-event`.

  To apply this change to your own project, update the `devDependencies` section in your `package.json` files:

  ```diff
   "devDependencies": {
     ... omitted dev dependencies ...
  -   "@testing-library/user-event": "^13.1.8",
  +   "@testing-library/user-event": "^14.0.0",
      ... omitted dev dependencies ...
   }
  ```

- df7862cfa6: Fixed a bug were the `react-hot-loader` transform was being applied to backend development builds.
- 230ad0826f: Bump to using `@types/node` v16
- c47509e1a0: Implemented changes suggested by Deepsource.io including multiple double non-null assertion operators and unexpected awaits for non-promise values.
- 948a56f401: Added a new experimental `repo list-deprecations` command, which scans the entire project for usage of deprecated APIs.
- 4782f9e925: Fixed misleading log message during frontend plugin creation.
- 0383cd0228: The `versions:*` commands no longer warns about duplicate plugin libraries, such as `@backstage/plugin-catalog-common`.
- Updated dependencies
  - @backstage/config-loader@1.1.0

## 0.17.0-next.3

### Patch Changes

- e80ecad93c: Bump the `rushstack` api generator libraries to their latest versions
- 3c26b2edb5: build(deps): bump `npm-packlist` from 3.0.0 to 5.0.0
- f512554910: Updated the plugin template to install version 14 of `@testing-library/user-event`.

  To apply this change to your own project, update the `devDependencies` section in your `package.json` files:

  ```diff
   "devDependencies": {
     ... omitted dev dependencies ...
  -   "@testing-library/user-event": "^13.1.8",
  +   "@testing-library/user-event": "^14.0.0",
      ... omitted dev dependencies ...
   }
  ```

- df7862cfa6: Fixed a bug were the `react-hot-loader` transform was being applied to backend development builds.
- 230ad0826f: Bump to using `@types/node` v16
- 0383cd0228: The `versions:*` commands no longer warns about duplicate plugin libraries, such as `@backstage/plugin-catalog-common`.
- Updated dependencies
  - @backstage/config-loader@1.1.0-next.1

## 0.17.0-next.2

### Patch Changes

- 6a341b2d87: build(deps): bump `@spotify/eslint-config-react` from 12.0.0 to 13.0.0
- 4782f9e925: Fixed misleading log message during frontend plugin creation.

## 0.17.0-next.1

### Minor Changes

- 1f7d4763ab: **BREAKING**: Bump the version range of `jest` from `^26.0.1` to `^27.5.1`. You can find the complete list of breaking changes [here](https://github.com/facebook/jest/releases/tag/v27.0.0).

  We strongly recommend to have completed the [package role migration](https://backstage.io/docs/tutorials/package-role-migration) before upgrading to this version, as the package roles are used to automatically determine the testing environment for each package. If you instead want to set an explicit test environment for each package, you can do so for example in the `"jest"` section in `package.json`. The default test environment for all packages is now `node`, which is also the new Jest default.

  Note that one of the breaking changes of Jest 27 is that the `jsdom` environment no longer includes `setImmediate` and `clearImmediate`, which means you might need to update some of your frontend packages. Another notable change is that `jest.useFakeTimers` now defaults to the `'modern'` implementation, which also mocks microtasks.

### Patch Changes

- c54ce828bd: build(deps): bump `eslint-plugin-jest` from 25.3.4 to 26.1.2
- f151dfee5a: build(deps): bump `eslint-webpack-plugin` from 2.6.0 to 3.1.1
- 7e7ba704be: build(deps): bump `@spotify/eslint-config-base` from 12.0.0 to 13.0.0
- ecd72391fb: build(deps): bump `@spotify/eslint-config-typescript`
- 5b3079694e: Stop logging "Stopped watcher" when shutting down the development backend.

## 0.16.1-next.0

### Patch Changes

- 6ad0c45648: Added an experimental `package fix` command which applies automated fixes to the target package. The initial fix that is available is to add missing monorepo dependencies to the target package.
- c47509e1a0: Implemented changes suggested by Deepsource.io including multiple double non-null assertion operators and unexpected awaits for non-promise values.
- 948a56f401: Added a new experimental `repo list-deprecations` command, which scans the entire project for usage of deprecated APIs.
- Updated dependencies
  - @backstage/config-loader@1.0.1-next.0

## 0.16.0

### Minor Changes

- 217547ae51: **BREAKING**: The provided Jest configuration now only matches files with a `.test.` infix, rather than any files that is suffixed with `test.<ext>`. In particular this means that files named just `test.ts` will no longer be considered a test file.

### Patch Changes

- 947ae3b40e: Applied the fix from version `0.15.3` of this package, which is part of the `v0.71.1` release of Backstage.
- 19eed0edd9: Fix for `overrides` not being properly forwarded from the extra configuration passed to `@backstage/cli/config/eslint-factory`.
- f24ef7864e: Minor typo fixes
- Updated dependencies
  - @backstage/config-loader@1.0.0
  - @backstage/config@1.0.0
  - @backstage/errors@1.0.0
  - @backstage/types@1.0.0

## 0.15.3

### Patch Changes

- Fixed an issue where the CLI would try and fail to require the `package.json` of other Backstage packages, like `@backstage/dev-utils/package.json`.

## 0.15.2

### Patch Changes

- 2c528506aa: Added `--since <ref>` flag for `repo build` command.`
- 60799cc5be: build(deps-dev): bump `@types/npm-packlist` from 1.1.2 to 3.0.0
- d3d1b82198: chore(deps): bump `minimatch` from 5.0.0 to 5.0.1
- e0a69ba49f: build(deps): bump `fs-extra` from 9.1.0 to 10.0.1
- 44cc7c3b95: Added a new ESLint configuration setup for packages, which utilizes package roles to generate the correct configuration. The new configuration is available at `@backstage/cli/config/eslint-factory`.

  Introduced a new `backstage-cli migrate package-lint-configs` command, which migrates old lint configurations to use `@backstage/cli/config/eslint-factory`.

- b1aacbf96a: Applied the fix from version `0.15.1` of this package, which was part of the `v0.70.1` release of Backstage.
- d2ecde959b: Package roles are now marked as stable and migration is encouraged. Please check out the [migration guide](https://backstage.io/docs/tutorials/package-role-migration).

  The new `package`, `repo`, and `migrate` command categories are now marked as stable.

  Marked all commands that are being replaced by the new `package` and `repo` commands as deprecated.

  The package templates used by the `create` command have all been updated to use package roles.

- f06da37290: The backend development setup now ignores the `"browser"` and `"module"` entry points in `package.json`, and instead always uses `"main"`.
- 6a1fe077ad: Changed the logic for how modules are marked as external in the Rollup build of packages. Rather than only marking dependencies and build-in Node.js modules as external, all non-relative imports are now considered external.
- dc6002a7b9: The `--since` flag of repo commands now silently falls back to using the provided `ref` directly if no merge base is available.
- Updated dependencies
  - @backstage/config-loader@0.9.7

## 0.15.2-next.0

### Patch Changes

- 2c528506aa: Added `--since <ref>` flag for `repo build` command.`
- d3d1b82198: chore(deps): bump `minimatch` from 5.0.0 to 5.0.1
- e0a69ba49f: build(deps): bump `fs-extra` from 9.1.0 to 10.0.1
- 44cc7c3b95: Added a new ESLint configuration setup for packages, which utilizes package roles to generate the correct configuration. The new configuration is available at `@backstage/cli/config/eslint-factory`.

  Introduced a new `backstage-cli migrate package-lint-configs` command, which migrates old lint configurations to use `@backstage/cli/config/eslint-factory`.

- b1aacbf96a: Applied the fix from version `0.15.1` of this package, which was part of the `v0.70.1` release of Backstage.
- d2ecde959b: Package roles are now marked as stable and migration is encouraged. Please check out the [migration guide](https://backstage.io/docs/tutorials/package-role-migration).

  The new `package`, `repo`, and `migrate` command categories are now marked as stable.

  Marked all commands that are being replaced by the new `package` and `repo` commands as deprecated.

  The package templates used by the `create` command have all been updated to use package roles.

- f06da37290: The backend development setup now ignores the `"browser"` and `"module"` entry points in `package.json`, and instead always uses `"main"`.
- 6a1fe077ad: Changed the logic for how modules are marked as external in the Rollup build of packages. Rather than only marking dependencies and build-in Node.js modules as external, all non-relative imports are now considered external.
- dc6002a7b9: The `--since` flag of repo commands now silently falls back to using the provided `ref` directly if no merge base is available.
- Updated dependencies
  - @backstage/config-loader@0.9.7-next.0

## 0.15.1

### Patch Changes

- Fixed an issue where the release stage entry point of packages were not resolved correctly.

## 0.15.0

### Minor Changes

- 8c3f30cb28: **BREAKING**: Removed the deprecated `app.<key>` template variables from the `index.html` templating. These should be replaced by using `config.getString("app.<key>")` instead.

### Patch Changes

- 46a19c599f: The CLI now bundles both version 16 and 17 of the patched `@hot-loader/react-dom` dependency, and selects the appropriate one based on what version of `react-dom` is installed within the app.

## 0.14.1

### Patch Changes

- 5cc7f48400: Fixed a bug in the built-in Jest configuration that prevented it from identifying packages that had migrated to using the new package scripts to run tests.
- 49ae6c9573: chore(deps-dev): bump `@types/rollup-plugin-postcss` from 2.0.1 to 3.1.4
- d64b8d3678: chore(deps): bump `minimatch` from 3.0.4 to 5.0.0
- d2e9d2a34f: chore(deps): bump `@hot-loader/react-dom` from 16.13.0 to 17.0.2
- c2f3a548cf: Fix building of backends with `repo build --all`, where it would previously only work if the build was executed within the backend package.
- 3d7ed5377a: Ignore setupTests and the file inside ./dev folder recursively. Eslint
  can not resolve relative paths as we defined in the rule import/no-extraneous-dependencies, and it does not apply this rule.

  A downside to use a recursive definition would be to checking all `dev` folders, which might not be wanted. Ensure you don't use
  the `dev` folder out of scope (must be used for dev. env. only)

- Updated dependencies
  - @backstage/config-loader@0.9.6

## 0.14.0

### Minor Changes

- 1fc0cd3896: Bumped Webpack and Rollup `svgr` dependencies and updated the AST template for `.icon.svg` modules. This means that SVG icon imports are now using SVGO v2.

### Patch Changes

- 0b74c72987: Added a new experimental and hidden `backstage-cli repo lint` command that can be used to lint all packages in the project, similar to `lerna run lint`.
- 532dae9c4c: The `versions:bump --release next` command is updated to compare the `main` and `next` release manifests and prefer the latest.
- 1ed305728b: Bump `node-fetch` to version 2.6.7 and `cross-fetch` to version 3.1.5
- c77c5c7eb6: Added `backstage.role` to `package.json`
- 22862486de: The `versions:bump` command now filters out `npm_` environment configuration when running `yarn install`. This has the effect of allowing it to consider local configuration files within the repository, which is the behavior that one would expect.
- 22862486de: The `versions:bump` command now also considers the root `package.json` when searching for updates. It has also received updates to its output, including a link the [Backstage upgrade helper](https://backstage.github.io/upgrade-helper) and silenced `yarn install` output.
- 7410e12268: Several changes were made to the new experimental package roles system. Unless you have been experimenting with using this new system, these changes have no affect on your project.

  Renamed the `backstage-cli migrate package-role` command to `backstage-cli migrate package-roles`.

  Updated the package role definitions by renaming `app` to `frontend`, `plugin-frontend` to `frontend-plugin`, `plugin-frontend-module` to `frontend-plugin-module`, `plugin-backend` to `backend-plugin`, and `plugin-backend-module` to `backend-plugin-module`

  The `backstage-cli migrate package-scripts` received several tweaks to make it more accurate. It now tries to maintain existing script arguments, like `--config` parameters for `build` and `start` scripts.

  The `script` command category has been renamed to `package`.

  The `backstage-cli package build` command set an incorrect target directory for `app` and `backend` packages, which has been fixed.

  The `backend:bundle` and `repo build` command for the `backend` role was previously ignoring building of bundled packages that had migrated to use package roles and the standard build script, this has now been fixed.

- c6bbafb516: Updated the default [sucrase](https://github.com/alangpierce/sucrase)-based Jest transform to include source maps if the environment variable `ENABLE_SOURCE_MAPS` is non-empty. This can be used to better support editor test debugging integrations.
- 7410e12268: The `test` command now automatically adds `--passWithNoTests` to the Jest invocation. To revert this behavior, pass `--passWithNoTests=false` or `--no-passWithNoTests`.
- Updated dependencies
  - @backstage/config-loader@0.9.4
  - @backstage/errors@0.2.1
  - @backstage/release-manifests@0.0.2
  - @backstage/cli-common@0.1.7
  - @backstage/config@0.1.14
  - @backstage/types@0.1.2

## 0.13.2

### Patch Changes

- bbbaa8ed61: The `plugin:diff` command no longer validates the existence of any of the files within `dev/` or `src/`.
- eaf67f0578: Introduced initial support for an experimental `backstage.role` field in package.json, as well as experimental and hidden `migrate` and `script` sub-commands. We do not recommend usage of any of these additions yet.
- aeb5c69abb: Introduces a new `--release` parameter to the `backstage-cli versions:bump` command.
  The release can be either a specific version, for example `0.99.1`, or the latest `main` or `next` release.
  The default behavior is to bump to the latest `main` release.
- d59b90852a: The experimental types build enabled by `--experimental-type-build` now runs in a separate worker thread.
- 50a19ff8dd: The file path printed by the default lint formatter is now relative to the repository root, rather than the individual package.
- 63181dee79: Tweaked frontend bundling configuration to avoid leaking declarations into global scope.
- fae2aee878: Removed the `import/no-duplicates` lint rule from the frontend and backend ESLint configurations. This rule is quite expensive to execute and only provides a purely cosmetic benefit, so we opted to remove it from the set of default rules. If you would like to keep this rule you can add it back in your local ESLint configuration:

  ```js
    'import/no-duplicates': 'warn'
  ```

- b906f98119: Rather than calling `yarn pack`, the `build-workspace` and `backend-bundle` commands now move files directly whenever possible. This cuts out several `yarn` invocations and speeds the packing process up by several orders of magnitude.
- d0c71e2aa4: Switched the `lint` command to invoke ESLint directly through its Node.js API rather than spawning a new process.
- d59b90852a: Introduced an experimental and hidden `repo` sub-command, that contains commands that operate on an entire monorepo rather than individual packages.
- Updated dependencies
  - @backstage/release-manifests@0.0.1

## 0.13.2-next.0

### Patch Changes

- bbbaa8ed61: The `plugin:diff` command no longer validates the existence of any of the files within `dev/` or `src/`.
- eaf67f0578: Introduced initial support for an experimental `backstage.role` field in package.json, as well as experimental and hidden `migrate` and `script` sub-commands. We do not recommend usage of any of these additions yet.
- d59b90852a: The experimental types build enabled by `--experimental-type-build` now runs in a separate worker thread.
- 50a19ff8dd: The file path printed by the default lint formatter is now relative to the repository root, rather than the individual package.
- 63181dee79: Tweaked frontend bundling configuration to avoid leaking declarations into global scope.
- fae2aee878: Removed the `import/no-duplicates` lint rule from the frontend and backend ESLint configurations. This rule is quite expensive to execute and only provides a purely cosmetic benefit, so we opted to remove it from the set of default rules. If you would like to keep this rule you can add it back in your local ESLint configuration:

  ```js
    'import/no-duplicates': 'warn'
  ```

- b906f98119: Rather than calling `yarn pack`, the `build-workspace` and `backend-bundle` commands now move files directly whenever possible. This cuts out several `yarn` invocations and speeds the packing process up by several orders of magnitude.
- d0c71e2aa4: Switched the `lint` command to invoke ESLint directly through its Node.js API rather than spawning a new process.
- d59b90852a: Introduced an experimental and hidden `repo` sub-command, that contains commands that operate on an entire monorepo rather than individual packages.

## 0.13.1

### Patch Changes

- 5bd0ce9e62: chore(deps): bump `inquirer` from 7.3.3 to 8.2.0
- 80f510caee: Log warning if unable to parse yarn.lock

## 0.13.1-next.1

### Patch Changes

- 5bd0ce9e62: chore(deps): bump `inquirer` from 7.3.3 to 8.2.0

## 0.13.1-next.0

### Patch Changes

- 80f510caee: Log warning if unable to parse yarn.lock

## 0.13.0

### Minor Changes

- 1ddf6d9d5a: Removes the previously deprecated `remove-plugin` command alongside the `--lax` option to `app:build`.

### Patch Changes

- c372a5032f: chore(deps): bump `jest-transform-yaml` from 0.1.1 to 1.0.0
- 1b4ab0d44c: Updated the dependency warning that is baked into `app:serve` to only warn about packages that are not allowed to have duplicates.
- dc46efa2cc: Switched the `WebpackDevServer` configuration to use client-side detection of the WebSocket protocol.
- 10086f5873: Upgraded `webpack`, `webpack-dev-server`,`fork-ts-checker-webpack-plugin`, `react-dev-utils`, and `react-hot-loader`. Since `ForkTsCheckerWebpackPlugin` no longer runs ESLint, we now include the `ESLintPlugin` from `eslint-webpack-plugin` if the `--check` flag is passed.

## 0.12.0

### Minor Changes

- 08fa6a604a: Removed the `typescript` dependency from the Backstage CLI in order to decouple the TypeScript version in Backstage projects. To keep using a specific TypeScript version, be sure to add an explicit dependency in your root `package.json`:

  ```json
    "dependencies": {
      ...
      "typescript": "~4.5.4",
    }
  ```

  We recommend using a `~` version range since TypeScript releases do not adhere to semver.

  It may be the case that you end up with errors if you upgrade the TypeScript version. This is because there was a change to TypeScript not long ago that defaulted the type of errors caught in `catch` blocks to `unknown`. You can work around this by adding `"useUnknownInCatchVariables": false` to the `"compilerOptions"` in your `tsconfig.json`:

  ```json
    "compilerOptions": {
      ...
      "useUnknownInCatchVariables": false
    }
  ```

  Another option is to use the utilities from `@backstage/errors` to assert the type of errors caught in `catch` blocks:

  ```ts
  import { assertError, isError } from '@backstage/errors';

  try {
    ...
  } catch (error) {
    assertError(error);
    ...
    // OR
    if (isError(error)) {
      ...
    }
  }
  ```

  Yet another issue you might run into when upgrading TypeScript is incompatibilities in the types from `react-use`. The error you would run into looks something like this:

  ```plain
  node_modules/react-use/lib/usePermission.d.ts:1:54 - error TS2304: Cannot find name 'DevicePermissionDescriptor'.

  1 declare type PermissionDesc = PermissionDescriptor | DevicePermissionDescriptor | MidiPermissionDescriptor | PushPermissionDescriptor;
  ```

  If you encounter this error, the simplest fix is to replace full imports of `react-use` with more specific ones. For example, the following:

  ```ts
  import { useAsync } from 'react-use';
  ```

  Would be converted into this:

  ```ts
  import useAsync from 'react-use/lib/useAsync';
  ```

### Patch Changes

- 6e34e2cfbf: Introduce `--deprecated` option to `config:check` to log all deprecated app configuration properties

  ```sh
  $ yarn backstage-cli config:check --lax --deprecated
  config:check --lax --deprecated
  Loaded config from app-config.yaml
  The configuration key 'catalog.processors.githubOrg' of app-config.yaml is deprecated and may be removed soon. Configure a GitHub integration instead.
  ```

- f2fe4d240b: Switched to only apply `@hot-loader/react-dom` [Webpack aliasing](https://github.com/hot-loader/react-dom/tree/master/source#webpack) when using React 16.
- 2a42d573d2: Introduced a new `--experimental-type-build` option to the various package build commands. This option switches the type definition build to be executed using API Extractor rather than a `rollup` plugin. In order for this experimental switch to work, you must also have `@microsoft/api-extractor` installed within your project, as it is an optional peer dependency.

  The biggest difference between the existing mode and the experimental one is that rather than just building a single `dist/index.d.ts` file, API Extractor will output `index.d.ts`, `index.beta.d.ts`, and `index.alpha.d.ts`, all in the `dist` directory. Each of these files will have exports from more unstable release stages stripped, meaning that `index.d.ts` will omit all exports marked with `@alpha` or `@beta`, while `index.beta.d.ts` will omit all exports marked with `@alpha`.

  In addition, the `prepack` command now has support for `alphaTypes` and `betaTypes` fields in the `publishConfig` of `package.json`. These optional fields can be pointed to `dist/types.alpha.d.ts` and `dist/types.beta.d.ts` respectively, which will cause `<name>/alpha` and `<name>/beta` entry points to be generated for the package. See the [`@backstage/catalog-model`](https://github.com/backstage/backstage/blob/master/packages/catalog-model/package.json) package for an example of how this can be used in practice.

- Updated dependencies
  - @backstage/config@0.1.13
  - @backstage/config-loader@0.9.3

## 0.12.0-next.0

### Minor Changes

- 08fa6a604a: Removed the `typescript` dependency from the Backstage CLI in order to decouple the TypeScript version in Backstage projects. To keep using a specific TypeScript version, be sure to add an explicit dependency in your root `package.json`:

  ```json
    "dependencies": {
      ...
      "typescript": "~4.5.4",
    }
  ```

  We recommend using a `~` version range since TypeScript releases do not adhere to semver.

  It may be the case that you end up with errors if you upgrade the TypeScript version. This is because there was a change to TypeScript not long ago that defaulted the type of errors caught in `catch` blocks to `unknown`. You can work around this by adding `"useUnknownInCatchVariables": false` to the `"compilerOptions"` in your `tsconfig.json`:

  ```json
    "compilerOptions": {
      ...
      "useUnknownInCatchVariables": false
    }
  ```

  Another option is to use the utilities from `@backstage/errors` to assert the type of errors caught in `catch` blocks:

  ```ts
  import { assertError, isError } from '@backstage/errors';

  try {
    ...
  } catch (error) {
    assertError(error);
    ...
    // OR
    if (isError(error)) {
      ...
    }
  }
  ```

### Patch Changes

- 6e34e2cfbf: Introduce `--deprecated` option to `config:check` to log all deprecated app configuration properties

  ```sh
  $ yarn backstage-cli config:check --lax --deprecated
  config:check --lax --deprecated
  Loaded config from app-config.yaml
  The configuration key 'catalog.processors.githubOrg' of app-config.yaml is deprecated and may be removed soon. Configure a GitHub integration instead.
  ```

- 2a42d573d2: Introduced a new `--experimental-type-build` option to the various package build commands. This option switches the type definition build to be executed using API Extractor rather than a `rollup` plugin. In order for this experimental switch to work, you must also have `@microsoft/api-extractor` installed within your project, as it is an optional peer dependency.

  The biggest difference between the existing mode and the experimental one is that rather than just building a single `dist/index.d.ts` file, API Extractor will output `index.d.ts`, `index.beta.d.ts`, and `index.alpha.d.ts`, all in the `dist` directory. Each of these files will have exports from more unstable release stages stripped, meaning that `index.d.ts` will omit all exports marked with `@alpha` or `@beta`, while `index.beta.d.ts` will omit all exports marked with `@alpha`.

  In addition, the `prepack` command now has support for `alphaTypes` and `betaTypes` fields in the `publishConfig` of `package.json`. These optional fields can be pointed to `dist/types.alpha.d.ts` and `dist/types.beta.d.ts` respectively, which will cause `<name>/alpha` and `<name>/beta` entry points to be generated for the package. See the [`@backstage/catalog-model`](https://github.com/backstage/backstage/blob/master/packages/catalog-model/package.json) package for an example of how this can be used in practice.

- Updated dependencies
  - @backstage/config@0.1.13-next.0
  - @backstage/config-loader@0.9.3-next.0

## 0.11.0

### Minor Changes

- 14e980acee: ESLint upgraded to version 8 and all it's plugins updated to newest version.

  If you use any custom plugins for ESLint please check compatibility.

  ```diff
  -    "@typescript-eslint/eslint-plugin": "^v4.33.0",
  -    "@typescript-eslint/parser": "^v4.28.3",
  +    "@typescript-eslint/eslint-plugin": "^5.9.0",
  +    "@typescript-eslint/parser": "^5.9.0",
  -    "eslint": "^7.30.0",
  +    "eslint": "^8.6.0",
  -    "eslint-plugin-import": "^2.20.2",
  -    "eslint-plugin-jest": "^24.1.0",
  -    "eslint-plugin-jsx-a11y": "^6.2.1",
  +    "eslint-plugin-import": "^2.25.4",
  +    "eslint-plugin-jest": "^25.3.4",
  +    "eslint-plugin-jsx-a11y": "^6.5.1",
  -    "eslint-plugin-react": "^7.12.4",
  -    "eslint-plugin-react-hooks": "^4.0.0",
  +    "eslint-plugin-react": "^7.28.0",
  +    "eslint-plugin-react-hooks": "^4.3.0",
  ```

  Please consult changelogs from packages if you find any problems.

### Patch Changes

- f302d24d34: Switch Webpack minification to use `esbuild` instead of `terser`.
- bee7082094: Update `config/eslint.js` to forbid imports of `@material-ui/icons/` as well.
- 7946418729: Switched to using `@manypkg/get-packages` to list monorepo packages, which provides better support for different kind of monorepo setups.
- Updated dependencies
  - @backstage/config@0.1.12
  - @backstage/errors@0.2.0
  - @backstage/config-loader@0.9.2

## 0.10.5

### Patch Changes

- 37123b4851: Bump `css-loader` from `5.2.6` to `6.5.1`
- 9534391ae4: Add --pattern option to override matching glob patterns for backstage versioning
- 4ce51ab0f1: Internal refactor of the `react-use` imports to use `react-use/lib/*` instead.

## 0.10.4

### Patch Changes

- 1d26017090: Fix issue with plugin:serve for Plugins not using Lerna monorepo.
- 9c3aaf3512: Bump `@typescript-eslint/eslint-plugin` to `4.33.0`
- 808828e4fa: remove inline CSS from serve_index.html
- 6e4080d31b: Add option to build command for minifying the generated code
- Updated dependencies
  - @backstage/config-loader@0.9.1

## 0.10.3

### Patch Changes

- dfc1110dc4: Added peerPluginDependencies option to experimentalInstallationRecipe for install command to install plugins it depends on.
- 58b0262dd9: Pruned unused dependencies.
- 5fdc8df0e8: The frontend configuration is now available as a `config` global during templating of the `index.html` file. This allows for much more flexibility as the values available during templating is not longer hardcoded to a fixed set of values.

  For example, to access the app title, you would now do the following:

  ```html
  <title><%= config.getString('app.title') %></title>
  ```

  Along with this change, usage of the existing `app.<key>` values has been deprecated and will be removed in a future release. The general pattern for migrating existing usage is to replace `<%= app.<key> %>` with `<%= config.getString('app.<key>') %>`, although in some cases you may need to use for example `config.has('app.<key>')` or `config.getOptionalString('app.<key>')` instead.

  The [`@backstage/create-app` changelog](https://github.com/backstage/backstage/blob/master/packages/create-app/CHANGELOG.md#049) also contains more details how to migrate existing usage.

- Updated dependencies
  - @backstage/config-loader@0.9.0

## 0.10.2

### Patch Changes

- 25dfc2d483: Add support for `.cjs` and `.mjs` extensions in local and dependency modules.

## 0.10.1

### Patch Changes

- 0ebb05eee2: Add cli option to minify the generated code of a plugin or backend package

  ```
  backstage-cli plugin:build --minify
  backstage-cli backend:build --minify
  ```

- cd450844f6: Updated the frontend plugin template to put React dependencies in `peerDependencies` by default, as well as allowing both React v16 and v17. This change can be applied to existing plugins by running `yarn backstage-cli plugin:diff` within the plugin package directory.

## 0.10.0

### Minor Changes

- ea99ef5198: Remove the `backend:build-image` command from the CLI and added more deprecation warnings to other deprecated fields like `--lax` and `remove-plugin`

### Patch Changes

- e7230ef814: Bump react-dev-utils to v12
- 416b68675d: build(dependencies): bump `style-loader` from 1.2.1 to 3.3.1
- Updated dependencies
  - @backstage/config-loader@0.8.1

## 0.9.1

### Patch Changes

- dde216acf4: Switch the default test coverage provider from the jest default one to `'v8'`, which provides much better coverage information when using the default Backstage test setup. This is considered a bug fix as the current coverage information is often very inaccurate.
- 719cc87d2f: Disable ES transforms in tests transformed by the `jestSucraseTransform.js`. This is not considered a breaking change since all code is already transpiled this way in the development setup.
- bab752e2b3: Change default port of backend from 7000 to 7007.

  This is due to the AirPlay Receiver process occupying port 7000 and preventing local Backstage instances on MacOS to start.

  You can change the port back to 7000 or any other value by providing an `app-config.yaml` with the following values:

  ```
  backend:
    listen: 0.0.0.0:7123
    baseUrl: http://localhost:7123
  ```

  More information can be found here: https://backstage.io/docs/conf/writing

- ee055cf6db: Update the default routes to use id instead of title
- Updated dependencies
  - @backstage/errors@0.1.5

## 0.9.0

### Minor Changes

- 25f637f39f: Tweaked style insertion logic to make sure that JSS stylesheets always receive the highest priority.

### Patch Changes

- 677bfc2dd0: Keep backstage.json in sync

  The `versions:bump` script now takes care about updating the `version` property inside `backstage.json` file. The file is created if is not present.

- 8809b6c0dd: Update the json-schema dependency version.
- fdfd2f8a62: remove double config dep
- 1e99c73c75: Update internal usage of `configLoader.loadConfig` that now returns an object instead of an array of configs.
- 6dcfe227a2: Added a scaffolder backend module template for the `create` command.
- 4ca3542fdd: Fixed a bug where calling `backstage-cli backend:bundle --build-dependencies` with no dependencies to be built would cause all monorepo packages to be built instead.
- 867ea81d15: bump `@rollup/plugin-commonjs` from 17.1.0 to 21.0.1
- 16d06f6ac3: Introduces new `backstage-cli create` command to replace `create-plugin` and make space for creating a wider array of things. The create command also adds a new template for creating isomorphic common plugin packages.
- Updated dependencies
  - @backstage/config-loader@0.8.0
  - @backstage/cli-common@0.1.6

## 0.8.2

### Patch Changes

- dd355bca46: Switched to dynamically determining the packages that are unsafe to repack when executing the CLI within the Backstage main repo.
- b393c4d4be: Fixed the `config:check` command that was incorrectly only validating frontend configuration. Also added a `--frontend` flag to the command which maintains that behavior.
- 0611f3b3e2: Reading app config from a remote server
- ec64d9590c: Make `ExitCodeError` call `super` early to avoid compiler warnings
- 8af66229e7: Bumped `@spotify/eslint-config-react` from `v10` to `v12`, dropping support for Node.js v12.
- a197708da9: Bumped `@spotify/eslint-config-typescript` from `v10` to `v12`, dropping support for Node.js v12.
- Updated dependencies
  - @backstage/config-loader@0.7.2

## 0.8.1

### Patch Changes

- f1e96dc5b1: Update usage of msw in default plugin template
- b0dc1fd241: bump `@spotify/eslint-config-base` from 9.0.2 to 12.0.0
- c5bb1df55d: Bump `msw` to `v0.35.0` to resolve [CVE-2021-32796](https://github.com/advisories/GHSA-5fg8-2547-mr8q).
- 10615525f3: Switch to use the json and observable types from `@backstage/types`
- Updated dependencies
  - @backstage/config@0.1.11
  - @backstage/cli-common@0.1.5
  - @backstage/errors@0.1.4
  - @backstage/config-loader@0.7.1

## 0.8.0

### Minor Changes

- b486adb8c6: The Jest configuration that's included with the Backstage CLI has received several changes.

  As a part of migrating to more widespread usage of ESM modules, the default configuration now transforms all source files everywhere, including those within `node_modules`. Due to this change the existing `transformModules` option has been removed and will be ignored. There is also a list of known packages that do not require transforms in the CLI, which will evolve over time. If needed there will also be an option to add packages to this list in the future, but it is not included yet to avoid clutter.

  To counteract the slowdown of the additional transforms that have been introduced, the default configuration has also been reworked to enable caching across different packages. Previously each package in a Backstage monorepo would have its own isolated Jest cache, but it is now shared between packages that have a similar enough Jest configuration.

  Another change that will speed up test execution is that the transformer for `.esm.js` files has been switched. It used to be an ESM transformer based on Babel, but it is also done by sucrase now since it is significantly faster.

  The changes above are not strictly breaking as all tests should still work. It may however cause excessive slowdowns in projects that have configured custom transforms in the `jest` field within `package.json` files. In this case it is either best to consider removing the custom transforms, or overriding the `transformIgnorePatterns` to instead use Jest's default `'/node_modules/'` pattern.

  This change also removes the `@backstage/cli/config/jestEsmTransform.js` transform, which can be replaced by using the `@backstage/cli/config/sucraseEsmTransform.js` transform instead.

### Patch Changes

- 36e67d2f24: Internal updates to apply more strict checks to throw errors.
- Updated dependencies
  - @backstage/config-loader@0.7.0
  - @backstage/errors@0.1.3

## 0.7.16

### Patch Changes

- 53bdc66623: add a --from <location> option to the plugin install command
- 84e24fcdaf: Bump sucrase to version 3.20.2
- 6583c6ac40: Add semicolon in template to make prettier happy
- c6f927d819: Bump mini-css-extract-plugin to v2
- 16f044cb6b: Update default backend ESLint configuration to allow usage of `__dirname` in tests.
- 1ef9e64901: Add an experimental `install <plugin>` command.

  Given a `pluginId`, the command looks for NPM packages matching `@backstage/plugin-{pluginId}` or `backstage-plugin-{pluginId}` or `{pluginId}`. It looks for the `experimentalInstallationRecipe` in their `package.json` for the steps of installation. Detailed documentation and API Spec to follow (and to be decided as well).

## 0.7.15

### Patch Changes

- ae4680b88d: The `create-plugin` command now passes the extension name via the `name` key
  in `createRoutableExtension()` calls in newly created plugins.
- df1242ffe4: Adding `--inspect-brk` as an option when debugging backend for development
- c7f2a2307d: When creating a backend plugin with `--backend` flag, don't add `-backend` if it's already suffixed
- 185fec5c0c: The default jest configuration used by the `test` command now supports yarn workspaces. By running `backstage-cli test` in the root of a monorepo, all packages will now automatically be included in the test suite and it will run just like it does within a package. Each package in the monorepo will still use its own local jest configuration, and only packages that have `backstage-cli test` in the `test` script within `package.json` will be included.
- Updated dependencies
  - @backstage/config-loader@0.6.10
  - @backstage/cli-common@0.1.4

## 0.7.14

### Patch Changes

- 3a8704f16b: Only serve static assets if there is a public folder during `app:serve` and `plugin:serve`. This fixes a common bug that would break `plugin:serve` with an `EBUSY` error.
- 40199b61d6: Configuration schema is now also collected from the root `package.json` if it exists.
- 2a6c393c06: The `create-plugin` command now prefers dependency versions ranges that are already in the lockfile.
- 58f91943ab: Improved ´plugin:diff´ check for the `package.json` `"files"` field.
- 12e074a6e4: Fix duplication checks to stop looking for the old core packages, and to allow some explicitly
- Updated dependencies
  - @backstage/config-loader@0.6.9

## 0.7.13

### Patch Changes

- c0c51c9710: Disabled ECMAScript transforms in app and backend builds in order to reduce bundle size and runtime performance. For the rationale and a full list of syntax that is no longer transformed, see https://github.com/alangpierce/sucrase#transforms. This also enables TypeScripts `useDefineForClassFields` flag by default, which in rare occasions could cause build failures. For instructions on how to mitigate issues due to the flag, see the [TypeScript documentation](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-3-7.html#the-usedefineforclassfields-flag-and-the-declare-property-modifier).
- e9f332a51c: Restrict imports on the form `../../plugins/x/src`
- febddedcb2: Bump `lodash` to remediate `SNYK-JS-LODASH-590103` security vulnerability
- 050797c5b3: Switched the Jest YAML transform from `yaml-jest` to `jest-transform-yaml`, which works with newer versions of Node.js.
- Updated dependencies
  - @backstage/config@0.1.10

## 0.7.12

### Patch Changes

- d835d112fe: replace the deprecated file-loader for fonts with assets module
- 15e324ce60: Set the default TZ (Timezone) env for the test command to be UTC so any date related tests are consistent across timezones.
- 9f1362dcc1: Upgrade `@material-ui/lab` to `4.0.0-alpha.57`.

## 0.7.11

### Patch Changes

- 13895db37: Support importing font files in tests.
  This fixes remaining issues from [#7019](https://github.com/backstage/backstage/pull/7019).
- Updated dependencies
  - @backstage/cli-common@0.1.3
  - @backstage/config-loader@0.6.8
  - @backstage/config@0.1.9

## 0.7.10

### Patch Changes

- 5e803edb8: Added support for importing font files. Imports in CSS via `url()` are supported for the final frontend bundle, but not for packages that are built for publishing. Module imports of fonts files from TypeScript are supported everywhere.
- b5118ff76: Updated dependencies

## 0.7.9

### Patch Changes

- f3bba3d2b: Remove debug logging
- 8ea1e96b3: Fix file path handling in diff commands on Windows.
- 2518aab58: Compensate for error formatting mismatch between Webpack 5 and react-dev-utils
- 1ac2961c3: Reintroduce Node.js shims that were removed in the Webpack 5 migration.
- 8d07a8b03: Add Buffer to `ProvidePlugin` since this is no longer provided in `webpack@5`
- fe506a0cf: Remove Webpack deprecation message when running build.
- 485438a56: Fix `backstage-cli backend:dev` argument passing
- Updated dependencies
  - @backstage/config@0.1.7
  - @backstage/config-loader@0.6.7

## 0.7.8

### Patch Changes

- c4ef9181a: Migrate to using `webpack@5` 🎉

## 0.7.7

### Patch Changes

- 6aa7c3db7: bump node-tar version to the latest
- e9d3983ee: Keep track of filtered configuration values when running frontend in development mode.
- Updated dependencies
  - @backstage/config@0.1.6
  - @backstage/config-loader@0.6.6

## 0.7.6

### Patch Changes

- 9d40fcb1e: - Bumping `material-ui/core` version to at least `4.12.2` as they made some breaking changes in later versions which broke `Pagination` of the `Table`.
  - Switching out `material-table` to `@material-table/core` for support for the later versions of `material-ui/core`
  - This causes a minor API change to `@backstage/core-components` as the interface for `Table` re-exports the `prop` from the underlying `Table` components.
  - `onChangeRowsPerPage` has been renamed to `onRowsPerPageChange`
  - `onChangePage` has been renamed to `onPageChange`
  - Migration guide is here: https://material-table-core.com/docs/breaking-changes

## 0.7.5

### Patch Changes

- 9a96b5da7: chore: bump `eslint` to `7.30.0`

## 0.7.4

### Patch Changes

- ae84b20cf: Revert the upgrade to `fs-extra@10.0.0` as that seemed to have broken all installs inexplicably.
- Updated dependencies
  - @backstage/config-loader@0.6.5

## 0.7.3

### Patch Changes

- a93e60fdc: Updated dependencies
- 55f49fcc7: Update dependencies
- ab5cc376f: Use new `isChildPath` export from `@backstage/cli-common`
- Updated dependencies
  - @backstage/cli-common@0.1.2

## 0.7.2

### Patch Changes

- 953a7e66f: updated plugin template to generate path equals plugin id for the root page
- 04248b8f9: chore: bump `msw` dependency in `create-plugin`
- e3d31b381: Make the `create-github-app` command disable webhooks by default.
- 8f100db75: chore: bump `@typescript-eslint/eslint-plugin` from 4.26.0 to 4.27.0
- 95e572305: chore: bump `del` from 5.1.0 to 6.0.0
- ece2b5dd1: chore: bump `@spotify/eslint-config-typescript` from 9.0.0 to 10.0.0
- 0ec31e596: chore: bump `@rollup/plugin-node-resolve` from 11.2.1 to 13.0.0
- 48c9fcd33: Migrated to use the new `@backstage/core-*` packages rather than `@backstage/core`.

## 0.7.1

### Patch Changes

- 3108ff7bf: Make `yarn dev` in newly created backend plugins respect the `PLUGIN_PORT` environment variable.

  You can achieve the same in your created backend plugins by making sure to properly call the port and CORS methods on your service builder. Typically in a file named `src/service/standaloneServer.ts` inside your backend plugin package, replace the following:

  ```ts
  const service = createServiceBuilder(module)
    .enableCors({ origin: 'http://localhost:3000' })
    .addRouter('/my-plugin', router);
  ```

  With something like the following:

  ```ts
  let service = createServiceBuilder(module)
    .setPort(options.port)
    .addRouter('/my-plugin', router);
  if (options.enableCors) {
    service = service.enableCors({ origin: 'http://localhost:3000' });
  }
  ```

- Updated dependencies
  - @backstage/config-loader@0.6.4

## 0.7.0

### Minor Changes

- 9cd3c533c: Switch from `ts-jest` to `@sucrase/jest-plugin`, improving performance and aligning transpilation with bundling.

  In order to switch back to `ts-jest`, install `ts-jest@^26.4.3` as a dependency in the root of your repo and add the following in the root `package.json`:

  ```json
  "jest": {
    "globals": {
      "ts-jest": {
        "isolatedModules": true
      }
    },
    "transform": {
      "\\.esm\\.js$": "@backstage/cli/config/jestEsmTransform.js",
      "\\.(js|jsx|ts|tsx)$": "ts-jest",
      "\\.(bmp|gif|jpg|jpeg|png|frag|xml|svg)$": "@backstage/cli/config/jestFileTransform.js",
      "\\.(yaml)$": "yaml-jest"
    }
  }
  ```

  Note that this will override the default jest transforms included with the `@backstage/cli`.

  It is possible that some test code needs a small migration as a result of this change, which stems from a difference in how `sucrase` and `ts-jest` transform module re-exports.

  Consider the following code:

  ```ts
  import * as utils from './utils';

  jest.spyOn(utils, 'myUtility').mockReturnValue(3);
  ```

  If the `./utils` import for example refers to an index file that in turn re-exports from `./utils/myUtility`, you would have to change the code to the following to work around the fact that the exported object from `./utils` ends up not having configurable properties, thus breaking `jest.spyOn`.

  ```ts
  import * as utils from './utils/myUtility';

  jest.spyOn(utils, 'myUtility').mockReturnValue(3);
  ```

### Patch Changes

- 7f7443308: Updated dependencies
- 21e8ebef5: Fix error message formatting in the packaging process.

  error.errors can be undefined which will lead to a TypeError, swallowing the actual error message in the process.

  For instance, if you break your tsconfig.json with invalid syntax, backstage-cli will not be able to build anything and it will be very hard to find out why because the underlying error message is hidden behind a TypeError.

## 0.6.14

### Patch Changes

- ee4eb5b40: Adjust the Webpack `devtool` module filename template to correctly resolve via the source maps to the source files.
- 84160313e: Mark the `create-github-app` command as ready for use and reveal it in the command list.
- 7e7c71417: Exclude core packages from package dependency diff.
- e7c5e4b30: Update installation instructions in README.
- 2305ab8fc: chore(deps): bump `@spotify/eslint-config-react` from 9.0.0 to 10.0.0
- 054bcd029: Deprecated the `backend:build-image` command, pointing to the newer `backend:bundle` command.

## 0.6.13

### Patch Changes

- 1cd0cacd9: Add support for transforming yaml files in jest with 'yaml-jest'
- 7a7da5146: Bumped `eslint-config-prettier` to `8.x`.
- 3a181cff1: Bump webpack-node-externals from `2.5.2` to `3.0.0`.
- Updated dependencies [2cf98d279]
- Updated dependencies [438a512eb]
  - @backstage/config-loader@0.6.3

## 0.6.12

### Patch Changes

- 2bfec55a6: Update `fork-ts-checker-webpack-plugin`
- Updated dependencies [290405276]
  - @backstage/config-loader@0.6.2

## 0.6.11

### Patch Changes

- 2cd70e164: Add context for versions:bump on what version it was bumped to. Updated tests for the same.
- 3be844496: chore: bump `ts-node` versions to 9.1.1
- e3fc89df6: update plugins created to use react-use 17.2.4

## 0.6.10

### Patch Changes

- f65adcde7: Fix some transitive dependency warnings in yarn
- fc79a6dd3: Added lax option to backstage-cli app:build command
- d8b81fd28: Bump `json-schema` dependency from `0.2.5` to `0.3.0`.
- Updated dependencies [d8b81fd28]
  - @backstage/config-loader@0.6.1
  - @backstage/config@0.1.5

## 0.6.9

### Patch Changes

- 4e5c94249: Add `config:docs` command that opens up reference documentation for the local configuration schema in a browser.
- 1373f4f12: No longer add newly created plugins to `plugins.ts` in the app, as it is no longer needed.
- 479b29124: Added support for Datadog rum events

## 0.6.8

### Patch Changes

- 60ce64aa2: Disable hot reloading in CI environments.

## 0.6.7

### Patch Changes

- Updated dependencies [82c66b8cd]
  - @backstage/config-loader@0.6.0

## 0.6.6

### Patch Changes

- 598f5bcfb: Lock down the version of webpack-dev-server as it's causing some nasty bugs someplace
- 4d248725e: Make the backend plugin template use the correct latest version of `express-promise-router`

## 0.6.5

### Patch Changes

- 84972540b: Lint storybook files, i.e. `*.stories.*`, as if they were tests.
- Updated dependencies [0434853a5]
  - @backstage/config@0.1.4

## 0.6.4

### Patch Changes

- 5ab5864f6: Add support for most TypeScript 4.1 syntax.

## 0.6.3

### Patch Changes

- 507513fed: Bump `@svgr/webpack` from `5.4.x` to `5.5.x`.
- e37d2de99: Bump `@testing-library/react` in the plugin template from `^10.4.1` to `^11.2.5`. To apply this to an existing plugin, update the dependency in your `package.json`.
- 11c6208fe: Fixed an issue where the `backend:dev` command would get stuck executing the backend process multiple times, causing port conflict issues.
- d4f0a1406: New config command to export the configuration schema. When running backstage-cli with yarn, consider using `yarn --silent backstage-cli config:schema` to get a clean output on `stdout`.
- b93538acc: Fix for type declaration input being required for build even if types aren't being built.
- 8871e7523: Bump `ts-loader` dependency range from `^7.0.4` to `^8.0.17`.

## 0.6.2

### Patch Changes

- e780e119c: Add missing `file-loader` dependency which could cause issues with loading images and other assets.
- 6266ddd11: The `yarn backstage-cli app:diff` has been broken since a couple of months. The command to perform updates `yarn backstage-cli versions:bump` prints change logs which seems to be a good replacement for this command.
- Updated dependencies [a1f5e6545]
  - @backstage/config@0.1.3

## 0.6.1

### Patch Changes

- 257a753ff: Updated transform of `.esm.js` files to be able to handle dynamic imports.
- 9337f509d: Tweak error message in lockfile parsing to include more information.
- 532bc0ec0: Upgrading to lerna@4.0.0.

## 0.6.0

### Minor Changes

- 19fe61c27: We have updated the default `eslint` rules in the `@backstage/cli` package.

  ```diff
  -'@typescript-eslint/no-shadow': 'off',
  -'@typescript-eslint/no-redeclare': 'off',
  +'no-shadow': 'off',
  +'no-redeclare': 'off',
  +'@typescript-eslint/no-shadow': 'error',
  +'@typescript-eslint/no-redeclare': 'error',
  ```

  The rules are documented [here](https://eslint.org/docs/rules/no-shadow) and [here](https://eslint.org/docs/rules/no-redeclare).

  This involved a large number of small changes to the code base. When you compile your own code using the CLI, you may also be
  affected. We consider these rules important, and the primary recommendation is to try to update your code according to the
  documentation above. But those that prefer to not enable the rules, or need time to perform the updates, may update their
  local `.eslintrc.js` file(s) in the repo root and/or in individual plugins as they see fit:

  ```js
  module.exports = {
    // ... other declarations
    rules: {
      '@typescript-eslint/no-shadow': 'off',
      '@typescript-eslint/no-redeclare': 'off',
    },
  };
  ```

  Because of the nature of this change, we're unable to provide a grace period for the update :(

### Patch Changes

- 398e1f83e: Update `create-plugin` template to use the new composability API, by switching to exporting a single routable extension component.
- e9aab60c7: Fixed module resolution of external libraries during backend development. Modules used to be resolved relative to the backend entrypoint, but are now resolved relative to each individual module.
- a08c4b0b0: Add check for outdated/duplicate packages to yarn start
- Updated dependencies [062df71db]
- Updated dependencies [e9aab60c7]
  - @backstage/config-loader@0.5.1

## 0.5.0

### Minor Changes

- 12a56cdfe: We've bumped the `@eslint-typescript` packages to the latest, which now add some additional rules that might cause lint failures.
  The main one which could become an issue is the [no-use-before-define](https://eslint.org/docs/rules/no-use-before-define) rule.

  Every plugin and app has the ability to override these rules if you want to ignore them for now.

  You can reset back to the default behaviour by using the following in your own `.eslint.js`

  ```js
  rules: {
    'no-use-before-define': 'off'
  }
  ```

  Because of the nature of this change, we're unable to provide a grace period for the update :(

### Patch Changes

- ef7957be4: Add `--lax` option to `config:print` and `config:check`, which causes all environment variables to be assumed to be set.
- Updated dependencies [ef7957be4]
- Updated dependencies [ef7957be4]
- Updated dependencies [ef7957be4]
  - @backstage/config-loader@0.5.0

## 0.4.7

### Patch Changes

- b604a9d41: Append `-credentials.yaml` to credentials file generated by `backstage-cli create-github-app` and display warning about sensitive contents.

## 0.4.6

### Patch Changes

- 94fdf4955: Get rid of all usages of @octokit/types, and bump the rest of the octokit dependencies to the latest version
- 08e9893d2: Handle no npm info
- 9cf71f8bf: Added experimental `create-github-app` command.

## 0.4.5

### Patch Changes

- 37a7d26c4: Use consistent file extensions for JS output when building packages.
- 818d45e94: Fix detection of external package child directories
- 0588be01f: Add `backend:bundle` command for bundling a backend package with dependencies into a deployment archive.
- b8abdda57: Add color to output from `versions:bump` in order to make it easier to spot changes. Also highlight possible breaking changes and link to changelogs.
- Updated dependencies [ad5c56fd9]
  - @backstage/config-loader@0.4.1

## 0.4.4

### Patch Changes

- d45efbc9b: Fix typo in .app.listen.port config schema

## 0.4.3

### Patch Changes

- 19554f6d6: Added GitHub Actions for Create React App, and allow better imports of files inside a module when they're exposed using `files` in `package.json`
- 7d72f9b09: Fix for `app.listen.host` configuration not properly overriding listening host.

## 0.4.2

### Patch Changes

- c36a01b4c: Re-enable symlink resolution during bundling, and switch to using a resolve plugin for external linked packages.

## 0.4.1

### Patch Changes

- 06dbe707b: Update experimental backend bundle command to only output archives to `dist/` instead of a full workspace mirror in `dist-workspace/`.
- 011708102: Fixes a big in the bundling logic that caused `node_modules` inside local monorepo packages to be transformed.
- 61897fb2c: Fix config schema for `.app.listen`
- Updated dependencies [e3bd9fc2f]
- Updated dependencies [e3bd9fc2f]
  - @backstage/config@0.1.2

## 0.4.0

### Minor Changes

- 00670a96e: sort product panels and navigation menu by greatest cost
  update tsconfig.json to use ES2020 api

### Patch Changes

- b4488ddb0: Added a type alias for PositionError = GeolocationPositionError
- 4a655c89d: Bump versions of `esbuild` and `rollup-plugin-esbuild`
- 8a16e8af8: Support `.npmrc` when building with private NPM registries
- Updated dependencies [4e7091759]
- Updated dependencies [b4488ddb0]
  - @backstage/config-loader@0.4.0

## 0.3.2

### Patch Changes

- 294295453: Only load config that applies to the target package for frontend build and serve tasks. Also added `--package <name>` flag to scope the config schema used by the `config:print` and `config:check` commands.
- f538e2c56: Make versions:bump install new versions of dependencies that were within the specified range as well as install new versions of transitive @backstage dependencies.
- 8697dea5b: Bump Rollup
- b623cc275: Narrow down the version range of rollup-plugin-esbuild to avoid breaking change in newer version

## 0.3.1

### Patch Changes

- 29a0ccab2: The CLI now detects and transforms linked packages. You can link in external packages by adding them to both the `lerna.json` and `package.json` workspace paths.
- faf311c26: New lint rule to disallow <type> assertions and promote `as` assertions. - @typescript-eslint/consistent-type-assertions
- 31d8b6979: Add experimental backend:bundle command
- 991345969: Add new `versions:check` and `versions:bump` commands to simplify version management and avoid conflicts

## 0.3.0

### Minor Changes

- 1722cb53c: Added support for loading and validating configuration schemas, as well as declaring config visibility through schemas.

  The new `loadConfigSchema` function exported by `@backstage/config-loader` allows for the collection and merging of configuration schemas from all nearby dependencies of the project.

  A configuration schema is declared using the `https://backstage.io/schema/config-v1` JSON Schema meta schema, which is based on draft07. The only difference to the draft07 schema is the custom `visibility` keyword, which is used to indicate whether the given config value should be visible in the frontend or not. The possible values are `frontend`, `backend`, and `secret`, where `backend` is the default. A visibility of `secret` has the same scope at runtime, but it will be treated with more care in certain contexts, and defining both `frontend` and `secret` for the same value in two different schemas will result in an error during schema merging.

  Packages that wish to contribute configuration schema should declare it in a root `"configSchema"` field in `package.json`. The field can either contain an inlined JSON schema, or a relative path to a schema file. Schema files can be in either `.json` or `.d.ts` format.

  TypeScript configuration schema files should export a single `Config` type, for example:

  ```ts
  export interface Config {
    app: {
      /**
       * Frontend root URL
       * @visibility frontend
       */
      baseUrl: string;
    };
  }
  ```

### Patch Changes

- 1722cb53c: Added configuration schema
- 902340451: Support specifying listen host/port for frontend
- Updated dependencies [1722cb53c]
  - @backstage/config-loader@0.3.0

## 0.2.0

### Minor Changes

- 28edd7d29: Create backend plugin through CLI
- 1d0aec70f: Upgrade dependency `esbuild@0.7.7`
- 72f6cda35: Adds a new `BACKSTAGE_CLI_BUILD_PARELLEL` environment variable to control
  parallelism for some build steps.

  This is useful in CI to help avoid out of memory issues when using `terser`. The
  `BACKSTAGE_CLI_BUILD_PARELLEL` environment variable can be set to
  `true | false | [integer]` to override the default behaviour. See
  [terser-webpack-plugin](https://github.com/webpack-contrib/terser-webpack-plugin#parallel)
  for more details.

- 8c2b76e45: **BREAKING CHANGE**

  The existing loading of additional config files like `app-config.development.yaml` using APP_ENV or NODE_ENV has been removed.
  Instead, the CLI and backend process now accept one or more `--config` flags to load config files.

  Without passing any flags, `app-config.yaml` and, if it exists, `app-config.local.yaml` will be loaded.
  If passing any `--config <path>` flags, only those files will be loaded, **NOT** the default `app-config.yaml` one.

  The old behaviour of for example `APP_ENV=development` can be replicated using the following flags:

  ```bash
  --config ../../app-config.yaml --config ../../app-config.development.yaml
  ```

- 8afce088a: Use APP_ENV before NODE_ENV for determining what config to load

### Patch Changes

- 3472c8be7: Add codeowners processor

  - Include ESNext.Promise in TypeScript compilation

- a3840bed2: Upgrade dependency rollup-plugin-typescript2 to ^0.27.3
- cba4e4d97: Including source maps with all packages
- 9a3b3dbf1: Fixed duplicate help output, and print help on invalid command
- 7bbeb049f: Change loadBackendConfig to return the config directly
- Updated dependencies [8c2b76e45]
- Updated dependencies [ce5512bc0]
  - @backstage/config-loader@0.2.0
