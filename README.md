# OpenVan APK Release Portal

Public APK download portal for OpenVan (Renter / Driver / Admin) apps.

## 🌐 Live URL

**https://lamkawaigary.github.io/opensystem/**

Static page hosted on GitHub Pages. Lists all 21 APK releases with direct download
links from `raw.githubusercontent.com`. No login required.

## 📦 APK Categories

| App | Count | Latest |
|---|---|---|
| 🛠️ Admin | 9 | `OpenVanAdmin-20260701-1450-debug.apk` |
| 🚚 Driver | 9 | `OpenVanDriver-20260702-1850-final-privacymask-debug.apk` |
| 📦 Renter | 3 | `OpenVanRenter-20260702-1841-final-phoneblockindependent-debug.apk` |

## 🔧 How it works

1. GitHub Pages serves the static `index.html` from this repo's `main` branch
2. The HTML contains hardcoded GitHub raw URLs for all 21 APK files (built at
   deploy time from the GitHub Contents API — see `apk_index.json`)
3. Visitor clicks "⬇️ 下載" button → browser downloads APK directly from
   `raw.githubusercontent.com` (which has no auth requirement)
4. Zero Firebase / Cloud / Auth / JavaScript module dependencies

## 🆚 Why not Firebase Hosting?

Firebase Hosting required admin SDK authentication for our `populateFiles`
deploy workflow, which started failing when the gcloud token expired. GitHub Pages
is simpler, more reliable, and zero-cost.

## 📝 Adding new APKs

Just upload the APK to this repo:

```bash
cd /path/to/repo
cp /path/to/new.apk apks/driver/
git add apks/driver/new.apk
git commit -m "Add new Driver APK"
git push origin main
```

The next deploy (or a manual re-run of the index generator) will pick up the new
file and add a card to the page.

## 🛠️ Rebuilding the index

The HTML is currently committed as a static file (not generated on every push).
To regenerate after adding new APKs:

```bash
# (Future) regenerate via the build script
./scripts/build-index.sh
```

For now, manually regenerate by running the Python builder in
`/tmp/opensystem-fix/` (one-off script, not part of this repo).

<!-- 2026-07-04T14:06:26Z -->
