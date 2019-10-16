---
layout: default
title: Demo
nav_order: 3
---

## Demo

The demo shows approximate string search in a dictionary with more than 200k English [words](https://raw.githubusercontent.com/suggest-go/suggest/master/pkg/suggest/testdata/words.dict)

*Please type "indpendnce"*

{% assign dict = "words" %}
{% include autocomplete.html %}

