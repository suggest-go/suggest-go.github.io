---
layout: default
title: Suggest visa sponsors
nav_order: 4
parent: Demo
---

## Suggest visa sponsors

The demo shows approximate string search in a dictionary with more than 30k [companies with visa sponsorship](https://assets.publishing.service.gov.uk/government/uploads/system/uploads/attachment_data/file/809016/2019-06-14_Tier_2_5_Register_of_Sponsors.pdf).

This example uses two provided features: [autocomplete](https://godoc.org/github.com/suggest-go/suggest/pkg/suggest#Service.Autocomplete) and [suggest](https://godoc.org/github.com/suggest-go/suggest/pkg/suggest#Service.Suggest).

*Please type "Bado.."*

{% assign dict = "sponsors" %}
{% include autocomplete.html %}
