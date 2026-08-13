# Kul Lab — UMass Dartmouth

Source for the Kul Lab website, built with [Jekyll](https://jekyllrb.com/) and deployed
to [GitHub Pages](https://docs.github.com/user/project/pages/).

---

## Quick start

### Prerequisites

- Ruby 3.0+ (3.2 recommended; matches the CI image)
- Bundler: `gem install bundler`

### Local preview

```bash
bundle install
bundle exec jekyll serve
```

The site will be live at `http://127.0.0.1:4000/`. Saved file changes auto-rebuild.

---

## Deploying on GitLab Pages

1. **Create a new GitHub project**, push this directory as the initial commit.
2. **Pick the right URL pattern**:
   - For a *user* page (`gkul.github.io`), name the project `gkul.github.io ` and leave `baseurl: ""` in `_config.yml`.
   - For a *project* page (`gkul.github.io/lab-website`), set `baseurl: "/lab-website"` in `_config.yml`.
3. Push to `main`. The pipeline in `.github-ci.yml` builds the site automatically and publishes it.
4. The Pages URL will appear under **Deploy → Pages** in your GitLab project.

To wire up a custom domain (e.g. `lab.cis.umassd.edu`), follow [GitLab's custom-domain docs](https://docs.github.com/user/project/pages/custom_domains_ssl_tls_certification/).

---

## Editing content

Almost all content lives in `_data/*.yml` — you almost never need to touch HTML.

| What                 | File                       |
| -------------------- | -------------------------- |
| News / announcements | `_data/news.yml`           |
| Lab members          | `_data/members.yml`        |
| Alumni               | `_data/alumni.yml`         |
| Publications         | `_data/publications.yml`   |
| Teaching schedule    | `_data/teaching.yml`       |
| Research areas       | `_data/research.yml`       |
| PI info / site title | `_config.yml`              |

### Adding a publication

Open `_data/publications.yml` and add a new entry under the right list (`journal`,
`conference`, `posters`, or `reports`). Mark the PI's name with a trailing `*`:

```yaml
- authors: [Some Student, "Gokhan Kul*", Another Coauthor]
  title: "Your Paper Title"
  url: https://link.to/paper
  venue: ACM Some Conference (SOMECONF)
  details: "City, State"
  year: "2026"
```

### Adding a news item

Add a new entry at the **top** of `_data/news.yml`:

```yaml
- date: Apr 2026
  body: "Brief HTML-allowed description. Use <strong>bold</strong> for emphasis."
```

### Adding a lab member

Add an entry to `_data/members.yml`:

```yaml
- name: Full Name
  initials: FN
  role: Ph.D. Student
  topic: Short description of project or area
  photo: filename.jpg   # optional; place in assets/img/
```

### Updating an alumnus's placement

Edit the `now:` field in `_data/alumni.yml`:

```yaml
- name: Some Alum
  then: "Ph.D., dissertation topic"
  now: "Now: Senior Engineer @ SomeCompany"
```

### Updating bio / contact info

Edit `_config.yml` — `pi:` block holds office, email, GitHub, etc. Page templates read from there.

---

## Items currently flagged `[EDIT]`

These were filled in based on your existing site and co-authored publications — please verify
before going live:

- **Lab members** (`_data/members.yml`) — current students were inferred from recent papers; remove anyone who has graduated and add anyone missing.
- **Alumni placements** (`_data/alumni.yml`) — `now:` fields are blank; fill in current positions.
- **Headshot** — drop a photo at `assets/img/kul.jpg` and uncomment the `<img>` line in `index.html`.
- **Member photos** — drop into `assets/img/` and reference by filename in `_data/members.yml`.
- **Google Scholar ID** — set `pi.scholar` in `_config.yml`.
- **News** — most recent entry is July 2024; add anything from late 2024–2026.

---

## Structure

```
.
├── _config.yml              # site config + PI info
├── _data/                   # all content as YAML
├── _includes/               # head, header, footer, topbar
├── _layouts/                # default + page templates
├── assets/
│   ├── css/style.scss       # main stylesheet (compiled by Jekyll)
│   └── img/                 # photos: drop them here
├── index.html               # home
├── research.html            # Research page
├── members.html             # Lab Members
├── publications.html        # Publications
├── teaching.html            # Teaching
├── news.html                # News
├── contact.html             # Contact
├── .gitlab-ci.yml           # CI pipeline → GitLab Pages
├── Gemfile                  # Ruby deps
└── README.md                # this file
```

---

## License

Content © Gokhan Kul. Stylesheet and templates: feel free to adapt for your own site.
