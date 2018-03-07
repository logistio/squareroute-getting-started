# Squareroute Getting Started

The below quickstart shows you how to make a curl request using bash.

* Clone this repository
```bash
git clone https://github.com/logistio/squareroute-getting-started.git
```
```bash
cd squareroute-getting-started
```

* Log into ```https://admin.squareroute.io```
* Copy your credentials from the dashboard on ```https://admin.squareroute.io/ro/settings/accounts```
![](docs/squareroute-settings.png)
![](docs/squareroute-client-id-secret.png)

* Paste in your respective values 
```bash
clientID= # e.g. tE9vGHSyP8kyu4SodfDczrOo1n7D5dnf
```
```bash
clientSecret= # e.g. 3MmE9r947MpQmfnwI357cmihotYgsZeeA0leVraWP4Y7amvIlYpkKVWRolZkVz55lRcBcGVPNZ36SdqfeXeEwdlhj2PWgQnzIHeHii2wTsAd2lbB53txNZBoPKZ5545i
```

* Submit the request
```bash
response=$(curl -X POST \
  https://api.squareroute.io/api/v1/ro/calculate \
  -H "accept: application/json" \
  -H "content-type: application/json" \
  -H "client-id: $clientID" \
  -H "client-secret: $clientSecret" \
  -d @data.json)
```

```bash
taskID=$(jq -r '.data.task_id' <<< "$response")
```

* Periodically poll for the status of the job
```bash
curl -X GET \
  https://api.squareroute.io/api/v1/ro/task/$taskID/status \
  -H 'accept: application/json' \
  -H "client-id: $clientID" \
  -H "client-secret: $clientSecret"
```

When the job status changes to ```FINISHED``` like below, proceed to retrieve the result. For small jobs this will be a couple of seconds.

```json
{
    "data": {
        "task_id": "ABCD1234",
        "status": "FINISHED",
        "updated_at": "2018-02-28 10:31:55"
    }
}
```
* Retrieve the result and save it to result.json
```bash
curl -X GET \
  https://api.squareroute.io/api/v1/ro/task/$taskID/result \
  -H 'accept: application/json' \
  -H "client-id: $clientID" \
  -H "client-secret: $clientSecret" \
  -o result.json
```

* View the file at result.json similar to the below.

```bash

```