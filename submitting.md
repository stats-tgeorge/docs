Submitting a paper to JOSS
==========================

If you've already developed a fully featured research code, released it under an [OSI-approved license](https://opensource.org/licenses), and written good documentation and tests, then we expect that it should take perhaps an hour or two to prepare and submit your paper to JOSS.
But please read these instructions carefully for a streamlined submission.

## Submission requirements

- The software should be open source as per the [OSI definition](https://opensource.org/osd).
- The software should have an **obvious** research application.
- You should be a major contributor to the software you are submitting.
- The software should be a significant contribution to the available open source software that either enables some new research challenges to be addressed or makes addressing research challenges significantly better (e.g., faster, easier, simpler).
- The software should be feature-complete (no half-baked solutions) and designed for maintainable extension (not one-off modifications). **Minor ‘utility’ packages, including ‘thin’ API clients, are not acceptable**.
- Your paper (`paper.md` and BibTeX files, plus any figures) must be hosted in a Git-based repository, ideally together with your software.

In addition, the software associated with your submission must:

- Be stored in a repository that can be cloned without registration.
- Be stored in a repository that is browsable online without registration.
- Have an issue tracker that is readable without registration.
- Permit individuals to create issues/file tickets against your repository.

JOSS publishes articles about research software. This definition includes software that: solves complex modeling problems in a scientific context (physics, mathematics, biology, medicine, social science, neuroscience, engineering); supports the functioning of research instruments or the execution of research experiments; extracts knowledge from large data sets; offers a mathematical library, or similar.

## Typical paper submission flow

Before you submit, you should:

- Make your software available in an open repository (GitHub, Bitbucket, etc.) and include an [OSI approved open source license](https://opensource.org/licenses).
- Make sure that the software complies with the [JOSS review criteria](review_criteria.html). In particular, your software should be full-featured, well-documented, and contain procedures (such as automated tests) for checking correctness.
- Write a short paper in Markdown format using `paper.md` as file name, including a title, summary, author names, affiliations, and key references. See our [example paper](#example-paper-and-bibliography) to follow the correct format.
- (Optional) create a metadata file describing your software and include it in your repository. We provide [a script](https://gist.github.com/arfon/478b2ed49e11f984d6fb) that automates the generation of this metadata.

## What should my paper contain?

```eval_rst
.. important:: Begin your paper with a summary of the high-level functionality of your software for a non-specialist reader. Avoid jargon in this section.
```

JOSS welcomes submissions from broadly diverse research areas. For this reason, we require that authors include in the paper some sentences that explain the software functionality and domain of use to a non-specialist reader. We also require that authors explain the research applications of the software. The paper should be between 250-1000 words.


Your paper should include:

- A list of the authors of the software and their affiliations, using the correct format (see the example below).
- A summary describing the high-level functionality and purpose of the software for a diverse, *non-specialist audience*.
- A clear *Statement of Need* that illustrates the research purpose of the software.
- A list of key references, including to other software addressing related needs.
- Mention (if applicable) of any past or ongoing research projects using the software and recent scholarly publications enabled by it.
- Acknowledgement of any financial support.

As this short list shows, JOSS papers are only expected to contain a limited set of metadata (see example below), a Statement of Need, Summary, Acknowledgements, and References sections. You can look at an [example accepted paper](http://bit.ly/2x22gxT). Given this format, a "full length" paper is not permitted, and software documentation such as API (Application Programming Interface) functionality should not be in the paper and instead should be outlined in the software documentation.

```eval_rst
.. important:: Your paper will be reviewed by two or more reviewers in a public GitHub issue. Take a look at the `review checklist <review_checklist.html>`_ and  `review criteria <review_criteria.html>`_ to better understand how your submission will be reviewed.
```
## How should my paper be formatted?

Submitted articles must use Markdown and must provide a metadata section at the beginning of the article. Format metadata using YAML, a human-friendly data serialization language (The Official YAML Web Site, 2022). The information provided is included in the title and sidebar of the generated PDF. 

### Article metadata

#### Names

Providing an author name is straight-forward: just set the `name` attribute. However, sometimes more control over the name is required.

##### Name parts

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

##### Particles

It's usually enough to place particles like "van", "von", "della", etc. at the end of the given name or at the beginning of the surname, depending on the details of how the name is used.

- `dropping-particle`
- `non-dropping-particle`

##### Literal names

The automatic construction of the full name from parts is geared towards common Western names. It may therefore be necessary sometimes to provide the display name explicitly. This is possible by setting the `literal` field, e.g., `literal: Tachibana Taki`. This feature should only be used as a last resort. <!-- e.g., `literal: 宮水 三葉`. -->

##### Example

```yaml
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

The name parts can also be collected under the author's `name`:

``` yaml
authors:
  - name:
      given-names: Kari
      surname: Nordmann
```

  <!-- - name: -->
  <!--     literal: 立花 瀧 -->
  <!--     given-names: 瀧 -->
  <!--     surname: 立花 -->


### Internal references

The goal of Open Journals is to provide authors with a seamless and pleasant writing experience. Since Markdown has no default mechanism to handle document internal references, known as “cross-references”, Open Journals supports a limited set of LaTex commands. In brief, elements that were marked with `\label` and can be referenced with `\ref` and `\autoref`.

[Open Journals]: https://theoj.org

    ![View of coastal dunes in a nature reserve on Sylt, an island in
    the North Sea. Sylt (Danish: *Slid*) is Germany's northernmost
    island.](sylt.jpg){#sylt width="100%"}

#### Tables and figures

Tables and figures can be referenced if they are given a *label* in the caption. In pure Markdown, this can be done by adding an empty span `[]{label="floatlabel"}` to the caption. LaTeX syntax is supported as well: `\label{floatlabel}`.

Link to a float element, i.e., a table or figure, with `\ref{identifier}` or `\autoref{identifier}`, where `identifier` must be defined in the float's caption. The former command results in just the float's number, while the latter inserts the type and number of the referenced float. E.g., in this document `\autoref{proglangs}` yields "\autoref{proglangs}", while `\ref{proglangs}` gives "\ref{proglangs}".

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

### Behind the scenes

Readers may wonder about the reasons behind some of the choices made for paper writing. Most often, the decisions were driven by radical pragmatism. For example, Markdown is not only nearly ubiquitous in the realms of software, but it can also be converted into many different output formats. The archiving standard for scientific articles is JATS, and the most popular publishing format is PDF. Open Journals has built its pipeline based on [pandoc](https://pandoc.org), a universal document converter that can produce both of these publishing formats as well as many more.

A common method for PDF generation is to go via LaTeX. However, support for tagging -- a requirement for accessible PDFs -- is not readily available for LaTeX. The current method used ConTeXt, to produce tagged PDF/A-3, a format suited for archiving [@pdfa3].

### Markdown
Markdown is a lightweight markup language used frequently in software development and online environments. Based on email conventions, it was developed in 2004 by John Gruber and Aaron Swartz. 

#### Inline markup

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

#### Links

Link syntax is `[link description](targetURL)`. E.g., this link to the [Journal of Open Source Software](https://joss.theoj.org/) is written as \
`[Journal of Open Source Software](https://joss.theoj.org/)`.

Open Journal publications are not limited by the constraints of print publications. We encourage authors to use hyperlinks for websites and other external resources. However, the standard scientific practice of citing the relevant publications should be followed regardless.

#### Grid Tables

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

#### Figures

To create a figure, a captioned image must appear by itself in a paragraph. The Markdown syntax for a figure is a link, preceded by an exclamation point (!) and a description.  
Example:  
`![This description will be the figure caption](path/to/image.png)`

In order to create a figure rather than an image, there must be a description included and the figure syntax must be the only element in the paragraph, i.e., it must be surrounded by blank lines.

Images that are larger than the text area are scaled to fit the page. You can give images an explicit height and/or width, e.g. when adding an image as part of a paragraph. The Markdown `![Nyan cat](nyan-cat.png){height="9pt"}` includes the image "nyan-cat.png" Nyan cat{height="9pt"} while scaling it to a height of 9 pt.

#### Citations

Bibliographic data should be collected in a file `paper.bib`; it should be formatted in the BibLaTeX format, although plain BibTeX is acceptable as well. All major citation managers offer to export these formats.

Cite a bibliography entry by referencing its identifier: `[@upper1974]` will create the reference "[@upper1974]". Omit the brackets when referring to the author as part of a sentence: "For a case study on writers block, see @upper1974." Please refer to the [pandoc manual](https://pandoc.org/MANUAL#extension-citations) for additional features, including page locators, prefixes, suffixes, and suppression of author names in citations.

#### Mathematical Formulæ

Mark equations and other math content with dollar signs (`$`). Use a single dollar sign (`$`) for math that will appear directly within the text. Use two dollar signs (`$$`) when the formula is to be presented centered and on a separate line, in "display" style. The formula itself must be given using TeX syntax.

To give some examples: When discussing a variable $x$ or a short formula like $\sin \frac{\pi}{2}$, we would write `$x$` and `$\sin \frac{\pi}{2}$`, respectively. However, for more complex formulæ, display style is more appropriate. Writing `$$\int_{-\infty}^{+\infty} e^{-x^2} \, dx = \sqrt{\pi}$$` will give us

$$\int_{-\infty}^{+\infty} e^{-x^2} \, dx = \sqrt{\pi}$$

#### Footnotes

Syntax for footnotes centers around the "caret" character `^`. The symbol is also used as a delimiter for superscript text and thereby mirrors the superscript numbers used to mark a footnote in the final text.[^markers]

``` markdown
Articles are published under a Creative Commons license[^1].
Software should use an OSI-approved license.

[^1]: An open license that allows reuse.
```

The above example results in the following output:

> Articles are published under a Creative Commons license[^1]. Software should use an OSI-approved license.
>
> [^1]: An open license that allows reuse.

Note: numbers do not have to be sequential, they will be reordered automatically in the publishing step. In fact, the identifier of a note can be any sequence of characters, like `[^marker]`, but may not contain whitespace characters.

[^markers]: it should be noted that some publishers prefer symbols or letters as footnote markers.

#### Blocks

The larger components of a document are called "blocks".

##### Headings

Headings are added with `#` followed by a space, where each additional `#` demotes the heading to a level lower in the hierarchy:

```markdown
# Section

## Subsection

### Subsubsection
```

Please start headings on the first level. The maximum supported level is 5, but paper authors are encouraged to limit themselves to headings of the first two or three levels.

###### Deeper nesting

Fourth- and fifth-level subsections – like this one and the following heading – are supported by the system; however, their use is discouraged. Use lists instead of forth- and fifth-level headings.


#### Lists

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

## Example paper and bibliography

This example `paper.md` is adapted from _Gala: A Python package for galactic dynamics_ by Adrian M. Price-Whelan [http://doi.org/10.21105/joss.00388](http://doi.org/10.21105/joss.00388):

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
    orcid: 0000-0003-0872-7098
    affiliation: "1, 2" # (Multiple affiliations must be quoted)
  - name: Author Without ORCID
    affiliation: 2
affiliations:
 - name: Lyman Spitzer, Jr. Fellow, Princeton University
   index: 1
 - name: Institution 2
   index: 2
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

``Gala`` is an Astropy-affiliated Python package for galactic dynamics. Python
enables wrapping low-level languages (e.g., C) for speed without losing
flexibility or ease-of-use in the user-interface. The API for ``Gala`` was
designed to provide a class-based and user-friendly interface to fast (C or
Cython-optimized) implementations of common operations such as gravitational
potential and force evaluation, orbit integration, dynamical transformations,
and chaos indicators for nonlinear dynamics. ``Gala`` also relies heavily on and
interfaces well with the implementations of physical units and astronomical
coordinate systems in the ``Astropy`` package [@astropy] (``astropy.units`` and
``astropy.coordinates``).

``Gala`` was designed to be used by both astronomical researchers and by
students in courses on gravitational dynamics or astronomy. It has already been
used in a number of scientific publications [@Pearson:2017] and has also been
used in graduate courses on Galactic dynamics to, e.g., provide interactive
visualizations of textbook material [@Binney:2008]. The combination of speed,
design, and support for Astropy functionality in ``Gala`` will enable exciting
scientific explorations of forthcoming data releases from the *Gaia* mission
[@gaia] by students and experts alike.

# Mathematics

Single dollars ($) are required for inline mathematics e.g. $f(x) = e^{\pi/x}$

Double dollars make self-standing equations:

$$\Theta(x) = \left\{\begin{array}{l}
0\textrm{ if } x < 0\cr
1\textrm{ else}
\end{array}\right.$$


# Citations

Citations to entries in paper.bib should be in
[rMarkdown](http://rmarkdown.rstudio.com/authoring_bibliographies_and_citations.html)
format.

For a quick reference, the following citation commands can be used:
- `@author:2001`  ->  "Author et al. (2001)"
- `[@author:2001]` -> "(Author et al., 2001)"
- `[@author1:2001; @author2:2001]` -> "(Author1 et al., 2001; Author2 et al., 2002)"

# Figures

Figures can be included like this: ![Example figure.](figure.png)

# Acknowledgements

We acknowledge contributions from Brigitta Sipocz, Syrtis Major, and Semyeong
Oh, and support from Kathryn Johnston during the genesis of this project.

# References
```

Example `paper.bib` file:

```
@article{Pearson:2017,
  	Adsnote = {Provided by the SAO/NASA Astrophysics Data System},
  	Adsurl = {http://adsabs.harvard.edu/abs/2017arXiv170304627P},
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
  	Adsnote = {Provided by the SAO/NASA Astrophysics Data System},
  	Adsurl = {http://adsabs.harvard.edu/abs/2008gady.book.....B},
  	Author = {{Binney}, J. and {Tremaine}, S.},
  	Booktitle = {Galactic Dynamics: Second Edition, by James Binney and Scott Tremaine.~ISBN 978-0-691-13026-2 (HB).~Published by Princeton University Press, Princeton, NJ USA, 2008.},
  	Publisher = {Princeton University Press},
  	Title = {{Galactic Dynamics: Second Edition}},
  	Year = 2008
}

@article{gaia,
    author = {{Gaia Collaboration}},
    title = "{The Gaia mission}",
    journal = {\aap},
    archivePrefix = "arXiv",
    eprint = {1609.04153},
    primaryClass = "astro-ph.IM",
    keywords = {space vehicles: instruments, Galaxy: structure, astrometry, parallaxes, proper motions, telescopes},
    year = 2016,
    month = nov,
    volume = 595,
    doi = {10.1051/0004-6361/201629272},
    adsurl = {http://adsabs.harvard.edu/abs/2016A%26A...595A...1G},
}

@article{astropy,
    author = {{Astropy Collaboration}},
    title = "{Astropy: A community Python package for astronomy}",
    journal = {\aap},
    archivePrefix = "arXiv",
    eprint = {1307.6212},
    primaryClass = "astro-ph.IM",
    keywords = {methods: data analysis, methods: miscellaneous, virtual observatory tools},
    year = 2013,
    month = oct,
    volume = 558,
    doi = {10.1051/0004-6361/201322068},
    adsurl = {http://adsabs.harvard.edu/abs/2013A%26A...558A..33A}
}
```

Note that the paper ends with a References heading, and the references are built automatically from the content in the `.bib` file. You should enter in-text citations in the paper body following correct [Markdown citation syntax](https://rmarkdown.rstudio.com/authoring_bibliographies_and_citations.html#citation_syntax).

## Submitting your paper

Submission is as simple as:

- Filling in the [short submission form](http://joss.theoj.org/papers/new)
- Waiting for the managing editor to start a pre-review issue over in the JOSS reviews repository: https://github.com/openjournals/joss-reviews

## No submission fees

There are no fees for submitting or publishing in JOSS. You can read more about our [cost and sustainability model](http://joss.theoj.org/about#costs).

## Preprint Policy

Authors are welcome to submit their papers to a preprint server ([arXiv](https://arxiv.org/), [bioRxiv](https://www.biorxiv.org/), [SocArXiv](https://socopen.org/), [PsyArXiv](https://psyarxiv.com/) etc.) at any point during the submission and review process.

Submission to a preprint server is _not_ considered a previous publication.

## Authorship

Purely financial (such as being named on an award) and organizational (such as general supervision of a research group) contributions are not considered sufficient for co-authorship of JOSS submissions, but active project direction and other forms of non-code contributions are. The authors themselves assume responsibility for deciding who should be credited with co-authorship, and co-authors must always agree to be listed. In addition, co-authors agree to be accountable for all aspects of the work, and to notify JOSS if any retraction or correction of mistakes are needed after publication.

## Submissions using proprietary languages/dev environments

We strongly prefer software that doesn't rely upon proprietary (paid for) development environments/programming languages. However, provided _your submission meets our requirements_ (including having a valid open source license) then we will consider your submission for review. Should your submission be accepted for review, we may ask you, the submitting author, to help us find reviewers who already have the required development environment installed.

## The review process

After submission:

- An Associate Editor-in-Chief will carry out an initial check of your submission, and proceed to assign a handling editor.
- The handling editor will assign two or more JOSS reviewers, and the review will be carried out in the [JOSS reviews repository](https://github.com/openjournals/joss-reviews).
- Authors will respond to reviewer-raised issues (if any are raised) on the submission repository's issue tracker. Reviewer and editor contributions, like any other contributions, should be acknowledged in the repository.
- Upon successful completion of the review, authors will make a tagged release of the software, and deposit a copy of the repository with a data-archiving service such as [Zenodo](https://zenodo.org/) or [figshare](https://figshare.com/), get a DOI for the archive, and update the review issue thread with the version number and DOI.
- After we assign a DOI for your accepted JOSS paper, its metadata is deposited with CrossRef and listed on the JOSS website.
- The review issue will be closed, and an automatic tweet from [@JOSS_TheOJ](https://twitter.com/JOSS_TheOJ) will announce it!

If you want to learn more details about the review process, take a look at the [reviewer guidelines](reviewer_guidelines.html).
