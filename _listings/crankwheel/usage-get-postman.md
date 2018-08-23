{
  "info": {
    "name": "CrankWheel Retrieve usage history",
    "_postman_id": "d2357608-01aa-4431-9274-d360549760de",
    "description": "This API endpoint retrieves usage history from your CrankWheel account.\n\n## Request\n\nNote the to= and from= query parameters which are timestamps.\n\nFor authentication, set your own API key in your environment or paste it instead of {{crankwheel-api-key}} in the value for the Authorization header under the Headers tab.\n\n## Response\n\nThe response is a JSON document.\n\nThe \"stats\" collection shows summary statistics for the number of meetings and number of total seconds in meetings both in aggregate and per agent.\n\nThe \"sessions\" list shows, for each session, the start and end time, the email of the agent presenting, the duration of the session in seconds, a log of the different things that were shared at different times, and information on how many viewers there were and where in the world they were located.",
    "schema": "https://schema.getpostman.com/json/collection/v2.0.0/"
  },
  "item": [
    {
      "name": "Retrieve",
      "item": [
        {
          "id": "aef73ac9-8700-4525-a720-c146419013fa",
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
              "id": "e22b3982-d06f-471f-8a56-bf25d1851c3d"
            }
          ]
        }
      ]
    }
  ]
}