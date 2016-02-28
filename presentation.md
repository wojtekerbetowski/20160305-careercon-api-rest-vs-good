# HTTP API

---

But first, who am I?

---

# Wojtek Erbetowski

Speaker & Organizer

_ @ Growbots (prev. HoE @ Polidea)

<!-- F***l story -->

---

# API
## REST
### HATEOAS


<!-- Why are you here? -->

---

A design pattern

---

not a specification*

---

## bikeshedding

---

words, words, words...

<!-- the big idea -->
<!-- prize frame -->

---

REpresentational State Transfer

---

## Common issues

<!-- secret sauce -->

---

## Common issues
### Media types

---

```
application/json
application/vnd.growbots.v2.json
```

---

## Common issues
### Embedding relatives

---

```
GET /user/184

{
  "name": "Bob",
  "location": {
    "country": "United States",
    "city": "San Francisco"
  }
}
```
---

```
GET /user/184

{
  "name": "Bob",
  "location": 845
}

GET /locations/845

...
```

------

```
GET /user/184

{
  "name": "Bob",
  "location": "http://myservice/locations/845"
}

```

---

## Common issues
### modifications

---

`/hotels/3734/reservations/345/confirm`

---

`POST /hotels/3734/reservations/345/confirm`

---

`PUT /hotels/3734/reservations/345`

---

```
PUT /hotels/3734/reservations/345

{
  "customer": 225325,
  "dateStart": "...",
  ...
  "confirmed": true,
  ...
}
```

---

```
PATCH /hotels/3734/reservations/345

{
  "confirmed": true
}
```

---

## Versioning

---

```
GET /users/1

{
  "name": "Walter White"
}

```

---

```
GET /users/1

{
  "firstName": "Walter",
  "lastName": "White"
}

```

---

```
GET /users/1
Accept: application/vnd.growbots.v1+json
```

---

```
GET /v1/users/1

```

---

```
GET /users/1
Host v1.myservice.com
```

---

## Naked objects/lists

---

```
GET /users

[
  {"name": "Bob"},
  ...
]
```
---

```
GET /users

[
  250,
  {"length": ...},
  {"meta": ...},
  {"name": "Bob"},
  ...
]
```

---
```
GET /users

{
  "data": [
    {"name": "Bob"},
    ...
  ]
}
```

---
```
GET /users

{
  "data": [
    {"name": "Bob"},
    ...
  ],
  "size": 250
}
```

---
```
GET /users/123

{
  "data": {
    "name": "Bob"
  }
}
```

---
```
GET /users/123

{
  "name": "Bob",
  "lastModified": "2016-..."
}
```

---

## {JSON:API}

---

```
{
  "links": {
    "self": "http://example.com/articles",
    "next": "http://example.com/articles?page[offset]=2",
    "last": "http://example.com/articles?page[offset]=10"
  },
  "data": [{
    "type": "articles",
    "id": "1",
    "attributes": {
      "title": "JSON API paints my bikeshed!"
    },
    "relationships": {
      "author": {
        "links": {
          "self": "http://example.com/articles/1/relationships/author",
          "related": "http://example.com/articles/1/author"
        },
        "data": { "type": "people", "id": "9" }
      }
    },
    "links": {
      "self": "http://example.com/articles/1"
    }
  }],
  "included": [{
    "type": "people",
    "id": "9",
    "attributes": {
      "first-name": "Dan",
      "last-name": "Gebhardt",
      "twitter": "dgeb"
    },
    "links": {
      "self": "http://example.com/people/9"
    }
  }]
}
```

---

# In a nutshell

<!-- don't argue, don't follow buzzwords -->
<!-- naked objects, versioning, JSON API -->

---

## Have a good one!
