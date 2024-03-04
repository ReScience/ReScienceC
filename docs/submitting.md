ReScience C Author guidelines
=============================

## Article types

ReScience C accepts three types of submissions:
 - Replication
 - Reproduction report
 - Letter

There is a fourth type, "editorial", but you have to join the editorial board before you can submit one!

Replication articles start from an already published paper by someone else, re-implement the computational methods from that paper, and use the newly written code to obtain ideally the same results. The article describes the challenges and obstacles encountered, and comments on the agreement of the final results with those from the original publication.

Reproduction reports describe attempts to re-run published code under different conditions, typically on a different computational environment. Examples would be running very old code on a modern computer, or porting code between non-standard computer systems. The report documents the required efforts and its success, which may be partial. The editors will reject submissions of trivial reproduction attempts, such as telling the world that you have successfully executed the examples from an on-line Python tutorial.

A letter is a short article presenting a comment or opinion on the current state of reproducibility and replicability in computational science. It may or may not be accompanied by code.

## Preprint Policy

Authors are welcome to submit their papers to a preprint server ([arXiv](https://arxiv.org/), [bioRxiv](https://www.biorxiv.org/), [SocArXiv](https://socopen.org/), [PsyArXiv](https://psyarxiv.com/) etc.) at any point before, during, or after the submission and review process.

Submission to a preprint server is _not_ considered a previous publication.

## Preparing your submission

A submission to ReScience C consists of two parts:
 - A publicly accessible [git](https://git-scm.com/) repository containing the code.
 - An article documenting your work.
 
The article must use Markdown and must provide a metadata section at the beginning of the article (see below for its required contents). Format metadata using [YAML](https://yaml.org/), a human-friendly data serialization language. The information provided is included in the title and sidebar of the generated PDF. For more details about the Markdown format accepted by the Open Journals publishing infrastructure, as well as an example paper, see below.

The only hard rule for the code is that it may not use or otherwise depend on proprietary software. Reviewers and readers must be able to run the code without buying any licenses or signing any legal agreements.

## Submitting your paper

Submission is as simple as:

- Filling in the [short submission form](https://resciencec.theoj.org/papers/new)
- Waiting for the managing editor to start a pre-review issue over in the ReScience C reviews repository: https://github.com/ReScience/ReScienceC-reviews

Submitted entries are first considered by a member of the editorial board, who may decide to reject the submission (e.g. if it is incomplete or in apporpriate), or assign it to a topic editor who will then proceed to look for reviewers. The reviewers evaluate the code and the accompanying material in continuous interaction with the authors in a GitHub isse. If the reviewers manage to run the code and obtain the same results as the ones advertised in the accompanying material, and if they consider that these results are a replication of the original work, the submission is accepted. If any of the reviewers cannot reproduce the results, the submission is rejected and authors are encouraged to resubmit an improved version.

## Article metadata

### Names

Providing an author name is straight-forward: just set the name attribute. However, sometimes more control over the name is required.

#### Name parts

There are many ways to describe the parts of names; we support the following:

 - given names,
 - surname,
 - dropping particle,
 - non-dropping particle,
 - and suffix.

We use a heuristic to parse names into these components. This parsing may produce the wrong result, in which case it is necessary to provide the relevant parts explicitly.

The respective field names are

 - `given-names` (aliases: `given`, `first`, `firstname`)
 - `surname` (aliases: `family`)
 - `suffix`

The full display name will be constructed from these parts, unless the `name` attribute is given as well.

#### Particles

It’s usually enough to place particles like “van”, “von”, “della”, etc. at the end of the given name or at the beginning of the surname, depending on the details of how the name is used.

 - `dropping-particle`
 - `non-dropping-particle`

> [color=red] What is the difference between a dropping and a non-dropping particle? When do I have to use either one, considering that it's "usually enough" to add particles to the name fields?

#### Literal names

The automatic construction of the full name from parts is geared towards common Western names. It may therefore be necessary sometimes to provide the display name explicitly. This is possible by setting the `literal` field, e.g., `literal: Tachibana Taki`. This feature should only be used as a last resort.

#### Example

```
authors:
  - name: John Doe
    affiliation: '1'

  - given-names: Ludwig
    dropping-particle: van
    surname: Beethoven
    affiliation: '3'

  # not recommended, but common aliases can be used for name parts.
  - given: Louis
    non-dropping-particle: de
    family: Broglie
    affiliation: '4'
```

The name parts can also be collected under the author’s name:

```
authors:
  - name:
      given-names: Kari
      surname: Nordmann
```

> [color=red] BG: Do I understand correctly that the only required metadata is the name of the authors? I am quite surprised... In the past we had the reference of the replicated paper, the link to the repository, to the paper... All of these are not necessary anymore?

## Markdown

Markdown is a lightweight markup language used frequently in software development and online environments. Based on email conventions, it was developed in 2004 by John Gruber and Aaron Swartz. 

### Inline markup

The markup in Markdown should be semantic, not presentations. The table below has some basic examples.

    +---------------------+-------------------------+-----------------------+
    | Markup              | Markdown example        | Rendered output       |
    +:====================+:=======================:+:=====================:+
    | emphasis            | `*this*`                | *this*                |
    +---------------------+-------------------------+-----------------------+
    | strong emphasis     | `**that**`              | **that**              |
    +---------------------+-------------------------+-----------------------+
    | strikeout           | `~~not this~~`          | ~~not this~~          |
    +---------------------+-------------------------+-----------------------+
    | subscript           | `H~2~O`                 | H~2~O                 |
    +---------------------+-------------------------+-----------------------+
    | superscript         | `Ca^2+^`                | Ca^2+^                |
    +---------------------+-------------------------+-----------------------+
    | underline           | `[underline]{.ul}`      | [underline]{.ul}      |
    +---------------------+-------------------------+-----------------------+
    | small caps          | `[Small Caps]{.sc}`     | [Small Caps]{.sc}     |
    +---------------------+-------------------------+-----------------------+
    | inline code         | `` `return 23` ``       | `return 23`           |
    +---------------------+-------------------------+-----------------------+

### Links

Link syntax is `[link description](targetURL)`. E.g., this link to the [Journal of Open Source Software](https://joss.theoj.org/) is written as \
`[Journal of Open Source Software](https://joss.theoj.org/)`.

Open Journal publications are not limited by the constraints of print publications. We encourage authors to use hyperlinks for websites and other external resources. However, the standard scientific practice of citing the relevant publications should be followed regardless.

### Grid Tables

Grid tables are made up of special characters which form the rows and columns, and also change table and style variables.

Complex information can be conveyed by using the following features not found in other table styles:

* spanning columns
* adding footers
* using intra-cellular body elements
* creating multi-row headers

Grid table syntax uses the characters "-", "=", "|", and "+" to represent the table outline:

* Hyphens (-) separate horizontal rows.
* Equals signs (=) produce a header when used to create the row under the header text.
* Equals signs (=) create a footer when used to enclose the last row of the table.
* Vertical bars (|) separate columns and also adjusts the depth of a row. 
* Plus signs (+) indicates a juncture between horizontal and parallel lines.

Note: Inserting a colon (:) at the boundaries of the separator line after the header will change text alignment. If there is no header, insert colons into the top line.

> [color=red] BG: I do not understand what it means that the semicolon will change the text alignement: it will change it in what way?

Sample grid table:

    +-------------------+------------+----------+----------+
    | Header 1          | Header 2   | Header 3 | Header 4 |
    |                   |            |          |          |
    +:=================:+:==========:+:========:+:========:+
    | row 1, column 1   | column 2   | column 3 | column 4 |
    +-------------------+------------+----------+----------+
    | row 2             | cells span columns               |
    +-------------------+------------+---------------------+
    | row 3             | cells      | - body              |
    +-------------------+ span rows  | - elements          |
    | row 4             |            | - here              |
    +===================+============+=====================+
    | Footer                                               |
    +===================+============+=====================+

### Figures and Images

To create a figure, a captioned image must appear by itself in a paragraph. The Markdown syntax for a figure is a link, preceded by an exclamation point (!) and a description.  
Example:  
`![This description will be the figure caption](path/to/image.png)`

In order to create a figure rather than an image, there must be a description included and the figure syntax must be the only element in the paragraph, i.e., it must be surrounded by blank lines.

Images that are larger than the text area are scaled to fit the page. You can give images an explicit height and/or width, e.g. when adding an image as part of a paragraph. The Markdown `![Nyan cat](nyan-cat.png){height="9pt"}` includes the image saved as `nyan-cat.png` while scaling it to a height of 9 pt.

### Citations

Bibliographic data should be collected in a file `paper.bib`; it should be formatted in the BibLaTeX format, although plain BibTeX is acceptable as well. All major citation managers offer to export these formats.

Cite a bibliography entry by referencing its identifier: `[@upper1974]` will create the reference "(Upper 1974)". Omit the brackets when referring to the author as part of a sentence: "For a case study on writer's block, see Upper (1974)." Please refer to the [pandoc manual](https://pandoc.org/MANUAL#extension-citations) for additional features, including page locators, prefixes, suffixes, and suppression of author names in citations.

The full citation will display as

> Upper, D. 1974. "The Unsuccessful Self-Treatment of a Case of \"Writer's Block\"." *Journal of Applied Behavior Analysis* 7 (3): 497. <https://doi.org/10.1901/jaba.1974.7-497a>.

### Mathematical Formulæ

Mark equations and other math content with dollar signs (`$`). Use a single dollar sign (`$`) for math that will appear directly within the text. Use two dollar signs (`$$`) when the formula is to be presented centered and on a separate line, in "display" style. The formula itself must be given using TeX syntax.

To give some examples: When discussing a variable *x* or a short formula like

```eval_rst
.. math::
    \sin \frac{\pi}{2}
```

we would write $x$ and

    $\sin \frac{\pi}{2}$

respectively. However, for more complex formulæ, display style is more appropriate. Writing

    $$\int_{-\infty}^{+\infty} e^{-x^2} \, dx = \sqrt{\pi}$$

will give us

$$\int_{-\infty}^{+\infty} e^{-x^2} \, dx = \sqrt{\pi}$$

### Footnotes

Syntax for footnotes centers around the "caret" character `^`. The symbol is also used as a delimiter for superscript text and thereby mirrors the superscript numbers used to mark a footnote in the final text.

``` markdown
Articles are published under a Creative Commons license[^1].
Software should use an OSI-approved license.

[^1]: An open license that allows reuse.
```

The above example results in the following output:

> ```eval_rst
>
> Articles are published under a Creative Commons license [#f1]_. Software should use an OSI-approved license.
>
> .. rubric:: Footnotes
>
> .. [#f1] An open license that allows reuse.
>
> ```

Note: numbers do not have to be sequential, they will be reordered automatically in the publishing step. In fact, the identifier of a note can be any sequence of characters, like `[^marker]`, but may not contain whitespace characters.


### Blocks

The larger components of a document are called "blocks".

#### Headings

Headings are added with `#` followed by a space, where each additional `#` demotes the heading to a level lower in the hierarchy:

```markdown
# Section

## Subsection

### Subsubsection
```

Please start headings on the first level. The maximum supported level is 5, but paper authors are encouraged to limit themselves to headings of the first two or three levels.

##### Deeper nesting

Fourth- and fifth-level subsections – like this one and the following heading – are supported by the system; however, their use is discouraged. Use lists instead of fourth- and fifth-level headings.


### Lists

Bullet lists and numbered lists, a.k.a. enumerations, offer an additional method to present sequential and hierarchical information.

``` markdown
- apples
- citrus fruits
  - lemons
  - oranges
```

- apples
- citrus fruits
  - lemons
  - oranges

Enumerations start with the number of the first item. Using the the first two [laws of thermodynamics](https://en.wikipedia.org/wiki/Laws_of_thermodynamics) as example,

``` markdown
0. If two systems are each in thermal equilibrium with a third, they are
   also in thermal equilibrium with each other.
1. In a process without transfer of matter, the change in internal
   energy, $\Delta U$, of a thermodynamic system is equal to the energy
   gained as heat, $Q$, less the thermodynamic work, $W$, done by the
   system on its surroundings. $$\Delta U = Q - W$$
```

Rendered:

0. If two systems are each in thermal equilibrium with a third, they are also in thermal equilibrium with each other.
1. In a process without transfer of matter, the change in internal energy, $\Delta U$, of a thermodynamic system is equal to the energy gained as heat, $Q$, less the thermodynamic work, $W$, done by the system on its surroundings. $$\Delta U = Q - W$$

### Internal references

Since Markdown has no default mechanism to handle document internal references, known as “cross-references”, Open Journals supports a limited set of LaTex commands. In brief, elements that were marked with `\label` and can be referenced with `\ref` and `\autoref`.

[Open Journals]: https://theoj.org

    ![View of coastal dunes in a nature reserve on Sylt, an island in
    the North Sea. Sylt (Danish: *Slid*) is Germany's northernmost
    island.](sylt.jpg){#sylt width="100%"}

> [color=red] I don't understand how this example relates to the paragraph above it.

#### Tables and figures

Tables and figures can be referenced if they are given a *label* in the caption. In pure Markdown, this can be done by adding an empty span `[]{label="floatlabel"}` to the caption. LaTeX syntax is supported as well: `\label{floatlabel}`.

Link to a float element, i.e., a table or figure, with `\ref{identifier}` or `\autoref{identifier}`, where `identifier` must be defined in the float's caption. The former command results in just the float's number, while the latter inserts the type and number of the referenced float. E.g., in this document `\autoref{proglangs}` yields "\autoref{proglangs}", while `\ref{proglangs}` gives "\ref{proglangs}".

> [color=red] The two examples make no sense at all to me.

: Comparison of programming languages used in the publishing tool. []{label="proglangs"}

    | Language | Typing          | Garbage Collected | Evaluation | Created |
    |----------|:---------------:|:-----------------:|------------|---------|
    | Haskell  | static, strong  | yes               | non-strict | 1990    |
    | Lua      | dynamic, strong | yes               | strict     | 1993    |
    | C        | static, weak    | no                | strict     | 1972    |

#### Equations

Cross-references to equations work similarly to those for floating elements. The difference is that, since captions are not supported for equations, the label must be included in the equation:

    $$a^n + b^n = c^n \label{fermat}$$

Referencing, however, is identical, with `\autoref{eq:fermat}` resulting in "\autoref{eq:fermat}".

$$a^n + b^n = c^n \label{eq:fermat}$$

Authors who do not wish to include the label directly in the formula can use a Markdown span to add the label:

    [$$a^n + b^n = c^n$$]{label="eq:fermat"}


## Example paper and bibliography

This example `paper.md` is adapted from _Gala: A Python package for galactic dynamics_ by Adrian M. Price-Whelan [http://doi.org/10.21105/joss.00388](http://doi.org/10.21105/joss.00388), published in [The Journal of Open Source Software](https://joss.theoj.org/), which uses the same publishing infrastructure as ReScience C.

For a complete description of available options to describe author names [see here](#names).

```
---
title: 'Gala: A Python package for galactic dynamics'
tags:
  - Python
  - astronomy
  - dynamics
  - galactic dynamics
  - milky way
authors:
  - name: Adrian M. Price-Whelan
    orcid: 0000-0000-0000-0000
    equal-contrib: true
    affiliation: "1, 2" # (Multiple affiliations must be quoted)
  - name: Author Without ORCID
    equal-contrib: true # (This is how you can denote equal contributions between multiple authors)
    affiliation: 2
  - name: Author with no affiliation
    corresponding: true # (This is how to denote the corresponding author)
    affiliation: 3
  - given-names: Ludwig
    dropping-particle: van
    surname: Beethoven
    affiliation: 3
affiliations:
 - name: Lyman Spitzer, Jr. Fellow, Princeton University, USA
   index: 1
 - name: Institution Name, Country
   index: 2
 - name: Independent Researcher, Country
   index: 3
date: 13 August 2017
bibliography: paper.bib

# Optional fields if submitting to a AAS journal too, see this blog post:
# https://blog.joss.theoj.org/2018/12/a-new-collaboration-with-aas-publishing
aas-doi: 10.3847/xxxxx <- update this with the DOI from AAS once you know it.
aas-journal: Astrophysical Journal <- The name of the AAS journal.
---

# Summary

The forces on stars, galaxies, and dark matter under external gravitational
fields lead to the dynamical evolution of structures in the universe. The orbits
of these bodies are therefore key to understanding the formation, history, and
future state of galaxies. The field of "galactic dynamics," which aims to model
the gravitating components of galaxies to study their structure and evolution,
is now well-established, commonly taught, and frequently used in astronomy.
Aside from toy problems and demonstrations, the majority of problems require
efficient numerical tools, many of which require the same base code (e.g., for
performing numerical orbit integration).

# Statement of need

`Gala` is an Astropy-affiliated Python package for galactic dynamics. Python
enables wrapping low-level languages (e.g., C) for speed without losing
flexibility or ease-of-use in the user-interface. The API for `Gala` was
designed to provide a class-based and user-friendly interface to fast (C or
Cython-optimized) implementations of common operations such as gravitational
potential and force evaluation, orbit integration, dynamical transformations,
and chaos indicators for nonlinear dynamics. `Gala` also relies heavily on and
interfaces well with the implementations of physical units and astronomical
coordinate systems in the `Astropy` package [@astropy] (`astropy.units` and
`astropy.coordinates`).

`Gala` was designed to be used by both astronomical researchers and by
students in courses on gravitational dynamics or astronomy. It has already been
used in a number of scientific publications [@Pearson:2017] and has also been
used in graduate courses on Galactic dynamics to, e.g., provide interactive
visualizations of textbook material [@Binney:2008]. The combination of speed,
design, and support for Astropy functionality in `Gala` will enable exciting
scientific explorations of forthcoming data releases from the *Gaia* mission
[@gaia] by students and experts alike.

# Mathematics

Single dollars ($) are required for inline mathematics e.g. $f(x) = e^{\pi/x}$

Double dollars make self-standing equations:

$$\Theta(x) = \left\{\begin{array}{l}
0\textrm{ if } x < 0\cr
1\textrm{ else}
\end{array}\right.$$

You can also use plain \LaTeX for equations
\begin{equation}\label{eq:fourier}
\hat f(\omega) = \int_{-\infty}^{\infty} f(x) e^{i\omega x} dx
\end{equation}
and refer to \autoref{eq:fourier} from text.

# Citations

Citations to entries in paper.bib should be in
[rMarkdown](http://rmarkdown.rstudio.com/authoring_bibliographies_and_citations.html)
format.

If you want to cite a software repository URL (e.g. something on GitHub without a preferred
citation) then you can do it with the example BibTeX entry below for @fidgit.

For a quick reference, the following citation commands can be used:
- `@author:2001`  ->  "Author et al. (2001)"
- `[@author:2001]` -> "(Author et al., 2001)"
- `[@author1:2001; @author2:2001]` -> "(Author1 et al., 2001; Author2 et al., 2002)"

# Figures

Figures can be included like this:
![Caption for example figure.\label{fig:example}](figure.png)
and referenced from text using \autoref{fig:example}.

Figure sizes can be customized by adding an optional second parameter:
![Caption for example figure.](figure.png){ width=20% }

# Acknowledgements

We acknowledge contributions from Brigitta Sipocz, Syrtis Major, and Semyeong
Oh, and support from Kathryn Johnston during the genesis of this project.

# References

```

Example `paper.bib` file:

```
@article{Pearson:2017,
  	url = {http://adsabs.harvard.edu/abs/2017arXiv170304627P},
  	Archiveprefix = {arXiv},
  	Author = {{Pearson}, S. and {Price-Whelan}, A.~M. and {Johnston}, K.~V.},
  	Eprint = {1703.04627},
  	Journal = {ArXiv e-prints},
  	Keywords = {Astrophysics - Astrophysics of Galaxies},
  	Month = mar,
  	Title = {{Gaps in Globular Cluster Streams: Pal 5 and the Galactic Bar}},
  	Year = 2017
}

@book{Binney:2008,
  	url = {http://adsabs.harvard.edu/abs/2008gady.book.....B},
  	Author = {{Binney}, J. and {Tremaine}, S.},
  	Booktitle = {Galactic Dynamics: Second Edition, by James Binney and Scott Tremaine.~ISBN 978-0-691-13026-2 (HB).~Published by Princeton University Press, Princeton, NJ USA, 2008.},
  	Publisher = {Princeton University Press},
  	Title = {{Galactic Dynamics: Second Edition}},
  	Year = 2008
}

@article{gaia,
    author = {{Gaia Collaboration}},
    title = "{The Gaia mission}",
    journal = {Astronomy and Astrophysics},
    archivePrefix = "arXiv",
    eprint = {1609.04153},
    primaryClass = "astro-ph.IM",
    keywords = {space vehicles: instruments, Galaxy: structure, astrometry, parallaxes, proper motions, telescopes},
    year = 2016,
    month = nov,
    volume = 595,
    doi = {10.1051/0004-6361/201629272},
    url = {http://adsabs.harvard.edu/abs/2016A%26A...595A...1G},
}

@article{astropy,
    author = {{Astropy Collaboration}},
    title = "{Astropy: A community Python package for astronomy}",
    journal = {Astronomy and Astrophysics},
    archivePrefix = "arXiv",
    eprint = {1307.6212},
    primaryClass = "astro-ph.IM",
    keywords = {methods: data analysis, methods: miscellaneous, virtual observatory tools},
    year = 2013,
    month = oct,
    volume = 558,
    doi = {10.1051/0004-6361/201322068},
    url = {http://adsabs.harvard.edu/abs/2013A%26A...558A..33A}
}

@misc{fidgit,
  author = {A. M. Smith and K. Thaney and M. Hahnel},
  title = {Fidgit: An ungodly union of GitHub and Figshare},
  year = {2020},
  publisher = {GitHub},
  journal = {GitHub repository},
  url = {https://github.com/arfon/fidgit}
}
```

Note that the paper begins by a metadata section (the enclosing --- lines are mandatory) and ends with a References heading, and the references are built automatically from the content in the `.bib` file. You should enter in-text citations in the paper body following correct [Markdown citation syntax](https://pandoc.org/MANUAL.html#extension-citations).  Also note that the references include full names of venues, e.g., journals and conferences, not abbreviations only understood in the context of a specific discipline.

## Checking that your paper compiles

ReScience C uses Pandoc to compile papers from their Markdown form into a PDF. There are a few different ways you can test that your paper is going to compile properly for ReScience C:

### GitHub Action

> [color=red] Do we have this GitHub Action for ReScience C as well?

If you're using GitHub for your repository, you can use the [Open Journals GitHub Action](https://github.com/marketplace/actions/open-journals-pdf-generator) to automatically compile your paper each time you update your repository.

The PDF is available via the Actions tab in your project and click on the latest workflow run. The zip archive file (including the `paper.pdf`) is listed in the run's Artifacts section.

### Docker

If you have Docker installed on your local machine, you can use the same Docker Image to compile a draft of your paper locally. In the example below, the `paper.md` file is in the `paper` directory. Upon successful execution of the command, the `paper.pdf` file will be created in the same location as the `paper.md` file:

```text
docker run --rm \
    --volume $PWD/paper:/data \
    --user $(id -u):$(id -g) \
    --env JOURNAL=resciencec \
    openjournals/inara
```

### Locally

The materials for the `inara` container image above are themselves open source and available in [its own repository](https://github.com/openjournals/inara). You can clone that repository and run the `inara` script locally with `make` after installing the necessary dependencies, which can be inferred from the [`Dockerfile`](https://github.com/openjournals/inara/blob/main/Dockerfile).


