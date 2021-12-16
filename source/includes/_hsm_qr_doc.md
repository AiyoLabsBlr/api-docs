## HSM (Quick Reply Buttons)

> HSM / Template Messages Example request

```bash
curl -X POST \
    "https://api.tellephant.com/v1/send-message" \
    -H "Content-Type: application/json" \
    -H "Accept: application/json" \
    -d '{"apikey":"ABCDEFGHIJKLMNOPQRSTUVWXYZ","to":919999999999,"channels":["whatsapp"],"whatsapp":{"contentType":"template","template":{"templateId":"dummy_template_name","language":"en","components":[]}}}'
```

````javascript
const url = new URL(
    "https://api.tellephant.com/v1/send-message"
);

let headers = {
    "Content-Type": "application/json",
    "Accept": "application/json",
};

let body = {
    "apikey": "ABCDEFGHIJKLMNOPQRSTUVWXYZ",
    "to": 919999999999,
    "channels": [
        "whatsapp"
    ],
    "whatsapp": {
        "contentType": "template",
        "template": {
            "templateId": "dummy_template_name",
            "language": "en",
            "components": []
        }
    }
}

fetch(url, {
    method: "POST",
    headers: headers,
    body: body
})
    .then(response =&gt; response.json())
    .then(json =&gt; console.log(json));```

```php
$client = new \GuzzleHttp\Client();
$response = $client-&gt;post(
    'https://api.tellephant.com/v1/send-message',
    [
        'headers' =&gt; [
            'Content-Type' =&gt; 'application/json',
            'Accept' =&gt; 'application/json',
        ],
        'json' =&gt; [
            'apikey' =&gt; 'ABCDEFGHIJKLMNOPQRSTUVWXYZ',
            'to' =&gt; 919999999999,
            'channels' =&gt; [
                'whatsapp',
            ],
            'whatsapp' =&gt; [
                'contentType' =&gt; 'template',
                'template' =&gt; [
                    'templateId' =&gt; 'dummy_template_name',
                    'language' =&gt; 'en',
                    'components' =&gt; [],
                ],
            ],
        ],
    ]
);
$body = $response-&gt;getBody();
print_r(json_decode((string) $body));```

```python
import requests
import json

url = 'https://api.tellephant.com/v1/send-message'
payload = {
    "apikey": "ABCDEFGHIJKLMNOPQRSTUVWXYZ",
    "to": 919999999999,
    "channels": [
        "whatsapp"
    ],
    "whatsapp": {
        "contentType": "template",
        "template": {
            "templateId": "dummy_template_name",
            "language": "en",
            "components": []
        }
    }
}
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}
response = requests.request('POST', url, headers=headers, json=payload)
response.json()
````

> Example Component HSM / Template (TEXT with Quick Reply buttons)

```json
   "components" : [
                 {
                     "type" : "body",
                     "parameters" : [
                         {
                             "type" : "text",
                             "text" : "Dummy Text 1"
                         },
                         {
                             "type" : "text",
                             "text" : "Dummy Text 2"
                         }

                    ]
                 }
             ]
```

> Example Component HSM / Template (IMAGE with Quick Reply buttons)

```json
   "components": [
                {
                    "type": "header",
                    "parameters": [
                        {
                            "type": "media",
                            "media": {
                                "type": "image",
                                "url": "https://tellephant.s3.ap-south-1.amazonaws.com/dummy-media/sample.jpeg"
                            }
                        }
                    ]
                },
                {
                    "type": "body",
                    "parameters": [
                        {
                            "type": "text",
                            "text": "Dummy Text 1"
                        },
                        {
                            "type": "text",
                            "text": "Dummy Text 2"
                        }
                    ]
                }
            ]
```

> Example Component HSM / Template (DOCUMENT with Quick Reply buttons)

```json
   "components": [
                {
                    "type": "header",
                    "parameters": [
                        {
                            "type": "media",
                            "media": {
                                "type": "document",
                                "url": "https://tellephant.s3.ap-south-1.amazonaws.com/dummy-media/sample.pdf",
                                "filename": "Sample PDF"
                            }
                        }
                    ]
                },
                {
                    "type": "body",
                    "parameters": [
                        {
                            "type": "text",
                            "text": "Dummy Text 1"
                        },
                        {
                            "type": "text",
                            "text": "Dummy Text 2"
                        }
                    ]
                }
            ]
```

> Example Component HSM / Template (VIDEO with Quick Reply buttons)

```json
   "components": [
                {
                    "type": "header",
                    "parameters": [
                        {
                            "type": "media",
                            "media": {
                                "type": "video",
                                "url": "https://tellephant.s3.ap-south-1.amazonaws.com/dummy-media/sample.mp4",
                                "caption": "Sample Video"
                            }
                        }
                    ]
                }
            ]
```

> Example Component HSM / Template (Location with Quick Reply buttons)

```json
"components": [
                {
                    "type": "header",
                    "parameters": [
                        {
                            "type": "location",
                            "location": {
                                "latitude": 51.5005765,
                                "longitude": 7.4954884
                            }
                        }
                    ]
                },
                {
                    "type": "body",
                    "parameters": [
                        {
                            "type": "text",
                            "text": "Your text here"
                        }
                    ]
                }
            ]
```

> Example response (200)

```json{
    "success": true,
    "messageId": "CAGHDVFHVFUDUYRFGUFJYR"
}
```

> Example response (401)

```json{
    "status": false,
    "error": "Invalid API Key Provided"
}
```

> Example response (401)

```json{
    "status": false,
    "error": "Please subscribe to addon first"
}
```

> Example response (403)

```json{
    "status": false,
    "error": "Balance Low! Please recharge!"
}
```

### Send messages via this path.

`POST v1/send-message`

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
        <td><code>to</code></td>
        <td>integer</td>
        <td>required</td>
        <td>Number to send the message</td>
    </tr>
    <tr>
        <td><code>channels</code></td>
        <td>array</td>
        <td>required</td>
        <td>Channel(s) to be used.</td>
    </tr>
    <tr>
        <td><code>whatsapp.contentType</code></td>
        <td>String</td>
        <td>required</td>
        <td>Content type used</td>
    </tr>
    <tr>
        <td><code>whatsapp.template</code></td>
        <td>array</td>
        <td>required</td>
        <td>Template Details</td>
    </tr>
    <tr>
        <td><code>whatsapp.template.templateId</code></td>
        <td>String</td>
        <td>required</td>
        <td>Template identifier string</td>
    </tr>
    <tr>
        <td><code>whatsapp.template.language</code></td>
        <td>String</td>
        <td>required</td>
        <td>Language in the template</td>
    </tr>
    <tr>
        <td><code>whatsapp.template.components</code></td>
        <td>array</td>
        <td>required</td>
        <td>Template Data</td>
    </tr>
    </tbody>
</table>

<aside class="success">
Note: 
Quick Replies are typically used if you wish to give your users the choice between 1–3 possible answers. 
The user then simply needs to tap one of the quick replies to answer to your message.
No extra component is required in the request to send an HSM / Template with Quick Reply buttons.
</aside>

### HSM / Template (Text with Quick Reply buttons)

<table>
    <thead>
    <tr>
        <th>Parameter</th>
        <th>In</th>
        <th>Type</th>
        <th>Status</th>
        <th>Description</th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td><code>parameters</code></td>
        <td>body</td>
        <td>array</td>
        <td>required</td>
        <td>Parameters to be used in Component</td>
    </tr>
    <tr>
        <td><code>type</code></td>
        <td>body</td>
        <td>String</td>
        <td>required</td>
        <td>Text component for Whatsapp HSM / Template</td>
    </tr>
    <tr>
        <td><code>text</code></td>
        <td>body</td>
        <td>String</td>
        <td>required</td>
        <td>The text to be sent</td>
    </tr>
    </tbody>
</table>

<img src="/images/apidoc_ss/waba_hsm_qr/Hsm_text_qr.jpg" style="width: 50%;" alt="text">

### HSM / Template (Image with Quick Reply buttons)

<table>
    <thead>
    <tr>
        <th>Parameter</th>
        <th>In</th>
        <th>Type</th>
        <th>Status</th>
        <th>Description</th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td><code>parameters</code></td>
        <td>header</td>
        <td>array</td>
        <td>required</td>
        <td>Parameters to be used in Component</td>
    </tr>
    <tr>
        <td><code>type</code></td>
        <td>header</td>
        <td>String</td>
        <td>required</td>
        <td>Media component for Whatsapp HSM / Template</td>
    </tr>
    <tr>
        <td><code>type</code></td>
        <td>media</td>
        <td>String</td>
        <td>required</td>
        <td>Image header</td>
    </tr>
    <tr>
        <td><code>url</code></td>
        <td>media</td>
        <td>String</td>
        <td>required</td>
        <td>The url of the location where the image is stored</td>
    </tr>
    <tr>
        <td><code>type</code></td>
        <td>body</td>
        <td>String</td>
        <td>required</td>
        <td>Text component for Whatsapp HSM / Template</td>
    </tr>
    <tr>
        <td><code>text</code></td>
        <td>body</td>
        <td>String</td>
        <td>required</td>
        <td>The text to be sent</td>
    </tr>
    </tbody>
</table>

<img src="/images/apidoc_ss/waba_hsm_qr/Hsm_image_qr.jpg" style="width: 50%;" alt="text">

### HSM / Template (Document with Quick Reply buttons)

<table>
    <thead>
    <tr>
        <th>Parameter</th>
        <th>In</th>
        <th>Type</th>
        <th>Status</th>
        <th>Description</th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td><code>parameters</code></td>
        <td>header</td>
        <td>array</td>
        <td>required</td>
        <td>Parameters to be used in Component</td>
    </tr>
    <tr>
        <td><code>type</code></td>
        <td>header</td>
        <td>String</td>
        <td>required</td>
        <td>Media component for Whatsapp HSM / Template</td>
    </tr>
    <tr>
        <td><code>type</code></td>
        <td>media</td>
        <td>String</td>
        <td>required</td>
        <td>Document header</td>
    </tr>
    <tr>
        <td><code>url</code></td>
        <td>media</td>
        <td>String</td>
        <td>required</td>
        <td>The url of the location where the document is stored</td>
    </tr>
    <tr>
        <td><code>filename</code></td>
        <td>media</td>
        <td>String</td>
        <td>required</td>
        <td>Document Name</td>
    </tr>
    <tr>
        <td><code>type</code></td>
        <td>body</td>
        <td>String</td>
        <td>required</td>
        <td>Text component for Whatsapp HSM / Template</td>
    </tr>
    <tr>
        <td><code>text</code></td>
        <td>body</td>
        <td>String</td>
        <td>required</td>
        <td>The text to be sent</td>
    </tr>
    </tbody>
</table>

<img src="/images/apidoc_ss/waba_hsm_qr/Hsm_doc_qr.jpg" style="width: 50%;" alt="text">

### HSM / Template (VIDEO with Quick Reply buttons)

<table>
    <thead>
    <tr>
        <th>Parameter</th>
        <th>In</th>
        <th>Type</th>
        <th>Status</th>
        <th>Description</th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td><code>parameters</code></td>
        <td>header</td>
        <td>array</td>
        <td>required</td>
        <td>Parameters to be used in Component</td>
    </tr>
    <tr>
        <td><code>type</code></td>
        <td>header</td>
        <td>String</td>
        <td>required</td>
        <td>Media component for Whatsapp HSM / Template</td>
    </tr>
    <tr>
        <td><code>type</code></td>
        <td>media</td>
        <td>String</td>
        <td>required</td>
        <td>Video header</td>
    </tr>
    <tr>
        <td><code>url</code></td>
        <td>media</td>
        <td>String</td>
        <td>required</td>
        <td>The url of the location where the video is stored</td>
    </tr>
    <tr>
        <td><code>caption</code></td>
        <td>media</td>
        <td>String</td>
        <td>optional</td>
        <td>Additional caption for the video.</td>
    </tr>
    </tbody>
</table>

<img src="/images/apidoc_ss/waba_hsm_qr/Hsm_video_qr.jpg" style="width: 50%;" alt="text">

### HSM / Template (LOCATION with Quick Reply buttons)

<table>
    <thead>
    <tr>
        <th>Parameter</th>
        <th>In</th>
        <th>Type</th>
        <th>Status</th>
        <th>Description</th>
    </tr>
    </thead>
    <tbody>
    <tr>
        <td><code>parameters</code></td>
        <td>header</td>
        <td>array</td>
        <td>required</td>
        <td>Parameters to be used in Component</td>
    </tr>
    <tr>
        <td><code>type</code></td>
        <td>header</td>
        <td>String</td>
        <td>required</td>
        <td>Location component for Whatsapp HSM / Template</td>
    </tr>
    <tr>
        <td><code>latitude</code></td>
        <td>location</td>
        <td>number(double)</td>
        <td>required</td>
        <td>Latitude component of location</td>
    </tr>
    <tr>
        <td><code>longitude</code></td>
        <td>location</td>
        <td>number(double)</td>
        <td>required</td>
        <td>Longitude component of location</td>
    </tr>
    <tr>
        <td><code>type</code></td>
        <td>body</td>
        <td>String</td>
        <td>required</td>
        <td>Text component for Whatsapp HSM / Template</td>
    </tr>
    <tr>
        <td><code>text</code></td>
        <td>body</td>
        <td>String</td>
        <td>required</td>
        <td>The text to be sent</td>
    </tr>
    </tbody>
</table>
