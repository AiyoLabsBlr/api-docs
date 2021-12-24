# User List APIs

> Example API request (Create new user list)

```bash
curl --location --request POST 'https://api.tellephant.com/v1/lists' \
--header 'Content-Type: application/json' \
--data-raw '{
    "apikey": "918273987123",
    "list_name": "test",
    "list_values": [
        {
            "name": "dhruv",
            "phone": "917082120985",
            "variables": {
                "var_1" : "201005"
            }
        }
    ],
    "list_columns": [
        "name",
        "phone",
        "var_1"
    ]
}
'
```

```javascript
var myHeaders = new Headers();
myHeaders.append("Content-Type", "application/json");

var raw = JSON.stringify({
  apikey: "918273987123",
  list_name: "test",
  list_values: [
    { name: "dhruv", phone: "917082120985", variables: { var_1: "201005" } },
  ],
  list_columns: ["name", "phone", "var_1"],
});

var requestOptions = {
  method: "POST",
  headers: myHeaders,
  body: raw,
  redirect: "follow",
};

fetch("https://api.tellephant.com/v1/lists", requestOptions)
  .then((response) => response.text())
  .then((result) => console.log(result))
  .catch((error) => console.log("error", error));
```

```php
<?php
$client = new http\Client;
$request = new http\Client\Request;
$request->setRequestUrl('https://api.tellephant.com/v1/lists');
$request->setRequestMethod('POST');
$body = new http\Message\Body;
$body->append('{
    "apikey": "918273987123",
    "list_name": "test",
    "list_values": [
        {
            "name": "dhruv",
            "phone": "917082120985",
            "variables": {
                "var_1" : "201005"
            }
        }
    ],
    "list_columns": [
        "name",
        "phone",
        "var_1"
    ]
}
');
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
payload = "{\n    \"apikey\": \"918273987123\",\n    \"list_name\": \"test\",\n    \"list_values\": [\n        {\n            \"name\": \"dhruv\",\n            \"phone\": \"917082120985\",\n            \"variables\": {\n                \"var_1\" : \"201005\"\n            }\n        }\n    ],\n    \"list_columns\": [\n        \"name\",\n        \"phone\",\n        \"var_1\"\n    ]\n}\n"
headers = {
  'Content-Type': 'application/json'
}
conn.request("POST", "/v1/lists", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```

### Create new user list

`POST v1/lists`

Body Parameters

| Parameter               | Type   | Status   | Description                                                                                  |
| ----------------------- | ------ | -------- | -------------------------------------------------------------------------------------------- |
| `apikey`                | String | required | API KEY Provided.                                                                            |
| `list_name`             | String | required | Name of List. Must be unique.                                                                |
| `list_values`           | Array  | required | List of users.                                                                               |
| `list_values.name`      | String | Optional | name of individual user in list.                                                             |
| `list_values.phone`     | String | required | phone number of individual user in list.                                                     |
| `list_values.variables` | Object | Optional | Variables of individual user in list. Each key in variables must follow var\_{number} format |
| `list_columns`          | Array  | required | List of keys used in list_values.                                                            |

> Example Response (Create new user list)

```json
{
  "code": 200,
  "data": {
    "list_name": "test 123",
    "list_values": [
      {
        "name": "dhruv",
        "phone": "917082120985",
        "variables": {
          "var_1": "201005"
        }
      }
    ],
    "list_columns": ["name", "phone", "var_1"],
    "user_id": "619f2e655259ba4d30248ee2",
    "updated_at": "2021-12-22 13:10:46",
    "created_at": "2021-12-22 13:10:46",
    "_id": "61c2d67e3a00374e3d5b5794"
  }
}
```

### Update user list

`PUT v1/lists`

Body Parameters

| Parameter               | Type   | Status   | Description                                                                                  |
| ----------------------- | ------ | -------- | -------------------------------------------------------------------------------------------- |
| `apikey`                | String | required | API KEY Provided.                                                                            |
| `list_id`               | String | required | Id of List you want to update.                                                               |
| `list_name`             | String | required | Name of List. Must be unique.                                                                |
| `list_values`           | Array  | required | List of users.                                                                               |
| `list_values.name`      | String | Optional | name of individual user in list.                                                             |
| `list_values.phone`     | String | required | phone number of individual user in list.                                                     |
| `list_values.variables` | Object | Optional | Variables of individual user in list. Each key in variables must follow var\_{number} format |

List columns cannot be updated. Only the values of list can be updated and list_values should match original list_columns.

> Example Response (Update user list)

```json
{
  "code": 200,
  "data": {
    "_id": "61bc46d2c63c212a5f760f12",
    "list_name": "testing...",
    "list_values": [
      {
        "name": "dhruv",
        "phone": "917082120985",
        "variables": {
          "var_1": "Mumbai"
        }
      }
    ],
    "list_columns": ["phone", "name", "var_1"],
    "user_id": "619f2e655259ba4d30248ee2",
    "updated_at": "2021-12-22 13:17:36",
    "created_at": "2021-12-17 13:44:10"
  }
}
```

### Get All User Lists

`GET v1/lists`

Body Parameters

| Parameter | Type   | Status   | Description      |
| --------- | ------ | -------- | ---------------- |
| `apikey`  | String | required | API KEY Provided |

> Example Response (All user lists)

```json
{
  "code": 200,
  "data": [
    {
      "_id": "61c2d67e3a00374e3d5b5794",
      "list_name": "test 123",
      "list_columns": ["name", "phone", "var_1", "var_2"],
      "user_id": "619f2e655259ba4d30248ee2",
      "updated_at": "2021-12-22 13:10:46",
      "created_at": "2021-12-22 13:10:46"
    },
    {
      "_id": "61c0238afa400169e85587b6",
      "list_name": "test",
      "list_columns": ["name", "phone"],
      "user_id": "619f2e655259ba4d30248ee2",
      "updated_at": "2021-12-20 12:02:42",
      "created_at": "2021-12-20 12:02:42"
    }
  ]
}
```

### Get User List Details

`GET v1/lists`

Body Parameters

| Parameter | Type   | Status   | Description                    |
| --------- | ------ | -------- | ------------------------------ |
| `apikey`  | String | required | API KEY Provided               |
| `list_id` | String | required | ID of list you want details of |

> Example Response (User List Detail)

```json
{
  "code": 200,
  "data": {
    "_id": "61c2d67e3a00374e3d5b5794",
    "list_name": "test 123",
    "list_values": [
      {
        "name": "dhruv",
        "phone": "917082120985",
        "variables": {
          "var_1": "201005"
        }
      }
    ],
    "list_columns": ["name", "phone", "var_1"],
    "user_id": "619f2e655259ba4d30248ee2",
    "updated_at": "2021-12-22 13:10:46",
    "created_at": "2021-12-22 13:10:46"
  }
}
```

### Delete User List

`DELETE v1/lists`

Body Parameters

| Parameter | Type   | Status   | Description                   |
| --------- | ------ | -------- | ----------------------------- |
| `apikey`  | String | required | API KEY Provided              |
| `list_id` | String | required | ID of list you want to delete |

> Example Response (Delete user list)

```json
{
  "code": 200,
  "message": "Successfully removed list with id 61c2d67e3a00374e3d5b5794",
  "data": 1
}
```

### Delete single user from list

`DELETE v1/lists`

Body Parameters

| Parameter | Type   | Status   | Description                              |
| --------- | ------ | -------- | ---------------------------------------- |
| `apikey`  | String | required | API KEY Provided                         |
| `list_id` | String | required | ID of list you want to delete from       |
| `phone`   | String | required | mobile number of user you want to remove |

> Example Response (Delete single user from list)

```json
{
  "code": 200,
  "message": "Successfully removed number 917092312685"
}
```
