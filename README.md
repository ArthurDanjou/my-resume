# Arthur Danjou's research CV

[![Build and deploy PDF](https://github.com/ArthurDanjou/my-resume/actions/workflows/deploy.yml/badge.svg)](https://github.com/ArthurDanjou/my-resume/actions/workflows/deploy.yml)

My English academic CV in applied mathematics and machine learning, written in
LaTeX. The PDF is built with GitHub Actions and published on Cloudflare Pages.

[View the latest CV](https://my-resume-cr9.pages.dev/) · [Personal website](https://arthurdanjou.fr)

## Repository structure

- [`cv.tex`](cv.tex) defines the typography, layout and section order.
- [`content/`](content/) contains separate files for the header, research
  interests, research experience, education, manuscript, projects, infrastructure
  and skills.
- [`output/pdf/arthur-danjou-cv.pdf`](output/pdf/arthur-danjou-cv.pdf) is the
  checked-in PDF. The online version is rebuilt from the source on each push.
- [`.github/workflows/deploy.yml`](.github/workflows/deploy.yml) builds and
  deploys the PDF.
- [`site/_redirects`](site/_redirects) serves the PDF at the site's root URL.

## Edit the CV

Update the relevant file in `content/`. Change styling or reorder sections in
`cv.tex`. Keep the PhD and manuscript entries current in
`content/education.tex` and `content/manuscript.tex`.

## Build

Requires a LaTeX distribution with pdfLaTeX and latexmk, such as TeX Live or
MacTeX. All packages used by the CV are included in a full TeX Live installation.

```sh
mkdir -p build output/pdf
latexmk -pdf -interaction=nonstopmode -halt-on-error -outdir=build cv.tex
cp build/cv.pdf output/pdf/arthur-danjou-cv.pdf
```

For Overleaf, upload `cv.tex` and the `content/` directory, then select pdfLaTeX.
The document does not require a bibliography, external fonts, images or Git
submodules.

## Deployment

The workflow `.github/workflows/deploy.yml` compiles `cv.tex` on every push to
`master` and can also be started manually. It installs the required TeX Live
2026 packages, caches build files in `build/` and deploys the PDF to the
Cloudflare Pages project `my-resume`.

The latest PDF is available at [my-resume-cr9.pages.dev](https://my-resume-cr9.pages.dev/)
and at `/arthur-danjou-cv.pdf`. The rule in `site/_redirects` also serves that
PDF at `/`.

Configure the following GitHub Actions repository secrets:

- `CLOUDFLARE_ACCOUNT_ID`. Use the account containing the `my-resume` project.
- `CLOUDFLARE_API_TOKEN`. Use an API token with Cloudflare Pages edit permission
  for that account.

For manual project creation and deployment, use an authenticated Wrangler CLI:

```sh
wrangler pages project create my-resume --production-branch=master --force
mkdir -p public
cp build/cv.pdf public/arthur-danjou-cv.pdf
cp site/_redirects public/_redirects
wrangler pages deploy public --project-name=my-resume --branch=master
```

The Pages project must exist before the workflow's first deployment. GitHub
Actions secrets from other repositories are not inherited by this repository.

## Layout

The presentation is inspired by
[Wassim Bouaziz's research CV](https://wesbz.github.io/assets/pdf/Resume_Wassim_Bouaziz_2026.pdf),
with Times-style typography, navy blue small-cap headings, short horizontal rules,
bold dates aligned to the right and research experience before education.
The header uses Arthur's short GitHub and LinkedIn links.
The first page groups research interests, research experience and education.
The second page presents the manuscript, selected projects and independent
infrastructure project, followed by technical skills and languages.

## Related work

- [Research profile](https://arthurdanjou.fr/research).
- [Publications](https://arthurdanjou.fr/publications).
- [Skills](https://arthurdanjou.fr/#skills).
- [M2 internship report](https://m2-internship-report.arthurdanjou.fr/).
- [Krum](https://github.com/calicarpa/krum), the Byzantine-resilient distributed
  learning library developed during my research internship.
- [ArtLab](https://arthurdanjou.fr/projects/artlab), my personal homelab.

Individual project pages are linked directly in the CV.
