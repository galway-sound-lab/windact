# WindACT site: setup guide (about 30 minutes)

## 1. Choose the owner account

Use a **GitHub organisation** (free), for example `galway-sound-lab`, rather than a personal account. Then the site stays with the lab after individual contracts end. First check whether the Sound Lab already has one. Add Eoin as an owner.

## 2. Create the repository

1. GitHub → **New repository** → name `windact` → **Public** → do *not* add a README.
2. Upload the files:
   - **Easy way:** on the empty repo page, click **uploading an existing file** and drag in everything from this folder.
     Hidden files (`.gitignore`, `.zenodo.json`) are easy to miss. On a Mac, press `Cmd+Shift+.` in Finder to show them.
   - **Git way:**
     ```bash
     cd windact
     git init -b main && git add . && git commit -m "Initial site"
     git remote add origin https://github.com/galway-sound-lab/windact.git
     git push -u origin main
     ```

## 3. Fill in the placeholders

Search for `TODO` across the files and replace them:
- `_config.yml`: set `url` to `https://galway-sound-lab.github.io` and fill in `contact_email`
- `galway-sound-lab` in `README.md`, `materials.md` and `CITATION.cff`
- Team names in `about.md`, `CITATION.cff` and `.zenodo.json` (add ORCID iDs if you have them)
- Logo: put the final SVG in `assets/img/` and uncomment the `<img>` line in `_layouts/default.html`. Add the SEAI logo to the **footer strip only**.

## 4. Turn on GitHub Pages

Repo → **Settings → Pages** → Source: **Deploy from a branch** → Branch: `main`, folder `/ (root)` → **Save**.
After 1–2 minutes the site is live at `https://galway-sound-lab.github.io/windact`.

## 5. Connect Zenodo

1. Go to https://zenodo.org → **Log in with GitHub**. If you already have a Zenodo account, link GitHub under Account → Linked accounts.
2. Zenodo → your name (top right) → **GitHub** → **Sync now** → turn on the switch next to `windact`.
3. **Organisation repo only:** GitHub must allow Zenodo to access the organisation.
   GitHub → Settings → Applications → **Authorized OAuth Apps** → Zenodo → **Grant** next to the organisation. An org owner may need to approve the request. If `windact` doesn't appear in Zenodo, this is usually the reason.

## 6. Make the first release, which creates the DOI

1. Repo → **Releases → Draft a new release** → tag `v0.1.0` → title "Website launch" → **Publish release**.
2. After a few minutes, open Zenodo → GitHub. The release appears with a **DOI**.
3. Copy the DOI badge (use the **concept DOI**, which always points to the latest version). Paste it into `README.md` and `index.md`.

Zenodo reads its metadata (title, authors, licence, funder note) from `.zenodo.json`.

## 7. Routine use

- **New release at each milestone**, for example `v0.2.0` when the protocol is shared. Each release gets its own DOI automatically.
- **Datasets:** upload directly to Zenodo (New upload → Dataset). In *Related works*, link the dataset to the GitHub DOI. Then add the dataset DOI to `data.md`. Do not put datasets in GitHub.
- **Never commit** raw audio, locations, survey records or anything personal. `.gitignore` blocks common data formats as a safety net, but it is not a guarantee.
- **News:** add one line at the top of "Latest" in `index.md`.
