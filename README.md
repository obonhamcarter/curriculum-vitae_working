![build](https://github.com/gkapfham/curriculum-vitae/workflows/build/badge.svg) ![release](https://github.com/gkapfham/curriculum-vitae/workflows/release/badge.svg)

# curriculum-vitae


This repository contains the curriculum vitae (CV) project of [Oliver Bonham-Carter](https://www.oliverbonhamcarter.com/). This project was both, inspired and stolen, from template code created by [Gregory M. Kapfhammer](https://www.gregorykapfhammer.com/) which used the following packages.

* [moutonf/CV](https://github.com/moutonf/CV)
* [moderncv](https://www.ctan.org/pkg/moderncv)
* [moderntimeline](https://github.com/raphink/moderntimeline)

## Development Environment

The curriculum vitae was originally compiled on an Ubuntu 16.04 LTS workstation
using `pdflatex` and `biber` from an old version of TeXLive. The curriculum
vitae is now compiled on an Arch Linux workstation using `latexmk` from the
TeXLive 2021 distribution. You should be able to compile the CV to a PDF file
using a wide variety of tools and operating systems and versions of TeXLive. If
you are unable to compile the CV with your development tools and your execution
environment, then please open a new issue and I will attempt to resolve your
concerns.

## Creating the Curriculum Vitae

For, clone the repository to your local computer:

```shell
git clone https://github.com/gkapfham/curriculum-vitae.git
```

Now, change into the directory that contains the repository's files and follow
all of the following steps the first time that you compile the CV:

```shell
cd curriculum-vitae
cd bibliography
git submodule init
git submodule update
cd ../
pdflatex cv_obc.tex
biber cv_obc.bcf
pdflatex cv_obc.tex
pdflatex cv_obc.tex
```

Remember, before you compile the CV, make sure that you have the bibliography in
a Git submodule:

```shell
cd bibliography
git submodule init
git submodule update
cd ../
```

As a reminder, you can compile the CV using the following commands:

```shell
pdflatex cv_obc.tex
biber cv_obc.bcf
pdflatex cv_obc.tex
pdflatex cv_obc.tex
```

Alternatively, once you have access to the `bibliography` submodule you can
compile the CV using a single command:

```shell
latexmk -pdf -pvc cv_obc.tex
```

## Releasing a New Version of the Curriculum Vitae

See what tag you are current on for the repository:

```shell
git describe --tags
```

Set a new tag for the release of the document:

```shell
git tag v1.0.0
```

Note that I follow the [Semantic Versioning Standard](https://semver.org/) when
defining the tags for the release of the curriculum vitae.

Push all of the changes and the new tag to GitHub:

```shell
git push -u origin master --tags
```

New releases of the curriculum vitae are now available through the
[releases](https://github.com/gkapfham/curriculum-vitae/releases) section of the
repository. Finally, please note that the automated release of the PDF of the
curriculum vitae works through GitHub Actions and the workflow in the
`.github/workflows/release.yml` file.
