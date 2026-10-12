# Research CV

English research curriculum vitae for Arthur Danjou. The document layout and
section order are defined in `cv.tex`. Each section has its own editable file in
`content/`. The compiled document is `output/pdf/arthur-danjou-cv.pdf`.

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

## Layout

The presentation is inspired by
[Wassim Bouaziz's research CV](https://wesbz.github.io/assets/pdf/Resume_Wassim_Bouaziz_2026.pdf),
with Times-style typography, navy blue small-cap headings, short horizontal rules,
bold dates aligned to the right and research experience before education.
The header uses Arthur's short GitHub and LinkedIn links.
The first page groups research interests, research experience and education.
The second page presents the manuscript, selected projects and independent
infrastructure project, followed by technical skills and languages.

## Content sources

The CV combines the supplied CV with dates confirmed by Arthur and the following
sources, consulted on 12 October 2026:

- [Research profile](https://arthurdanjou.fr/research). This supplies the doctoral
  topic, supervision team and initial signSGD project.
- [Publications and talks](https://arthurdanjou.fr/publications). This supplies
  the manuscript status. The talk shown on the site is a placeholder, as
  clarified by Arthur, and is excluded from the CV.
- [Skills](https://arthurdanjou.fr/#skills). This supplies the technical skills
  and mathematical foundations. R, TensorFlow and Keras are excluded from the
  skills section at Arthur's request. Historical project descriptions retain
  the tools actually used.
- [M2 internship report](https://m2-internship-report.arthurdanjou.fr/). This
  documents the internship contributions and experimental adaptations.
- [Krum](https://github.com/calicarpa/krum). This supplies the software scope and
  public code link.
- Academic project pages linked directly in the CV.
- Research project pages for Krum and the Byzantine-robust aggregation
  reproduction, linked directly in the CV.
- The ArtNotes note `2.homelab/Homelab 🏠.md` and its linked notes
  `Home Assistant 🏡.md` and `Réseau et IoT 🌐.md`, together with the current
  [ArtLab project page](https://arthurdanjou.fr/projects/artlab). These supply
  the independent infrastructure project. Planned network upgrades are
  excluded. The notes are content sources and are not needed for compilation.
- The current manuscript source in `../krum-paper/main.tex`. This supplies the
  exact working title, author order and academic email address. It is only a
  content source and is not needed to compile the CV.

The PhD is explicitly listed as starting in November 2026. The manuscript is
listed as in preparation for JMLR MLOSS, without claiming submission or
acceptance. The education entries retain the M1 and M2 distinction of the French
degree system. The selected projects cover research software development, paper
reproductions and academic coursework.
Other professional experience is omitted at Arthur's request. The personal
homelab is presented separately in `content/infrastructure.tex`.

After the PhD begins, update its status in `content/education.tex`. Update the
title and status in `content/manuscript.tex` when its bibliographic details are
final.
