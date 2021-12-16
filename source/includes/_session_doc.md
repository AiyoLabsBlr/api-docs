## Session Messages

> Session Messages Example request

```bash
curl -X POST \
    "https://api.tellephant.com/v1/send-message" \
    -H "Content-Type: application/json" \
    -H "Accept: application/json" \
    -d '{"apikey":"ABCDEFGHIJKLMNOPQRSTUVWXYZ","to":919999999999,"channels":["whatsapp"],"whatsapp": {}}'
```

```javascript
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
    "whatsapp": {}
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
            'whatsapp' =&gt; [],
        ],
    ]
);
$body = $response-&gt;getBody();
print_r(json_decode((string) $body));
```

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
    "whatsapp": {}
}
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}
response = requests.request('POST', url, headers=headers, json=payload)
response.json()
```

> Example Component Session Message (TEXT)

```json
"whatsapp" : {
        "contentType" : "text",
        "text" : "You message here"
    }

```

> Example Component Session Message (IMAGE)

```json
"whatsapp": {
        "contentType": "media",
        "media": {
            "type": "image",
            "url": "https://tellephant.s3.ap-south-1.amazonaws.com/dummy-media/sample.jpeg"
            "caption": "Some text description"
        }
    }

```

> Example Component Session Message (DOCUMENT)

```json
"whatsapp": {
        "contentType": "media",
        "media": {
            "type": "document",
            "url": "https://tellephant.s3.ap-south-1.amazonaws.com/dummy-media/sample.pdf",
            "filename" : "Sample PDF"
        }
    }

```

> Example Component Session Message (STICKER)

```json
"whatsapp": {
        "contentType": "media",
        "media": {
            "type": "sticker",
            "url": "https://tellephant.s3.ap-south-1.amazonaws.com/dummy-media/sample.webp"
        }
    }

```

> Example Component Session Message (VIDEO)

```json
"whatsapp": {
        "contentType": "media",
        "media": {
            "type": "video",
            "url": "https://tellephant.s3.ap-south-1.amazonaws.com/dummy-media/sample.mp4"
            "caption" : "Sample Video"
        }
    }

```

> Example Component Session Message (AUDIO)

```json
"whatsapp": {
        "contentType": "media",
        "media": {
            "type": "audio",
            "url": "https://tellephant.s3.ap-south-1.amazonaws.com/dummy-media/audio.mp3",
            "caption" : "Sample Audio"
        }
    }

```

> Example Component Session Message (LOCATION)

```json
"whatsapp": {
        "contentType": "location",
        "location": {
            "longitude": -73.9855,
            "latitude": 40.7580,
            "name" : "Times Square",
            "address" : "Manhattan, NY 10036, United States"
        }
    }

```

> Example Component Session Message (CONTACT)

```json
"whatsapp": {
        "contentType": "contacts",
        "contacts": [
            {
                "name": {
                    "formattedName": "XYZ ABC",
                    "firstName" : "XYZ"
                },
                "phones": [
                    {
                        "phone": "919999999999",
                        "type": "WORK"
                    }
                ]
            }
        ]
    }

```

> Example Component Session Message (Interactive List)

```json
"whatsapp": {
    "contentType": "interactive",
    "interactive": {
        "subType": "list",
        "components": {
            "header": {
                "type": "text",
                "text": "Choose your menu"
            },
            "body": {
                "type": "text",
                "text": "Hi Sarah, select your menu from the bottom list. Dressings and toppings are selected later on"
            },
            "footer": {
                "type": "text",
                "text": "Your tellephant food team"
            },
            "list": {
                "title": "Your menu",
                "sections": [
                    {
                        "title": "Vegan",
                        "rows": [
                            {
                                "payload": "green-dream-34987-234897234-234",
                                "title": "Green dream",
                                "description": "A bowl full of tasty leaves, soy beans and cucumber"
                            },
                            {
                                "payload": "rainbow-meets-rice-34987-234897234-234",
                                "title": "Rainbow meets rice",
                                "description": "A colorful selection of vegetables on a cozy bed of basmati rice"
                            }
                        ]
                    },
                    {
                        "title": "Vegetarian",
                        "rows": [
                            {
                                "payload": "italo-classic-34987-234897234-234",
                                "title": "Italo Classic",
                                "description": "Slices of tomates, with plucked pieces of mozzarella and basil leaves"
                            },
                            {
                                "payload": "egg-and-peas-34987-234897234-234",
                                "title": "Egg & Peas",
                                "description": "Tasty slices of eggs, on a whole wheat pasta salad with peas"
                            }
                        ]
                    }
                ]
            }
        }
    }
}

```

> Example Component Session Message (Interactive Reply Buttons) - Text Header

```json
"whatsapp": {
    "contentType": "interactive",
    "interactive": {
        "subType": "buttons",
        "components": {
            "header": {
                "type": "text",
                "text": "Your request is queued"
            },
            "body": {
                "type": "text",
                "text": "How would you rate your bot experience"
            },
            "footer": {
                "type": "text",
                "text": "Your service bot"
            },
            "buttons": [
                {
                    "type": "reply",
                    "reply": {
                        "payload": "987298-40980jvkdm9-234234234",
                        "title": "Poor"
                    }
                },
                {
                    "type": "reply",
                    "reply": {
                        "payload": "987298-dsfgjlkhgdf-dg09u834334",
                        "title": "OK"
                    }
                },
                {
                    "type": "reply",
                    "reply": {
                        "payload": "9080923445nlkjß0_gß0923845083245dfg",
                        "title": "Good"
                    }
                }
            ]
        }
    }
}

```

> Example Component Session Message (Interactive Reply Buttons) - Image Header

```json
"whatsapp": {
    "contentType": "interactive",
    "interactive": {
        "subType": "buttons",
        "components": {
            "header": {
                "type": "image",
                "image": {
                    "url": "https://tellephant.s3.ap-south-1.amazonaws.com/dummy-media/sample.jpeg"
                }
            },
            "body": {
                "type": "text",
                "text": "How would you rate your bot experience"
            },
            "footer": {
                "type": "text",
                "text": "Your service bot"
            },
            "buttons": [
                {
                    "type": "reply",
                    "reply": {
                        "payload": "987298-40980jvkdm9-234234234",
                        "title": "Poor"
                    }
                },
                {
                    "type": "reply",
                    "reply": {
                        "payload": "987298-dsfgjlkhgdf-dg09u834334",
                        "title": "OK"
                    }
                },
                {
                    "type": "reply",
                    "reply": {
                        "payload": "9080923445nlkjß0_gß0923845083245dfg",
                        "title": "Good"
                    }
                }
            ]
        }
    }
}

```

> Example Component Session Message (Interactive Reply Buttons) - Document Header

```json
"whatsapp": {
    "contentType": "interactive",
    "interactive": {
        "subType": "buttons",
        "components": {
            "header": {
                "type": "document",
                "document": {
                    "url": "https://tellephant.s3.ap-south-1.amazonaws.com/dummy-media/sample.pdf",
                    "filename" : "Sample"
                }
            },
            "body": {
                "type": "text",
                "text": "How would you rate your bot experience"
            },
            "footer": {
                "type": "text",
                "text": "Your service bot"
            },
            "buttons": [
                {
                    "type": "reply",
                    "reply": {
                        "payload": "987298-40980jvkdm9-234234234",
                        "title": "Poor"
                    }
                },
                {
                    "type": "reply",
                    "reply": {
                        "payload": "987298-dsfgjlkhgdf-dg09u834334",
                        "title": "OK"
                    }
                },
                {
                    "type": "reply",
                    "reply": {
                        "payload": "9080923445nlkjß0_gß0923845083245dfg",
                        "title": "Good"
                    }
                }
            ]
        }
    }
}

```

> Example Component Session Message (Interactive Reply Buttons) - Video Header

```json
"whatsapp": {
    "contentType": "interactive",
    "interactive": {
        "subType": "buttons",
        "components": {
            "header": {
                "type": "video",
                "video": {
                    "url": "https://tellephant.s3.ap-south-1.amazonaws.com/dummy-media/sample.mp4"
                }
            },
            "body": {
                "type": "text",
                "text": "How would you rate your bot experience"
            },
            "footer": {
                "type": "text",
                "text": "Your service bot"
            },
            "buttons": [
                {
                    "type": "reply",
                    "reply": {
                        "payload": "987298-40980jvkdm9-234234234",
                        "title": "Poor"
                    }
                },
                {
                    "type": "reply",
                    "reply": {
                        "payload": "987298-dsfgjlkhgdf-dg09u834334",
                        "title": "OK"
                    }
                },
                {
                    "type": "reply",
                    "reply": {
                        "payload": "9080923445nlkjß0_gß0923845083245dfg",
                        "title": "Good"
                    }
                }
            ]
        }
    }
}

```

### Send session messages via this path.

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
        <td>Number to send the otp</td>
    </tr>
    <tr>
        <td><code>channels</code></td>
        <td>array</td>
        <td>required</td>
        <td>Channel(s) to be used.</td>
    </tr>
    <tr>
        <td><code>whatsapp</code></td>
        <td>array</td>
        <td>required</td>
        <td>Session message type and other details.</td>
    </tr>

    </tbody>

</table>

### Session Message (Text)

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
        <td><code>contentType</code></td>
        <td>string</td>
        <td>required</td>
        <td>Text header for Whatsapp Session message</td>
    </tr>
    <tr>
        <td><code>text</code></td>
        <td>String</td>
        <td>required</td>
        <td>The text to be sent</td>
    </tr>
    </tbody>
</table>
<span class="ml-5">
    <img src="/images/apidoc_ss/waba_session/text.jpg" style="width: 50%;" alt="text">
</span>

### Session Message (IMAGE)

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
        <td><code>contentType</code></td>
        <td>string</td>
        <td>required</td>
        <td>Media header for Whatsapp Session message</td>
    </tr>
    <tr>
        <td><code>type</code></td>
        <td>String</td>
        <td>required</td>
        <td>Type of media used</td>
    </tr>
    <tr>
        <td><code>url</code></td>
        <td>String</td>
        <td>required</td>
        <td>Location where the image is stored</td>
    </tr>
    <tr>
        <td><code>caption</code></td>
        <td>String</td>
        <td>required</td>
        <td>Text description alongwith</td>
    </tr>
    </tbody>
</table>
<img src="/images/apidoc_ss/waba_session/image.jpg" style="width: 50%;" alt="text">

### Session Message (DOCUMENT)

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
        <td><code>contentType</code></td>
        <td>string</td>
        <td>required</td>
        <td>Media header for Whatsapp Session message</td>
    </tr>
    <tr>
        <td><code>type</code></td>
        <td>String</td>
        <td>required</td>
        <td>Type of media used</td>
    </tr>
    <tr>
        <td><code>url</code></td>
        <td>String</td>
        <td>required</td>
        <td>Location where the document is stored</td>
    </tr>
    <tr>
        <td><code>filename</code></td>
        <td>String</td>
        <td>Required</td>
        <td>Title for the document</td>
    </tr>
    </tbody>
</table>
<img src="/images/apidoc_ss/waba_session/document.jpg" style="width: 50%;" alt="text">

### Session Message (STICKER)

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
        <td><code>contentType</code></td>
        <td>string</td>
        <td>required</td>
        <td>Media header for Whatsapp Session message</td>
    </tr>
    <tr>
        <td><code>type</code></td>
        <td>String</td>
        <td>required</td>
        <td>Type of media used</td>
    </tr>
    <tr>
        <td><code>url</code></td>
        <td>String</td>
        <td>required</td>
        <td>Location where the sticker is stored</td>
    </tr>
    </tbody>
</table>
<img src="/images/apidoc_ss/waba_session/sticker.jpg" style="width: 50%;" alt="text">

### Session Message (VIDEO)

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
        <td><code>contentType</code></td>
        <td>string</td>
        <td>required</td>
        <td>Media header for Whatsapp Session message</td>
    </tr>
    <tr>
        <td><code>type</code></td>
        <td>String</td>
        <td>required</td>
        <td>Type of media used</td>
    </tr>
    <tr>
        <td><code>url</code></td>
        <td>String</td>
        <td>required</td>
        <td>Location where the video is stored</td>
    </tr>
    <tr>
        <td><code>caption</code></td>
        <td>String</td>
        <td>optional</td>
        <td>Text description alongwith</td>
    </tr>
    </tbody>
</table>
<img src="/images/apidoc_ss/waba_session/video.jpg" style="width: 50%;" alt="text">

### Session Message (AUDIO)

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
        <td><code>contentType</code></td>
        <td>string</td>
        <td>required</td>
        <td>Media header for Whatsapp Session message</td>
    </tr>
    <tr>
        <td><code>type</code></td>
        <td>String</td>
        <td>required</td>
        <td>Type of media used</td>
    </tr>
    <tr>
        <td><code>url</code></td>
        <td>String</td>
        <td>required</td>
        <td>Location where the audio file is stored</td>
    </tr>
    <tr>
        <td><code>caption</code></td>
        <td>String</td>
        <td>optional</td>
        <td>Text description alongwith</td>
    </tr>
    </tbody>
</table>
<img src="/images/apidoc_ss/waba_session/audio.jpg" style="width: 50%;" alt="text">

### Session Message (LOCATION)

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
        <td><code>contentType</code></td>
        <td>string</td>
        <td>required</td>
        <td>Location header for Whatsapp Session message</td>
    </tr>
    <tr>
        <td><code>longitude</code></td>
        <td>number(double)</td>
        <td>required</td>
        <td>Logitude component of location</td>
    </tr>
    <tr>
        <td><code>latitude</code></td>
        <td>number(double)</td>
        <td>required</td>
        <td>Latitude component of location</td>
    </tr>
    <tr>
        <td><code>name</code></td>
        <td>String</td>
        <td>required</td>
        <td>Name of the location</td>
    </tr>
    <tr>
        <td><code>address</code></td>
        <td>String</td>
        <td>required</td>
        <td>Address of the location</td>
    </tr>
    </tbody>
</table>
<img src="/images/apidoc_ss/waba_session/location.jpg" style="width: 50%;" alt="text">

### Session Message (CONTACT)

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
        <td><code>contentType</code></td>
        <td>string</td>
        <td>required</td>
        <td>Contact header for Whatsapp Session message</td>
    </tr>
    <tr>
        <td><code>formattedName</code></td>
        <td>String</td>
        <td>required</td>
        <td>Full name of the entity</td>
    </tr>
    <tr>
        <td><code>firstName</code></td>
        <td>String</td>
        <td>required</td>
        <td>First name of the entity</td>
    </tr>
    <tr>
        <td><code>phone</code></td>
        <td>String</td>
        <td>required</td>
        <td>Contact phone number details</td>
    </tr>
    <tr>
        <td><code>type</code></td>
        <td>String</td>
        <td>required</td>
        <td>Type of contact</td>
    </tr>
    </tbody>
</table>
<img src="/images/apidoc_ss/waba_session/contact.jpg" style="width: 50%;" alt="text">

### Session Message (Interactive List)

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
        <td><code>interactive.subType</code></td>
        <td>string</td>
        <td>required</td>
        <td>Interactive list header for Whatsapp Session message</td>
    </tr>
    <tr>
        <td><code>components.header</code></td>
        <td>object</td>
        <td>optional</td>
        <td>Message header</td>
    </tr>
    <tr>
        <td><code>header.text</code></td>
        <td>string</td>
        <td>required</td>
        <td>Header text content</td>
    </tr>
    <tr>
        <td><code>components.body</code></td>
        <td>object</td>
        <td>required</td>
        <td>Message body text</td>
    </tr>
    <tr>
        <td><code>body.text</code></td>
        <td>string</td>
        <td>required</td>
        <td>Message body content</td>
    </tr>
    <tr>
        <td><code>components.footer</code></td>
        <td>object</td>
        <td>optional</td>
        <td>Message footer</td>
    </tr>
    <tr>
        <td><code>footer.text</code></td>
        <td>string</td>
        <td>required</td>
        <td>Message footer content</td>
    </tr>
    <tr>
        <td><code>list.title</code></td>
        <td>string</td>
        <td>optional</td>
        <td>Title of the list (Max length: 24 characters)</td>
    </tr>
    <tr>
        <td><code>list.section</code></td>
        <td>array</td>
        <td>required</td>
        <td>Array of section objects (minimum of 1 and maximum of 10)</td>
    </tr>
    <tr>
        <td><code>section.title</code></td>
        <td>string</td>
        <td>required (if multiple sections)</td>
        <td>Title of the section (Max length: 24 characters)</td>
    </tr>
    <tr>
        <td><code>section.rows</code></td>
        <td>array</td>
        <td>required</td>
        <td>Contains a list of rows.</td>
    </tr>
    <tr>
        <td><code>rows.title</code></td>
        <td>string</td>
        <td>required</td>
        <td>row title (Max length: 24 characters)</td>
    </tr>
    <tr>
        <td><code>rows.payload</code></td>
        <td>string</td>
        <td>required</td>
        <td>payload (Max length: 200 characters)</td>
    </tr>
    <tr>
        <td><code>rows.description</code></td>
        <td>string</td>
        <td>optional</td>
        <td>description (Max length: 72 characters)</td>
    </tr>
    </tbody>
</table>
<br>

<aside class="success">
Note:
Maximum 10 number of <b>rows</b> allowed. Rows can be wrapped up in sections. A <b>section</b> shall have at least one row.<br>
<b>Payload</b> must be unique for every row.
</aside>

<img src="/images/apidoc_ss/waba_session/list1.jpg" style="width: 20%; margin-left: 3re5; v" alt="text">
<img src="/images/apidoc_ss/waba_session/list2.jpg" style="width: 50%;" alt="text">

### Session Message (Interactive Reply Buttons) - Text Header

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
        <td><code>interactive.subType</code></td>
        <td>string</td>
        <td>required</td>
        <td>Interactive buttons header for Whatsapp Session message</td>
    </tr>
    <tr>
        <td><code>components.header</code></td>
        <td>object</td>
        <td>optional</td>
        <td>Message header</td>
    </tr>
    <tr>
        <td><code>header.type</code></td>
        <td>string</td>
        <td>required</td>
        <td>Type of header</td>
    </tr>
    <tr>
        <td><code>header.text</code></td>
        <td>string</td>
        <td>required</td>
        <td>Header text content</td>
    </tr>
    <tr>
        <td><code>components.body</code></td>
        <td>object</td>
        <td>required</td>
        <td>Message body</td>
    </tr>
    <tr>
        <td><code>body.text</code></td>
        <td>string</td>
        <td>required</td>
        <td>Message body content</td>
    </tr>
    <tr>
        <td><code>components.footer</code></td>
        <td>object</td>
        <td>optional</td>
        <td>Message footer</td>
    </tr>
    <tr>
        <td><code>footer.text</code></td>
        <td>string</td>
        <td>required</td>
        <td>Message footer content</td>
    </tr>
    <tr>
        <td><code>buttons.type</code></td>
        <td>string</td>
        <td>required</td>
        <td>Type of buttons</td>
    </tr>
    <tr>
        <td><code>reply.title</code></td>
        <td>string</td>
        <td>required </td>
        <td>Button title (Max length: 20 characters)</td>
    </tr>
    <tr>
        <td><code>reply.payload</code></td>
        <td>string</td>
        <td>required</td>
        <td>Payload (Max length: 256 characters)</td>
    </tr>
    </tbody>
</table>
<br>

<aside>
<b>Note:</b>
Maximum 3 and minimum 1 <b>button</b> shall be included in this request.
</aside>

<img src="/images/apidoc_ss/waba_session/btn_text.jpg" style="width: 50%;" alt="text">

### Session Message (Interactive Reply Buttons) - Image Header

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
        <td><code>interactive.subType</code></td>
        <td>string</td>
        <td>required</td>
        <td>Interactive buttons header for Whatsapp Session message</td>
    </tr>
    <tr>
        <td><code>components.header</code></td>
        <td>object</td>
        <td>optional</td>
        <td>Message header</td>
    </tr>
    <tr>
        <td><code>header.type</code></td>
        <td>string</td>
        <td>required</td>
        <td>Type of header</td>
    </tr>
    <tr>
        <td><code>header.image.url</code></td>
        <td>string</td>
        <td>required</td>
        <td>The url of the location where the image is stored</td>
    </tr>
    <tr>
        <td><code>components.body</code></td>
        <td>object</td>
        <td>required</td>
        <td>Message body</td>
    </tr>
    <tr>
        <td><code>body.text</code></td>
        <td>string</td>
        <td>required</td>
        <td>Message body content</td>
    </tr>
    <tr>
        <td><code>components.footer</code></td>
        <td>object</td>
        <td>optional</td>
        <td>Message footer</td>
    </tr>
    <tr>
        <td><code>footer.text</code></td>
        <td>string</td>
        <td>required</td>
        <td>Message footer content</td>
    </tr>
    <tr>
        <td><code>buttons.type</code></td>
        <td>string</td>
        <td>required</td>
        <td>Type of buttons</td>
    </tr>
    <tr>
        <td><code>reply.title</code></td>
        <td>string</td>
        <td>required </td>
        <td>Button title (Max length: 20 characters)</td>
    </tr>
    <tr>
        <td><code>reply.payload</code></td>
        <td>string</td>
        <td>required</td>
        <td>Payload (Max length: 256 characters)</td>
    </tr>
    </tbody>
</table>
<br>

<aside class="success">
<b>Note:</b>
Maximum 3 and minimum 1 <b>button</b> shall be included in this request.
</aside>

<img src="/images/apidoc_ss/waba_session/btn_image.jpg" style="width: 50%;" alt="text">

### Session Message (Interactive Reply Buttons) - Document Header

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
        <td><code>interactive.subType</code></td>
        <td>string</td>
        <td>required</td>
        <td>Interactive buttons header for Whatsapp Session message</td>
    </tr>
    <tr>
        <td><code>components.header</code></td>
        <td>object</td>
        <td>optional</td>
        <td>Message header</td>
    </tr>
    <tr>
        <td><code>header.type</code></td>
        <td>string</td>
        <td>required</td>
        <td>Type of header</td>
    </tr>
    <tr>
        <td><code>header.document.url</code></td>
        <td>string</td>
        <td>required</td>
        <td>The url of the location where the pdf is stored</td>
    </tr>
    <tr>
        <td><code>header.document.filename</code></td>
        <td>string</td>
        <td>required</td>
        <td>PDF file name</td>
    </tr>
    <tr>
        <td><code>components.body</code></td>
        <td>object</td>
        <td>required</td>
        <td>Message body</td>
    </tr>
    <tr>
        <td><code>body.text</code></td>
        <td>string</td>
        <td>required</td>
        <td>Message body content</td>
    </tr>
    <tr>
        <td><code>components.footer</code></td>
        <td>object</td>
        <td>optional</td>
        <td>Message footer</td>
    </tr>
    <tr>
        <td><code>footer.text</code></td>
        <td>string</td>
        <td>required</td>
        <td>Message footer content</td>
    </tr>
    <tr>
        <td><code>buttons.type</code></td>
        <td>string</td>
        <td>required</td>
        <td>Type of buttons</td>
    </tr>
    <tr>
        <td><code>reply.title</code></td>
        <td>string</td>
        <td>required </td>
        <td>Button title (Max length: 20 characters)</td>
    </tr>
    <tr>
        <td><code>reply.payload</code></td>
        <td>string</td>
        <td>required</td>
        <td>Payload (Max length: 256 characters)</td>
    </tr>
    </tbody>
</table>
<br>

<aside class="success">
<b>Note:</b>
Maximum 3 and minimum 1 <b>button</b> shall be included in this request.
</aside>

<img src="/images/apidoc_ss/waba_session/btn_document.jpg" style="width: 50%;" alt="text">

### Session Message (Interactive Reply Buttons) - Video Header

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
        <td><code>interactive.subType</code></td>
        <td>string</td>
        <td>required</td>
        <td>Interactive buttons header for Whatsapp Session message</td>
    </tr>
    <tr>
        <td><code>components.header</code></td>
        <td>object</td>
        <td>optional</td>
        <td>Message header</td>
    </tr>
    <tr>
        <td><code>header.type</code></td>
        <td>string</td>
        <td>required</td>
        <td>Type of header</td>
    </tr>
    <tr>
        <td><code>header.video.url</code></td>
        <td>string</td>
        <td>required</td>
        <td>The url of the location where the video is stored</td>
    </tr>
    <tr>
        <td><code>components.body</code></td>
        <td>object</td>
        <td>required</td>
        <td>Message body</td>
    </tr>
    <tr>
        <td><code>body.text</code></td>
        <td>string</td>
        <td>required</td>
        <td>Message body content</td>
    </tr>
    <tr>
        <td><code>components.footer</code></td>
        <td>object</td>
        <td>optional</td>
        <td>Message footer</td>
    </tr>
    <tr>
        <td><code>footer.text</code></td>
        <td>string</td>
        <td>required</td>
        <td>Message footer content</td>
    </tr>
    <tr>
        <td><code>buttons.type</code></td>
        <td>string</td>
        <td>required</td>
        <td>Type of buttons</td>
    </tr>
    <tr>
        <td><code>reply.title</code></td>
        <td>string</td>
        <td>required </td>
        <td>Button title (Max length: 20 characters)</td>
    </tr>
    <tr>
        <td><code>reply.payload</code></td>
        <td>string</td>
        <td>required</td>
        <td>Payload (Max length: 256 characters)</td>
    </tr>
    </tbody>
</table>
<br>

<aside class="success">
<b>Note:</b>
Maximum 3 and minimum 1 <b>button</b> shall be included in this request.
</aside>

<img src="/images/apidoc_ss/waba_session/btn_video.jpg" style="width: 50%;" alt="text">
