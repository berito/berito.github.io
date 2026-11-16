# berito.github.io

Source of [berito.github.io](https://berito.github.io), my personal website. Built with Jekyll and the [al-folio](https://github.com/alshedivat/al-folio)
theme.

## Requirements

- Docker with Docker Compose, or Ruby 3.3 with Bundler
- Node.js 20, for the format check

## Usage

```bash
docker compose up -d
```

Serves the site at http://localhost:8080 and rebuilds on every change. `docker compose down` stops it.

```bash
bundle install
bundle exec jekyll serve
```

The same without Docker, at http://localhost:4000.

```bash
npm ci
npm run lint:prettier
```

Checks formatting. `npx prettier . --write` fixes it.

## Content

| Path                      | Content                                    |
| ------------------------- | ------------------------------------------ |
| `_pages/about.md`         | Home page                                  |
| `_pages/projects.md`      | Projects page; projects go in `_projects/` |
| `_pages/blog.md`          | Writing page; posts go in `_posts/`        |
| `_pages/teaching.md`      | Teaching page                              |
| `_data/cv.yml`            | CV, rendered on `/cv/` and as the PDF      |
| `_data/socials.yml`       | Profile links                              |
| `_sass/_custom.scss`      | Site colours and fonts                     |
| `assets/img/prof_pic.jpg` | Profile photo                              |

## CV PDF

The PDF is built from `_data/cv.yml` with [RenderCV](https://rendercv.com) by the `Render a CV` workflow on every push that changes it. To build it
locally:

```bash
python3 -m pip install -r requirements.txt
rendercv render _data/cv.yml --settings assets/rendercv/settings.yaml
```

## Deployment

Every push to `main` builds the site and publishes it to the `gh-pages` branch, which GitHub Pages serves.
