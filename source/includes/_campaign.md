# Campaign APIs

> Example API request (Create new campaign)

```bash
curl --location --request POST 'https://api.tellephant.com/v1/campaign' \
--header 'Content-Type: application/json' \
--data-raw '{
    "apikey": "918273987123",
    "campaign_name": "test api campaign",
    "template": "account_live_new",
    "list_id": "61c18f26575fe61939296e42",
    "variables": [
        "name",
        "phone"
    ],
    "is_test": true
}'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({
  apikey: "918273987123",
  campaign_name: "test api campaign",
  template: "account_live_new",
  list_id: "61c18f26575fe61939296e42",
  variables: ["name", "phone"],
  is_test: true,
});

var requestOptions = {
  method: "POST",
  headers: myHeaders,
  body: raw,
  redirect: "follow",
};

fetch("https://api.tellephant.com/v1/campaign", requestOptions)
  .then((response) => response.text())
  .then((result) => console.log(result))
  .catch((error) => console.log("error", error));
```

```php
<?php
$client = new http\Client;
$request = new http\Client\Request;
$request->setRequestUrl('https://api.tellephant.com/v1/campaign');
$request->setRequestMethod('POST');
$body = new http\Message\Body;
$body->append('{
    "apikey": "918273987123",
    "campaign_name": "test api campaign",
    "template": "account_live_new",
    "list_id": "61c18f26575fe61939296e42",
    "variables": [
        "name",
        "phone"
    ],
    "is_test": true
}');
$request->setBody($body);
$request->setOptions(array());
$request->setHeaders(array(
  'Content-Type' => 'application/json'
));
$client->enqueue($request)->send();
$response = $client->getResponse();
echo $response->getBody();

```

```python
import http.client

conn = http.client.HTTPSConnection("api.tellephant.com")
payload = "{\n    \"apikey\": \"918273987123\",\n    \"campaign_name\": \"test api campaign\",\n    \"template\": \"account_live_new\",\n    \"list_id\": \"61c18f26575fe61939296e42\",\n    \"variables\": [\n        \"name\",\n        \"phone\"\n    ],\n    \"is_test\": true\n}"
headers = {
  'Content-Type': 'application/json'
}
conn.request("POST", "/v1/campaign", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

### Create new campaign

Used to broadcast messages to a list of users.

`POST v1/campaign`

Body Parameters

| Parameter             | Type            | Status   | Description                                |
| --------------------- | --------------- | -------- | ------------------------------------------ |
| `apikey`              | String          | required | API KEY Provided                           |
| `campaign_name`       | String          | required | Name of campaign                           |
| `template`            | String          | required | HSM template used for messages             |
| `list_id`             | String          | required | List to which messages are sent            |
| `variables`           | Array           | required | Template Variables                         |
| `attachment_variable` |                 | optional | Attachment Variable                        |
| `cta_variable`        |                 | optional | CTA Variable                               |
| `campaign_delivery`   | timestamp (int) | optional | Schedule broadcast for this time           |
| `is_test`             | boolean         | optional | Test broadcast by sending only one message |



> Example Response (Create new campaign)

```json
{
    "code": 200,
    "message": "Congratulations, Your Campaign Has Been Sent!",
    "data": {
        "channel": "whatsapp",
        "campaign_name": "test api campaign",
        "template": "account_live_new",
        "list_type": "list",
        "list_id": "61c0238afa400169e85587b6",
        "variables": [
            "name",
            "phone"
        ],
        "attachment_variable": null,
        "cta_variable": null,
        "location_variable": {
            "latitude": null,
            "longitude": null
        },
        "campaign_delivery": {
            "created": 1640156740
        },
        "test": true,
        "user_id": "619f2e655259ba4d30248ee2",
        "campaign_status": "created",
        "template_id": "619f2e6a5259ba4d30248ee8",
        "updated_at": "2021-12-22 02:05:41",
        "created_at": "2021-12-22 02:05:41",
        "_id": "61c2ce453a00374e3d5b5792"
    }
}
```



### Get All Campaigns

`GET v1/campaign`

Body Parameters

| Parameter | Type   | Status   | Description      |
| --------- | ------ | -------- | ---------------- |
| `apikey`  | String | required | API KEY Provided |


> Example Response (All campaigns)

```json
{
    "code": 200,
    "data": [
        {
            "_id": "61c20f6b1d95f426317a2",
            "channel": "whatsapp",
            "campaign_name": "test api campaign",
            "template": "account_live_new",
            "list_type": "list",
            "list_id": "61c0238afa400169e8",
            "variables": [
                "name",
                "phone"
            ],
            "attachment_variable": null,
            "cta_variable": null,
            "campaign_delivery": {
                "created": 1640107883
            },
            "test": true,
            "user_id": "619f2e655259ba4d3",
            "campaign_status": "created",
            "template_id": "a4d30248ee8",
            "updated_at": "2021-12-21 23:01:23",
            "created_at": "2021-12-21 23:01:23"
        },
        {
            "_id": "61c20cd058c7205d942e4",
            "channel": "whatsapp",
            "campaign_name": "test api campaign",
            "template": "account_live_new",
            "list_type": "list",
            "list_id": "61c0238afa400169e8",
            "variables": [
                "name",
                "phone"
            ],
            "attachment_variable": null,
            "cta_variable": null,
            "campaign_delivery": {
                "created": 1640107215
            },
            "test": true,
            "user_id": "619f2e655259ba4d3",
            "campaign_status": "created",
            "template_id": "f55e611e5e9",
            "updated_at": "2021-12-21 22:50:16",
            "created_at": "2021-12-21 22:50:16"
        }
    ]
}
```


### Get Campaign Details

`GET v1/campaign/details`

Body Parameters

| Parameter     | Type   | Status   | Description                        |
| ------------- | ------ | -------- | ---------------------------------- |
| `apikey`      | String | required | API KEY Provided                   |
| `campaign_id` | String | required | ID of campaign you want details of |


> Example Response (Campaign Detail)

```json
{
    "code": 200,
    "data": {
        "messages": [
            {
                "_id": "61c210211bb912599368df02",
                "user_id": "619b5c8fb493ab68a24e50c2",
                "to_number": "917982347685",
                "template_id": "account_live_new",
                "message": "Hi dhruv,\n\nWelcome to Aiyo Labs. Your account number 917982347685 has been set up and is now live.",
                "message_status": "seen",
                "updated_at": "2021-12-21 23:04:35",
                "created_at": "2021-12-21 23:04:25"
            }
        ],
        "campaign": {
            "_id": "61c2101a06b6b413656988d2",
            "channel": "whatsapp",
            "campaign_name": "test api campaign",
            "template": "account_live_new",
            "list_type": "list",
            "list_id": "61c18f26575fe61939296e42",
            "variables": [
                "name",
                "phone"
            ],
            "attachment_variable": null,
            "cta_variable": null,
            "location_variable": {
                "latitude": null,
                "longitude": null
            },
            "campaign_delivery": {
                "created": 1640108058,
                "processing": 1640108064,
                "completed": 1640108065
            },
            "test": true,
            "user_id": "619b5c8fb493ab68a24e50c2",
            "campaign_status": "completed",
            "template_id": "619b5c90b493ab68a24e50c8",
            "updated_at": "2021-12-21 23:04:25",
            "created_at": "2021-12-21 23:04:18"
        },
        "total": 1,
        "delivered": 0,
        "seen": 1,
        "failed": 0,
        "accepted": 0,
        "seen_rate": 100
    }
}
```
