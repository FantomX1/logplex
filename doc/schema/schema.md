## <a name="resource-channel"></a>Channel

A channel is a log stream.

### Attributes

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **drains** | *array* | drains under the channel | `[{"id"=>123456, "token"=>"d.01234567-89ab-cdef-0123-456789abcdef", "url"=>"https://example.org"}]` |
| **channel** | *string* | unique identifier of a channel | `"123456"` |
| **channel_id** | *integer* | unique identifier of a channel (deprecated) | `123456` |
| **tokens** | *array* | tokens under the channel | `[{"token"=>"t.01234567-89ab-cdef-0123-456789abcdef", "name"=>"my-token"}]` |

### Channel Create (Deprecated)

Create a new channel.

```
POST /channels
```

#### Required Parameters

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **name** | *string* | a name for the channel | `"my-channel"` |


#### Optional Parameters

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **tokens** | *array* | names of tokens to create | `["my-token","your-token"]` |


#### Curl Example

```bash
$ curl -n -X POST https://logplex.heroku.com/channels \
  -H "Content-Type: application/json" \
 \
  -d '{
  "name": "my-channel",
  "tokens": [
    "my-token",
    "your-token"
  ]
}'
```


#### Response Example

```
HTTP/1.1 201 Created
```

```json
{
  "channel_id": 123456,
  "tokens": {
    "my-token": "t.01234567-89ab-cdef-0123-456789abcdef",
    "your-token": "t.5b432a82-2c03-4ecd-a8d4-a75d627b29ab"
  }
}
```

### Channel Delete (Deprecated)

Delete an existing channel.

```
DELETE /v2/channels/{channel_channel_id}
```


#### Curl Example

```bash
$ curl -n -X DELETE https://logplex.heroku.com/v2/channels/$CHANNEL_CHANNEL_ID \
  -H "Content-Type: application/json" \
```


#### Response Example

```
HTTP/1.1 200 OK
```

```json

```

### Channel Info (Deprecated)

Info for existing channel.

```
GET /v2/channels/{channel_channel_id}
```


#### Curl Example

```bash
$ curl -n https://logplex.heroku.com/v2/channels/$CHANNEL_CHANNEL_ID
```


#### Response Example

```
HTTP/1.1 200 OK
```

```json
{
  "channel_id": 123456,
  "tokens": {
    "my-token": "t.01234567-89ab-cdef-0123-456789abcdef",
    "your-token": "t.5b432a82-2c03-4ecd-a8d4-a75d627b29ab"
  }
}
```

### Channel Create or Update

Create or update a channel.

```
PUT /v3/channels/{channel_channel}
```

#### Optional Parameters

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **tokens** | *array* | names of tokens to create | `["my-token","your-token"]` |


#### Curl Example

```bash
$ curl -n -X PUT https://logplex.heroku.com/v3/channels/$CHANNEL_CHANNEL \
  -H "Content-Type: application/json" \
 \
  -d '{
  "tokens": [
    "my-token",
    "your-token"
  ]
}'
```


#### Response Example

```
HTTP/1.1 200 OK
```

```json
{
  "channel": "123456",
  "tokens": {
    "my-token": "t.01234567-89ab-cdef-0123-456789abcdef",
    "your-token": "t.5b432a82-2c03-4ecd-a8d4-a75d627b29ab"
  }
}
```

### Channel Info

Info for existing channel.

```
GET /v3/channels/{channel_channel}
```


#### Curl Example

```bash
$ curl -n https://logplex.heroku.com/v3/channels/$CHANNEL_CHANNEL
```


#### Response Example

```
HTTP/1.1 200 OK
```

```json
{
  "channel": "123456",
  "tokens": {
    "my-token": "t.01234567-89ab-cdef-0123-456789abcdef",
    "your-token": "t.5b432a82-2c03-4ecd-a8d4-a75d627b29ab"
  }
}
```

### Channel Delete

Delete an existing channel.

```
DELETE /v3/channels/{channel_channel}
```


#### Curl Example

```bash
$ curl -n -X DELETE https://logplex.heroku.com/v3/channels/$CHANNEL_CHANNEL \
  -H "Content-Type: application/json" \
```


#### Response Example

```
HTTP/1.1 204 No Content
```

```json

```


## <a name="resource-drain"></a>Drain

Drains are log stream tee targets.

### Attributes

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **id** | *integer* | unique identifier of drain | `123456` |
| **token** | *string* | drain token | `"d.01234567-89ab-cdef-0123-456789abcdef"` |
| **url** | *string* | drain destination | `"https://example.org"` |

### Drain Create (Deprecated)

Create a new drain.

```
POST /v2/channels/{channel_channel_id}/drains
```

#### Required Parameters

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **url** | *string* | drain destination | `"https://example.org"` |



#### Curl Example

```bash
$ curl -n -X POST https://logplex.heroku.com/v2/channels/$CHANNEL_CHANNEL_ID/drains \
  -H "Content-Type: application/json" \
 \
  -d '{
  "url": "https://example.org"
}'
```


#### Response Example

```
HTTP/1.1 201 Created
```

```json
{
  "id": 123456,
  "token": "d.01234567-89ab-cdef-0123-456789abcdef",
  "url": "https://example.org"
}
```

### Drain Create

Create a new drain.

```
POST /v3/channels/{channel_channel}/drains
```

#### Required Parameters

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **url** | *string* | drain destination | `"https://example.org"` |



#### Curl Example

```bash
$ curl -n -X POST https://logplex.heroku.com/v3/channels/$CHANNEL_CHANNEL/drains \
  -H "Content-Type: application/json" \
 \
  -d '{
  "url": "https://example.org"
}'
```


#### Response Example

```
HTTP/1.1 201 Created
```

```json
{
  "id": 123456,
  "token": "d.01234567-89ab-cdef-0123-456789abcdef",
  "url": "https://example.org"
}
```

### Drain Delete (Deprecated)

Delete an existing drain.

```
DELETE /v2/channels/{channel_channel_id}/drains/{drain_id}
```


#### Curl Example

```bash
$ curl -n -X DELETE https://logplex.heroku.com/v2/channels/$CHANNEL_CHANNEL_ID/drains/$DRAIN_ID \
  -H "Content-Type: application/json" \
```


#### Response Example

```
HTTP/1.1 200 OK
```

```json

```

### Drain Delete

Delete an existing drain.

```
DELETE /v3/channels/{channel_channel}/drains/{drain_id}
```


#### Curl Example

```bash
$ curl -n -X DELETE https://logplex.heroku.com/v3/channels/$CHANNEL_CHANNEL/drains/$DRAIN_ID \
  -H "Content-Type: application/json" \
```


#### Response Example

```
HTTP/1.1 204 No Content
```

```json

```

### Drain Update (Deprecated)

Update an existing drain.

```
POST /v2/channels/{channel_channel_id}/drains/{drain_id}
```

#### Required Parameters

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **url** | *string* | drain destination | `"https://example.org"` |



#### Curl Example

```bash
$ curl -n -X POST https://logplex.heroku.com/v2/channels/$CHANNEL_CHANNEL_ID/drains/$DRAIN_ID \
  -H "Content-Type: application/json" \
 \
  -d '{
  "url": "https://example.org"
}'
```


#### Response Example

```
HTTP/1.1 200 OK
```

```json
{
  "id": 123456,
  "token": "d.01234567-89ab-cdef-0123-456789abcdef",
  "url": "https://example.org"
}
```

### Drain Update

Update an existing drain.

```
PUT /v3/channels/{channel_channel}/drains/{drain_id}
```

#### Required Parameters

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **url** | *string* | drain destination | `"https://example.org"` |



#### Curl Example

```bash
$ curl -n -X PUT https://logplex.heroku.com/v3/channels/$CHANNEL_CHANNEL/drains/$DRAIN_ID \
  -H "Content-Type: application/json" \
 \
  -d '{
  "url": "https://example.org"
}'
```


#### Response Example

```
HTTP/1.1 200 OK
```

```json
{
  "id": 123456,
  "token": "d.01234567-89ab-cdef-0123-456789abcdef",
  "url": "https://example.org"
}
```


## <a name="resource-health"></a>Healthchecks



### Healthchecks 

Performs a health check against the API.

```
GET /healthcheck
```


#### Curl Example

```bash
$ curl -n https://logplex.heroku.com/healthcheck
```


#### Response Example

```
HTTP/1.1 200 OK
```

```json
{
  "status": "normal"
}
```


## <a name="resource-session"></a>Session

Sessions fetch recent and real-time logs from channels.

### Attributes

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **url** | *string* | session URL to GET to retrieve logs | `"https://logplex.heroku.com/sessions/d58fb90e-c2bd-4e16-bfe0-e9e7cc7bff7f"` |

### Session Create (Deprecated)

Create a new session.

```
POST /v2/sessions
```

#### Required Parameters

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **channel_id** | *string* | unique identifier of channel (must be a string) | `"12345"` |


#### Optional Parameters

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **num** | *nullable string* | number of log lines to fetch<br/> **default:** `"100"` | `null` |
| **tail** | *nullable boolean* | if present with any value, start a live tail session | `null` |


#### Curl Example

```bash
$ curl -n -X POST https://logplex.heroku.com/v2/sessions \
  -H "Content-Type: application/json" \
 \
  -d '{
  "channel_id": "12345",
  "num": "5"
}'
```


#### Response Example

```
HTTP/1.1 201 Created
```

```json
{
  "url": "https://logplex.heroku.com/sessions/d58fb90e-c2bd-4e16-bfe0-e9e7cc7bff7f"
}
```

### Session Create

Create a new session.

```
POST /v3/sessions
```

#### Required Parameters

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **channel** | *string* | unique identifier of channel (must be a string) | `"12345"` |


#### Optional Parameters

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **num** | *nullable string* | number of log lines to fetch<br/> **default:** `"100"` | `null` |
| **tail** | *nullable boolean* | if present with any value, start a live tail session | `null` |


#### Curl Example

```bash
$ curl -n -X POST https://logplex.heroku.com/v3/sessions \
  -H "Content-Type: application/json" \
 \
  -d '{
  "channel_id": "12345",
  "num": "5"
}'
```


#### Response Example

```
HTTP/1.1 201 Created
```

```json
{
  "url": "https://logplex.heroku.com/sessions/d58fb90e-c2bd-4e16-bfe0-e9e7cc7bff7f"
}
```

### Session Logs

Get the chunk encoded session log data. If tail was specified the connection is long lived.

```
GET /sessions/{session_session_id}
```


#### Curl Example

```bash
$ curl -n https://logplex.heroku.com/sessions/$SESSION_SESSION_ID
```


#### Response Example

```
HTTP/1.1 200 OK
Transfer-Encoding: chunked

```

```json
2012-12-10T03:00:48Z+00:00 app[console.1]: test message 1
2012-12-10T03:00:49Z+00:00 app[console.1]: test message 2
2012-12-10T03:00:50Z+00:00 app[console.1]: test message 3
2012-12-10T03:00:51Z+00:00 app[console.1]: test message 4
2012-12-10T03:00:52Z+00:00 app[console.1]: test message 5

```


## <a name="resource-token"></a>Token

Tokens are log producers.

### Attributes

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **token** | *string* | unique identifier of token | `"t.01234567-89ab-cdef-0123-456789abcdef"` |
| **name** | *string* | name of token | `"my-token"` |

### Token Create (Deprecated)

Create a new token.

```
POST /v2/channels/{channel_channel_id}/tokens
```

#### Required Parameters

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **name** | *string* | name of token | `"my-token"` |



#### Curl Example

```bash
$ curl -n -X POST https://logplex.heroku.com/v2/channels/$CHANNEL_CHANNEL_ID/tokens \
  -H "Content-Type: application/json" \
 \
  -d '{
  "name": "my-token"
}'
```


#### Response Example

```
HTTP/1.1 201 Created
```

```json
{
  "token": "t.01234567-89ab-cdef-0123-456789abcdef",
  "name": "my-token"
}
```

### Token Create

Create a new token.

```
POST /v3/channels/{channel_channel}/tokens
```

#### Required Parameters

| Name | Type | Description | Example |
| ------- | ------- | ------- | ------- |
| **name** | *string* | name of token | `"my-token"` |



#### Curl Example

```bash
$ curl -n -X POST https://logplex.heroku.com/v3/channels/$CHANNEL_CHANNEL/tokens \
  -H "Content-Type: application/json" \
 \
  -d '{
  "name": "my-token"
}'
```


#### Response Example

```
HTTP/1.1 201 Created
```

```json
{
  "token": "t.01234567-89ab-cdef-0123-456789abcdef",
  "name": "my-token"
}
```


