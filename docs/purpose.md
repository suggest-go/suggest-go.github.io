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

<div id="remote" class="suggest-query-form">
    <input type="search" id="query" class="typeahead" placeholder="Type model name ...">
</div>

<script src="/assets/js/jquery-1.10.2.js"></script>
<script src="/assets/js/typeahead.js"></script>

<script type="text/javascript">
    var suggest = new Bloodhound({
        datumTokenizer: Bloodhound.tokenizers.whitespace,
        queryTokenizer: Bloodhound.tokenizers.whitespace,
        remote: {
            url: "https://suggest-words-demo.herokuapp.com/suggest/cars/%QUERY/?topK=5&metric=Cosine&similarity=0.3",
            wildcard: '%QUERY',
            rateLimitWait: 200,
            transform: function (data) {
                return data.map(function (item) {
                    return item.Value;
                });
            },
            filter: false,
        }
    });

    $('#remote .typeahead').typeahead({
        minLength: 2,
        highlight: true,
        hint: false,
        autoselect: false,
    }, {
        name: 'suggest-cars',
        source: suggest,
    });
</script>

### Spellchecker

Context-sensitive spell checker could be very useful for such cases as:

* Phrase completion while you type
* Did you mean feature
* Checks for misspellings in a text

![Demo](/assets/spellchecker-demo.gif)
