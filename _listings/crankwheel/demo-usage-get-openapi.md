---
swagger: "2.0"
x-collection-name: CrankWheel
x-complete: 0
info:
  title: CrankWheel Retrieve demo request history
  description: |-
    This API endpoint allows you to retrieve a history of demo requests made to your account in a given time period.

    ## Request

    Note the to= and from= query parameters, which are timestamps.

    For authentication, set your own API key in your environment or paste it instead of {{crankwheel-api-key}} in the value for the Authorization header under the Headers tab.

    ## Response

    The response is a JSON document.

    The top level shows the number of cancelled demo requests during the period as total_canceled_requests.

    It also has a list indexed as sessions.

    Each session in the list shows:
    * start_ts: The timestamp of the start of the session
    * last_event_ts: The timestamp of the last event received during the session, i.e. roughly when the session ended
    * availability_bucket: Which bucket of availability the CrankWheel system believed it was in. Values can be full_capacity if it believed that more than 50% of agents were available to do a demo, half_capacity if it believed that 50% or fewer were available, and no_capacity if it believed no agents were available. Availability is determined based on whether an agent has been active at their computer in the last 10 minutes, and also based on whether they are already screen sharing using CrankWheel.
    * seconds_to_respondHow many seconds it took to respond to the request, i.e. until an agent said they would handle it. If no agent handled the request (yet), the value will be never.
    * handled_by will be present if an agent handled the request and will show the agent's email address.
    * call_confirmed: Whether a call was confirmed. Values can be true, false or if the request was never responded to, n/a.
    * screenshared: Whether a screenshare was initiated after the call commenced. Values can be true, false or if a call was never initiated, n/a.
    * accepted_from shows a value of extension, email or n/a.

    Lastly, the session contains a prospect_info object.

    The fixed prospect_info keys are:
    * prospect-phone: The phone number entered by the prospect.
    * prospect-request-origin: The web page the request originated on. If originated from an email campaign, it will look like https://meeting.is/ss/showu/COMPANYSHORTNAME, possibly with parameters after the company's short name.
    * prospect-utm-source, prospect-utm-medium, prospect-utm-campaign, prospect-utm-term and prospect-utm-content: These reflect UTM parameters if they were present on the web page where the prospect requested a demo.

    Information determined by lead enrichment, which may not always be 100% accurate:
    * prospect-location: Geographic location of the prospect as determined by their IP address.
    * prospect-enrich-full-name: The prospect's full name.
    * prospect-enrich-country: The prospect's country.
    * prospect-enrich-state: The prospect's state within their country.
    * prospect-enrich-company: The prospect's company name.
    * prospect-enrich-title: The prospect's title.
    * prospect-enrich-seniority: The prospect's level of seniority, for example "executive".
    * prospect-enrich-linkedin: The URL of the prospect's LinkedIn profile.
    * prospect-enrich-twitter: The URL of the prospect's Twitter profile.
    * prospect-enrich-company-sector: The sector of the prospect's company.
    * prospect-enrich-company-industry: The industry of the prospect's company.
    * prospect-enrich-company-employees: The number of employees at the prospect's company, or a range e.g. 10-20.
    * prospect-enrich-company-description: A brief description of the prospect's company.
    * prospect-enrich-company-linkedin: The URL of the prospect's company's LinkedIn profile.
    * prospect-enrich-company-twitter: The URL of the prospect's company's Twitter profile.
    * prospect-enrich-company-marketcap: The market capitalization of the prospect's company.

    In addition, each lead capture question gets a key. Here is the default set, but keys for custom questions will inherit the name assigned to the question when it is created, e.g. prospect-shoesize for a question where you set the ID as shoesize:
    * prospect-name: The prospect's name as entered by themselves.
    * prospect-email: The prospect's email address as entered by themselves.
    * prospect-company: The prospect's company name as entered by themselves.
    * prospect-job-title: The prospect's title as entered by themselves.
    * prospect-website: The prospect's company's web page as entered by themselves.
  version: "1.0"
host: meeting.is
basePath: /ss/api
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /usage:
    get:
      summary: Retrieve usage history
      description: |-
        This API endpoint retrieves usage history from your CrankWheel account.

        ## Request

        Note the to= and from= query parameters which are timestamps.

        For authentication, set your own API key in your environment or paste it instead of {{crankwheel-api-key}} in the value for the Authorization header under the Headers tab.

        ## Response

        The response is a JSON document.

        The "stats" collection shows summary statistics for the number of meetings and number of total seconds in meetings both in aggregate and per agent.

        The "sessions" list shows, for each session, the start and end time, the email of the agent presenting, the duration of the session in seconds, a log of the different things that were shared at different times, and information on how many viewers there were and where in the world they were located.
      operationId: UsageGet
      x-api-path-slug: usage-get
      parameters:
      - in: query
        name: from
      - in: query
        name: to
      responses:
        200:
          description: OK
      tags:
      - Retrieve
      - Usage
      - History
  /demo_usage:
    get:
      summary: Retrieve demo request history
      description: |-
        This API endpoint allows you to retrieve a history of demo requests made to your account in a given time period.

        ## Request

        Note the to= and from= query parameters, which are timestamps.

        For authentication, set your own API key in your environment or paste it instead of {{crankwheel-api-key}} in the value for the Authorization header under the Headers tab.

        ## Response

        The response is a JSON document.

        The top level shows the number of cancelled demo requests during the period as total_canceled_requests.

        It also has a list indexed as sessions.

        Each session in the list shows:
        * start_ts: The timestamp of the start of the session
        * last_event_ts: The timestamp of the last event received during the session, i.e. roughly when the session ended
        * availability_bucket: Which bucket of availability the CrankWheel system believed it was in. Values can be full_capacity if it believed that more than 50% of agents were available to do a demo, half_capacity if it believed that 50% or fewer were available, and no_capacity if it believed no agents were available. Availability is determined based on whether an agent has been active at their computer in the last 10 minutes, and also based on whether they are already screen sharing using CrankWheel.
        * seconds_to_respondHow many seconds it took to respond to the request, i.e. until an agent said they would handle it. If no agent handled the request (yet), the value will be never.
        * handled_by will be present if an agent handled the request and will show the agent's email address.
        * call_confirmed: Whether a call was confirmed. Values can be true, false or if the request was never responded to, n/a.
        * screenshared: Whether a screenshare was initiated after the call commenced. Values can be true, false or if a call was never initiated, n/a.
        * accepted_from shows a value of extension, email or n/a.

        Lastly, the session contains a prospect_info object.

        The fixed prospect_info keys are:
        * prospect-phone: The phone number entered by the prospect.
        * prospect-request-origin: The web page the request originated on. If originated from an email campaign, it will look like https://meeting.is/ss/showu/COMPANYSHORTNAME, possibly with parameters after the company's short name.
        * prospect-utm-source, prospect-utm-medium, prospect-utm-campaign, prospect-utm-term and prospect-utm-content: These reflect UTM parameters if they were present on the web page where the prospect requested a demo.

        Information determined by lead enrichment, which may not always be 100% accurate:
        * prospect-location: Geographic location of the prospect as determined by their IP address.
        * prospect-enrich-full-name: The prospect's full name.
        * prospect-enrich-country: The prospect's country.
        * prospect-enrich-state: The prospect's state within their country.
        * prospect-enrich-company: The prospect's company name.
        * prospect-enrich-title: The prospect's title.
        * prospect-enrich-seniority: The prospect's level of seniority, for example "executive".
        * prospect-enrich-linkedin: The URL of the prospect's LinkedIn profile.
        * prospect-enrich-twitter: The URL of the prospect's Twitter profile.
        * prospect-enrich-company-sector: The sector of the prospect's company.
        * prospect-enrich-company-industry: The industry of the prospect's company.
        * prospect-enrich-company-employees: The number of employees at the prospect's company, or a range e.g. 10-20.
        * prospect-enrich-company-description: A brief description of the prospect's company.
        * prospect-enrich-company-linkedin: The URL of the prospect's company's LinkedIn profile.
        * prospect-enrich-company-twitter: The URL of the prospect's company's Twitter profile.
        * prospect-enrich-company-marketcap: The market capitalization of the prospect's company.

        In addition, each lead capture question gets a key. Here is the default set, but keys for custom questions will inherit the name assigned to the question when it is created, e.g. prospect-shoesize for a question where you set the ID as shoesize:
        * prospect-name: The prospect's name as entered by themselves.
        * prospect-email: The prospect's email address as entered by themselves.
        * prospect-company: The prospect's company name as entered by themselves.
        * prospect-job-title: The prospect's title as entered by themselves.
        * prospect-website: The prospect's company's web page as entered by themselves.
      operationId: DemoUsageGet
      x-api-path-slug: demo-usage-get
      parameters:
      - in: query
        name: from
      - in: query
        name: to
      responses:
        200:
          description: OK
      tags:
      - Retrieve
      - Demo
      - Request
      - History
x-streamrank:
  polling_total_time_average: 0
  polling_size_download_average: 0
  streaming_total_time_average: 0
  streaming_size_download_average: 0
  change_yes: 0
  change_no: 0
  time_percentage: 0
  size_percentage: 0
  change_percentage: 0
  last_run: ""
  days_run: 0
  minute_run: 0
---