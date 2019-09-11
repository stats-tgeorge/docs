Review criteria
===============

## The JOSE paper

As outlined in the [submission guidelines provided to authors](submitting.html#what-should-my-paper-contain), the JOSE paper (the compiled PDF associated with this submission) should only include:

- Title, and author list with affiliations
- Description of the software or learning module
- Statement of need
- Key references, including the submission archive

Detailed documentation should be present in the repository of the submitted software or module, is reviewed there, and does not need to be included in the paper.

```eval_rst
.. important:: Note that software paper's *should not* include software documentation such as API (Application Programming Interface) functionality, as this should be outlined in the software documentation.
```

## Submission requirements

```eval_rst
.. important:: Note, if you've not yet been involved in a JOSE review, you can see an example JOSE review checklist `here <review_checklist.html>`_. 
```

### License

The submission should be open, under the [Open Definition](http://opendefinition.org/).
Any text content or graphical objects should be under a Creative Commons license
(ideally [CC-BY](https://creativecommons.org/licenses/by/4.0/)) and code components
should be under an [OSI-approved license](https://opensource.org/licenses/alphabetical).
License information must be clearly visible in the submission's online repository,
which must include a plain-text `LICENSE` file.

> **Acceptable:** A plain-text `LICENSE` file with the contents of an OSI-approved license<br />            
> **Not acceptable:** A phrase such as 'MIT license' in a `README` file

### Statement of need

A key component of the JOSE paper is a statement by the authors, explaining the contribution made by the submitted artifacts to computationally enabled teaching and learning, and describing how they might be used by others. The criterion is less one of novelty, than _need_: submissions targeting subjects or applications already addressed by other resources are _eligible_, if the authors make a case for why they might be adopted by learners or other instructors.

### Community guidelines

The online repository of the software or learning module needs to contain clear
guidelines for potential contributors who may want to: 

- Contribute to the software/module
- Report issues or problems with the software/module
- Seek support

### Specific requirements for software submissions

**Documentation:** The software repository should contain enough documentation to understand the functionality of the software, to guide through the build process (including a list of dependencies), and to complete examples of use.

**Tests:** Software quality depends on testing. Ideally, the software should include an automated test suite, but it's also acceptable to include documented manual steps to test the functionality of the software.

**Examples:** Potential users of new software rely on well-documented examples to get started. Reviewers will look for examples of use that illustrate beginner and advanced functionality

> **Good**: A package management file such as a `Gemfile` or `package.json` or equivalent
> **OK**: A list of dependencies to install
> **Bad (not acceptable)**: Reliance on other software not listed by the authors

### Specific requirements for learning modules

**Substance:** A learning module should cover a substantial portion of material to
achieve plainly clear learning objectives. The ideal module consists of a few lessons,building up a well-rounded topic, as a full tutorial or _part_ of a term or semester
course. This direction follows trends and recommendations to 'modularize' courses,
both online and on-campus—one example is the 2014 report on the 
[Future of MIT Education](http://news.mit.edu/2014/future-of-mit-education-0804).
The module should contain well-written and complete presentation of the material,
weaved with the computatational portions and sample output.

**Pedagogical soundness:** Instructional design of the module should be intentional
and apparent. For example, the weaving of text, images, code and output might apply
the [worked-example effect](https://en.wikipedia.org/wiki/Worked-example_effect),
deliberately. The authors should briefly explain their design in the JOSE paper.


## Other considerations

### Authorship

As part of the review process, you are asked to check whether the submitting author has made a "substantial contribution" to the submitted software (as determined by the commit history) and to check that "the full list of paper authors seems appropriate and complete?"

As discussed in the [submission guidelines for authors](submitting.html#authorship), authorship is a complex topic with different practices in different communities.  Ultimately, the authors themselves are responsible for deciding which contributions are sufficient for co-authorship, although JOSE policy is that purely financial contributions are not considered sufficient. Your job as a reviewer is to check that the list of authors appears reasonable, and if it's not obviously complete/correct, to raise this as a question during the review.

### What happens if the submission I'm reviewing doesn't meet the JOSE criteria?

We ask that reviewers grade submissions in one of three categories: 1) Accept 2) Minor Revisions 3) Major Revisions. Unlike some journals, we do not reject outright submissions requiring major revisions. We like to give the author as long as they need to make these modifications/improvements.
