---
layout: default
title: Suggest models
nav_order: 2
parent: Demo
---

## Suggest vehicle model names

The demo shows an approximate string search in a vehicle dictionary with more than 2k model names.

This example uses two provided features: [autocomplete](https://godoc.org/github.com/suggest-go/suggest/pkg/suggest#Service.Autocomplete) and [suggest](https://godoc.org/github.com/suggest-go/suggest/pkg/suggest#Service.Suggest).

*Please type "Volks"*

{% assign dict = "cars" %}
{% include autocomplete.html %}
