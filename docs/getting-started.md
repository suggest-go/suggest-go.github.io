---
layout: default
title: Getting Started
nav_order: 2
---

## Getting started
{: .fs-6 .fw-300 }

{: .mt-6 }
The best way to start with `suggest` package is to write some working example.

- First of all, we should download `suggest` package via `go get` command.

```console
$ go get github.com/suggest-go/suggest
```

{: .mt-6 }
- We should specify the dictionary on which we are going to perform approximate string search.
Here we use `InMemoryDictionary`, that holds all dictionary items in RAM memory.

```go
dict := dictionary.NewInMemoryDictionary([]string{
    "Nissan March",
    "Nissan Juke",
    "Nissan Maxima",
    "Nissan Murano",
    "Nissan Note",
    "Toyota Mark II",
    "Toyota Corolla",
    "Toyota Corona",
})

```

{: .mt-6 }
- We have to tell `suggest` package how to build the search index for the dictionary above.

```go

indexDescription := suggest.IndexDescription {
    Name:      "cars",
    NGramSize: 3,
    Wrap:      [2]string{"$", "$"},
    Pad:       "$",
    Alphabet:  []string{"english", "$"},
}

```

where

{: .fs-2}
- Name - is the dictionary name. `suggest` provides fuzzy search support for multiple dictionaries.
- NGramSize - is the size of [n-grams](https://en.wikipedia.org/wiki/N-gram).
- Wrap - is a [2]string array, where the first and the last elements are used for wrapping each dictionary word. It allows searching candidates with more precision.
- Pad - Symbols that are not in the Alphabet, will be replaced with the pad.
- Alphabet - is a allowed sequence of characters.


{: .mt-6 }
- Create index builder, service. Here we create Runtime index builder, which will build
search index on fly. (otherwise we should create a search index with indexer cli)

```go
builder, err := suggest.NewRAMBuilder(dict, indexDescription)

if err != nil {
    log.Fatalf("Unexpected error: %v", err)
}

service := suggest.NewService()

if err := service.AddIndex(indexDescription.Name, dict, builder); err != nil {
    log.Fatalf("Unexpected error: %v", err)
}
```

And it is all. Now to perform a query to the service, we do the next:
{: .mt-6 }

```go
// declare a search configuration (query, topK elements, type of metric, min similarity)
searchConf, err := suggest.NewSearchConfig("niss ma", 5, metric.CosineMetric(), 0.4)

if err != nil {
    log.Fatalf("Unexpected error: %v", err)
}

result, err := service.Suggest("cars", searchConf)

if err != nil {
    log.Fatalf("Unexpected error: %v", err)
}

values := make([]string, 0, len(result))

for _, item := range result {
    values = append(values, item.Value)
}

fmt.Println(values)
// Output: [Nissan Maxima Nissan March]
```
