# Webhook Management

APIs for managing account level information

## Get Webhooks

[Get the current webhooks]

> Example request

```bash
curl -X POST \
    "https://app.tellephant.com/api/v2/user/webhook" \
    -H "Content-Type: application/json" \
    -H "Accept: application/json" \
    -d '{"apikey":"CAGHDVFHVFUDUYRFGUFJYR"}'
```

```javascript
const url = new URL(
    "https://app.tellephant.com/api/v2/user/webhook"
);

let headers = {
    "Content-Type": "application/json",
    "Accept": "application/json",
};

let body = {
    "apikey": "CAGHDVFHVFUDUYRFGUFJYR"
}

fetch(url, {
    method: "POST",
    headers: headers,
    body: body
})
    .then(response =&gt; response.json())
    .then(json =&gt; console.log(json));
```

```php
$client = new \GuzzleHttp\Client();
$response = $client-&gt;post(
    'https://app.tellephant.com/api/v2/user/webhook',
    [
        'headers' =&gt; [
            'Content-Type' =&gt; 'application/json',
            'Accept' =&gt; 'application/json',
        ],
        'json' =&gt; [
            'apikey' =&gt; 'CAGHDVFHVFUDUYRFGUFJYR',
        ],
    ]
);
$body = $response-&gt;getBody();
print_r(json_decode((string) $body));
```

```python
import requests
import json

url = 'https://app.tellephant.com/api/v2/user/webhook'
payload = {
    "apikey": "CAGHDVFHVFUDUYRFGUFJYR"
}
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}
response = requests.request('POST', url, headers=headers, json=payload)
response.json()
```

> Example response (200)

```json
{
  "success": true,
  "webhooks": {
    "delivery_response": {
      "url": "https://requestbin.com/r/XXXXXXXX",
      "status": false
    },
    "incoming_message": {
      "url": "https://requestbin.com/r/XXXXXXXXX",
      "status": true
    }
  }
}
```

> Example response (422)

```json
{
  "status": false,
  "error": {
    "apikey": ["The apikey field is required."]
  }
}
```

> Example response (401)

```json
{
  "status": false,
  "error": "Invalid API Key Provided"
}
```

### HTTP Request

`POST api/v2/user/webhook`

### Body Parameters

<table>
<thead>
<tr>
<th>Parameter</th>
<th>Type</th>
<th>Status</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>apikey</code></td>
<td>String</td>
<td>required</td>
<td>API KEY Provided.</td>
</tr>
</tbody>
</table>

## Update Webhooks

[Update the current webhooks]

> Example request

```bash
curl -X POST \
    "https://app.tellephant.com/api/v2/user/webhook/update" \
    -H "Content-Type: application/json" \
    -H "Accept: application/json" \
    -d '{"apikey":"CAGHDVFHVFUDUYRFGUFJYR","webhook_type":"delivery_response","webhook_endpoint":"\"https:\/\/requestbin.com\/r\/xxxxxxxx\"","webhook_status":"true"}'
```

```javascript
const url = new URL(
    "https://app.tellephant.com/api/v2/user/webhook/update"
);

let headers = {
    "Content-Type": "application/json",
    "Accept": "application/json",
};

let body = {
    "apikey": "CAGHDVFHVFUDUYRFGUFJYR",
    "webhook_type": "delivery_response",
    "webhook_endpoint": "\"https:\/\/requestbin.com\/r\/xxxxxxxx\"",
    "webhook_status": "true"
}

fetch(url, {
    method: "POST",
    headers: headers,
    body: body
})
    .then(response =&gt; response.json())
    .then(json =&gt; console.log(json));
```

```php
$client = new \GuzzleHttp\Client();
$response = $client-&gt;post(
    'https://app.tellephant.com/api/v2/user/webhook/update',
    [
        'headers' =&gt; [
            'Content-Type' =&gt; 'application/json',
            'Accept' =&gt; 'application/json',
        ],
        'json' =&gt; [
            'apikey' =&gt; 'CAGHDVFHVFUDUYRFGUFJYR',
            'webhook_type' =&gt; 'delivery_response',
            'webhook_endpoint' =&gt; '"https://requestbin.com/r/xxxxxxxx"',
            'webhook_status' =&gt; 'true',
        ],
    ]
);
$body = $response-&gt;getBody();
print_r(json_decode((string) $body));
```

```python
import requests
import json

url = 'https://app.tellephant.com/api/v2/user/webhook/update'
payload = {
    "apikey": "CAGHDVFHVFUDUYRFGUFJYR",
    "webhook_type": "delivery_response",
    "webhook_endpoint": "\"https:\/\/requestbin.com\/r\/xxxxxxxx\"",
    "webhook_status": "true"
}
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}
response = requests.request('POST', url, headers=headers, json=payload)
response.json()
```

> Example response (200)

```json
{
  "success": true,
  "message": "Webhook successfully updated."
}
```

> Example response (422)

```json
{
  "status": false,
  "error": {
    "apikey": ["The apikey field is required."],
    "webhook_type": ["The webhook type field is required."],
    "webhook_endpoint": ["The webhook endpoint field is required."],
    "webhook_status": ["The webhook status field is required."]
  }
}
```

> Example response (401)

```json
{
  "status": false,
  "error": "Invalid API Key Provided"
}
```

### HTTP Request

`POST api/v2/user/webhook/update`

### Body Parameters

<table>
<thead>
<tr>
<th>Parameter</th>
<th>Type</th>
<th>Status</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td><code>apikey</code></td>
<td>String</td>
<td>required</td>
<td>API KEY Provided.</td>
</tr>
<tr>
<td><code>webhook_type</code></td>
<td>String</td>
<td>required</td>
<td>Webhook Type Provided.</td>
</tr>
<tr>
<td><code>webhook_endpoint</code></td>
<td>Url</td>
<td>required</td>
<td>Webhook Endpoint Provided.</td>
</tr>
<tr>
<td><code>webhook_status</code></td>
<td>Boolean</td>
<td>required</td>
<td>Webhook Status Provided.</td>
</tr>
</tbody>
</table>

## Message Delivery Response

### Message Accepted Response

` { "messageId": "60003fae6203e5098b751213", "status": "accepted", "timestamp": "2021-01-14T12:57:20.032134Z" }`

### Message Delivery Response

` { "messageId": "60003fae6203e5098b751213", "status": "delivered", "timestamp": "2021-01-14T12:57:20.253171Z" }`

### Message Seen Response

` { "messageId": "60003fae6203e5098b751213", "status": "seen", "timestamp": "2021-01-14T12:57:45Z" }`
<br>

<aside class="success">
Note: For every WhatsApp message sent, there are three hits made to your webhook url i.e. (accepted, delivered and seen).
</aside>

## Incoming Payload (Text)
`
{
    "messageId": "600042f62905c2668e678deb",
    "from": "Sender_number_with_country_code",
    "sender_name": "Sender_name",
    "to": "Recipient_number_with_country_code",
    "timestamp": "2021-01-14T13:11:17Z",
    "content_type": "text",
    "text": "Message_body",
    "received_at": "2021-01-14T13:11:17Z"
}`

<aside class="success">
Note: for every WhatsApp text message sent by the user to your Official WhatsApp Business Account, the incoming response is as shown above.
</aside>

## Incoming Payload (Image)
`
{
    "messageId": "6000442d78789049501796f9",
    "from": "Sender_number_with_country_code",
    "sender_name": "Sender_name",
    "to": "Recipient_number_with_country_code",
    "timestamp": "2021-01-14T13:16:28Z",
    "content_type": "image",
    "media_url": "file_url",
    "received_at": "2021-01-14T13:16:28Z"
}`

<aside class="success">
Note: for every WhatsApp image message sent by the user to your Official WhatsApp Business Account, the incoming response is as shown above.
</aside>

## Incoming Payload (Document)
`
{
    "messageId": "600044a8536544020b0a1346",
    "from": "Sender_number_with_country_code",
    "sender_name": "Sender_name",
    "to": "Recipient_number_with_country_code",
    "timestamp": "2021-01-14T13:18:30Z",
    "content_type": "document",
    "media_url": "file_url",
    "filename": "file_name.pdf",
    "caption": "file_caption",
    "received_at": "2021-01-14T13:18:30Z"
}`

<aside class="success">
Note: for every WhatsApp pdf message sent by the user to your Official WhatsApp Business Account, the incoming response is as shown above.
</aside>

## Incoming Payload (Sticker)
`
{
    "messageId": "600138de6e99f9269c24252d",
    "from": "Sender_number_with_country_code",
    "sender_name": "Sender_name",
    "to": "Recipient_number_with_country_code",
    "timestamp": "2021-01-15T06:40:28Z",
    "content_type": "sticker",
    "media_url": "file_url",
    "received_at": "2021-01-15T06:40:28Z"
}`

<aside class="success">
Note: for every WhatsApp sticker message sent by the user to your Official WhatsApp Business Account, the incoming response is as shown above.
</aside>

## Incoming Payload (Video)
`
{
    "messageId": "60013953d0d9562caa25fee2",
    "from": "Sender_number_with_country_code",
    "sender_name": "Sender_name",
    "to": "Recipient_number_with_country_code",
    "timestamp": "2021-01-15T06:42:22Z",
    "content_type": "video",
    "media_url": "file_url",
    "received_at": "2021-01-15T06:42:22Z"
}`

<aside class="success">
Note: for every WhatsApp video message sent by the user to your Official WhatsApp Business Account, the incoming response is as shown above.
</aside>

## Incoming Payload (Audio)
`
{
    "messageId": "600139a3650de2794016f889",
    "from": "Sender_number_with_country_code",
    "sender_name": "Sender_name",
    "to": "Recipient_number_with_country_code",
    "timestamp": "2021-01-15T06:43:46Z",
    "content_type": "voice",
    "media_url": "file_url",
    "received_at": "2021-01-15T06:43:46Z"
}`

<aside class="success">
Note: for every WhatsApp audio message sent by the user to your Official WhatsApp Business Account, the incoming response is as shown above.
</aside>

## Incoming Payload (Location)
`
{
    "messageId": "600139f1d935a0795a64ef0c",
    "from": "Sender_number_with_country_code",
    "sender_name": "Sender_name",
    "to": "Recipient_number_with_country_code",
    "timestamp": "2021-01-15T06:45:04Z",
    "content_type": "location",
    "location": {
        "longitude": 77.0952894,
        "latitude": 28.6297149
    },
    "received_at": "2021-01-15T06:45:04Z"
}`

<aside class="success">
Note: for every WhatsApp location message sent by the user to your Official WhatsApp Business Account, the incoming response is as shown above.
</aside>

## Incoming Payload (Contact)
`
{
    "messageId": "60013a52d0d9562caa25fee6",
    "from": "Sender_number_with_country_code",
    "sender_name": "Sender_name",
    "to": "Recipient_number_with_country_code",
    "timestamp": "2021-01-15T06:46:42Z",
    "content_type": "contacts",
    "contacts": [
        {
            "addresses": [],
            "emails": [],
            "ims": [],
            "name": {
                "firstName": "First_name",
                "middleName": "Middle_name",
                "lastName": "Last_name",
                "formattedName": "Full_Name"
            },
            "org": {
                "company": "Company_Name"
            },
            "phones": [
                {
                    "phone": "Number_with_country_code",
                    "type": "Mobile",
                    "waId": "formated_number"
                }
            ],
            "urls": []
        }
    ],
    "received_at": "2021-01-15T06:46:42Z"
}`

<aside class="success">
Note: for every WhatsApp contact message sent by the user to your Official WhatsApp Business Account, the incoming response is as shown above.
</aside>
