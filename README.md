# Neurolight Meeting Notes

MkDocs Material site for hosting markdown documentation on GitHub Pages. **Drop markdown files into `docs/` and push** — GitHub Actions handles the rest.

## Quick Start

1. **Clone** the repo
2. **Add** `.md` files to `docs/`
3. **Push** to `main`
4. Enable **GitHub Pages** in repo settings (once)
5. Done — your site deploys automatically

## Adding New Markdown Files

Place any `.md` file in the `docs/` folder. Navigation is **auto-generated** — no config changes needed.

| File path | Navigation |
|-----------|------------|
| `docs/foo.md` | Top-level: "Foo" |
| `docs/meetings/week1.md` | Under "meetings": "Week1" |
| `docs/guides/setup.md` | Under "guides": "Setup" |

### Tips

- Use `# Your Title` as the first line for the display name (otherwise filename is used)
- Create subfolders to organize content: `docs/meetings/`, `docs/guides/`, etc.
- Within each folder, pages appear in alphabetical order

## Testing Locally

```bash
pip install -r requirements.txt
mkdocs serve
```

If you hit an externally-managed Python error, use a virtual environment:

```bash
python3 -m venv .venv && source .venv/bin/activate  # or: .venv\Scripts\activate on Windows
pip install -r requirements.txt
mkdocs serve
```

Open [http://127.0.0.1:8000](http://127.0.0.1:8000) in your browser.

## Deploying to GitHub Pages

1. **Push** to the `main` branch
2. GitHub Actions builds the site and deploys to `gh-pages`
3. **Enable GitHub Pages** (one-time setup):
   - Go to **Settings** → **Pages**
   - **Source**: Deploy from a branch
   - **Branch**: `gh-pages` / `/(root)`
   - Click Save
4. Site is live at `https://YOUR_USERNAME.github.io/neurolight-meeting-notes/`

## Configuration

Edit `mkdocs.yml` to customize:

- `site_name`, `site_description`
- `repo_url`, `site_url` (replace `YOUR_USERNAME` with your GitHub username)
- Theme colors, features, plugins

## Project Structure

```
.
├── docs/           # Drop .md files here
│   └── index.md    # Home page
├── mkdocs.yml      # MkDocs config (omit nav for auto-discovery)
├── requirements.txt
└── .github/
    └── workflows/
        └── deploy.yml   # Builds and deploys on push to main
```
