---
layout: default
title: Spellchecker
nav_order: 2
parent: Demo
---

## Spellchecker demo

Online spellchecker demo is coming soon
{: .label .label-yellow }

You can run a spellchecker CLI locally, we should do the next steps:

* Clone and build the `suggest` package
```
$ git clone https://github.com/suggest-go/suggest.git
$ make build
```

* Download an English [language model](https://app.box.com/s/elogon8jdimqjdvfncr06b0qjngasljc) built on [Blog Authorship Corpus](http://u.cs.biu.ac.il/~koppel/BlogCorpus.htm)

* Extract downloaded language model and perform
```
$ go run pkg/cmd/spellchecker/main.go -config PATH_TO_LM/config.json
```

{: .mt-6 }

![Demo](/assets/spellchecker-demo.gif)
