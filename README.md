pandoc-jats
===========

A Lua [custom writer for Pandoc](http://johnmacfarlane.net/pandoc/README.html#custom-writers) generating [JATS 1.0 XML](http://jats.nlm.nih.gov/archiving/tag-library/1.0/index.html).

### Installation
Just download the file `JATS.lua` and put it in a convenient location. Pandoc includes a lua interpreter, so lua need not be installed separately. You need at least Pandoc version 1.12, released September 2013 (this release added YAML metadata and Lua writer support).

### Usage
To convert the markdown file `example1.md` into the JATS XML file `example1.xml`, using the bibliography `example.bib` and the citation style `apa.csl` use the following command:

    pandoc -f examples/example1.md --filter pandoc-citeproc --bibliography=examples/example.bib --csl=examples/apa.csl -t JATS.lua -o example1.xml

### Metadata
The metadata required for JATS can be stored in a YAML header - the same format that is also used by the Jekyll static blog generator. An example [from a recent blog post](http://blog.martinfenner.org/2013/12/11/what-can-article-level-metrics-do-for-you/) is below:

    --
    layout: post
    title: "What Can Article Level Metrics Do for You?"
    tags: [example, markdown, article-level metrics, reproducibility]
    article:
      type: research-article
      publisher-id: PBIOLOGY-D-13-03338
      doi: 10.1371/journal.pbio.1001687
      pub-date: 2013-10-22
      heading: Essay
    journal:
      publisher-id: plos
      publisher-name: Public Library of Science
      publisher-loc: San Francisco, USA
      nlm-ta: PLoS Biol
      pmc: plosbiol
      title: PLoS Biology
      eissn: 1545-7885
      pissn: 1544-9173
    authors:
     - surname: Fenner
       given-names: Martin
       orcid: http://orcid.org/0000-0003-1419-2405
       email: mfenner@plos.org
       corresp: true
    copyright:
      holder: Martin Fenner
      year: 2013
      text: "This is an open-access article distributed under the terms of the Creative Commons Attribution License, which permits unrestricted use, distribution, and reproduction in any medium, provided the original author and source are credited."
      type: open-access
      link: http://creativecommons.org/licenses/by/3.0/
    ---

### Validation
The JATS XML should be validated, for example with the excellent [jats-conversion](https://github.com/PeerJ/jats-conversion) tools written by Alf Eaton.

### To Do
The focus of the first release was to generate valid JATS. This means that not all elements and attributes are supported, or that the support could be improved (e.g. for references). We also want to add configuration settings for publisher and journal elements, so that we don't have to store them in the article metadata. And the Lua code should be refactored, e.g. the `Doc` function is too complex.

### Feedback
This tool needs extensive testing with as many markdown documents as possible. Please open an issue in the [Issue Tracker](https://github.com/mfenner/pandoc-jats/issues) if you find a conversion problem.

### License
© 2013 Martin Fenner. Released under the [GPL]((http://www.gnu.org/copyleft/gpl.html), version 2 or greater. See LICENSE for more info.