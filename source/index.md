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

> To authorize endpoint urls, example:

```ruby
require 'httparty'

response = HTTParty.get('http://jobhuk.com/api/v1/companies.json', headers: {"Token" => "API_TOKEN"})
companies = response.body
```

```shell
curl "http://jobhuk.com/api/v1/companies.json"
  -H "Token: API_TOKEN"  
```

> Make sure to replace `API_TOKEN` with your API key.

Jobhuk uses API keys to allow access to the API. You can register a new Jobhuk API key at our [Partner Portal](https://jobhuk.com/partner/signup).

Jobhuk expects for the API_TOKEN to be included in all API requests to the server in a header that looks like the following:

`Token: API_TOKEN`

<aside class="notice">
You must replace `API_TOKEN` with your personal API key.
</aside>

# Companies 

## List of Companies

```ruby
require 'httparty'

response = HTTParty.get('http://jobhuk.com/api/v1/companies.json', headers: {"Token" => "API_TOKEN"})
companies = response.body
```

```shell
curl "http://jobhuk.com/api/v1/companies.json"
  -H "Token: API_TOKEN"  
```

> The above command returns JSON structured like this:

```json
[
  {
    "id":2,
    "name":"jobhuk",
    "address":"610 Brazos St. Suite 300D Austin TX 78701",
    "website":"http://jobhuk.com",
    "phone":"+1 (855)-855-8359",
    "fax":"+1 (855)-855-8359",
    "city":"Austin",
    "state":"TX",
    "zip":"78701",
    "created_at":"2015-04-16T04:59:14-05:00",
    "image":"https://jobhuk.s3.amazonaws.com/uploads/company_images/company/image/1089/jobhuk_logo_stacked_600r.jpg",
    "founded":"2014",
    "about":"Jobhuk is a unique self service platform serving as 'CrowdSourced Hiring MarketPlace' .... new marketplace which virtually exists in staffing in email, phone and verbal conversations.",
    "description":"Jobhuk is a unique self service platform serving as 'CrowdSourced Hiring MarketPlace' .... new marketplace which virtually exists in staffing in email, phone and verbal conversations.",
    "social_profile_links":["https://www.facebook.com/Jobhuk", "https://www.linkedin.com/company/jobhuk"],
    "email":"contact@jobhuk.com",
    "about_team":"",
    "tag_line":"recruitment marketplace",
    "about_benefits":"",
    "relation_type":"staffing",
    "verified":"true"
  },
  {
    "id":3,
    "name":"Some Company"
  }
]
```

This endpoint retrieves list of companies created by you.

### HTTP Request

`GET http://jobhuk.com/api/v1/companies`

## Create Company

```ruby
require 'httparty'

response = HTTParty.post("http://whosflying.com/api/v1/company.json", { body: {company: {name: "jobhuk", website: "http://jobhuk.com", phone: 8558558359, company_type: "staffing"}}, headers: {"Token" => "API_TOKEN"} })
company = response.body
```

```shell
curl "http://whosflying.com/api/v1/company.json" 
  -X POST 
  -H "Token:TW6SV34JL+M/WaVMY0tytrII2PJ1xAjSkV73qq2Gmzgv+8q0zSeIhijCLVSc9eSEb9jjuug/8ZtucVSacMFgeA=="
  --data "company[name]=test110&company[website]=test110.com&company[phone]=1234567890" 
```

> The above command returns JSON structured like this:

```json
{
  "id":2,
  "name":"jobhuk",
  "address":"610 Brazos St. Suite 300D Austin TX 78701",
  "website":"http://jobhuk.com",
  "phone":"+1 (855)-855-8359",
  "fax":"+1 (855)-855-8359",
  "city":"Austin",
  "state":"TX",
  "zip":"78701",
  "created_at":"2015-04-16T04:59:14-05:00",
  "image":"https://jobhuk.s3.amazonaws.com/uploads/company_images/company/image/1089/jobhuk_logo_stacked_600r.jpg",
  "founded":"2014",
  "about":"Jobhuk is a unique self service platform serving as 'CrowdSourced Hiring MarketPlace' .... new marketplace which virtually exists in staffing in email, phone and verbal conversations.",
  "description":"Jobhuk is a unique self service platform serving as 'CrowdSourced Hiring MarketPlace' .... new marketplace which virtually exists in staffing in email, phone and verbal conversations.",
  "social_profile_links":["https://www.facebook.com/Jobhuk", "https://www.linkedin.com/company/jobhuk"],
  "email":"contact@jobhuk.com",
  "about_team":"",
  "tag_line":"recruitment marketplace",
  "about_benefits":"",
  "relation_type":"staffing",
  "verified":"true"
}
```

This endpoint creates a company in jobhuk.

### HTTP Request

`POST http://jobhuk.com/api/v1/company.json`

### POST Parameters

Parameter | Value   | Description
--------- | ------  | -----------
company<br>required | hash | company fields hash
company[name]<br>required | string | company name
company[website]<br>required | string | official website of the company
company[phone]<br>required | integer | contact phone number
company[company_type]<br>required | string | Type of the company. <br>Must be one of staffing, employer, partner. 
company[tag_line]<br>optional | string | company tag line
company[email]<br>optional | string | contact email address
company[address]<br>optional | string | company address
company[fax]<br>optional | string | company fax number
company[city]<br>optional | string | city
company[state]<br>optional | string | state
company[zip]<br>optional | string | zip code
company[logo]<br>optional | string | company logo url
company[year_founded]<br>optional | integer | company founded year
company[short_description]<br>optional | string | company short description
company[long_description]<br>optional | string | company long description
company[about_team]<br>optional | string | information about company team
company[about_benefits]<br>optional | string | information about company benefits

## Get Company

```ruby
require 'httparty'

response = HTTParty.get('http://jobhuk.com/api/v1/company/2.json', headers: {"Token" => "API_TOKEN"})
companies = response.body
```

```shell
curl "http://jobhuk.com/api/v1/company/2.json"
  -H "Token: API_TOKEN"
```

> The above command returns JSON structured like this:

```json
{
  "id":2,
  "name":"jobhuk",
  "address":"610 Brazos St. Suite 300D Austin TX 78701",
  "website":"http://jobhuk.com",
  "phone":"+1 (855)-855-8359",
  "fax":"+1 (855)-855-8359",
  "city":"Austin",
  "state":"TX",
  "zip":"78701",
  "created_at":"2015-04-16T04:59:14-05:00",
  "image":"https://jobhuk.s3.amazonaws.com/uploads/company_images/company/image/1089/jobhuk_logo_stacked_600r.jpg",
  "founded":"2014",
  "about":"Jobhuk is a unique self service platform serving as 'CrowdSourced Hiring MarketPlace' .... new marketplace which virtually exists in staffing in email, phone and verbal conversations.",
  "description":"Jobhuk is a unique self service platform serving as 'CrowdSourced Hiring MarketPlace' .... new marketplace which virtually exists in staffing in email, phone and verbal conversations.",
  "social_profile_links":["https://www.facebook.com/Jobhuk", "https://www.linkedin.com/company/jobhuk"],
  "email":"contact@jobhuk.com",
  "about_team":"",
  "tag_line":"recruitment marketplace",
  "about_benefits":"",
  "relation_type":"staffing",
  "verified":"true"
}
```

This endpoint retrieves a specific company information.

### HTTP Request

`GET http://jobhuk.com/api/v1/company/<id>.json`

### URL Parameters

Parameter | Description
--------- | -----------
id | The id of the company to retrieve

## Edit Company

```ruby
require 'httparty'

response = HTTParty.post("http://whosflying.com/api/v1/company/2.json", { body: {company: {name: "jobhuk", website: "http://jobhuk.com", phone: 8558558359, company_type: "staffing"}}, headers: {"Token" => "API_TOKEN"} })
company = response.body
```

```shell
curl "http://whosflying.com/api/v1/company/2.json" 
  -X POST 
  -H "Token:TW6SV34JL+M/WaVMY0tytrII2PJ1xAjSkV73qq2Gmzgv+8q0zSeIhijCLVSc9eSEb9jjuug/8ZtucVSacMFgeA=="
  --data "company[name]=test110&company[website]=test110.com&company[phone]=1234567890" 
```

> The above command returns JSON structured like this:

```json
{
  "id":2,
  "name":"jobhuk",
  "address":"610 Brazos St. Suite 300D Austin TX 78701",
  "website":"http://jobhuk.com",
  "phone":"+1 (855)-855-8359",
  "fax":"+1 (855)-855-8359",
  "city":"Austin",
  "state":"TX",
  "zip":"78701",
  "created_at":"2015-04-16T04:59:14-05:00",
  "image":"https://jobhuk.s3.amazonaws.com/uploads/company_images/company/image/1089/jobhuk_logo_stacked_600r.jpg",
  "founded":"2014",
  "about":"Jobhuk is a unique self service platform serving as 'CrowdSourced Hiring MarketPlace' .... new marketplace which virtually exists in staffing in email, phone and verbal conversations.",
  "description":"Jobhuk is a unique self service platform serving as 'CrowdSourced Hiring MarketPlace' .... new marketplace which virtually exists in staffing in email, phone and verbal conversations.",
  "social_profile_links":["https://www.facebook.com/Jobhuk", "https://www.linkedin.com/company/jobhuk"],
  "email":"contact@jobhuk.com",
  "about_team":"",
  "tag_line":"recruitment marketplace",
  "about_benefits":"",
  "relation_type":"staffing",
  "verified":"true"
}
```

This endpoint updates specific company information given by id.

### HTTP Request

`PUT http://jobhuk.com/api/v1/company/<id>.json`

### POST Parameters

Parameter | Value   | Description
--------- | ------  | -----------
id | integer | jobhuk company id 
company<br>required | hash | company fields hash
company[name]<br>required | string | company name
company[website]<br>required | string | official website of the company
company[phone]<br>required | integer | contact phone number
company[company_type]<br>required | string | Type of the company. <br>Must be one of staffing, employer, partner. 
company[tag_line]<br>optional | string | company tag line
company[email]<br>optional | string | contact email address
company[address]<br>optional | string | company address
company[fax]<br>optional | string | company fax number
company[city]<br>optional | string | city
company[state]<br>optional | string | state
company[zip]<br>optional | string | zip code
company[logo]<br>optional | string | company logo url
company[year_founded]<br>optional | integer | company founded year
company[short_description]<br>optional | string | company short description
company[long_description]<br>optional | string | company long description
company[about_team]<br>optional | string | information about company team
company[about_benefits]<br>optional | string | information about company benefits

# Jobs

# Candidates
