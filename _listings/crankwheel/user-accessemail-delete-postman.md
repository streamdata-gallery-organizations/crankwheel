{
  "info": {
    "name": "CrankWheel Delete company user",
    "_postman_id": "29abe957-9be9-4a56-906d-d25a5ae89cc4",
    "description": "Removes a single email from the list of allowed emails on your company account.\n\nResponds with 204 No Content on success, and a body of \"User access deleted successfully.\"",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "Retrieve",
      "item": [
        {
          "id": "04692cf6-c61f-4cfe-afdb-9f434bea5748",
          "name": "UsageGet",
          "request": {
            "url": "http://meeting.is/ss/api/usage?from=%7B%7D&to=%7B%7D",
            "method": "GET",
            "header": [
              {
                "key": "Accept",
                "value": "*/*",
                "disabled": false
              }
            ],
            "body": {
              "mode": "raw"
            },
            "description": "This API endpoint retrieves usage history from your CrankWheel account.\n\n## Request\n\nNote the to= and from= query parameters which are timestamps.\n\nFor authentication, set your own API key in your environment or paste it instead of {{crankwheel-api-key}} in the value for the Authorization header under the Headers tab.\n\n## Response\n\nThe response is a JSON document.\n\nThe \"stats\" collection shows summary statistics for the number of meetings and number of total seconds in meetings both in aggregate and per agent.\n\nThe \"sessions\" list shows, for each session, the start and end time, the email of the agent presenting, the duration of the session in seconds, a log of the different things that were shared at different times, and information on how many viewers there were and where in the world they were located."
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "7388f038-9bed-4852-9465-a653091386a2"
            }
          ]
        },
        {
          "id": "b1b38259-57fd-4934-b3d9-281dc80a1c78",
          "name": "DemoUsageGet",
          "request": {
            "url": "http://meeting.is/ss/api/demo_usage?from=%7B%7D&to=%7B%7D",
            "method": "GET",
            "header": [
              {
                "key": "Accept",
                "value": "*/*",
                "disabled": false
              }
            ],
            "body": {
              "mode": "raw"
            },
            "description": "This API endpoint allows you to retrieve a history of demo requests made to your account in a given time period.\n\n## Request\n\nNote the to= and from= query parameters, which are timestamps.\n\nFor authentication, set your own API key in your environment or paste it instead of {{crankwheel-api-key}} in the value for the Authorization header under the Headers tab.\n\n## Response\n\nThe response is a JSON document.\n\nThe top level shows the number of cancelled demo requests during the period as total_canceled_requests.\n\nIt also has a list indexed as sessions.\n\nEach session in the list shows:\n* start_ts: The timestamp of the start of the session\n* last_event_ts: The timestamp of the last event received during the session, i.e. roughly when the session ended\n* availability_bucket: Which bucket of availability the CrankWheel system believed it was in. Values can be full_capacity if it believed that more than 50% of agents were available to do a demo, half_capacity if it believed that 50% or fewer were available, and no_capacity if it believed no agents were available. Availability is determined based on whether an agent has been active at their computer in the last 10 minutes, and also based on whether they are already screen sharing using CrankWheel.\n* seconds_to_respondHow many seconds it took to respond to the request, i.e. until an agent said they would handle it. If no agent handled the request (yet), the value will be never.\n* handled_by will be present if an agent handled the request and will show the agent's email address.\n* call_confirmed: Whether a call was confirmed. Values can be true, false or if the request was never responded to, n/a.\n* screenshared: Whether a screenshare was initiated after the call commenced. Values can be true, false or if a call was never initiated, n/a.\n* accepted_from shows a value of extension, email or n/a.\n\nLastly, the session contains a prospect_info object.\n\nThe fixed prospect_info keys are:\n* prospect-phone: The phone number entered by the prospect.\n* prospect-request-origin: The web page the request originated on. If originated from an email campaign, it will look like https://meeting.is/ss/showu/COMPANYSHORTNAME, possibly with parameters after the company's short name.\n* prospect-utm-source, prospect-utm-medium, prospect-utm-campaign, prospect-utm-term and prospect-utm-content: These reflect UTM parameters if they were present on the web page where the prospect requested a demo.\n\nInformation determined by lead enrichment, which may not always be 100% accurate:\n* prospect-location: Geographic location of the prospect as determined by their IP address.\n* prospect-enrich-full-name: The prospect's full name.\n* prospect-enrich-country: The prospect's country.\n* prospect-enrich-state: The prospect's state within their country.\n* prospect-enrich-company: The prospect's company name.\n* prospect-enrich-title: The prospect's title.\n* prospect-enrich-seniority: The prospect's level of seniority, for example \"executive\".\n* prospect-enrich-linkedin: The URL of the prospect's LinkedIn profile.\n* prospect-enrich-twitter: The URL of the prospect's Twitter profile.\n* prospect-enrich-company-sector: The sector of the prospect's company.\n* prospect-enrich-company-industry: The industry of the prospect's company.\n* prospect-enrich-company-employees: The number of employees at the prospect's company, or a range e.g. 10-20.\n* prospect-enrich-company-description: A brief description of the prospect's company.\n* prospect-enrich-company-linkedin: The URL of the prospect's company's LinkedIn profile.\n* prospect-enrich-company-twitter: The URL of the prospect's company's Twitter profile.\n* prospect-enrich-company-marketcap: The market capitalization of the prospect's company.\n\nIn addition, each lead capture question gets a key. Here is the default set, but keys for custom questions will inherit the name assigned to the question when it is created, e.g. prospect-shoesize for a question where you set the ID as shoesize:\n* prospect-name: The prospect's name as entered by themselves.\n* prospect-email: The prospect's email address as entered by themselves.\n* prospect-company: The prospect's company name as entered by themselves.\n* prospect-job-title: The prospect's title as entered by themselves.\n* prospect-website: The prospect's company's web page as entered by themselves."
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "7289ea50-0a87-4c82-9d3c-40cd37e85a0b"
            }
          ]
        }
      ]
    },
    {
      "name": "List",
      "item": [
        {
          "id": "32e77378-bb7d-45be-92f4-c96f90059a88",
          "name": "UserAccessGet",
          "request": {
            "url": "http://meeting.is/ss/api/user_access",
            "method": "GET",
            "header": [
              {
                "key": "Accept",
                "value": "*/*",
                "disabled": false
              }
            ],
            "body": {
              "mode": "raw"
            },
            "description": "Retrieve a full list of all users in your company account. For each user, their email address, privilege level and whether they are in your pool of users handling demo requests is shown.\n\nPossible values for **privilege** are:\n* **user** (a normal user of the system)\n* **admin** (a user who can invite others, change configuration of the company account, and more)\n* **owner** (an admin who is also the billing contact for the company)\n* **reporting** (a non-admin who has access to reporting functionality only)\n\nPossible values for **in_demo_pool** are **true**, **false** and **null** which should be considered the same as **false**.\n\nThe users' email address is shown in the **email** attribute."
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "ade4ed04-595f-44e2-971a-c73cb2b7676b"
            }
          ]
        }
      ]
    },
    {
      "name": "Company",
      "item": [
        {
          "id": "c1433405-cd7f-4e39-a04f-8f26e58b26ee",
          "name": "UserAccessPost2",
          "request": {
            "url": "http://meeting.is/ss/api/user_access",
            "method": "POST",
            "header": [
              {
                "key": "Content-Type",
                "value": "{}",
                "description": "",
                "disabled": false
              },
              {
                "key": "Accept",
                "value": "*/*",
                "disabled": false
              }
            ],
            "body": {
              "mode": "urlencoded",
              "urlencoded": [
                {
                  "key": "user_access[email]",
                  "value": "{}",
                  "disabled": false,
                  "description": ""
                },
                {
                  "key": "user_access[in_demo_pool]",
                  "value": "{}",
                  "disabled": false,
                  "description": ""
                },
                {
                  "key": "user_access[privilege]",
                  "value": "{}",
                  "disabled": false,
                  "description": ""
                },
                {
                  "key": "user_access[send_onboarding_email]",
                  "value": "{}",
                  "disabled": false,
                  "description": ""
                }
              ]
            },
            "description": "Create a single new user in your company account.\n\nPOST with a form-data body with a single parameter **user_access** containing as a JSON object the user's **email**, **privilege** and **in_demo_pool** attributes as well as a **send_onboarding_email** attribute.\n\nPossible values for **privilege** are:\n* **user** (a normal user of the system)\n* **admin** (a user who can invite others, change configuration of the company account, and more)\n* **owner** (an admin who is also the billing contact for the company)\n* **reporting** (a non-admin who has access to reporting functionality only)\n\nPossible values for **in_demo_pool** are **true** and **false**.\n\nThe users' email address is set as the **email** attribute.\n\nOn a successful create, this endpoint will respond with a 201 Created response code, and the body of the response will be JSON showing the **email**, **privilege** and **in_demo_pool** attributes of the created user.\n\nNote that \"creating\" a company user technically just lists their email as being allowed to access the company. The actual user account that stores their credentials and so on will only get created if they either click on the link in the email they receive if you set **send_onboarding_email** to **true** and choose a password, or if they initiate registration using the same email address and continue through to account creation. Feel free to email us at support@crankwheel.com if this is confusing :)"
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "b4091f1d-1286-431c-b7ef-727cc8a60672"
            }
          ]
        },
        {
          "id": "5542eb77-6d9c-4f34-8fd6-a8e665699397",
          "name": "UserAccessByEmailDelete",
          "request": {
            "url": {
              "protocol": "http",
              "host": "meeting.is",
              "path": [
                "ss",
                "api",
                "user_access/:email"
              ],
              "variable": [
                {
                  "id": "email",
                  "value": "{}",
                  "type": "string"
                }
              ]
            },
            "method": "DELETE",
            "header": [
              {
                "key": "Accept",
                "value": "*/*",
                "disabled": false
              }
            ],
            "body": {
              "mode": "raw"
            },
            "description": "Removes a single email from the list of allowed emails on your company account.\n\nResponds with 204 No Content on success, and a body of \"User access deleted successfully.\""
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "8d8d3010-758d-4474-af60-ba807c8af14b"
            }
          ]
        }
      ]
    },
    {
      "name": "Show",
      "item": [
        {
          "id": "8decefe7-56aa-4f59-83c2-06fd58ea98c3",
          "name": "UserAccessByEmailGet",
          "request": {
            "url": {
              "protocol": "http",
              "host": "meeting.is",
              "path": [
                "ss",
                "api",
                "user_access/:email"
              ],
              "variable": [
                {
                  "id": "email",
                  "value": "{}",
                  "type": "string"
                }
              ]
            },
            "method": "GET",
            "header": [
              {
                "key": "Accept",
                "value": "*/*",
                "disabled": false
              }
            ],
            "body": {
              "mode": "raw"
            },
            "description": "Retrieve a single user in your company account. Their email address, privilege level and whether they are in your pool of users handling demo requests is shown.\n\nPossible values for **privilege** are:\n* **user** (a normal user of the system)\n* **admin** (a user who can invite others, change configuration of the company account, and more)\n* **owner** (an admin who is also the billing contact for the company)\n* **reporting** (a non-admin who has access to reporting functionality only)\n\nPossible values for **in_demo_pool** are **true**, **false** and **null** which should be considered the same as **false**.\n\nThe users' email address is shown in the **email** attribute."
          },
          "response": [
            {
              "status": "OK",
              "code": 200,
              "name": "Response_200",
              "id": "fb62170a-cb33-4589-b8f1-96b2486f774e"
            }
          ]
        }
      ]
    }
  ]
}