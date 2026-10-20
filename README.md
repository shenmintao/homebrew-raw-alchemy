# Homebrew tap for Raw Alchemy Studio

Install the pre-built [Raw Alchemy Studio](https://github.com/shenmintao/Raw-Alchemy)
application on **Apple Silicon with macOS 26 or later**:

```bash
brew tap shenmintao/raw-alchemy
brew install --cask shenmintao/raw-alchemy/raw-alchemy-studio
open -a RawAlchemy
```

This repository contains the Cask, documentation, licence and validation workflow.
Homebrew downloads the DMG from the application's GitHub Releases during
installation. Source code, sample photos, models and release binaries stay in the
application repository.

Homebrew installs `RawAlchemy.app` in Applications with Python bundled. The app
processes photos locally. The current macOS release is not notarized; if macOS
blocks the first launch, follow
[Apple's instructions](https://support.apple.com/102445) to open it through
System Settings > Privacy & Security > Open Anyway.

## Upgrade or uninstall

```bash
brew update
brew upgrade --cask shenmintao/raw-alchemy/raw-alchemy-studio
brew uninstall --cask shenmintao/raw-alchemy/raw-alchemy-studio
```

## Migrate from the application repository

If you used `brew tap shenmintao/raw-alchemy https://github.com/shenmintao/Raw-Alchemy.git`,
replace that large checkout once:

```bash
# Skip the uninstall line if the app is not installed.
brew uninstall --cask shenmintao/raw-alchemy/raw-alchemy-studio
brew untap shenmintao/raw-alchemy
brew tap shenmintao/raw-alchemy
brew install --cask shenmintao/raw-alchemy/raw-alchemy-studio
```

如果之前将应用源码仓库添加为 tap，请按上述步骤迁移。添加这个独立 tap
只需下载安装配置；安装应用时再从 Releases 下载 DMG。

## Maintainers

After publishing a stable macOS release in `shenmintao/Raw-Alchemy`, update
`version` and `sha256` in `Casks/raw-alchemy-studio.rb`. Use the DMG's entry in
that release's `SHA256SUMS.txt`; do not use the checksum of the checksum file.
The URL derives the tag and asset name from `version`. Update the compatibility
Cask in the application repository while its legacy tap remains supported.

Validate on a supported Mac before publishing:

```bash
brew style --cask shenmintao/raw-alchemy/raw-alchemy-studio
brew audit --cask shenmintao/raw-alchemy/raw-alchemy-studio
brew fetch --cask shenmintao/raw-alchemy/raw-alchemy-studio
```

Report application problems in the
[application issue tracker](https://github.com/shenmintao/Raw-Alchemy/issues).
