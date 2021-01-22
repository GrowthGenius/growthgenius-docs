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

# Authentication

growthgenius uses API keys to allow access to the API.

growthgenius expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: YOUR API KEY HERE`

Additionally, every request EXCEPT the User API should include the user_id as an additional query parameter.

# User API

A user is a member of a team on growthgenius.

## Get All Contacts

### HTTP Request

`GET https://api.growthgenius.com/integrations/v1/users`

This endpoint retrieves all users who have enabled integrations

> The above command returns JSON structured like this:

```json
{
  "users": [
    {
      id: 1,
      team_id: 2,
      created_at: "2019-03-21T16:11:00.024-04:00"
      email: "dev@growthgenius.com"
      email_bcc: "tim@cnn.com"
      first_name: "Okay"
      full_name: "Okay Senior"
      last_name: "Senior"
      reporting_email: "reporting-dev@growthgenius.com"
      roles: ["superadmin", "admin"]

    }
  ]
```

# Enrichment API

The Enrichment API lets you look up person and company data based on an email or domain. For example, you could retrieve a person’s name, location and social handles from an email. Or you could lookup a company’s location, headcount or logo based on their domain name.

Note: You’ll only be charged once per 30 day period for each unique request, so if you didn’t store the data properly or need to re-run a series of requests for any reason, those won’t count against your allotment.

## Person API

The Person API lets you retrieve social information associated with an email address, such as a person’s name, location and Twitter handle.

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
  "contact": {
    "annual_revenue": null,
    "bad_data_reason": null,
    "city": null,
    "company_address": null,
    "company_city": "Melbourne",
    "company_country": "New Zealand",
    "company_linkedin_url": "linkedin.com/company/anz",
    "company_name": "Anz",
    "company_name_informal": null,
    "company_state": "Victoria",
    "contact_account": { "id": 485499, "status": "cold" },
    "contact_account_id": 485499,
    "corporate_phone": null,
    "country": "New Zealand",
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
    "email": "tony.barkley@anz.com",
    "email_confidence": 100,
    "email_status": null,
    "employee_count": null,
    "facebook_url": null,
    "first_name": "Tony",
    "first_phone": null,
    "full_name": "Tony Barkley",
    "home_phone": null,
    "id": 1102755,
    "industry": "Banking",
    "keywords": "banking, finance, retail banking, commercial banking, credit risk, credit, financial risk, loans, credit analysis, relationship management, risk management, core banking, portfolio management, financial analysis, business relationship management, internet banking, mobile banking",
    "label_names": null,
    "last_name": "Barkley",
    "linkedin_url": "linkedin.com/in/tony-barkley-92824584",
    "linkedin_username": "tony-barkley-92824584",
    "lists": null,
    "mobile_phone": "NaN",
    "name": "Tony Barkley",
    "other_phone": null,
    "prospect_id": 236811124,
    "seo_description": null,
    "stage": null,
    "state": "Bay Of Plenty",
    "status": "Ongoing",
    "technologies": "",
    "title": "Relationship Associate",
    "twitter_url": null,
    "unstructured_data": null,
    "updated_at": "2021-01-19T17:07:20.529-05:00",
    "upload_identifier": null,
    "user_id": 1,
    "website": "anz.com",
    "work_phone": null
  }
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

# Discovery API

A Contact is a person your team has explicitly added to your database. It can be from prospected from GrowthGenius, manually added by your team, or created by the API.

# Prospector API

A Contact is a person your team has explicitly added to your database. It can be from prospected from GrowthGenius, manually added by your team, or created by the API.

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
    "annual_revenue": null,
    "bad_data_reason": null,
    "city": null,
    "company_address": null,
    "company_city": "San Francisco",
    "company_country": "USA",
    "company_linkedin_url": "linkedin.com/company/anz",
    "company_name": "Apple Inc.",
    "company_name_informal": "Apple",
    "company_state": "Victoria",
    "contact_account": { "id": 485499, "status": "cold" },
    "contact_account_id": 485499,
    "corporate_phone": null,
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
    "email_status": null,
    "employee_count": null,
    "facebook_url": null,
    "first_name": "Tony",
    "first_phone": null,
    "full_name": "Steve Jobs",
    "home_phone": null,
    "id": 1102755,
    "industry": "Computers",
    "keywords": "banking, finance, retail banking, commercial banking, credit risk, credit, financial risk, loans, credit analysis, relationship management, risk management, core banking, portfolio management, financial analysis, business relationship management, internet banking, mobile banking",
    "label_names": null,
    "last_name": "Barkley",
    "linkedin_url": "linkedin.com/in/tony-barkley-92824584",
    "linkedin_username": "tony-barkley-92824584",
    "lists": null,
    "mobile_phone": "NaN",
    "name": "Tony Barkley",
    "other_phone": null,
    "prospect_id": 236811124,
    "seo_description": null,
    "stage": null,
    "state": "Bay Of Plenty",
    "status": "Ongoing",
    "technologies": "",
    "title": "Relationship Associate",
    "twitter_url": null,
    "unstructured_data": null,
    "updated_at": "2021-01-19T17:07:20.529-05:00",
    "upload_identifier": null,
    "user_id": 1,
    "website": "anz.com",
    "work_phone": null
  }
}
```

|

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
      "value": "Tim Zheng, CEO, Apollo",
      "display_name": "Tim Zheng, CEO, Apollo"
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
  "contacts": [
    {
      "annual_revenue": null,
      "bad_data_reason": null,
      "city": null,
      "company_address": null,
      "company_city": "San Francisco",
      "company_country": "USA",
      "company_linkedin_url": "linkedin.com/company/anz",
      "company_name": "Apple Inc.",
      "company_name_informal": "Apple",
      "company_state": "Victoria",
      "contact_account": { "id": 485499, "status": "cold" },
      "contact_account_id": 485499,
      "corporate_phone": null,
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
      "email_status": null,
      "employee_count": null,
      "facebook_url": null,
      "first_name": "Tony",
      "first_phone": null,
      "full_name": "Steve Jobs",
      "home_phone": null,
      "id": 1102755,
      "industry": "Computers",
      "keywords": "banking, finance, retail banking, commercial banking, credit risk, credit, financial risk, loans, credit analysis, relationship management, risk management, core banking, portfolio management, financial analysis, business relationship management, internet banking, mobile banking",
      "label_names": null,
      "last_name": "Barkley",
      "linkedin_url": "linkedin.com/in/tony-barkley-92824584",
      "linkedin_username": "tony-barkley-92824584",
      "lists": null,
      "mobile_phone": "NaN",
      "name": "Tony Barkley",
      "other_phone": null,
      "prospect_id": 236811124,
      "seo_description": null,
      "stage": null,
      "state": "Bay Of Plenty",
      "status": "Ongoing",
      "technologies": "",
      "title": "Relationship Associate",
      "twitter_url": null,
      "unstructured_data": null,
      "updated_at": "2021-01-19T17:07:20.529-05:00",
      "upload_identifier": null,
      "user_id": 1,
      "website": "anz.com",
      "work_phone": null
    }
  ]
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
      "value": "Tim Zheng, CEO, Apollo",
      "display_name": "Tim Zheng, CEO, Apollo"
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
