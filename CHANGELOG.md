## 2.1.2 (June 7, 2026)
  - Added the `.yml` variants (`chart.yml`, `values.yml`) to the Helm icon file associations for consistency with the existing `.yaml` mappings

## 2.1.1 (June 7, 2026)
  - Removed the Kubernetes manifest file associations from the Helm icon (e.g. `kustomization.yaml`, `skaffold.yaml`, `*.k8s.yaml`, `deployment.yaml`, `service.yaml`, …); the Helm icon now applies only to Helm chart files

## 2.1.0 (June 6, 2026)
  - Added a custom YAML icon (bold "YML" lettering) for `yaml`, `yml` (moved off the Configuration icon)
  - Added a Docker icon for `dockerfile`, `*.dockerfile`, `.dockerignore` and `docker-compose` / `compose` files
  - Added a PowerShell icon for `ps1`, `psm1`, `psd1`, `ps1xml`, `pssc`, `psrc` (moved off the Console icon)
  - Added a Razor icon for `cshtml`, `razor` (replacing the generic Parameter icon)
  - Added a Helm icon for Helm charts (`Chart.yaml`, `Chart.lock`, `values.yaml`, `values.schema.json`, `.helmignore`, `.tpl`)
  - Reused the Helm/wheel icon for Kubernetes manifests (`kustomization.yaml`, `skaffold.yaml`, `*.k8s.yaml`, and common kinds like `deployment.yaml`, `service.yaml`, `ingress.yaml`, `configmap.yaml`, …)

## 2.0.1 (June 6, 2026)
  - Added `yaml`, `yml`, `env` and `.env*` / `dockerfile` mappings to the Configuration icon
  - Wired up the Markdown icon for `md`, `markdown`, `mdx`, `mdown`, `mkd`, `mdwn`
  - Added `log`, `nfo` to the Text icon
  - Added extra shells (`zsh`, `fish`, `ksh`) and shell rc files to the Console icon
  - Added more database (`sqlite3`, `db`, `db3`, `s3db`), key (`p12`, `pfx`, `ppk`, `gpg`), certificate (`der`, `p7b`) and archive (`bz2`, `lz`, `lzma`, `z`, `cab`, `iso`, `dmg`) extensions

## 2.0.0 (May 3, 2024)
  - Rewrote package with gulp 5.0 and mjs
  - Added `mjs`, `cjs`, `mts`, `cts` to `js` and `ts` icons 

## 1.6.6 (March 11, 2020)
  - Feature: Adding .csx file extension to CS icon. Thanks [@AdrianWilczynski](https://github.com/AdrianWilczynski)! 
  - Feature: Adding .razor file extension to Parameter icon. Thanks [@AdrianWilczynski](https://github.com/AdrianWilczynski)! 
  
## 1.6.5 (October 5, 2018)
  - Change: Using underscore as prefix for test extension filenames

## 1.6.4 (October 5, 2018)
  - Fix: .fsproj, .vbproj and .vcxproj file extensions. Thanks [@christofferjerrebo](https://github.com/christofferjerrebo)!
  - Change: Prefixing test extension files with 'test' to help debugging icon issues

## 1.6.3 (September 20, 2018)
  - Fix: CSApplication icon is now used for .csproj file extensions instead of file name.

## 1.6.2 (April 20, 2018)
  - Feature: Adding .s file to Assembler icon.

## 1.6.1 (November 11, 2017)
  - Fix: Root folder icons were not showing.

## 1.6.0 (November 10, 2017)
  - Feature: Adding file icons for Assembler, Make, and PDF.
  - Feature: Adding root folder icons for multi-root support.
  - Change: Changed extension logo image to PNG version.

## 1.5.0 (February 27, 2017)
  - Feature: Adding Pug file icon and associating it with .pug extension.
  - Feature: Setting .c file extension to use CFile icon.

## 1.4.0 (February 02, 2017)
  - Feature: Setting TOML file extension to use SettingsFile icon.

## 1.3.0 (January 19, 2017)
  - Feature: Adding Rust icons for "rs" and "rlib" extensions.

## 1.2.0 (January 07, 2017)
  - Feature: Adding WebFolder and WebFolderExpanded icons for "wwwroot" folder.

## 1.1.9 (November 15, 2016)
  - Feature: Adding custom icons for Adobe Illustrator, Indesign, and Photoshop.

## 1.1.8 (November 4, 2016)
  - Change: Improving dark colorful colors to match Visual Studio's rendering.
  - Change: Bringing Office icons in line with high contrast theme.
  - Change: Slight change to JSON icon's small oval for better rendering in VS Code.
  - Change: Updating readme with new images and info.

## 1.1.7 (November 1, 2016)
  - Feature: Adding Microsoft Office icons for popular extensions.

## 1.1.6 (October 29, 2016)
  - Change: Dark colorful colors have been slightly lightened for visibility.

## 1.1.5 (October 27, 2016)
  - Feature: Adding additional VS icons and remapping associations.
  - Change: Visual Studio icon is now using VisualStudioSettingFile_16x.svg.
  - Change: Test extension filenames now just include the extension.

## 1.1.4 (October 25, 2016)
  - Feature: Adding image file icon and associations.

## 1.1.3 (October 24, 2016)
  - Adding ignore file to exclude src, test, and other non-essential files/folders from being included in the extension build.

## 1.1.2 (October 24, 2016)
  - Optimizing SVG logo to remove unnecessary paths.

## 1.1.1 (October 24, 2016)
  - Keeping test files because they don't change.

## 1.1.0 (October 24, 2016)
  - Changing theme name to "Studio Icons"
  - Feature: High Contrast icons for high contrast theme.

## 1.1.0 (October 24, 2016)
  - Changing theme name to "Studio Icons"
  - Feature: High Contrast icons for high contrast theme.

## 1.0.4 (October 21, 2016)
  - Enhancement: Cleaning up build script and refactoring to source .js file.

## 1.0.3 (October 21, 2016)

## 1.0.2 (October 21, 2016)

## 1.0.1 (October 21, 2016)

## 1.0.0 (October 21, 2016)
  - Public release of icon theme.
