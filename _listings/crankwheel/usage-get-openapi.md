---
swagger: "2.0"
x-collection-name: CrankWheel
x-complete: 0
info:
  title: CrankWheel Retrieve usage history
  description: |-
    This API endpoint retrieves usage history from your CrankWheel account.

    ## Request

    Note the to= and from= query parameters which are timestamps.

    For authentication, set your own API key in your environment or paste it instead of {{crankwheel-api-key}} in the value for the Authorization header under the Headers tab.

    ## Response

    The response is a JSON document.

    The "stats" collection shows summary statistics for the number of meetings and number of total seconds in meetings both in aggregate and per agent.

    The "sessions" list shows, for each session, the start and end time, the email of the agent presenting, the duration of the session in seconds, a log of the different things that were shared at different times, and information on how many viewers there were and where in the world they were located.
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