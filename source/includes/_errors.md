# Errors

Tellephant APIs uses conventional HTTP response codes to indicate the success or failure of an API request.

Error Code | Meaning
---------- | -------
200 - OK | The request was successful.
400 - Bad request | The request is invalid.
401 - Unauthorized | No valid API key was provided.
404 - Not found	| The requested endpoint does not exist.
429 - Too many requests | You have reached your usage limit. Contact support to upgrade your plan to increase your limit.
5XX - Server errors | Something went wrong on ScrapeHunt's end.
