---
title: Jobhuk API Reference

language_tabs:
  - shell
  - ruby

toc_footers:
  - <a href='http://developer.jobhuk.com/api'>Sign Up for a Developer Key</a>  

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

Jobhuk uses API keys to allow access to the API. [Get API TOKEN](http://developer.jobhuk.com/api).

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
{
    "successful": true,
    "count": 35,
    "active_company_id": "314",
    "companies": [{
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
        "logo":"https://jobhuk.s3.amazonaws.com/uploads/company_images/company/image/1089/jobhuk_logo_stacked_600r.jpg",
        "founded":"2014",
        "about":"Jobhuk is a unique self service platform serving as 'CrowdSourced Hiring MarketPlace' .... new marketplace which virtually exists in staffing in email, phone and verbal conversations.",
        "description":"Jobhuk is a unique self service platform serving as 'CrowdSourced Hiring MarketPlace' .... new marketplace which virtually exists in staffing in email, phone and verbal conversations.",
        "social_profile_links":["https://www.facebook.com/Jobhuk", "https://www.linkedin.com/company/jobhuk"],
        "email":"contact@jobhuk.com",
        "about_team":"",
        "tag_line":"recruitment marketplace",
        "about_benefits":"",
        "company_type":"staffing",
        "verified":"true"
      }, {
        "id":3,
        "name":"Some Company"
      }
    ]
}
```

This endpoint retrieves list of companies created by you.

### HTTP Request

`GET http://jobhuk.com/api/v1/companies`

## Create Company

```ruby
require 'httparty'

response = HTTParty.post("http://jobhuk.com/api/v1/companies.json", { body: {company: {name: "jobhuk", website: "http://jobhuk.com", phone: 8558558359, company_type: "staffing"}}, headers: {"Token" => "API_TOKEN"} })
company = response.body
```

```shell
curl "http://jobhuk.com/api/v1/companies.json"
  -X POST 
  -H "Token:TW6SV34JL+M/WaVMY0tytrII2PJ1xAjSkV73qq2Gmzgv+8q0zSeIhijCLVSc9eSEb9jjuug/8ZtucVSacMFgeA=="
  --data "company[name]=test110&company[website]=test110.com&company[phone]=1234567890" 
```

> The above command returns JSON structured like this:

```json
{
    "successful": true,
    "company":{
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
    "logo":"https://jobhuk.s3.amazonaws.com/uploads/company_images/company/image/1089/jobhuk_logo_stacked_600r.jpg",
    "founded":"2014",
    "about":"Jobhuk is a unique self service platform serving as 'CrowdSourced Hiring MarketPlace' .... new marketplace which virtually exists in staffing in email, phone and verbal conversations.",
    "description":"Jobhuk is a unique self service platform serving as 'CrowdSourced Hiring MarketPlace' .... new marketplace which virtually exists in staffing in email, phone and verbal conversations.",
    "social_profile_links":["https://www.facebook.com/Jobhuk", "https://www.linkedin.com/company/jobhuk"],
    "email":"contact@jobhuk.com",
    "about_team":"",
    "tag_line":"recruitment marketplace",
    "about_benefits":"",
    "company_type":"staffing",
    "verified":"true"
    }
}
```

This endpoint creates a company in jobhuk.

### HTTP Request

`POST http://jobhuk.com/api/v1/companies.json`

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

response = HTTParty.get('http://jobhuk.com/api/v1/companies/2.json', headers: {"Token" => "API_TOKEN"})
companies = response.body
```

```shell
curl "http://jobhuk.com/api/v1/companies/2.json"
  -H "Token: API_TOKEN"
```

> The above command returns JSON structured like this:

```json
{
    "successful": true,
    "company":{
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
    "logo":"https://jobhuk.s3.amazonaws.com/uploads/company_images/company/image/1089/jobhuk_logo_stacked_600r.jpg",
    "founded":"2014",
    "about":"Jobhuk is a unique self service platform serving as 'CrowdSourced Hiring MarketPlace' .... new marketplace which virtually exists in staffing in email, phone and verbal conversations.",
    "description":"Jobhuk is a unique self service platform serving as 'CrowdSourced Hiring MarketPlace' .... new marketplace which virtually exists in staffing in email, phone and verbal conversations.",
    "social_profile_links":["https://www.facebook.com/Jobhuk", "https://www.linkedin.com/company/jobhuk"],
    "email":"contact@jobhuk.com",
    "about_team":"",
    "tag_line":"recruitment marketplace",
    "about_benefits":"",
    "company_type":"staffing",
    "verified":"true"
    }
}
```

This endpoint retrieves a specific company information.

### HTTP Request

`GET http://jobhuk.com/api/v1/companies/<id>.json`

### URL Parameters

Parameter | Value | Description
--------- | ----- | -----
id | integer | The id of the company to retrieve

## Edit Company

```ruby
require 'httparty'

response = HTTParty.put("http://jobhuk.com/api/v1/companies/2.json", { body: {company: {name: "jobhuk", website: "http://jobhuk.com", phone: 8558558359, company_type: "staffing"}}, headers: {"Token" => "API_TOKEN"} })
company = response.body
```

```shell
curl "http://jobhuk.com/api/v1/companies/2.json"
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
  "logo":"https://jobhuk.s3.amazonaws.com/uploads/company_images/company/image/1089/jobhuk_logo_stacked_600r.jpg",
  "founded":"2014",
  "about":"Jobhuk is a unique self service platform serving as 'CrowdSourced Hiring MarketPlace' .... new marketplace which virtually exists in staffing in email, phone and verbal conversations.",
  "description":"Jobhuk is a unique self service platform serving as 'CrowdSourced Hiring MarketPlace' .... new marketplace which virtually exists in staffing in email, phone and verbal conversations.",
  "social_profile_links":["https://www.facebook.com/Jobhuk", "https://www.linkedin.com/company/jobhuk"],
  "email":"contact@jobhuk.com",
  "about_team":"",
  "tag_line":"recruitment marketplace",
  "about_benefits":"",
  "company_type":"staffing",
  "verified":"true"
}
```

This endpoint updates specific company information given by id.

### HTTP Request

`PUT http://jobhuk.com/api/v1/companies/<id>.json`

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

## All Jobs

```ruby
require 'httparty'

response = HTTParty.get("http://jobhuk.com/api/v1/jobs.json", headers: {"Token" => "API_TOKEN"})
jobs = response.body
```

```shell
curl http://jobhuk.com/api/v1/jobs.json
  -H "Token: API_TOKEN"
```

> The above command returns JSON structured like this:

```json
{
  "successful":true,
  "count":10,
  "jobs":[
    {
      "id":1115,
      "title":"Senior Software Engineer",
      "location":"Austin, TX",
      "description":"his is a senior software engineer position to support the software development for field portable analytical instruments...",
      "job_type":"Contract",
      "comp_range":4,
      "show_market_place":"true",
      "hide_salary":null,
      "active":true,
      "joining_date":null,
      "travel_percentage":null,
      "relocation":null,
      "payment_duration":"60",      
      "client_name":null,
      "compensation":12800,
      "finders_fee_amount":"2400.0",
      "finders_fee":5.0,
      "finders_fee_type":"percentage",
      "hourly_rate":"50.0",
      "duration":8,
      "duration_type":"Weeks",
      "skills":"java, mysql",
      "company": {
          "short_description": "",
          "long_description": "",
          "year_founded": "2013",
          "logo": "https://jobhuk-staging.s3.amazonaws.com/uploads/company_images/company/image/23/Screen_Shot_2014-06-13_at_7.59.14_AM.png",
          "company_type": null,
          "id": 23,
          "name": "Visa Inc11",
          "address": "3500",
          "website": "visa.com",
          "phone": "(111) 111-1111",
          "fax": null,
          "city": "Austin",
          "state": "Texas",
          "zip": "78759",
          "created_at": "2013-06-29T16:27:19-05:00",
          "social_profile_links": null,
          "email": null,
          "about_team": "<p>s</p>\r\n",
          "tag_line": "csssdsd",
          "about_benefits": "<p>s</p>\r\n",
          "verified": false
      }
    }, {
      "id":1116,
      "title":"Senior Software Engineer",
      "location":"Austin, TX",
      "description":"his is a senior software engineer position to support the software development for field portable analytical instruments...",
      "job_type":"Contract"        
    }
  ]
}
```

This endpoint gets all jobs posted in jobhuk.

### HTTP Request

`GET http://jobhuk.com/api/v1/jobs.json`

## My Jobs

```ruby
require 'httparty'

response = HTTParty.get("http://jobhuk.com/api/v1/jobs.json", headers: {"Token" => "API_TOKEN"})
jobs = response.body
```

```shell
curl http://jobhuk.com/api/v1/jobs.json
  -H "Token: API_TOKEN"
```

> The above command returns JSON structured like this:

```json
{
  "successful":true,
  "count":10,
  "jobs":[
    {
      "id":1115,
      "title":"r_api1 job contrat1",
      "location":"hyderabad",
      "description":"this is job from r_api user from api",
      "job_type":"Contract",
      "comp_range":4,
      "show_market_place":"true",
      "hide_salary":null,
      "active":true,
      "joining_date":null,
      "travel_percentage":null,
      "relocation":null,
      "payment_duration":"60",
      "city":"Hyderabad",
      "state":"Andhra Pradesh",
      "country":"India",
      "country_code":null,
      "zip_code":null,
      "client_name":null,
      "compensation":12800,
      "finders_fee_amount":"2400.0",
      "finders_fee":5.0,
      "finders_fee_type":"percentage",
      "hourly_rate":"50.0",
      "duration":8,
      "duration_type":"Weeks",
      "skills":"java, orcale",
      "company": {
          "short_description": "<p>Visa...</p>\r\n",
          "long_description": "<p>s</p>\r\n",
          "year_founded": "2013",
          "logo": "https://jobhuk-staging.s3.amazonaws.com/uploads/company_images/company/image/23/Screen_Shot_2014-06-13_at_7.59.14_AM.png",
          "company_type": null,
          "id": 23,
          "name": "Visa Inc11",
          "address": "3500",
          "website": "visa.com",
          "phone": "(111) 111-1111",
          "fax": null,
          "city": "Austin",
          "state": "Texas",
          "zip": "78759",
          "created_at": "2013-06-29T16:27:19-05:00",
          "social_profile_links": null,
          "email": null,
          "about_team": "<p>s</p>\r\n",
          "tag_line": "csssdsd",
          "about_benefits": "<p>s</p>\r\n",
          "verified": false
      }
    }, {
      "id":1115,
      "title":"r_api1 job contrat1",
      "location":"hyderabad",
      "description":"this is job from r_api user from api",
      "job_type":"Contract"        
    }
  ]
}
```

This endpoint get list of jobs approved by jobhuk admin and posted by you in jobhuk

### HTTP Request

`GET http://jobhuk.com/api/v1/my_jobs.json`

## Create Job

```ruby
require 'httparty'

response = HTTParty.post("http://jobhuk.com/api/v1/my_jobs.json", {body: {job: {company_id: 297, title: 'Senior Software Engineer', description: 'This is a senior software engineer position to support the software development for field portable analytical instruments...', location: 'Austin, TX', job_type: 'FullTime', comp_range: 5, compensation: 100000, finders_fee_type: 'percentage', finders_fee: 5, skills: 'Java, Oracle', industry: 'engineering'}}, headers: {"Token" => API_TOKEN}})
job = response.body
```

```shell
curl http://jobhuk.com/api/v1/my_jobs.json
  -X POST
  -H "Token: API_TOKEN"
  --data "job[company_id]=297&job[title]=Senior Software Engineer&job[description]=This is a senior software engineer position to support the software development for field portable analytical instruments...&job[location]=Austin, TX&job[job_type]=FullTime&job[comp_range]=5&job[compensation]=100000&job[finders_fee_type]=percentage&job[finders_fee]=5&job[skills]=Java, Oracle&job[industry]=engineering"
```

> The above command returns JSON structured like this:

```json
{
  "successful":true,
  "job": {
    "id":1117,
    "title":"Senior Software Engineer",
    "location":"Austin, TX",
    "description":"This is a senior software engineer position to support the software development for field portable analytical instruments...",
    "job_type":"FullTime",
    "comp_range":5,
    "show_market_place":true,
    "hide_salary":true,
    "active":true,
    "joining_date":null,
    "travel_percentage":null,
    "relocation":null,
    "payment_duration":"60",
    "city":"Austin",
    "state":"TX",
    "country":"United States",
    "country_code":null,
    "zip_code":null,
    "client_name":null,
    "compensation":100000,
    "finders_fee_amount":"4000.0",
    "finders_fee":5.0,
    "finders_fee_type":"percentage",
    "hourly_rate":null,
    "duration":null,
    "duration_type":null,
    "skills":"Java, Oracle",
    "company": {
      "short_description": "<p>Visa...</p>\r\n",
      "long_description": "<p>s</p>\r\n",
      "year_founded": "2013",
      "logo": "https://jobhuk-staging.s3.amazonaws.com/uploads/company_images/company/image/23/Screen_Shot_2014-06-13_at_7.59.14_AM.png",
      "company_type": null,
      "id": 23,
      "name": "Visa Inc11",
      "address": "3500",
      "website": "visa.com",
      "phone": "(111) 111-1111",
      "fax": null,
      "city": "Austin",
      "state": "Texas",
      "zip": "78759",
      "created_at": "2013-06-29T16:27:19-05:00",
      "social_profile_links": null,
      "email": null,
      "about_team": "<p>s</p>\r\n",
      "tag_line": "csssdsd",
      "about_benefits": "<p>s</p>\r\n",
      "verified": false
    }
  } 
}
```

This endpoint post a job in jobhuk.

### HTTP Request

`POST http://jobhuk.com/api/v1/jobs.json`

### POST Parameters

Parameter | Value   | Description
--------- | ------  | -----------
job<br>required | hash | job fields hash
job[company_id]<br>required | integer | company id for job
job[title]<br>required | string | title of the job
job[description]<br>required | string | description of the job
job[location]<br>required | string | location of the job
job[job_type]<br>required | string | type of the job<br>Must be one of FullTime, Contract. 
job[comp_range]<br>optional | integer | compensation range in percentage
job[compensation]<br>required for fulltime jobs | integer | candidate compensation for job
job[finders_fee_type]<br>required for fulltime jobs | string | finders fee type Must be one of percentage, fixed. 
job[finders_fee]<br>required for fulltime jobs | integer | finders fee percentage if finders fee type is percentage
job[finders_fee_amount]<br>required for fulltime jobs | integer | finders fee amount if finders fee type is fixed
job[duration_type]<br>required for contract jobs | string | Must be one of Hours, Weeks, Months.  
job[duration]<br>required for contract jobs | integer | job duration like 320 hours or 4 weeks or 2 months
job[hourly_rate]<br>required for contract jobs | integer | hourly rate for contract jobs.
job[active]<br>optional | boolean | job active for candidates to apply.
job[show_market_place]<br>optional | boolean | true showing jobhuk market place.
job[joining_date]<br>optional | string | candidate joining date Must be yyyy-mm-dd format.
job[travel_percentage]<br>optional | integer | candidate relocation charges percentage 
job[relocation]<br>optional | boolean | is candidate ready to relocation for job 
job[payment_duration]<br>optional | integer | finders fee payment duration in days
job[client_name]<br>optional | string | client company name for this job if required
job[skills]<br>optional | string | list skills required for this job comma separated.
job[industry]<br>optional | string | job industry type

## Get Job

```ruby
require 'httparty'

response = HTTParty.get("http://jobhuk.com/api/v1/jobs/1117.json", headers: {"Token" => "API_TOKEN"})
job = response.body
```

```shell
curl http://jobhuk.com/api/v1/jobs/1117.json
  -H "Token:API_TOKEN"
```

> The above command returns JSON structured like this:

```json
{
  "successful":true,
  "job": {
    "id":1117,
    "title":"Senior Software Engineer",
    "location":"Austin, TX",
    "description":"This is a senior software engineer position to support the software development for field portable analytical instruments...",
    "job_type":"FullTime",
    "comp_range":5,
    "show_market_place":true,
    "hide_salary":true,
    "active":true,
    "joining_date":null,
    "travel_percentage":null,
    "relocation":null,
    "payment_duration":"60",
    "city":"Austin",
    "state":"TX",
    "country":"United States",
    "country_code":null,
    "zip_code":null,
    "client_name":null,
    "compensation":100000,
    "finders_fee_amount":"4000.0",
    "finders_fee":5.0,
    "finders_fee_type":"percentage",
    "hourly_rate":null,
    "duration":null,
    "duration_type":null,
    "skills":"Java, Oracle",
    "company": {
      "short_description": "<p>Visa...</p>\r\n",
      "long_description": "<p>s</p>\r\n",
      "year_founded": "2013",
      "logo": "https://jobhuk-staging.s3.amazonaws.com/uploads/company_images/company/image/23/Screen_Shot_2014-06-13_at_7.59.14_AM.png",
      "company_type": null,
      "id": 23,
      "name": "Visa Inc11",
      "address": "3500",
      "website": "visa.com",
      "phone": "(111) 111-1111",
      "fax": null,
      "city": "Austin",
      "state": "Texas",
      "zip": "78759",
      "created_at": "2013-06-29T16:27:19-05:00",
      "social_profile_links": null,
      "email": null,
      "about_team": "<p>s</p>\r\n",
      "tag_line": "csssdsd",
      "about_benefits": "<p>s</p>\r\n",
      "verified": false
    }
  } 
}
```

This endpoint get a specific job details given by id

### HTTP Request

`GET http://jobhuk.com/api/v1/jobs/<id>.json`

### URL Parameters

Parameter | Value   | Description
--------- | ------  | -----------
id<br>required | integer | unique job id

## Edit Job

```ruby
require 'httparty'

response = HTTParty.put("http://jobhuk.com/api/v1/jobs/1117.json", {body: {job: {company_id: 297, title: 'Senior Software Engineer', description: 'This is a senior software engineer position to support the software development for field portable analytical instruments...', location: 'Austin, TX', job_type: 'FullTime', comp_range: 5, compensation: 100000, finders_fee_type: 'percentage', finders_fee: 5, skills: 'Java, Oracle', industry: 'engineering'}}, headers: {"Token" => API_TOKEN}})
job = response.body
```

```shell
curl http://jobhuk.com/api/v1/jobs/1117.json
  -X PUT
  -H "Token: API_TOKEN"
  --data "job[company_id]=297&job[title]=Senior Software Engineer&job[description]=This is a senior software engineer position to support the software development for field portable analytical instruments...&job[location]=Austin, TX&job[job_type]=FullTime&job[comp_range]=5&job[compensation]=100000&job[finders_fee_type]=percentage&job[finders_fee]=5&job[skills]=Java, Oracle&job[industry]=engineering"
```

> The above command returns JSON structured like this:

```json
{
  "successful":true,
  "job": {
    "id":1117,
    "title":"Senior Software Engineer",
    "location":"Austin, TX",
    "description":"This is a senior software engineer position to support the software development for field portable analytical instruments...",
    "job_type":"FullTime",
    "comp_range":5,
    "show_market_place":true,
    "hide_salary":true,
    "active":true,
    "joining_date":null,
    "travel_percentage":null,
    "relocation":null,
    "payment_duration":"60",
    "city":"Austin",
    "state":"TX",
    "country":"United States",
    "country_code":null,
    "zip_code":null,
    "client_name":null,
    "compensation":100000,
    "finders_fee_amount":"4000.0",
    "finders_fee":5.0,
    "finders_fee_type":"percentage",
    "hourly_rate":null,
    "duration":null,
    "duration_type":null,
    "skills":"Java, Oracle",
    "company": {
      "short_description": "<p>Visa...</p>\r\n",
      "long_description": "<p>s</p>\r\n",
      "year_founded": "2013",
      "logo": "https://jobhuk-staging.s3.amazonaws.com/uploads/company_images/company/image/23/Screen_Shot_2014-06-13_at_7.59.14_AM.png",
      "company_type": null,
      "id": 23,
      "name": "Visa Inc11",
      "address": "3500",
      "website": "visa.com",
      "phone": "(111) 111-1111",
      "fax": null,
      "city": "Austin",
      "state": "Texas",
      "zip": "78759",
      "created_at": "2013-06-29T16:27:19-05:00",
      "social_profile_links": null,
      "email": null,
      "about_team": "<p>s</p>\r\n",
      "tag_line": "csssdsd",
      "about_benefits": "<p>s</p>\r\n",
      "verified": false
    }
  } 
}
```

This endpoint edit specific job details given by id

### HTTP Request

`PUT http://jobhuk.com/api/v1/jobs/<id>.json`

### POST Parameters

Parameter | Value   | Description
--------- | ------  | -----------
id<br>required | integer | unique job id
job<br>required | hash | job fields hash
job[company_id]<br>required | integer | company id for job
job[title]<br>required | string | title of the job
job[description]<br>required | string | description of the job
job[location]<br>required | string | location of the job
job[job_type]<br>required | string | type of the job<br>Must be one of FullTime, Contract. 
job[comp_range]<br>optional | integer | compensation range in percentage
job[compensation]<br>required for fulltime jobs | integer | candidate compensation for job
job[finders_fee_type]<br>required for fulltime jobs | string | finders fee type Must be one of percentage, fixed. 
job[finders_fee]<br>required for fulltime jobs | integer | finders fee percentage if finders fee type is percentage
job[finders_fee_amount]<br>required for fulltime jobs | integer | finders fee amount if finders fee type is fixed
job[duration_type]<br>required for contract jobs | string | Must be one of Hours, Weeks, Months.  
job[duration]<br>required for contract jobs | integer | job duration like 320 hours or 4 weeks or 2 months
job[hourly_rate]<br>required for contract jobs | integer | hourly rate for contract jobs.
job[active]<br>optional | boolean | job active for candidates to apply.
job[show_market_place]<br>optional | boolean | true showing jobhuk market place.
job[joining_date]<br>optional | string | candidate joining date Must be yyyy-mm-dd format.
job[travel_percentage]<br>optional | integer | candidate relocation charges percentage 
job[relocation]<br>optional | boolean | is candidate ready to relocation for job 
job[payment_duration]<br>optional | integer | finders fee payment duration in days
job[client_name]<br>optional | string | client company name for this job if required
job[skills]<br>optional | string | list skills required for this job comma separated.
job[industry]<br>optional | string | job industry type

## Delete Job

```ruby
require 'httparty'

response = HTTParty.delete("http://jobhuk.com/api/v1/jobs/1117.json", headers: {"Token" => "API_TOKEN"})
```

```shell
curl http://jobhuk.com/api/v1/jobs/1117.json
  -X DELETE
  -H "Token: API_TOKEN"
  
```

> The above command returns JSON structured like this:

```json
{
    "successful": true,
    "job": "Deleted successfully 1117. This operation is irreversible."
}
```

This endpoint deletes specific job given by id.
This operation is irreversible.

### HTTP Request

`DELETE http://jobhuk.com/api/v1/jobs/<id>.json`

### URL Parameters

Parameter | Value   | Description
--------- | ------  | -----------
id<br>required | integer | unique job id

# Candidates

## Submit Candidate
```ruby
require 'httparty'

response = HTTParty.post("http://jobhuk.com/api/v1/jobs/1115/candidates", query: {candidate: {name: "john", email: "johnd@hatchforce.com", phone: 8558558359, public_profile_url: "https://www.linkedin.com/in/scottsantucci", :resume_file => File.new('/home/user/Downloads/josha_d.pdf')}},{headers:{"Token"=>"API_TOKEN"}})
candidate = response.body
```

```shell
 curl "https/jobhuk.com/api/v1/jobs/1121/candidates"
   -X POST 
   -H "Token: API_TOKEN"
   -F "candidate[name]=john" 
   -F "candidate[email]=johnd@hatchforce.com" 
   -F "candidate[phone]=1234567890" 
   -F "candidate[public_profile_url]=https://www.linkedin.com/in/scottsantucci" 
   -F "candidate[resume_file]=@/home/user/downloads/johnd_cv.docx" 
```

> The above command returns JSON structured like this:

```json
{
  "successful": true,
  "success": "Resume submitted successfully",
  "candidate": {
    "submission": {
        "candidate_action": null,
        "contact_details": "name: john, Email: johnd@hatchforce.com",
        "created_at": "2015-04-18T06:06:42-05:00",
        "expire_at": null,
        "id": 534,
        "job_id": 1121,
        "phone_number": "1234567890",
        "public_profile_url": "https://www.linkedin.com/in/scottsantucci",
        "referral_id": 812,
        "submission_type": "resume",
        "updated_at": "2015-04-18T06:06:42-05:00",
        "user_id": 667
    },
    "referral": {
        "admin_approved": null,
        "another_source_discard": null,
        "candidate": "johnd@hatchforce.com",
        "candidate_action": null,
        "candidate_rating": null,
        "candidate_type": null,
        "created_at": "2015-04-18T06:06:42-05:00",
        "discard_feedback": null,
        "discarded_by": null,
        "expertise_in": null,
        "hire_feedback": null,
        "id": 812,
        "job_id": 1115,
        "match_score": null,
        "matching_skills": null,
        "notes": null,
        "referral_rating": null,
        "referral_type": "referral_submission",
        "status": "submitted",
        "tag": null,
        "target_user_id": 667,
        "token": "7b7283c4",
        "updated_at": "2015-04-18T06:06:42-05:00",
        "user_id": 640,
        "verified": false
    },
    "candidate": {
        "account_type": "individual",
        "active_company_id": null,
        "balanced_customer_id": null,
        "balanced_customer_uri": null,
        "blocked": false,
        "created_at": "2015-04-18T06:06:27-05:00",
        "deleted_at": null,
        "digest_frequency": 3,
        "email": "johnd@hatchforce.com",
        "facebook_auto_post": false,
        "id": 667,
        "job_alert_flag": null,
        "job_alert_skill": null,
        "job_new_alert": null,
        "linkedin_auto_post": false,
        "slug": "johnd",
        "token": "932be4f1",
        "twitter_auto_post": false,
        "updated_at": "2015-04-18T06:06:40-05:00",
        "vetted": false
    }
  }
}
```

This endpoint submit's candidate to specific job.

### HTTP Request

`POST http://jobhuk.com/api/v1/jobs/<job_id>/candidates`

### POST Parameters

Parameter | Value   | Description
--------- | ------  | -----------
job_id<br>required | integer | unique job id
candidate[name]<br>required | string | Name of the candidate
candidate[email]<br>required | string | Email of the candidate
candidate[phone]<br>required | integer | Phone number of the candidate
candidate[resume_file]<br>required | string | candidate resume file
candidate[public_profile_url]<br>required | string | candidate's linkedin or facebook profile urls

## All Candidates
```ruby
require 'httparty'

response = HTTParty.get("http://jobhuk.com/api/v1/jobs/1117/candidates", headers: {"Token" => "API_TOKEN"})
candidates = response.body
```

```shell
curl http://jobhuk.com/api/v1/jobs/1117/candidates 
  -H "Token:API_TOKEN"
```

> The above command returns JSON structured like this:

```json
{
  "successful": true,
  "submitted_users": [{
    "submission_id": 533,
    "job_id": 1115,
    "candidate": {
        "name": "John",
        "profile_image": "https://jobhuk.com/assets/profile.jpeg",
        "profile_page": "http://jobhuk.com/me/johnd"
    },
    "referral_status": "submitted",
    "discard_feedback": 0,
    "candidate_rating": 0,
    "referral_rating": 0,
    "hire_feedback": 0,
    "resume": "https://jobhuk-staging.s3.amazonaws.com/uploads/resume/resume/resume_file/414/Sr__ROR_Developer.docx",
    "interview_details": {},
    "conversations_count": 0,
    "verified": false,
    "discarded_by": " "
  }, {
    "submission_id": 521,
    "job_id": 1115,
    "candidate": {
        "name": "Alex",
        "profile_image": "https://jobhuk.com/assets/profile.jpeg",
        "profile_page": "http://jobhuk.com/me/alexd"
    },
    "referral_status": "submitted",
    "discard_feedback": 0,
    "candidate_rating": 2,
    "referral_rating": 3,
    "hire_feedback": 0,
    "resume": "https://jobhuk-staging.s3.amazonaws.com/uploads/resume/resume/resume_file/402/Sr__ROR_Developer.docx",
    "interview_details": {},
    "conversations_count": 0,
    "verified": false,
    "discarded_by": " "
  }]
}
```

This endpoint returns all candidates for this job.

### HTTP Request

`GET http://jobhuk.com/api/v1/jobs/<job_id>/candidates`

### URL Parameters

Parameter | Value   | Description
--------- | ------  | -----------
job_id<br>required | integer | unique job id

## Submitted Candidates

```ruby
require 'httparty'

response = HTTParty.get("http://jobhuk.com/api/v1/jobs/1115/submitted_candidates", headers: {"Token" => "API_TOKEN"})
candidates = response.body
```

```shell
curl http://jobhuk.com/api/v1/jobs/1115/submitted_candidates 
  -H "Token:API_TOKEN"
```

> The above command returns JSON structured like this:

```json
{
  "successful": true,
  "submitted_users": [{
    "submission_id": 533,
    "job_id": 1115,
    "candidate": {
        "name": "John",
        "profile_image": "https://jobhuk.com/assets/profile.jpeg",
        "profile_page": "http://jobhuk.com/me/johnd"
    },
    "referral_status": "submitted",
    "discard_feedback": 0,
    "candidate_rating": 0,
    "referral_rating": 0,
    "hire_feedback": 0,
    "resume": "https://jobhuk-staging.s3.amazonaws.com/uploads/resume/resume/resume_file/414/Sr__ROR_Developer.docx",
    "interview_details": {},
    "conversations_count": 0,
    "verified": false,
    "discarded_by": " "
  }, {
    "submission_id": 521,
    "job_id": 1115,
    "candidate": {
        "name": "Alex",
        "profile_image": "https://jobhuk.com/assets/profile.jpeg",
        "profile_page": "http://jobhuk.com/me/alexd"
    },
    "referral_status": "submitted",
    "discard_feedback": 0,
    "candidate_rating": 2,
    "referral_rating": 3,
    "hire_feedback": 0,
    "resume": "https://jobhuk-staging.s3.amazonaws.com/uploads/resume/resume/resume_file/402/Sr__ROR_Developer.docx",
    "interview_details": {},
    "conversations_count": 0,
    "verified": false,
    "discarded_by": " "
  }]
}
```

This endpoint returns specific candidates submitted to job by you as a recruiter

### HTTP Request

`GET http://jobhuk.com/api/v1/jobs/<job_id>/submitted_candidates`

### URL Parameters

Parameter | Value   | Description
--------- | ------  | -----------
job_id<br>required | integer | unique job id


## Get Candidate

```ruby
require 'httparty'

response = HTTParty.get("http://jobhuk.com/api/v1/jobs/1115/candidates/536", headers: {"Token" => "API_TOKEN"})
candidates = response.body
```

```shell
curl http://jobhuk.com/api/v1/jobs/1115/candidates/536 
  -H "Token:API_TOKEN"
```

> The above command returns JSON structured like this:

```json
{
    "successful": true,
    "candidate": {
        "submission": {
            "id": 535,
            "job_id": 1115,
            "user_id": 668,
            "referral_id": 813,
            "submission_type": "resume",
            "contact_details": "name: John, Email: johnd@hatchforce.com",
            "candidate_action": null,
            "phone_number": "1234567812",
            "public_profile_url": "https://www.linkedin.com/in/scottsantucci",
            "expire_at": null,
            "created_at": "2015-04-18T07:36:35-05:00",
            "updated_at": "2015-04-18T07:36:35-05:00"
        },
        "user": {
            "name": "John",
            "profile_image": "https://jobhuk.com/assets/profile.jpeg",
            "profile_page": "http://whosflying.com/me/johnd"
        },
        "referral_status": "submitted",
        "referral_tag": null,
        "resume": "https://jobhuk-staging.s3.amazonaws.com/uploads/resume/resume/resume_file/416/we2.txt",
        "interview_details": null,
        "feedback": null,
        "conversations_count": 0,
        "job": {
            "id": 1115,
            "title": "r_api1 job contrat1",
            "location": "hyderabad",
            "description": "this is job from r_api user from api",
            "job_type": "Contract",
            "comp_range": 4,
            "show_market_place": true,
            "hide_salary": null,
            "active": true,
            "joining_date": null,
            "travel_percentage": null,
            "relocation": null,
            "payment_duration": "60",
            "city": "Hyderabad",
            "state": "Andhra Pradesh",
            "country": "India",
            "country_code": null,
            "zip_code": null,
            "client_name": null,
            "compensation": 12800,
            "finders_fee_amount": "2400.0",
            "finders_fee": 5,
            "finders_fee_type": "percentage",
            "hourly_rate": "50.0",
            "duration": 8,
            "duration_type": "Weeks",
            "skills": "",
            "company": {
                "short_description": null,
                "long_description": null,
                "year_founded": null,
                "logo": "https://jobhuk.com/assets/company.png",
                "company_type": "staffing",
                "id": 297,
                "name": "r_api11",
                "address": null,
                "website": "r_api1.com",
                "phone": "1112223333",
                "fax": null,
                "city": null,
                "state": null,
                "zip": null,
                "created_at": "2015-04-16T04:15:14-05:00",
                "social_profile_links": null,
                "email": null,
                "about_team": null,
                "tag_line": null,
                "about_benefits": null,
                "verified": false
            }
        }
    }
}
```

This endpoint returns submitted candidate details to specific job 

### HTTP Request

`GET http://jobhuk.com/api/v1/jobs/<job_id>/candidates/<id>`

### URL Parameters

Parameter | Value   | Description
--------- | ------  | -----------
job_id<br>required | integer | unique job id
id<br>required | integer | unique candidate id

# Industries

## Get Industries

```ruby
require 'httparty'

response = HTTParty.get("http://jobhuk.com/api/v1/industries", headers: {"Token" => "API_TOKEN"})
candidates = response.body
```

```shell
curl http://jobhuk.com/api/v1/industries 
  -H "Token:API_TOKEN"
```

> The above command returns JSON structured like this:

```json
{
    "successful": true,
    "industries": [
        {
            "id": 59,
            "name": "Human Resources"
        },          
        {
            "id": 175,
            "name": "Product Management"
        },
        {
            "id": 176,
            "name": "Customer Service"
        },
        {
            "id": 177,
            "name": "Quality Assurance"
        },         
        {
            "id": 184,
            "name": "Other"
        }
    ]
}
```

This endpoint returns list of industries 

### HTTP Request

`GET http://jobhuk.com/api/v1/industries`


