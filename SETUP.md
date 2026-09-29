# Setup

1. Create a **public** repository named exactly `nicemondominic`.
2. Copy the contents of this package into the repository root.
3. Commit and push to `main`.
4. In GitHub: **Settings → Actions → General → Workflow permissions → Read and write permissions**.
5. Open **Actions → Update profile art → Run workflow** once.
6. The workflow will refresh `data/contributions.json` and `contrib-heatmap.svg` daily.

## Regenerating the portrait

The original photo is intentionally not included in the public package.

Put a copy at `assets/source-photo.jpg`, then:

```bash
python -m venv .venv
# Windows
.venv\Scripts\activate
# macOS/Linux
source .venv/bin/activate

pip install -r scripts/requirements.txt
python scripts/prep_photo.py assets/source-photo.jpg
python scripts/make_ascii_svg.py
```

The checked-in `nicemon-ascii.svg` already contains the portrait generated from your uploaded image, so you can publish the profile without exposing the original photo.

## Notes

The contribution SVG starts with a visual placeholder. The first successful GitHub Action run replaces it with the live public contribution calendar.

No GitHub personal access token is stored in this workflow.
