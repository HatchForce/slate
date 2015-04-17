---
title: Jobhuk API Reference

language_tabs:
  - shell
  - ruby

toc_footers:
  - <a href='https://jobhuk.com/partner/signup'>Sign Up for a Developer Key</a>  

includes:
  - errors

search: true
---

# Introduction

Welcome to the Jobhuk API! You can use our API to access Jobhuk API endpoints, you publish your jobs in our website and get candidates.

We have language bindings in Shell and Ruby! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication

> To authorize, use this code:

```ruby
require 'kittn'

api = Jobhuk::APIClient.authorize!('meowmeowmeow')
```


```shell
# With shell, you can just pass the correct header with each request
curl -H 'Token: <API_TOKEN>' -X POST -d  http://jobhuk.com/api/v1/company.json
```

> Make sure to replace `API_TOKEN` with your API key.

Jobhuk uses API keys to allow access to the API. You can register a new Jobhuk API key at our [Partner Portal](https://jobhuk.com/partner/signup).

Jobhuk expects for the API_TOKEN to be included in all API requests to the server in a header that looks like the following:

`Token: API_TOKEN`

<aside class="notice">
You must replace `API_TOKEN` with your personal API key.
</aside>

# Companies

## Get All Kittens

```ruby
require 'kittn'

api = Jobhuk::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```shell
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Isis",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```ruby
require 'kittn'

api = Jobhuk::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/3"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Isis",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">If you're not using an administrator API key, note that some kittens will return 403 Forbidden if they are hidden for admins only.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the cat to retrieve

# Jobs

# Candidates