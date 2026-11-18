# Failsafe for STVN Lab - Multi MaDa2110 — what to do (about 10 minutes)

The app side is already in (module Licence): after 14 days without the licence server the app looks for
`unlock.lic` in this repository. This folder is ready to become that repository.

1. GitHub → New repository → **public**, name `multi-mada2110-failsafe`, no README. Upload / push the contents of
   this folder, including the hidden `.github` folder.
2. GitHub → Settings → Developer settings → Fine-grained tokens → Generate: only this repository,
   **Contents: Read and write**, longest expiry.
3. Licence server → product `multi-mada2110` → its settings (`product.json` "settings"):
   `"FAILSAFE_REPO": "<your user>/multi-mada2110-failsafe", "FAILSAFE_TOKEN": "github_pat_…", "FAILSAFE_BRANCH": "main"`
   → restart. The product's admin page → Failsafe shows "last still alive" within a minute.
4. Admin page → Failsafe → **Download unlock file** → in the repository: Settings → Secrets and variables → Actions →
   New repository secret `FAILSAFE_UNLOCK` = the whole file. Delete the download.
5. Actions → Licence failsafe → Run workflow (leave "no") → "OK".
6. In the app folder: `bash set-licence-key.sh https://licence.digitalserver.synology.me` — it now also writes the
   failsafe address into the app (it says "Failsafe: the app looks for the unlock at …"). Build.
