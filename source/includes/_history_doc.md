## Message History

> Message History Example request

```bash
curl --location --request POST 'https://api.tellephant.com/v1/message-history' \
--header 'Content-Type: application/json' \
--data-raw '{
    "apikey" : "< apikey >",
    "messageId" : "< message id >"
}'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({ apikey: "< apikey >", messageId: "< message id >" });
30;

var requestOptions = {
  method: "POST",
  headers: myHeaders,
  body: raw,
  redirect: "follow",
};

fetch("https://api.tellephant.com/v1/message-history", requestOptions)
  .then((response) => response.text())
  .then((result) => console.log(result))
  .catch((error) => console.log("error", error));
```

```php
$client = new http\Client;
$request = new http\Client\Request;
$request->setRequestUrl('https://api.tellephant.com/v1/message-history');
$request->setRequestMethod('POST');
$body = new http\Message\Body;
$body->append('{
    "apikey" : "< apikey >",
    "messageId" : "< message id >"
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
import requests

url = "https://api.tellephant.com/v1/message-history"

payload="{\"apikey\" : \"< apikey >\",    \"messageId\" : \"< message id >\"}"
headers = {
  'Content-Type': 'application/json'
}

response = requests.request("POST", url, headers=headers, data=payload)

print(response.text)
```

> Example response (200)

```json
[
  {
    "message_state": "message-accepted",
    "happened_at": "2021-09-01T11:04:48+00:00"
  },
  {
    "message_state": "message-delivered",
    "happened_at": "2021-09-01T11:04:49+00:00"
  },
  {
    "message_state": "message-read",
    "happened_at": "2021-09-01T11:06:32+00:00"
  }
]
```

> Example response (401)

```json
{
  "error": "Invalid API Key Provided"
}
```

> Example response (404)

```json
{
  "error": "Message not found"
}
```

### Check message history via this path.

`POST v1/message-history`

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
        <td><code>messageId</code></td>
        <td>String</td>
        <td>required</td>
        <td>A unique key returned for every message sent</td>
    </tr>
    </tbody>
</table>

<aside class="success">
<b>Note:</b> 
The <b>messageId</b> is returned for every HSM/template and session message that is sent.
</aside>
