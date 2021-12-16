## OTP Service

APIs for using OTP as a Service

### Generate OTP

[Request for an OTP.]

> Example request

```bash
curl -X POST \
    "https://api.tellephant.com/v1/send-otp" \
    -H "Content-Type: application/json" \
    -H "Accept: application/json" \
    -d '{"apikey":"ABCDEFGHIJKLMNOPQRSTUVWXYZ","to":919999999999,"organisation_name":"Aiyo Labs"}'
```

```javascript
const url = new URL(
    "https://api.tellephant.com/v1/send-otp"
);

let headers = {
"Content-Type": "application/json",
"Accept": "application/json",
};

let body = {
"apikey": "ABCDEFGHIJKLMNOPQRSTUVWXYZ",
"to": 919999999999,
"organisation_name": "Aiyo Labs"
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
    'https://api.tellephant.com/v1/send-otp',
    [
        'headers' =&gt; [
            'Content-Type' =&gt; 'application/json',
            'Accept' =&gt; 'application/json',
        ],
        'json' =&gt; [
            'apikey' =&gt; 'ABCDEFGHIJKLMNOPQRSTUVWXYZ',
            'to' =&gt; 919999999999,
            'organisation_name' =&gt; 'Aiyo Labs',
        ],
    ]
);
$body = $response-&gt;getBody();
print_r(json_decode((string) $body));
```

```python
import requests
import json

url = 'https://api.tellephant.com/v1/send-otp'
payload = {
    "apikey": "ABCDEFGHIJKLMNOPQRSTUVWXYZ",
    "to": 919999999999,
    "organisation_name": "Aiyo Labs"
}
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}
response = requests.request('POST', url, headers=headers, json=payload)
response.json()
```

> Example response (201)

```json
{
  "success": true,
  "otpId": "CAGHDVFHVFUDUYRFGUFJYR"
}
```

> Example response (422)

```json
{
  "status": false,
  "error": {
    "apikey": ["The apikey field is required."],
    "to": ["The to field is required."],
    "organisation_name": ["The organisation_name field is required."]
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

> Example response (401)

```json
{
  "status": false,
  "error": "Please subscribe to addon first"
}
```

> Example response (403)

```json
{
  "status": false,
  "error": "Balance Low! Please recharge!"
}
```

### HTTP Request

`POST v1/send-otp`

#### Body Parameters

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
<td><code>to</code></td>
<td>integer</td>
<td>required</td>
<td>to send OTP to.</td>
</tr>
<tr>
<td><code>organisation_name</code></td>
<td>String</td>
<td>required</td>
<td>Name of the organisation.</td>
</tr>
</tbody>
</table>

### Validate the OTP

[Verify the OTP if it&#039;s correct]

> Example request

```bash
curl -X POST \
    "https://api.tellephant.com/v1/validate-otp" \
    -H "Content-Type: application/json" \
    -H "Accept: application/json" \
    -d '{"apikey":"pi","otpId":"CAGHDVFHVFUDUYRFGUFJYR","otp":123456}'
```

```javascript
const url = new URL(
    "https://api.tellephant.com/v1/validate-otp"
);

let headers = {
"Content-Type": "application/json",
"Accept": "application/json",
};

let body = {
"apikey": "pi",
"otpId": "CAGHDVFHVFUDUYRFGUFJYR",
"otp": 123456
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
    'https://api.tellephant.com/v1/validate-otp',
    [
        'headers' =&gt; [
            'Content-Type' =&gt; 'application/json',
            'Accept' =&gt; 'application/json',
        ],
        'json' =&gt; [
            'apikey' =&gt; 'pi',
            'otpId' =&gt; 'CAGHDVFHVFUDUYRFGUFJYR',
            'otp' =&gt; 123456,
        ],
    ]
);
$body = $response-&gt;getBody();
print_r(json_decode((string) $body));
```

```python
import requests
import json

url = 'https://api.tellephant.com/v1/validate-otp'
payload = {
    "apikey": "pi",
    "otpId": "CAGHDVFHVFUDUYRFGUFJYR",
    "otp": 123456
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
  "message": "OTP is valid"
}
```

> Example response (200)

```json
{
  "success": false,
  "message": "OTP is either expired or already used."
}
```

> Example response (200)

```json
{
  "success": false,
  "message": "Invalid OtpId Provided."
}
```

> Example response (200)

```json
{
  "success": false,
  "message": "OTP does not match."
}
```

> Example response (422)

```json
{
  "status": false,
  "error": {
    "apikey": ["The apikey field is required."],
    "otpId": ["The otpId field is required."],
    "otp": ["The otp field is required."]
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

`POST v1/validate-otp`

#### Body Parameters

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
<td><code>otpId</code></td>
<td>String</td>
<td>required</td>
<td>OTP ID Received.</td>
</tr>
<tr>
<td><code>otp</code></td>
<td>integer</td>
<td>required</td>
<td>OTP to verify.</td>
</tr>
</tbody>
</table>
