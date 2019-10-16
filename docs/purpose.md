---
layout: default
title: Purpose
nav_order: 1
---

# Purpose
{: .fs-6 .fw-300 }

### TopK approximate string search in a dictionary

Let's imagine you have a website, for instance, an automotive website.
There could be a lot of dictionaries, such as a list of vehicle models names, cities (countries), cars spares and etc.
Some of these dictionaries could be pretty large, and it might be tedious for a customer to choose the correct option from the dictionary.
Having the possibility of Top-k approximate string search in a dictionary is significant in these cases.

This demo shows autocomplete feature for the dictionary of 2000 vehicle model names.

*Please type "tayota cmry"*

{% assign dict = "cars" %}
{% include autocomplete.html %}

### Spellchecker

Context-sensitive spell checker could be very useful for such cases as:

* Phrase completion while you type
* Did you mean feature
* Checks for misspellings in a text

{: .mt-6 }

![Demo](/assets/spellchecker-demo.gif)
