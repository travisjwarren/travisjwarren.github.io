# travisjwarren.github.io

Source for [travisjwarren.github.io](https://travisjwarren.github.io), the portfolio site of Travis Warren. It's a single page that introduces me and walks through the projects I've built: InjuryIQ, Power Rankings and Demonwiki.

The site is plain [Jekyll](https://jekyllrb.com) published by GitHub Pages. There's no JavaScript, build pipeline or theme gem. GitHub builds and deploys it on every push to `master`.

## How it's organised

| Path | What it holds |
| --- | --- |
| `_config.yml` | Site title, role line, description, and the GitHub and LinkedIn usernames used for the profile links |
| `_data/projects.yml` | Every project on the page: summary, links, stat sheet, "What I built" list and stack |
| `index.html` | The home page. It loops over `_data/projects.yml`, so adding a project needs no HTML |
| `_layouts/default.html` | The page shell: skip link, main content and footer |
| `_includes/head.html` | Meta tags, Open Graph tags, Google Fonts and the stylesheet |
| `_includes/links.html` | The GitHub and LinkedIn links, used in the intro and the footer |
| `css/site.css` | All styles, with light and dark colour schemes defined as custom properties on `:root` |
| `images/` | Project logos referenced from `_data/projects.yml` |
| `404.html` | The not-found page, which also catches the retired CatThree blog addresses |

## Editing content

- **Change a project or add one:** edit `_data/projects.yml`. Each entry takes `name`, `summary`, `links`, `body`, `built`, `stack` and `stats`, plus an optional `logo` (a path under `images/`, shown as a rounded square beside the project name; a square image at least 160px wide keeps it sharp). An odd number of stats is fine, because the last one spans the full row.
- **Change the role line or profile links:** edit `role`, `github_username` or `linkedin_username` in `_config.yml`. Leave `linkedin_username` empty to hide the LinkedIn link.
- **Stat sheet figures** are a snapshot counted from each project's repository in October 2026. Update them by hand when they drift.

## Running it locally

You need Ruby 3.x and Bundler.

```bash
bundle install
bundle exec jekyll serve
```

Then open http://localhost:4000. The site rebuilds when you save a file, so refresh the browser to see the change (or add `--livereload` to refresh it automatically). Changes to `_config.yml` need a restart.

The `Gemfile` uses the `github-pages` gem, which pins the same Jekyll and plugin versions GitHub Pages builds with, so what you see locally matches what deploys. `webrick` is included because Ruby 3 no longer bundles the web server `jekyll serve` needs.

## Deploying

Merge to `master`. GitHub Pages runs its "pages build and deployment" workflow, which you can watch on the repository's Actions tab, and the site updates within a minute or two.
