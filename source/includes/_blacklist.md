# Blacklist APIs

> Example API request (Get Contacts)

```bash
curl --location --request POST 'https://api.tellephant.com/v1/user/blacklist' \
--header 'Content-Type: application/json' \
--data-raw '{
    "apikey": "",
    "type": "blocked"
}'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({ apikey: "", type: "blocked" });

var requestOptions = {
  method: "POST",
  headers: myHeaders,
  body: raw,
  redirect: "follow",
};

fetch("https://api.tellephant.com/v1/user/blacklist", requestOptions)
  .then((response) => response.text())
  .then((result) => console.log(result))
  .catch((error) => console.log("error", error));
```

```php
<?php
$client = new http\Client;
$request = new http\Client\Request;
$request->setRequestUrl('https://api.tellephant.com/v1/user/blacklist');
$request->setRequestMethod('POST');
$body = new http\Message\Body;
$body->append('{
    "apikey": "",
    "type": "blocked"
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
payload = "{\n    \"apikey\": \"\",\n    \"type\": \"blocked\"\n}"
headers = {
  'Content-Type': 'application/json'
}
conn.request("POST", "/v1/user/blacklist", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

### Get Contacts

Used to broadcast messages to a list of users.

`POST v1/user/blacklist`

Body Parameters

| Parameter | Type   | Status   | Description                                      |
| --------- | ------ | -------- | ------------------------------------------------ |
| `apikey`  | String | required | API KEY Provided                                 |
| `type`    | String | required | Type of list - blacklist,whitelist,block,unblock |

> Example Response (Get Contacts)

```json
{
  "data": ["919999733549", "918946924778"]
}
```

### Update Contacts

`POST v1/user/blacklist/update`

Body Parameters

| Parameter  | Type          | Status   | Description                                      |
| ---------- | ------------- | -------- | ------------------------------------------------ |
| `apikey`   | String        | required | API KEY Provided                                 |
| `contacts` | Array<String> | required | Array of phone numbers                           |
| `type`     | String        | required | Type of list - blacklist,whitelist,block,unblock |

> Example Response (Update Contacts)

```json
{
  "success": true,
  "message": "Contact(s) successfully blacklisted"
}
```
