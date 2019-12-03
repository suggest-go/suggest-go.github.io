---
layout: default
title: Spellchecker
nav_order: 2
parent: Demo
---

## Spellchecker demo

The demo shows spellchecker feature for restricted N-Gram language model built on
[Blog Authorship Corpus](http://u.cs.biu.ac.il/~koppel/BlogCorpus.htm)


{% include spellchecker.html %}

{: .mt-10 }
## Run locally

You can run a spellchecker CLI locally, we should do the next steps:

* Clone and build the `suggest` package
```
$ git clone https://github.com/suggest-go/suggest.git
$ make build
```

* Download an English [language model](https://app.box.com/s/elogon8jdimqjdvfncr06b0qjngasljc) built on [Blog Authorship Corpus](http://u.cs.biu.ac.il/~koppel/BlogCorpus.htm)

* Extract downloaded language model and perform
```
$ build/./spellchecker eval -c PATH_TO_LM/config.json
```

or in order to run http server, do the next
```
$ build/./spellchecker service-run -c PATH_TO_LM/config.json -p 8083
$ curl http://localhost:8083/predict/ja/
```
