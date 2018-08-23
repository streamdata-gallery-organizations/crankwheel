{
  "info": {
    "name": "CrankWheel Retrieve demo request history",
    "_postman_id": "39f654d4-705b-4c12-8776-49250398b98d",
    "description": "This API endpoint allows you to retrieve a history of demo requests made to your account in a given time period.\n\n## Request\n\nNote the to= and from= query parameters, which are timestamps.\n\nFor authentication, set your own API key in your environment or paste it instead of {{crankwheel-api-key}} in the value for the Authorization header under the Headers tab.\n\n## Response\n\nThe response is a JSON document.\n\nThe top level shows the number of cancelled demo requests during the period as total_canceled_requests.\n\nIt also has a list indexed as sessions.\n\nEach session in the list shows:\n* start_ts: The timestamp of the start of the session\n* last_event_ts: The timestamp of the last event received during the session, i.e. roughly when the session ended\n* availability_bucket: Which bucket of availability the CrankWheel system believed it was in. Values can be full_capacity if it believed that more than 50% of agents were available to do a demo, half_capacity if it believed that 50% or fewer were available, and no_capacity if it believed no agents were available. Availability is determined based on whether an agent has been active at their computer in the last 10 minutes, and also based on whether they are already screen sharing using CrankWheel.\n* seconds_to_respondHow many seconds it took to respond to the request, i.e. until an agent said they would handle it. If no agent handled the request (yet), the value will be never.\n* handled_by will be present if an agent handled the request and will show the agent's email address.\n* call_confirmed: Whether a call was confirmed. Values can be true, false or if the request was never responded to, n/a.\n* screenshared: Whether a screenshare was initiated after the call commenced. Values can be true, false or if a call was never initiated, n/a.\n* accepted_from shows a value of extension, email or n/a.\n\nLastly, the session contains a prospect_info object.\n\nThe fixed prospect_info keys are:\n* prospect-phone: The phone number entered by the prospect.\n* prospect-request-origin: The web page the request originated on. If originated from an email campaign, it will look like https://meeting.is/ss/showu/COMPANYSHORTNAME, possibly with parameters after the company's short name.\n* prospect-utm-source, prospect-utm-medium, prospect-utm-campaign, prospect-utm-term and prospect-utm-content: These reflect UTM parameters if they were present on the web page where the prospect requested a demo.\n\nInformation determined by lead enrichment, which may not always be 100% accurate:\n* prospect-location: Geographic location of the prospect as determined by their IP address.\n* prospect-enrich-full-name: The prospect's full name.\n* prospect-enrich-country: The prospect's country.\n* prospect-enrich-state: The prospect's state within their country.\n* prospect-enrich-company: The prospect's company name.\n* prospect-enrich-title: The prospect's title.\n* prospect-enrich-seniority: The prospect's level of seniority, for example \"executive\".\n* prospect-enrich-linkedin: The URL of the prospect's LinkedIn profile.\n* prospect-enrich-twitter: The URL of the prospect's Twitter profile.\n* prospect-enrich-company-sector: The sector of the prospect's company.\n* prospect-enrich-company-industry: The industry of the prospect's company.\n* prospect-enrich-company-employees: The number of employees at the prospect's company, or a range e.g. 10-20.\n* prospect-enrich-company-description: A brief description of the prospect's company.\n* prospect-enrich-company-linkedin: The URL of the prospect's company's LinkedIn profile.\n* prospect-enrich-company-twitter: The URL of the prospect's company's Twitter profile.\n* prospect-enrich-company-marketcap: The market capitalization of the prospect's company.\n\nIn addition, each lead capture question gets a key. Here is the default set, but keys for custom questions will inherit the name assigned to the question when it is created, e.g. prospect-shoesize for a question where you set the ID as shoesize:\n* prospect-name: The prospect's name as entered by themselves.\n* prospect-email: The prospect's email address as entered by themselves.\n* prospect-company: The prospect's company name as entered by themselves.\n* prospect-job-title: The prospect's title as entered by themselves.\n* prospect-website: The prospect's company's web page as entered by themselves.",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "Retrieve",
      "item": [
        {
          "id": "bda77dab-3d3b-4a62-b986-d15468c582aa",
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
              "id": "70e06b29-c0d6-450b-b171-3a3ed0dc4be7"
            }
          ]
        },
        {
          "id": "698a72b1-c6a6-4a74-95ab-1ed0515932d7",
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
              "id": "2715b991-e4a5-4079-808c-f863f5ca862e"
            }
          ]
        }
      ]
    }
  ]
}