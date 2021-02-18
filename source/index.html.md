---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

search: true

code_clipboard: true
---

# Introduction

Welcome to the GrowthGenius API! You can use our API to access GrowthGenius API endpoints, which can get information on various contacts, accounts, and campaigns.

# Data Sets

### API Dataset

All Records Have -- Name + One other piece of PII

Number of Profiles: 2,721,090,761

Main Use Cases: Enrichment

### LinkedIn Data

All Records Have -- Linkedin URL

Number of Profiles: 571,536,238

Main Use Cases: Candidate Search, Prospect Search, Custom Audiences, Career Path Prediction/Labor Force Modeling, Investment Sourcing

### Email Data

All Records Have -- Email

Number of Profiles: 645,912,636

Main Use Cases: Email Enrichment, Sales Lead Generation, Candidate Outreach

### Street Address Data

All Records Have -- Street Address

Number of Profiles: 359,910,157

Main Use Cases: Contact Info Enrichment, Sales and Marketing, Skiptracing, Background Checks

### Mobile Phone Data

All Records Have -- Mobile Phone Number

Number of Profiles: 253,398,383

Main Use Cases: Direct Dial Outreach, Caller ID

### Phone Data

All Records Have -- Any Phone Number

Number of Profiles: 664,345,129

Main Use Cases: Skiptracing, Background Checks

### Developer Data

All Records Have -- Github URL

Number of Profiles: 3,125,978

Main Use Cases: Recruiting, Investment Sourcing

# Authentication

growthgenius uses API keys to allow access to the API.

growthgenius expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: YOUR API KEY HERE`

Additionally, every request should include the user_id as an additional query parameter.

# User API

A user is a member of a team on growthgenius.

## Get User Information

### HTTP Request

`GET https://api.growthgenius.com/integrations/v1/users/`

This endpoint returns the information of the user corresponding to the provided user_id.

> The above command returns JSON structured like this:

```json
{
  "user": {
    id: 1,
    team_id: 2,
    created_at: "2019-03-21T16:11:00.024-04:00",
    email: "dev@growthgenius.com"
    email_bcc: "dev@cnn.com"
    first_name: "Okay"
    full_name: "Okay Senior"
    last_name: "Senior"
    reporting_email: "reporting-dev@growthgenius.com"
    roles: ["superadmin", "admin"]
  }
}
```

# Enrichment API

The Enrichment API lets you look up person and company data based on an email or domain. For example, you could retrieve a person’s name, location and social handles from an email. Or you could lookup a company’s location, headcount or logo based on their domain name.

Note: You’ll only be charged once per 30 day period for each unique request, so if you didn’t store the data properly or need to re-run a series of requests for any reason, those won’t count against your allotment.

## Person API

The Person API lets you retrieve social information associated with an email address, such as a person’s name, location and Twitter handle.

```ruby
require 'growthgenius'

api = growthgenius::APIClient.authorize!("YOUR API KEY HERE")
api.company.get
```

```shell
curl -X GET -H "Content-Type: application/json" -H "Cache-Control: no-cache" -d '{
    "api_key": "YOUR API KEY HERE",
}' "https://api.growthgenius.com/integrations/v1/companies/find?domain=tesla.com"
```

```javascript
const growthgenius = require("growthgenius");

let api = growthgenius.authorize("YOUR API KEY HERE");
let contacts = api.contacts.get();
```

> The above command returns JSON structured like this:

```json
{
  "id": "qEnOZ5Oh0poWnQ1luFBfVw_0000",
  "full_name": "will richman",
  "first_name": "will",
  "middle_initial": "g",
  "middle_name": "gordon",
  "last_name": "richman",
  "gender": "male",
  "birth_year": "1989",
  "birth_date": null,
  "linkedin_url": "linkedin.com/in/willrichman",
  "linkedin_username": "willrichman",
  "linkedin_id": "145991517",
  "facebook_url": "facebook.com/dewillrichman",
  "facebook_username": "dewillrichman",
  "facebook_id": "1089351304",
  "twitter_url": "twitter.com/willrichman5",
  "twitter_username": "willrichman5",
  "github_url": null,
  "github_username": null,
  "work_email": "will@growthgenius.com",
  "mobile_phone": "+17788893825",
  "industry": "computer software",
  "job_title": "co-founder and chief executive officer",
  "job_title_role": null,
  "job_title_sub_role": null,
  "job_title_levels": ["owner", "cxo"],
  "job_company_id": "growthgenius",
  "job_company_name": "GrowthGenius",
  "job_company_website": "growthgenius.com",
  "job_company_size": "11-50",
  "job_company_founded": "2015",
  "job_company_industry": "computer software",
  "job_company_linkedin_url": "linkedin.com/company/growthgenius",
  "job_company_linkedin_id": "18170482",
  "job_company_facebook_url": "facebook.com/growthgenius",
  "job_company_twitter_url": "twitter.com/growthgenius",
  "job_company_type": "private",
  "job_company_ticker": null,
  "job_company_location_name": "toronto, ontario, canada",
  "job_company_location_locality": "toronto",
  "job_company_location_metro": "toronto, ontario",
  "job_company_location_region": "ontario",
  "job_company_location_geo": "37.77,-122.41",
  "job_company_location_street_address": "47 front street",
  "job_company_location_address_line_2": "suite 1670",
  "job_company_location_postal_code": "94105",
  "job_company_location_country": "canada",
  "job_company_location_continent": "north america",
  "job_last_updated": "2020-12-01",
  "job_start_date": "2015-03",
  "job_summary": "GrowthGenius helps people with data. Leverage our dataset of 1.5 billion unique person profiles as your data foundation to build products, enrich person profiles, power predictive modeling/AI, analysis, and more. We build and maintain our data from our powerful Data Union. We work with thousands of data science teams as their engineering focused data partner.",
  "location_name": "toronto, ontario, canada",
  "location_locality": "toronto",
  "location_metro": "toronto, ontario",
  "location_region": "ontario",
  "location_country": "canada",
  "location_continent": "north america",
  "location_street_address": null,
  "location_address_line_2": null,
  "location_postal_code": null,
  "location_geo": "37.77,-122.41",
  "location_last_updated": "2020-12-01",
  "linkedin_connections": 9621,
  "inferred_salary": ">250,000",
  "inferred_years_experience": 8,
  "summary": "Interested in solving sales",
  "phone_numbers": ["+17788893825"],
  "emails": [
    {
      "address": "srichman@ubritishcolumbia.edu",
      "type": null
    },
    {
      "address": "will@bitmaker.com",
      "type": "professional"
    },
    {
      "address": "will@growthgenius.co",
      "type": "professional"
    },
    {
      "address": "will.richman@growthgenius.co",
      "type": "professional"
    },
    {
      "address": "will@growthgenius.com",
      "type": "current_professional"
    },
    {
      "address": "srichman@growthgenius.com",
      "type": "current_professional"
    },
    {
      "address": "will.richman@growthgenius.com",
      "type": "current_professional"
    }
  ],
  "possible_emails": [
    {
      "address": "will@datemyschool.com",
      "type": "professional"
    }
  ],
  "interests": [
    "location based services",
    "mobile",
    "social media",
    "colleges",
    "university students",
    "consumer internet",
    "college campuses"
  ],
  "skills": [
    "entrepreneurship",
    "start ups",
    "management",
    "public speaking",
    "strategic partnerships",
    "strategy",
    "fundraising",
    "saas",
    "enterprise technology sales",
    "social networking"
  ],
  "location_names": [
    "toronto, ontario, canada",
    "albany, ontario, canada",
    "vancouver, british columbia, canada"
  ],
  "regions": ["ontario, canada", "british columbia, canada"],
  "countries": ["canada"],
  "street_addresses": [],
  "experience": [
    {
      "company": {
        "name": "bitmaker",
        "size": "1-10",
        "id": "bitmaker",
        "founded": "2013",
        "industry": "computer software",
        "location": {
          "name": "vancouver, british columbia, canada",
          "locality": "vancouver",
          "region": "british columbia",
          "metro": "vancouver, british columbia",
          "country": "canada",
          "continent": "north america",
          "street_address": "1231 northwest hoyt street",
          "address_line_2": "suite 202",
          "postal_code": "97209",
          "geo": "45.52,-122.67"
        },
        "linkedin_url": "linkedin.com/company/bitmaker",
        "linkedin_id": "3019184",
        "facebook_url": null,
        "twitter_url": "twitter.com/bitmaker",
        "website": "bitmaker.com",
        "raw": ["bitmaker", "bitmaker, inc"],
        "ticker": null,
        "type": "private",
        "fuzzy_match": false
      },
      "location_names": [],
      "end_date": "2015-02",
      "start_date": "2012-08",
      "title": {
        "name": "co-founder",
        "raw": ["co-founder"],
        "role": null,
        "sub_role": null,
        "levels": ["owner"]
      },
      "is_primary": false,
      "summary": "Helping SMBs get more sales meetings with their ideal customers"
    },
    {
      "company": {
        "name": "GrowthGenius",
        "size": "11-50",
        "id": "growthgenius",
        "founded": "2015",
        "industry": "computer software",
        "location": {
          "name": "toronto, ontario, canada",
          "locality": "toronto",
          "region": "ontario",
          "metro": "toronto, ontario",
          "country": "canada",
          "continent": "north america",
          "street_address": "47 front street",
          "address_line_2": "suite 200",
          "postal_code": "94105",
          "geo": "37.77,-122.41"
        },
        "linkedin_url": "linkedin.com/company/growthgenius",
        "linkedin_id": "18170482",
        "facebook_url": "facebook.com/growthgenius",
        "twitter_url": "twitter.com/growthgenius",
        "website": "growthgenius.com",
        "raw": ["GrowthGenius"],
        "ticker": null,
        "type": "private",
        "fuzzy_match": true
      },
      "location_names": [],
      "end_date": null,
      "start_date": "2015-03",
      "title": {
        "name": "co-founder and chief executive officer",
        "raw": ["co-founder &amp; ceo", "co-founder & ceo"],
        "role": null,
        "sub_role": null,
        "levels": ["owner", "cxo"]
      },
      "is_primary": true,
      "summary": "GrowthGenius helps people with data. Leverage our dataset of 1.5 billion unique person profiles as your data foundation to build products, enrich person profiles, power predictive modeling/AI, analysis, and more. We build and maintain our data from our powerful Data Union. We work with thousands of data science teams as their engineering focused data partner. I consult with our engineering customers to solve data building challenges - will@growthgenius.com"
    }
  ],
  "education": [
    {
      "school": {
        "name": "university of british columbia",
        "type": "post-secondary institution",
        "id": "64LkgfdwWYkCC2TjbldMDQ_0",
        "location": {
          "name": "vancouver, british columbia, canada",
          "locality": "vancouver",
          "region": "british columbia",
          "country": "canada",
          "continent": "north america"
        },
        "linkedin_url": "linkedin.com/school/university-of-british columbia",
        "facebook_url": "facebook.com/universityofbritish columbia",
        "twitter_url": "twitter.com/ubritish columbia",
        "linkedin_id": "19207",
        "website": "ubritishcolumbia.edu",
        "domain": "ubritishcolumbia.edu",
        "raw": ["university of british columbia"]
      },
      "end_date": "2014",
      "start_date": "2010",
      "gpa": null,
      "degrees": [],
      "majors": ["entrepreneurship"],
      "minors": [],
      "raw": [
        "data analytics & entrepreneurship",
        ", entrepreneurship",
        "entrepreneurship"
      ],
      "summary": "Entrepreneurship at University of Western british columbia"
    }
  ],
  "profiles": [
    {
      "network": "linkedin",
      "id": "145991517",
      "url": "linkedin.com/in/willrichman",
      "username": "willrichman"
    },
    {
      "network": "facebook",
      "id": "1089351304",
      "url": "facebook.com/dewillrichman",
      "username": "dewillrichman"
    },
    {
      "network": "twitter",
      "id": null,
      "url": "twitter.com/willrichman5",
      "username": "willrichman5"
    },
    {
      "network": "linkedin",
      "id": null,
      "url": "linkedin.com/in/will-richman-9b9a8540",
      "username": "will-richman-9b9a8540"
    },
    {
      "network": "angellist",
      "id": null,
      "url": "angel.co/dewillrichman",
      "username": "dewillrichman"
    },
    {
      "network": "gravatar",
      "id": null,
      "url": "gravatar.com/willrichman5",
      "username": "willrichman5"
    },
    {
      "network": "klout",
      "id": null,
      "url": "klout.com/willrichman5",
      "username": "willrichman5"
    },
    {
      "network": "aboutme",
      "id": null,
      "url": "about.me/will_richman",
      "username": "will_richman"
    }
  ],
  "possible_profiles": [
    {
      "network": "angellist",
      "id": null,
      "url": "angel.co/will-richman-1",
      "username": "will-richman-1"
    },
    {
      "network": "twitter",
      "id": null,
      "url": "twitter.com/growthgenius",
      "username": "growthgenius"
    },
    {
      "network": "klout",
      "id": null,
      "url": "klout.com/bitmaker_dev",
      "username": "bitmaker_dev"
    },
    {
      "network": "linkedin",
      "id": null,
      "url": "linkedin.com/in/will-richman-4b92813b",
      "username": "will-richman-4b92813b"
    },
    {
      "network": "twitter",
      "id": null,
      "url": "twitter.com/willrichman1",
      "username": "willrichman1"
    }
  ],
  "certifications": [],
  "languages": [],
  "version_status": {
    "status": "updated",
    "contains": [],
    "previous_version": "12.0",
    "current_version": "13.0"
  }
}
```

### Attributes

The dot notation indicates that the property is one level deep inside a hash. No attributes are guaranteed to be present, and if we can’t find data on a specific network, then we’ll return a null value for that attribute.

| Attribute    | Description                                                                                                                                                                                                                                                     | Example                    |
| ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------- |
| first_name   | First Name                                                                                                                                                                                                                                                      | Elon                       |
| last_name    | Last Name                                                                                                                                                                                                                                                       | Musk                       |
| title        | Title                                                                                                                                                                                                                                                           | CEO                        |
| account_id   | ID of the Account (Optional)                                                                                                                                                                                                                                    | "583f2f7ed9ced98ab5bfXXXX" |
| account_name | Account Name                                                                                                                                                                                                                                                    | Tesla                      |
| email        | Email                                                                                                                                                                                                                                                           | elon@tesla.com             |
| website_url  | The organization website Apollo can use to enrich data for you. DO NOT pass in personal social media URLs such as "http://www.linkedin.com/profile_url", or your data will be incorrectly enriched. This argument will be ignored if you pass in a valid email. | "http://www.tesla.com"     |

## Company API

Our Company API lets you lookup company data via a domain name.

```ruby
require 'growthgenius'

api = growthgenius::APIClient.authorize!("YOUR API KEY HERE")
api.company.get
```

```shell
curl -X GET -H "Content-Type: application/json" -H "Cache-Control: no-cache" -d '{
    "api_key": "YOUR API KEY HERE",
}' "https://api.growthgenius.com/integrations/v1/companies/find?domain=tesla.com"
```

```javascript
const growthgenius = require("growthgenius");

let api = growthgenius.authorize("YOUR API KEY HERE");
let contacts = api.contacts.get();
```

> The above command returns JSON structured like this:

```json
{
  "size": 219238,
  "id": "google",
  "website": "google.com",
  "name": "google",
  "founded": "1998",
  "size_range": "10001+",
  "location": {
    "name": "mountain view, california, united states",
    "locality": "mountain view",
    "region": "california",
    "metro": "san francisco, california",
    "country": "united states",
    "continent": "north america",
    "street_address": "1600 amphitheatre parkway",
    "postal_code": "94043",
    "address_line_2": "1234"
  },
  "industry": "internet",
  "facebook_url": "facebook.com/google",
  "twitter_url": "twitter.com/google",
  "crunchbase_url": "crunchbase.com/organization/google",
  "linkedin_url": "linkedin.com/company/google",
  "linkedin_id": "linkedin.com/company/1441",
  "email_domains": ["google.com"],
  "ticker": "GOOGL",
  "type": "public",
  "profiles": [
    "linkedin.com/company/google",
    "linkedin.com/company/1441",
    "facebook.com/google",
    "twitter.com/google",
    "crunchbase.com/organization/google"
  ],
  "tags": [
    "media and entertainment",
    "messaging and telecommunications",
    "information technology",
    "video",
    "email",
    "search engine",
    "content and publishing",
    "blogging platforms",
    "advertising",
    "collaboration"
  ],
  "summary": "google is a multinational corporation that specializes in internet-related services and products. the company’s product portfolio includes google search, which provides users with access to information online; knowledge graph that allows users to search for things, people, or places as well as builds systems recognizing speech and understanding natural language; google now, which provides information to users when they need it; product listing ads that offer product image, price, and merchant information;  adwords, an auction-based advertising program; adsense, which enables websites that are part of the google network to deliver ads; google display, a display advertising network; doubleclick ad exchange, a marketplace for the trading display ad space; and youtube that offers video, interactive, and other ad formats.  additionally, the company offers android, an open-source mobile software platform; hardware products, including chromebook, chrome, chromecast, and nexus devices; google+",
  "headline": null,
  "alternative_names": [
    "google inc.",
    "google deepmind",
    "google inc",
    "google, inc.",
    "google.com",
    "google fiber",
    "google, inc",
    "google germany gmbh",
    "google india",
    "google ireland"
  ],
  "alternative_domains": [
    "googlevideo.com",
    "google.nl",
    "google.pt",
    "gkecnapps.cn",
    "youtube.com",
    "youtu.be",
    "youtubeeducation.com",
    "gstatic.cn",
    "youtubekids.com",
    "googleadapis.com"
  ],
  "affiliated_profiles": [
    "youtube",
    "google-cloud",
    "think-with-google",
    "google-ads-",
    "googleworkspace",
    "google-analytics",
    "googlemarketingplatform",
    "google-ad-manager",
    "grow-with-google",
    "google-cloud-partners",
    "google-for-startups",
    "google-small-business",
    "x",
    "google-partners",
    "rework-with-google",
    "googleplaydev",
    "googleadmob",
    "google-user-research.",
    "google-news-initiative",
    "adometry"
  ]
}
```

### HTTP Request

`GET https://api.growthgenius.com/integrations/v1/companies/find?domain=tesla.com`

### Attributes

| Attribute    | Description                                                                                                                                                                                                                                                     | Example                    |
| ------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------- |
| first_name   | First Name                                                                                                                                                                                                                                                      | Elon                       |
| last_name    | Last Name                                                                                                                                                                                                                                                       | Musk                       |
| title        | Title                                                                                                                                                                                                                                                           | CEO                        |
| account_id   | ID of the Account (Optional)                                                                                                                                                                                                                                    | "583f2f7ed9ced98ab5bfXXXX" |
| account_name | Account Name                                                                                                                                                                                                                                                    | Tesla                      |
| email        | Email                                                                                                                                                                                                                                                           | elon@tesla.com             |
| website_url  | The organization website Apollo can use to enrich data for you. DO NOT pass in personal social media URLs such as "http://www.linkedin.com/profile_url", or your data will be incorrectly enriched. This argument will be ignored if you pass in a valid email. | "http://www.tesla.com"     |

# Contact API

A Contact is a person your team has explicitly added to your database. It can be from prospected from GrowthGenius, manually added by your team, or created by the API.

## Create a Contact

```
POST "https://api.growthgenius.com/integrations/v1/contacts"
Request parameters:

```

GrowthGenius does not run any deduplication during CREATE. If your record contains the same email or name+company as an existing contact, GrowthGenius will create a new contact instead of updating the existing contact.

### HTTP Request

`POST https://api.growthgenius.com/integrations/v1/contacts`

### Query Parameters

contact: {
first_name: "Steve",
last_name: "Jobs",
email: "sjobs@apple.com" (see response JSON for additional fields)
}

> The above command returns JSON structured like this:

```json
{
  "contact": {
    "annual_revenue": "$100 millon+",
    "bad_data_reason": null,
    "city": "toronto",
    "company_address": "123 Water St.",
    "company_city": "toronto",
    "company_country": "USA",
    "company_linkedin_url": "linkedin.com/company/anz",
    "company_name": "Apple Inc.",
    "company_name_informal": "Apple",
    "company_state": "ontario",
    "contact_account": { "id": 485499, "status": "cold" },
    "contact_account_id": 485499,
    "corporate_phone": "777-889-3825",
    "country": "USA",
    "created_at": "2021-01-19T17:06:25.730-05:00",
    "custom1": null,
    "custom2": null,
    "custom3": null,
    "custom4": null,
    "custom5": null,
    "custom6": null,
    "custom7": null,
    "custom8": null,
    "custom9": null,
    "email": "sjobs@apple.com",
    "email_confidence": 100,
    "email_status": "valid",
    "employee_count": "10,000+",
    "facebook_url": "facebook.com/steve",
    "first_name": "Steve",
    "first_phone": "778-889-3825",
    "full_name": "Steve Jobs",
    "home_phone": "778-889-3825",
    "id": 1102755,
    "industry": "Computers",
    "keywords": "banking, finance, retail banking, commercial banking, credit risk, credit, financial risk, loans, credit analysis, relationship management, risk management, core banking, portfolio management, financial analysis, business relationship management, internet banking, mobile banking",
    "label_names": null,
    "last_name": "Jobs",
    "linkedin_url": "linkedin.com/in/steve-jobs",
    "linkedin_username": "steve-jobs",
    "lists": null,
    "mobile_phone": "778-889-3825",
    "name": "Steve Jobs",
    "other_phone": "778-889-3825",
    "prospect_id": 236811124,
    "seo_description": "Think differently",
    "stage": "Replied",
    "state": "ontario",
    "status": "Ongoing",
    "technologies": "salesforce, stripe, intercom",
    "title": "CEO",
    "twitter_url": "twitter.com/steve",
    "unstructured_data": null,
    "updated_at": "2021-01-19T17:07:20.529-05:00",
    "upload_identifier": null,
    "user_id": 1,
    "website": "apple.com",
    "work_phone": "778-889-3825"
  }
}
```

## Update a Contact

### HTTP Request

`PATCH https://api.growthgenius.com/integrations/v1/contacts/:id`

This endpoint updates a contact.

### Query Parameters

Same as create.

Returns same JSON as create

## Delete a Contact

### HTTP Request

`DELETE https://api.growthgenius.com/integrations/v1/contacts/:id`

This endpoint deletes a contact.

## Search Contacts

```ruby
require 'growthgenius'

api = growthgenius::APIClient.authorize!("YOUR API KEY HERE")
api.contacts.get
```

```python
import growthgenius

api = growthgenius.authorize("YOUR API KEY HERE")
api.contacts.get()
```

```shell
curl -X POST -H "Content-Type: application/json" -H "Cache-Control: no-cache" -d '{
    "api_key": "YOUR API KEY HERE",
    "q_keywords": "Elon Musk, CEO, Tesla",
    "sort_by_field": "contact_last_activity_date",
    "sort_ascending": false
}' "https://api.growthgenius.com/integrations/v1/contacts/search"
```

```javascript
const growthgenius = require("growthgenius");

let api = growthgenius.authorize("YOUR API KEY HERE");
let contacts = api.contacts.get();
```

> The above command returns JSON structured like this:

```json
{
  "contacts": [
    {
      "contact": {
        "id": "d54c54ad-40be-4305-8a34-0ab44710b90d",
        "full_name": "Elon Musk",
        "fist_name": "Elon",
        "last_name": "Musk",
        "email": "elon@tesla.com",
        "//": "..."
      }
    },
    {
      "contact": {
        "id": "d54c54ad-40be-4305-8a34-0ab44710b90d",
        "full_name": "Elon Musk",
        "fist_name": "Elon",
        "last_name": "Musk",
        "email": "elon@tesla.com",
        "//": "..."
      }
    }
  ],
  "breadcrumbs": [
    {
      "label": "Contains Keywords",
      "signal_field_name": "q_keywords",
      "value": "Will Richman, COO, GrowthGenius",
      "display_name": "Will Richman, COO, GrowthGenius"
    }
  ],
  "partial_results_only": false,
  "disable_eu_prospecting": false,
  "partial_results_limit": 10000,
  "pagination": {
    "page": 1,
    "per_page": 25,
    "total_entries": 1,
    "total_pages": 1
  },
  "num_fetch_result": null
}
```

This endpoint retrieves all contacts.

=======

> > > > > > > 6f07fdee6482b694346309dfe3e01db241b285df

### HTTP Request

`GET https://api.growthgenius.com/integrations/v1/contacts`

This endpoint retrieves all contacts updated between provided datetimes.

### Query Parameters

{
from: <datetime>
to: <datetime>
}

> The above command returns JSON structured like this:

```json
{
  "contact": {
    "annual_revenue": "$100 millon+",
    "bad_data_reason": null,
    "city": "toronto",
    "company_address": "123 Water St.",
    "company_city": "toronto",
    "company_country": "USA",
    "company_linkedin_url": "linkedin.com/company/anz",
    "company_name": "Apple Inc.",
    "company_name_informal": "Apple",
    "company_state": "ontario",
    "contact_account": { "id": 485499, "status": "cold" },
    "contact_account_id": 485499,
    "corporate_phone": "777-889-3825",
    "country": "USA",
    "created_at": "2021-01-19T17:06:25.730-05:00",
    "custom1": null,
    "custom2": null,
    "custom3": null,
    "custom4": null,
    "custom5": null,
    "custom6": null,
    "custom7": null,
    "custom8": null,
    "custom9": null,
    "email": "sjobs@apple.com",
    "email_confidence": 100,
    "email_status": "valid",
    "employee_count": "10,000+",
    "facebook_url": "facebook.com/steve",
    "first_name": "Steve",
    "first_phone": "778-889-3825",
    "full_name": "Steve Jobs",
    "home_phone": "778-889-3825",
    "id": 1102755,
    "industry": "Computers",
    "keywords": "banking, finance, retail banking, commercial banking, credit risk, credit, financial risk, loans, credit analysis, relationship management, risk management, core banking, portfolio management, financial analysis, business relationship management, internet banking, mobile banking",
    "label_names": null,
    "last_name": "Jobs",
    "linkedin_url": "linkedin.com/in/steve-jobs",
    "linkedin_username": "steve-jobs",
    "lists": null,
    "mobile_phone": "778-889-3825",
    "name": "Steve Jobs",
    "other_phone": "778-889-3825",
    "prospect_id": 236811124,
    "seo_description": "Think differently",
    "stage": "Replied",
    "state": "ontario",
    "status": "Ongoing",
    "technologies": "salesforce, stripe, intercom",
    "title": "CEO",
    "twitter_url": "twitter.com/steve",
    "unstructured_data": null,
    "updated_at": "2021-01-19T17:07:20.529-05:00",
    "upload_identifier": null,
    "user_id": 1,
    "website": "apple.com",
    "work_phone": "778-889-3825"
  }
}
```

## Get a Specific Contact

### HTTP Request

`GET https://api.growthgenius.com/integrations/v1/contacts/:id`

This endpoint retrieves a specific contact.

Returns same JSON as create.

# Message API

A Message represents a communication between a User and a Contact

## Create a Message

```
POST "https://api.growthgenius.com/integrations/v1/messages"
Request parameters:

```

GrowthGenius does not run any deduplication during CREATE.

### HTTP Request

`POST https://api.growthgenius.com/integrations/v1/messages`

### Query Parameters

"message": {
contact_id: 155715
message_type: "sales_force_message"
rendered_copy: "Hey Louis,↵↵You hate prospecting. I love it. Maybe it's a perfect match?"
rendered_subject: null
sent_at: "2019-08-09T07:10:41.275-04:00"
team_id: 1
user_id: 78
}

> The above command returns JSON structured like this:

```json
{
  "message": {
    id: 393642
    contact_id: 155715
    message_type: "sales_force_message"
    rendered_copy: "Hey Louis,↵↵You hate prospecting. I love it. Maybe it's a perfect match?"
    rendered_subject: null
    sent_at: "2019-08-09T07:10:41.275-04:00"
    team_id: 1
    user_id: 78
  }
}
```

## Update a Message

### HTTP Request

`PATCH https://api.growthgenius.com/integrations/v1/messages/:id`

This endpoint updates a message.

### Query Parameters

Same as create.

Returns same JSON as create

## Delete a Message

### HTTP Request

`DELETE https://api.growthgenius.com/integrations/v1/messages/:id`

This endpoint deletes a message.

> The above command returns JSON structured like this:

```json
{
  "messages": [
    {
      "message": {
        "id": "d54c54ad-40be-4305-8a34-0ab44710b90d",
        "full_name": "Elon Musk",
        "fist_name": "Elon",
        "last_name": "Musk",
        "email": "elon@tesla.com",
        "//": "..."
      }
    },
    {
      "message": {
        "id": "d54c54ad-40be-4305-8a34-0ab44710b90d",
        "full_name": "Elon Musk",
        "fist_name": "Elon",
        "last_name": "Musk",
        "email": "elon@tesla.com",
        "//": "..."
      }
    }
  ],
  "breadcrumbs": [
    {
      "label": "Contains Keywords",
      "signal_field_name": "q_keywords",
      "value": "Will Richman, COO, GrowthGenius",
      "display_name": "Will Richman, COO, GrowthGenius"
    }
  ],
  "partial_results_only": false,
  "disable_eu_prospecting": false,
  "partial_results_limit": 10000,
  "pagination": {
    "page": 1,
    "per_page": 25,
    "total_entries": 1,
    "total_pages": 1
  },
  "num_fetch_result": null
}
```

# This endpoint retrieves all messages.

## Get All Messages

### HTTP Request

`GET https://api.growthgenius.com/integrations/v1/messages`

This endpoint retrieves all messages updated between provided datetimes.

### Query Parameters

{
from: <datetime>
to: <datetime>
}

> The above command returns JSON structured like this:

```json
{
  "messages": [
    {
    id: 393642
    contact_id: 155715
    message_type: "sales_force_message"
    rendered_copy: "Hey Louis,↵↵You hate prospecting. I love it. Maybe it's a perfect match?"
    rendered_subject: null
    sent_at: "2019-08-09T07:10:41.275-04:00"
    team_id: 1
    user_id: 78
  }]
}
```

## Get a Specific Message

### HTTP Request

`GET https://api.growthgenius.com/integrations/v1/messages/:id`

This endpoint retrieves a specific message.

Returns same JSON as create.
