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

response = HTTParty.get('http://api.jobhuk.com/companies.json', headers: {"Token" => "API_TOKEN"})
companies = response.body
```

```shell
curl "http://api.jobhuk.com/companies.json"
  -H "Token: API_TOKEN"  
```

> Make sure to replace `API_TOKEN` with your API key.

Jobhuk uses API keys to allow access to the API. [Get API TOKEN](http://developer.jobhuk.com/api).

Jobhuk expects for the API_TOKEN to be included in all API requests to the server in a header that looks like the following:

`Token: API_TOKEN`

`ACCEPT: application/vnd.jobhuk.v1`

<aside class="notice">
You must replace `API_TOKEN` with your personal API key.
</aside>

# Companies 

## List of Companies

```ruby
require 'httparty'

response = HTTParty.get('http://api.jobhuk.com/companies.json', headers: {"Token" => "API_TOKEN"})
companies = response.body
```

```shell
curl "http://api.jobhuk.com/companies.json"
  -H "Token: API_TOKEN"  
```

> The above command returns JSON structured like this:

```json
{
    "successful": true,
    "count": 2,
    "active_company_id": "1281",
    "companies": [
        {
            "short_description": "jobhukapi",
            "long_description": "Jobhuk API is an austin based company",
            "year_founded": "2010",
            "logo": "https://jobhuk.s3.amazonaws.com/uploads/company_images/company/image/1281/header_logo-1dc784d557ca8383748e986a661bd504.png",
            "company_type": "employer",
            "id": 1281,
            "name": "JobhukAPI",
            "address": "#302 ",
            "website": "www.jobhukapi.com",
            "phone": "1234567890",
            "fax": "0987654321",
            "city": "Austin",
            "state": "TX",
            "zip": "78703",
            "created_at": "2015-04-20T06:18:05-05:00",
            "social_profile_links": null,
            "email": "care@jobhukapi.com",
            "about_team": "jobhukapi.com",
            "tag_line": "Jobhuk API",
            "about_benefits": "jobhukapi.com",
            "verified": false
        },
        {
            "short_description": "venkysoft",
            "long_description": "venkysoft is a austin based comapany",
            "year_founded": "2010"
        }
    ]
}
```

This endpoint retrieves list of companies created by you.

### HTTP Request

`GET http://api.jobhuk.com/companies`

## Create Company

```ruby
require 'httparty'

response = HTTParty.post("http://api.jobhuk.com/companies.json", { body: {company: {name: "jobhuk", website: "http://jobhuk.com", phone: 8558558359, company_type: "staffing"}}, headers: {"Token" => "API_TOKEN"} })
company = response.body
```

```shell
curl "http://api.jobhuk.com/companies.json"
  -X POST 
  -H "Token:TW6SV34JL+M/WaVMY0tytrII2PJ1xAjSkV73qq2Gmzgv+8q0zSeIhijCLVSc9eSEb9jjuug/8ZtucVSacMFgeA=="
  --data "company[name]=test110&company[website]=test110.com&company[phone]=1234567890" 
```

> The above command returns JSON structured like this:

```json
{
    "successful": true,
    "company": {
        "id": 1281,
        "name": "jobhukapi",
        "website": "www.jobhukapi.com",
        "company_type": "employer",
        "phone": "1234567890",
        "tag_line": "jobhukapi",
        "address": "suite no 302",
        "fax": "0987654321",
        "city": "Austin",
        "state": "TX",
        "zip": "78703",
        "logo": "https://jobhuk.s3.amazonaws.com/uploads/company_images/company/image/1283/header_logo-1dc784d557ca8383748e986a661bd504.png",
        "year_founded": "2010",
        "short_description": "jobhukapi",
        "long_description": "Jobhuk API is an austin based company",
        "email": "care@jobhukapi.com",
        "about_team": "jobhukapi",
        "about_benefits": "jobhukapi"
    }
}
```

This endpoint creates a company in jobhuk.

### HTTP Request

`POST http://api.jobhuk.com/companies.json`

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

response = HTTParty.get('http://api.jobhuk.com/companies/1281.json', headers: {"Token" => "API_TOKEN"})
companies = response.body
```

```shell
curl "http://api.jobhuk.com/companies/1281.json"
  -H "Token: API_TOKEN"
```

> The above command returns JSON structured like this:

```json
{
    "successful": true,
    "company": {
        "short_description": "jobhukapi",
        "long_description": "Jobhuk API is an austin based company",
        "year_founded": "2010",
        "logo": "https://jobhuk.s3.amazonaws.com/uploads/company_images/company/image/1281/header_logo-1dc784d557ca8383748e986a661bd504.png",
        "company_type": "employer",
        "id": 1281,
        "name": "jobhukapi test",
        "address": "suite no 302",
        "website": "www.jobhukapi.com",
        "phone": "1234567890",
        "fax": "0987654321",
        "city": "Austin",
        "state": "TX",
        "zip": "78703",
        "created_at": "2015-04-20T06:18:05-05:00",
        "social_profile_links": null,
        "email": "care@jobhukapi.com",
        "about_team": "jobhukapi",
        "tag_line": "jobhukapi",
        "about_benefits": "jobhukapi",
        "verified": false
    }
}
```

This endpoint retrieves a specific company information.

### HTTP Request

`GET http://api.jobhuk.com/companies/<id>.json`

### URL Parameters

Parameter | Value | Description
--------- | ----- | -----
id | integer | The id of the company to retrieve

## Edit Company

```ruby
require 'httparty'

response = HTTParty.put("http://api.jobhuk.com/companies/1281.json", { body: {company: {name: "jobhuk", website: "http://jobhuk.com", phone: 8558558359, company_type: "staffing"}}, headers: {"Token" => "API_TOKEN"} })
company = response.body
```

```shell
curl "http://api.jobhuk.com/companies/1281.json"
  -X POST 
  -H "Token:TW6SV34JL+M/WaVMY0tytrII2PJ1xAjSkV73qq2Gmzgv+8q0zSeIhijCLVSc9eSEb9jjuug/8ZtucVSacMFgeA=="
  --data "company[name]=test110&company[website]=test110.com&company[phone]=1234567890" 
```

> The above command returns JSON structured like this:

```json
{
    "successful": true,
    "message": "Successfully updated company.",
    "company": {
        "short_description": "jobhukapi",
        "long_description": "Jobhuk API is an austin based company",
        "year_founded": "2010",
        "logo": "https://jobhuk.s3.amazonaws.com/uploads/company_images/company/image/1281/header_logo-1dc784d557ca8383748e986a661bd504.png",
        "company_type": "employer",
        "id": 1281,
        "name": "jobhukapi test",
        "address": "suite no 302",
        "website": "www.jobhukapi.com",
        "phone": "1234567890",
        "fax": "0987654321",
        "city": "Austin",
        "state": "TX",
        "zip": "78703",
        "created_at": "2015-04-20T06:18:05-05:00",
        "social_profile_links": null,
        "email": "care@jobhukapi.com",
        "about_team": "jobhukapi",
        "tag_line": "jobhukapi",
        "about_benefits": "jobhukapi",
        "verified": false
    }
}
```

This endpoint updates specific company information given by id.

### HTTP Request

`PUT http://api.jobhuk.com/companies/<id>.json`

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

response = HTTParty.get("http://api.jobhuk.com/jobs.json", headers: {"Token" => "API_TOKEN"})
jobs = response.body
```

```shell
curl http://api.jobhuk.com/jobs.json
  -H "Token: API_TOKEN"
```

> The above command returns JSON structured like this:

```json
{
    "successful": true,
    "count": 2,
    "jobs": [
        {
            "id": 1318,
            "title": "Ruby Senior Programmer ",
            "location": "Auxtin",
            "description": "Ruby Programmer ",
            "job_type": "FullTime",
            "comp_range": 0,
            "show_market_place": true,
            "hide_salary": true,
            "active": true,
            "joining_date": null,
            "travel_percentage": null,
            "relocation": null,
            "payment_duration": "60",
            "city": "Austin",
            "state": "TX",
            "country": "United States",
            "country_code": null,
            "zip_code": null,
            "client_name": null,
            "compensation": 120000,
            "finders_fee_amount": "8640.0",
            "finders_fee": 9,
            "finders_fee_type": "percentage",
            "hourly_rate": null,
            "duration": null,
            "duration_type": null,
            "skills": "ruby, rails, jquery, mysql",
            "industry": {
                "id": 181,
                "name": "it industry"
            },
            "company": {
                "short_description": "jobhukapi",
                "long_description": "Jobhuk API is an austin based company",
                "year_founded": "2010",
                "logo": "https://jobhuk.s3.amazonaws.com/uploads/company_images/company/image/1281/header_logo-1dc784d557ca8383748e986a661bd504.png",
                "company_type": "employer",
                "id": 1281,
                "name": "jobhukapi test",
                "address": "suite no 302",
                "website": "www.jobhukapi.com",
                "phone": "1234567890",
                "fax": "0987654321",
                "city": "Austin",
                "state": "TX",
                "zip": "78703",
                "created_at": "2015-04-20T06:18:05-05:00",
                "social_profile_links": null,
                "email": "care@jobhukapi.com",
                "about_team": "jobhukapi",
                "tag_line": "jobhukapi",
                "about_benefits": "jobhukapi",
                "verified": false
            }
        },
        {
          "id": 1317,
          "title": "Ruby Programmer ",
          "location": "Auxtin"          
        }
    ]
}
```

This endpoint gets all jobs posted in jobhuk.

### HTTP Request

`GET http://api.jobhuk.com/jobs.json`

## My Jobs

```ruby
require 'httparty'

response = HTTParty.get("http://api.jobhuk.com/my_jobs.json", headers: {"Token" => "API_TOKEN"})
jobs = response.body
```

```shell
curl http://api.jobhuk.com/my_jobs.json
  -H "Token: API_TOKEN"
```

> The above command returns JSON structured like this:

```json
{
    "successful": true,
    "count": 2,
    "jobs": [
        {
            "id": 1318,
            "title": "Ruby Senior Programmer ",
            "location": "Auxtin",
            "description": "Ruby Programmer ",
            "job_type": "FullTime",
            "comp_range": 0,
            "show_market_place": true,
            "hide_salary": true,
            "active": true,
            "joining_date": null,
            "travel_percentage": null,
            "relocation": null,
            "payment_duration": "60",
            "city": "Austin",
            "state": "TX",
            "country": "United States",
            "country_code": null,
            "zip_code": null,
            "client_name": null,
            "compensation": 120000,
            "finders_fee_amount": "8640.0",
            "finders_fee": 9,
            "finders_fee_type": "percentage",
            "hourly_rate": null,
            "duration": null,
            "duration_type": null,
            "skills": "ruby, rails, jquery, mysql",
            "industry": {
                "id": 181,
                "name": "it industry"
            },
            "company": {
                "short_description": "jobhukapi",
                "long_description": "Jobhuk API is an austin based company",
                "year_founded": "2010",
                "logo": "https://jobhuk.s3.amazonaws.com/uploads/company_images/company/image/1281/header_logo-1dc784d557ca8383748e986a661bd504.png",
                "company_type": "employer",
                "id": 1281,
                "name": "jobhukapi test",
                "address": "suite no 302",
                "website": "www.jobhukapi.com",
                "phone": "1234567890",
                "fax": "0987654321",
                "city": "Austin",
                "state": "TX",
                "zip": "78703",
                "created_at": "2015-04-20T06:18:05-05:00",
                "social_profile_links": null,
                "email": "care@jobhukapi.com",
                "about_team": "jobhukapi",
                "tag_line": "jobhukapi",
                "about_benefits": "jobhukapi",
                "verified": false
            }
        },
        {
          "id": 1317,
          "title": "Ruby Programmer ",
          "location": "Auxtin"          
        }
    ]
}
```

This endpoint get list of jobs approved by jobhuk admin and posted by you in jobhuk

### HTTP Request

`GET http://api.jobhuk.com/my_jobs.json`

## Create Job

```ruby
require 'httparty'

response = HTTParty.post("http://api.jobhuk.com/jobs.json.json", {body: {job: {company_id: 297, title: 'Senior Software Engineer', description: 'This is a senior software engineer position to support the software development for field portable analytical instruments...', location: 'Austin, TX', job_type: 'FullTime', comp_range: 5, compensation: 100000, finders_fee_type: 'percentage', finders_fee: 5, skills: 'Java, Oracle', industry: 'engineering'}}, headers: {"Token" => API_TOKEN}})
job = response.body
```

```shell
curl http://api.jobhuk.com/jobs.json
  -X POST
  -H "Token: API_TOKEN"
  --data "job[company_id]=297&job[title]=Senior Software Engineer&job[description]=This is a senior software engineer position to support the software development for field portable analytical instruments...&job[location]=Austin, TX&job[job_type]=FullTime&job[comp_range]=5&job[compensation]=100000&job[finders_fee_type]=percentage&job[finders_fee]=5&job[skills]=Java, Oracle&job[industry]=engineering"
```

> The above command returns JSON structured like this:

```json
{
    "successful": true,
    "code": 200,
    "job": {
        "id": 1318,
        "title": "Ruby Programmer ",
        "location": "Auxtin",
        "description": "Ruby Programmer ",
        "job_type": "FullTime",
        "comp_range": 0,
        "show_market_place": true,
        "hide_salary": true,
        "active": true,
        "joining_date": null,
        "travel_percentage": null,
        "relocation": null,
        "payment_duration": "60",
        "city": "Austin",
        "state": "TX",
        "country": "United States",
        "country_code": null,
        "zip_code": null,
        "client_name": null,
        "compensation": 120000,
        "finders_fee_amount": "8640.0",
        "finders_fee": 9,
        "finders_fee_type": "percentage",
        "hourly_rate": null,
        "duration": null,
        "duration_type": null,
        "skills": "Ruby,Rails,jQuery,MySql",
        "industry": {
            "id": 181,
            "name": "it industry"
        },
        "company": {
            "short_description": "jobhukapi",
            "long_description": "Jobhuk API is an austin based company",
            "year_founded": "2010",
            "logo": "https://jobhuk.s3.amazonaws.com/uploads/company_images/company/image/1281/header_logo-1dc784d557ca8383748e986a661bd504.png",
            "company_type": "employer",
            "id": 1281,
            "name": "jobhukapi test",
            "address": "suite no 302",
            "website": "www.jobhukapi.com",
            "phone": "1234567890",
            "fax": "0987654321",
            "city": "Austin",
            "state": "TX",
            "zip": "78703",
            "created_at": "2015-04-20T06:18:05-05:00",
            "social_profile_links": null,
            "email": "care@jobhukapi.com",
            "about_team": "jobhukapi",
            "tag_line": "jobhukapi",
            "about_benefits": "jobhukapi",
            "verified": false
        }
    }
}
```

This endpoint post a job in jobhuk.

### HTTP Request

`POST http://api.jobhuk.com/jobs.json`

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

response = HTTParty.get("http://api.jobhuk.com/jobs/1318.json", headers: {"Token" => "API_TOKEN"})
job = response.body
```

```shell
curl http://api.jobhuk.com/jobs/1318.json
  -H "Token:API_TOKEN"
```

> The above command returns JSON structured like this:

```json
{
    "successful": true,
    "job": {
        "id": 1318,
        "title": "Ruby Programmer ",
        "location": "Auxtin",
        "description": "Ruby Programmer ",
        "job_type": "FullTime",
        "comp_range": 0,
        "show_market_place": true,
        "hide_salary": true,
        "active": true,
        "joining_date": null,
        "travel_percentage": null,
        "relocation": null,
        "payment_duration": "60",
        "city": "Austin",
        "state": "TX",
        "country": "United States",
        "country_code": null,
        "zip_code": null,
        "client_name": null,
        "compensation": 120000,
        "finders_fee_amount": "8640.0",
        "finders_fee": 9,
        "finders_fee_type": "percentage",
        "hourly_rate": null,
        "duration": null,
        "duration_type": null,
        "skills": "ruby, rails, jquery, mysql",
        "industry": {
            "id": 181,
            "name": "it industry"
        },
        "company": {
            "short_description": "jobhukapi",
            "long_description": "Jobhuk API is an austin based company",
            "year_founded": "2010",
            "logo": "https://jobhuk.s3.amazonaws.com/uploads/company_images/company/image/1281/header_logo-1dc784d557ca8383748e986a661bd504.png",
            "company_type": "employer",
            "id": 1281,
            "name": "jobhukapi test",
            "address": "suite no 302",
            "website": "www.jobhukapi.com",
            "phone": "1234567890",
            "fax": "0987654321",
            "city": "Austin",
            "state": "TX",
            "zip": "78703",
            "created_at": "2015-04-20T06:18:05-05:00",
            "social_profile_links": null,
            "email": "care@jobhukapi.com",
            "about_team": "jobhukapi",
            "tag_line": "jobhukapi",
            "about_benefits": "jobhukapi",
            "verified": false
        }
    }
}
```

This endpoint get a specific job details given by id

### HTTP Request

`GET http://api.jobhuk.com/jobs/<id>.json`

### URL Parameters

Parameter | Value   | Description
--------- | ------  | -----------
id<br>required | integer | unique job id

## Edit Job

```ruby
require 'httparty'

response = HTTParty.put("http://api.jobhuk.com/jobs/1318.json", {body: {job: {company_id: 1281, title: 'Senior Software Engineer', description: 'This is a senior software engineer position to support the software development for field portable analytical instruments...', location: 'Austin, TX', job_type: 'FullTime', comp_range: 5, compensation: 100000, finders_fee_type: 'percentage', finders_fee: 5, skills: 'Java, Oracle', industry: 'engineering'}}, headers: {"Token" => API_TOKEN}})
job = response.body
```

```shell
curl http://api.jobhuk.com/jobs/1318.json
  -X PUT
  -H "Token: API_TOKEN"
  --data "job[company_id]=1281&job[title]=Senior Software Engineer&job[description]=This is a senior software engineer position to support the software development for field portable analytical instruments...&job[location]=Austin, TX&job[job_type]=FullTime&job[comp_range]=5&job[compensation]=100000&job[finders_fee_type]=percentage&job[finders_fee]=5&job[skills]=Java, Oracle&job[industry]=engineering"
```

> The above command returns JSON structured like this:

```json
{
    "successful": true,
    "job": {
        "id": 1318,
        "title": "Ruby Senior Programmer ",
        "location": "Auxtin",
        "description": "Ruby Programmer ",
        "job_type": "FullTime",
        "comp_range": 0,
        "show_market_place": true,
        "hide_salary": true,
        "active": true,
        "joining_date": null,
        "travel_percentage": null,
        "relocation": null,
        "payment_duration": "60",
        "city": "Austin",
        "state": "TX",
        "country": "United States",
        "country_code": null,
        "zip_code": null,
        "client_name": null,
        "compensation": 120000,
        "finders_fee_amount": "8640.0",
        "finders_fee": 9,
        "finders_fee_type": "percentage",
        "hourly_rate": null,
        "duration": null,
        "duration_type": null,
        "skills": "Ruby,Rails,jQuery,MySql",
        "industry": {
            "id": 181,
            "name": "it industry"
        },
        "company": {
            "short_description": "jobhukapi",
            "long_description": "Jobhuk API is an austin based company",
            "year_founded": "2010",
            "logo": "https://jobhuk.s3.amazonaws.com/uploads/company_images/company/image/1281/header_logo-1dc784d557ca8383748e986a661bd504.png",
            "company_type": "employer",
            "id": 1281,
            "name": "jobhukapi test",
            "address": "suite no 302",
            "website": "www.jobhukapi.com",
            "phone": "1234567890",
            "fax": "0987654321",
            "city": "Austin",
            "state": "TX",
            "zip": "78703",
            "created_at": "2015-04-20T06:18:05-05:00",
            "social_profile_links": null,
            "email": "care@jobhukapi.com",
            "about_team": "jobhukapi",
            "tag_line": "jobhukapi",
            "about_benefits": "jobhukapi",
            "verified": false
        }
    }
}
```

This endpoint edit specific job details given by id

### HTTP Request

`PUT http://api.jobhuk.com/jobs/<id>.json`

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

response = HTTParty.delete("http://api.jobhuk.com/jobs/1318.json", headers: {"Token" => "API_TOKEN"})
```

```shell
curl http://api.jobhuk.com/jobs/1318.json
  -X DELETE
  -H "Token: API_TOKEN"
  
```

> The above command returns JSON structured like this:

```json
{
    "successful": true,
    "job": "Deleted successfully 1318. This operation is irreversible."
}
```

This endpoint deletes specific job given by id.
This operation is irreversible.

### HTTP Request

`DELETE http://api.jobhuk.com/jobs/<id>.json`

### URL Parameters

Parameter | Value   | Description
--------- | ------  | -----------
id<br>required | integer | unique job id

# Candidates

## Submit Candidate
```ruby
require 'httparty'

response = HTTParty.post("http://api.jobhuk.com/jobs/1281/candidates", query: {candidate: {name: "john", email: "johnd@hatchforce.com", phone: 8558558359, public_profile_url: "https://www.linkedin.com/in/scottsantucci", :resume_file => File.new('/home/user/Downloads/josha_d.pdf')}},{headers:{"Token"=>"API_TOKEN"}})
candidate = response.body
```

```shell
 curl "http://api.jobhuk.com/jobs/1281/candidates"
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
    "code": 200,
    "candidate": {
        "submission": {
            "id": 3417,
            "job_id": 1281,
            "user_id": 7841,
            "referral_id": 11563,
            "submission_type": "resume",
            "contact_details": "name: test, Email: test@hatchforce.com",
            "phone_number": "7679873541",
            "public_profile_url": "https://jobhuk.s3.amazonaws.com/assets/v3.0/header_logo-1dc784d557ca8383748e986a661bd504.png",
            "created_at": "2015-04-20T07:19:11-05:00"
        },
        "referral": {
            "id": 11563,
            "referral_type": "referral_submission",
            "target_user_id": 7841,
            "another_source_discard": null,
            "admin_approved": null,
            "verified": false,
            "created_at": "2015-04-20T07:19:11-05:00"
        },
        "user": {
            "id": 7841,
            "email": "test@hatchforce.com",
            "account_type": "individual"
        },
        "profile": {
            "id": 7773,
            "first_name": "test",
            "middle_name": null,
            "last_name": " ",
            "social_picture": null,
            "public_profile_url": null
        },
        "profile_image": "",
        "profile_page": "https://jobhuk.com/me/test6",
        "resume": {
            "resume_file": "https://jobhuk.s3.amazonaws.com/uploads/resume/resume/resume_file/3371/test_resume.doc"
        }
    }
}
```

This endpoint submit's candidate to specific job.

### HTTP Request

`POST http://api.jobhuk.com/jobs/<job_id>/candidates`

### POST Parameters

Parameter | Value   | Description
--------- | ------  | -----------
job_id<br>required | integer | unique job id
candidate[name]<br>required | string | Name of the candidate
candidate[email]<br>required | string | Email of the candidate
candidate[phone]<br>required | integer | Phone number of the candidate
candidate[resume_file]<br>required | string | candidate resume file must be pdf or doc
candidate[public_profile_url]<br>required | string | candidate's linkedin or facebook profile urls

## All Candidates
```ruby
require 'httparty'

response = HTTParty.get("http://api.jobhuk.com/jobs/1281/candidates", headers: {"Token" => "API_TOKEN"})
candidates = response.body
```

```shell
curl http://api.jobhuk.com/jobs/1281/candidates 
  -H "Token:API_TOKEN"
```

> The above command returns JSON structured like this:

```json
{
    "successful": true,
    "count": 4,
    "candidates": [
        {
            "submission": {
                "id": 3417,
                "job_id": 1281,
                "user_id": 7841,
                "referral_id": 11563,
                "submission_type": "resume",
                "contact_details": "name: test, Email: test@hatchforce.com",
                "phone_number": "7679873541",
                "public_profile_url": "https://jobhuk.s3.amazonaws.com/assets/v3.0/header_logo-1dc784d557ca8383748e986a661bd504.png",
                "created_at": "2015-04-20T07:19:11-05:00"
            },
            "referral": {
                "id": 11563,
                "referral_type": "referral_submission",
                "target_user_id": 7841,
                "another_source_discard": null,
                "admin_approved": true,
                "verified": false,
                "created_at": "2015-04-20T07:19:11-05:00"
            },
            "user": {
                "id": 7841,
                "email": "test@hatchforce.com",
                "account_type": "individual"
            },
            "profile": {
                "id": 7773,
                "first_name": "test",
                "middle_name": null,
                "last_name": " ",
                "social_picture": null,
                "public_profile_url": null
            },
            "profile_image": "",
            "profile_page": "https://jobhuk.com/me/test6",
            "resume": {
                "resume_file": "https://jobhuk.s3.amazonaws.com/uploads/resume/resume/resume_file/3371/test_resume.doc"
            }
        },
        {
            "submission": {
                "id": 3415,
                "job_id": 1281,
                "user_id": 7839,
                "referral_id": 11561,
                "submission_type": "resume",
                "contact_details": "name: venky1, Email: venkykvs@hatchforce.com",
                "phone_number": "6679873541",
                "public_profile_url": "https://jobhuk.s3.amazonaws.com/assets/v3.0/header_logo-1dc784d557ca8383748e986a661bd504.png",
                "created_at": "2015-04-20T07:18:17-05:00"
            },
            "referral": {
                "id": 11561,
                "referral_type": "referral_submission",
                "target_user_id": 7839,
                "another_source_discard": null,
                "admin_approved": null,
                "verified": false,
                "created_at": "2015-04-20T07:18:17-05:00"
            },
            "user": {
                "id": 7839,
                "email": "venkykvs@hatchforce.com",
                "account_type": "individual"
            },
            "profile": {
                "id": 7771,
                "first_name": "venky1",
                "middle_name": null,
                "last_name": " ",
                "social_picture": null,
                "public_profile_url": null
            },
            "profile_image": "",
            "profile_page": "https://jobhuk.com/me/venkykvs",
            "resume": {
                "resume_file": "https://jobhuk.s3.amazonaws.com/uploads/resume/resume/resume_file/3369/venky.doc"
            }
        }
    ]
}
```

This endpoint returns all candidates for this job.

### HTTP Request

`GET http://api.jobhuk.com/jobs/<job_id>/candidates`

### URL Parameters

Parameter | Value   | Description
--------- | ------  | -----------
job_id<br>required | integer | unique job id

## Submitted Candidates

```ruby
require 'httparty'

response = HTTParty.get("http://api.jobhuk.com/jobs/1281/submitted_candidates", headers: {"Token" => "API_TOKEN"})
candidates = response.body
```

```shell
curl http://api.jobhuk.com/jobs/1281/submitted_candidates 
  -H "Token:API_TOKEN"
```

> The above command returns JSON structured like this:

```json
{
    "successful": true,
    "count": 4,
    "candidates": [
        {
            "submission": {
                "id": 3417,
                "job_id": 1281,
                "user_id": 7841,
                "referral_id": 11563,
                "submission_type": "resume",
                "contact_details": "name: test, Email: test@hatchforce.com",
                "phone_number": "7679873541",
                "public_profile_url": "https://jobhuk.s3.amazonaws.com/assets/v3.0/header_logo-1dc784d557ca8383748e986a661bd504.png",
                "created_at": "2015-04-20T07:19:11-05:00"
            },
            "referral": {
                "id": 11563,
                "referral_type": "referral_submission",
                "target_user_id": 7841,
                "another_source_discard": null,
                "admin_approved": null,
                "verified": false,
                "created_at": "2015-04-20T07:19:11-05:00"
            },
            "user": {
                "id": 7841,
                "email": "test@hatchforce.com",
                "account_type": "individual"
            },
            "profile": {
                "id": 7773,
                "first_name": "test",
                "middle_name": null,
                "last_name": " ",
                "social_picture": null,
                "public_profile_url": null
            },
            "profile_image": "",
            "profile_page": "https://jobhuk.com/me/test6",
            "resume": {
                "resume_file": "https://jobhuk.s3.amazonaws.com/uploads/resume/resume/resume_file/3371/test_resume.doc"
            }
        },
        {
            "submission": {
                "id": 3415,
                "job_id": 1281,
                "user_id": 7839,
                "referral_id": 11561,
                "submission_type": "resume",
                "contact_details": "name: venky1, Email: venkykvs@hatchforce.com",
                "phone_number": "6679873541",
                "public_profile_url": "https://jobhuk.s3.amazonaws.com/assets/v3.0/header_logo-1dc784d557ca8383748e986a661bd504.png",
                "created_at": "2015-04-20T07:18:17-05:00"
            },
            "referral": {
                "id": 11561,
                "referral_type": "referral_submission",
                "target_user_id": 7839,
                "another_source_discard": null,
                "admin_approved": null,
                "verified": false,
                "created_at": "2015-04-20T07:18:17-05:00"
            },
            "user": {
                "id": 7839,
                "email": "venkykvs@hatchforce.com",
                "account_type": "individual"
            },
            "profile": {
                "id": 7771,
                "first_name": "venky1",
                "middle_name": null,
                "last_name": " ",
                "social_picture": null,
                "public_profile_url": null
            },
            "profile_image": "",
            "profile_page": "https://jobhuk.com/me/venkykvs",
            "resume": {
                "resume_file": "https://jobhuk.s3.amazonaws.com/uploads/resume/resume/resume_file/3369/venky.doc"
            }
        }
    ]
}
```

This endpoint returns specific candidates submitted to job by you as a recruiter

### HTTP Request

`GET http://api.jobhuk.com/jobs/<job_id>/submitted_candidates`

### URL Parameters

Parameter | Value   | Description
--------- | ------  | -----------
job_id<br>required | integer | unique job id


## Get Candidate

```ruby
require 'httparty'

response = HTTParty.get("http://api.jobhuk.com/jobs/1281/candidates/3417", headers: {"Token" => "API_TOKEN"})
candidates = response.body
```

```shell
curl http://api.jobhuk.com/jobs/1281/candidates/3417 
  -H "Token:API_TOKEN"
```

> The above command returns JSON structured like this:

```json
{
    "successful": true,
    "code": 200,
    "candidate": {
        "submission": {
            "id": 3417,
            "job_id": 1281,
            "user_id": 7841,
            "referral_id": 11563,
            "submission_type": "resume",
            "contact_details": "name: test, Email: test@hatchforce.com",
            "phone_number": "7679873541",
            "public_profile_url": "https://jobhuk.s3.amazonaws.com/assets/v3.0/header_logo-1dc784d557ca8383748e986a661bd504.png",
            "created_at": "2015-04-20T07:19:11-05:00"
        },
        "referral": {
            "id": 11563,
            "referral_type": "referral_submission",
            "target_user_id": 7841,
            "another_source_discard": null,
            "admin_approved": null,
            "verified": false,
            "created_at": "2015-04-20T07:19:11-05:00"
        },
        "user": {
            "id": 7841,
            "email": "test@hatchforce.com",
            "account_type": "individual"
        },
        "profile": {
            "id": 7773,
            "first_name": "test",
            "middle_name": null,
            "last_name": " ",
            "social_picture": null,
            "public_profile_url": null
        },
        "profile_image": "",
        "profile_page": "https://jobhuk.com/me/test6",
        "resume": {
            "resume_file": "https://jobhuk.s3.amazonaws.com/uploads/resume/resume/resume_file/3371/test_resume.doc"
        }
    }
}
```

This endpoint returns submitted candidate details to specific job 

### HTTP Request

`GET http://api.jobhuk.com/jobs/<job_id>/candidates/<id>`

### URL Parameters

Parameter | Value   | Description
--------- | ------  | -----------
job_id<br>required | integer | unique job id
id<br>required | integer | unique candidate id

# Industries

## Get Industries

```ruby
require 'httparty'

response = HTTParty.get("http://api.jobhuk.com/industries", headers: {"Token" => "API_TOKEN"})
candidates = response.body
```

```shell
curl http://api.jobhuk.com/industries 
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
            "id": 124,
            "name": "Research"
        },
        {
            "id": 149,
            "name": "Software Development"
        },
        {
            "id": 191,
            "name": "Finance"
        },
        {
            "id": 204,
            "name": "Administrative"
        },
        {
            "id": 205,
            "name": "Information Technology"
        },
        {
            "id": 206,
            "name": "Advertising"
        },
        {
            "id": 207,
            "name": "Legal"
        },
        {
            "id": 208,
            "name": "Business Development"
        },
        {
            "id": 209,
            "name": "Marketing"
        },
        {
            "id": 210,
            "name": "Client Services"
        },
        {
            "id": 211,
            "name": "Computers/Hardware"
        },
        {
            "id": 212,
            "name": "Product/Creative"
        },
        {
            "id": 213,
            "name": "Computers/Software"
        },
        {
            "id": 214,
            "name": "Product Management"
        },
        {
            "id": 215,
            "name": "Customer Service"
        },
        {
            "id": 216,
            "name": "Quality Assurance"
        },
        {
            "id": 217,
            "name": "Engineering"
        },
        {
            "id": 218,
            "name": "Executive Management"
        },
        {
            "id": 219,
            "name": "Sales"
        },
        {
            "id": 220,
            "name": "Technical Support"
        },
        {
            "id": 221,
            "name": "Other"
        }
    ]
}
```

This endpoint returns list of industries 

### HTTP Request

`GET http://api.jobhuk.com/industries`


