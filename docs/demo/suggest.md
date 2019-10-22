---
layout: default
title: Suggest
nav_order: 1
parent: Demo
---

## Suggest demo

The demo shows approximate string search in a dictionary with more than 200k English [words](https://raw.githubusercontent.com/suggest-go/suggest/master/pkg/suggest/testdata/words.dict).

This example uses two provided features: [autocomplete](https://godoc.org/github.com/suggest-go/suggest/pkg/suggest#Service.Autocomplete) and [suggest](https://godoc.org/github.com/suggest-go/suggest/pkg/suggest#Service.Suggest).

*Please type "indpendnce"*

{% assign dict = "words" %}
{% include autocomplete.html %}
