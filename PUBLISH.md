# Publish Commands

Run these commands after `gh auth login -h github.com` succeeds.

```bash
cd /private/tmp/DOWNitUP-Desktop-releases

gh repo create DOWNitUP-Desktop-releases \
  --public \
  --source . \
  --remote origin \
  --push \
  --description "DOWNitUP desktop release downloads" \
  --homepage "https://romreviewer.github.io/DOWNitUP-Desktop-releases"

gh release create v1.0.0 \
  /Users/sanchit/Development/MultiplatformProjects/Untitled/DOWNitUP/composeApp/build/compose/binaries/main/dmg/DOWNitUP-1.0.0.dmg \
  DOWNitUP-1.0.0.dmg.sha256 \
  --title "DOWNitUP Desktop v1.0.0" \
  --notes "Initial public macOS desktop DMG. This build is unsigned and not notarized, so macOS may show a Gatekeeper warning."

gh api \
  --method POST \
  /repos/romreviewer/DOWNitUP-Desktop-releases/pages \
  -f source.branch=main \
  -f source.path=/
```

After Pages is enabled, the download page should be available at:

```text
https://romreviewer.github.io/DOWNitUP-Desktop-releases/
```
