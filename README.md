# Squareroute Getting Started

The below quickstart shows you how to make a curl request using bash.

* Log into ```https://admin.squareroute.io```
* Copy your credentials from the dashboard on ```https://admin.squareroute.io/ro/settings/accounts```
![](docs/squareroute-settings.png)
![](docs/squareroute-client-id-secret.png)

* Paste in your respective values 
```bash
clientID = # e.g. tE9vGHSyP8kyu4SodfDczrOo1n7D5dnf
```
```bash
clientSecret = # e.g. 3MmE9r947MpQmfnwI357cmihotYgsZeeA0leVraWP4Y7amvIlYpkKVWRolZkVz55lRcBcGVPNZ36SdqfeXeEwdlhj2PWgQnzIHeHii2wTsAd2lbB53txNZBoPKZ5545i
```

* Create the json task object as a variable on the command line:
```bash
task=$(cat <<EOF
{
   "calculation_type": "COST_MATRIX",
   "locations": [
       {
           "id": "73-dame-street",
           "name": "The Olympia, 72 Dame Street",
           "lat": 53.344193,
           "lng": -6.266069
       },
       {
           "id": "24-wexford-street",
           "name": "Whelans, 24 Wexford Street Dame Street",
           "lat": 53.336586,
           "lng": -6.265628
       },
       {
           "id": "82-parnell-street",
           "name": "Fibbers, 82 Parnell Street",
           "lat": 53.352970,
           "lng": -6.260457
       },
       {
           "id": "15-ormond-quay-upper",
           "name": "Sin é, 15 Ormond Quay Upper",
           "lat": 53.345898, 
           "lng": -6.269489
       },
       {
           "id": "8-leeson-st-lower",
           "name": "Sugar Club, 8 Leeson Street Lower",
           "lat": 53.335571, 
           "lng": -6.256543
       }
   ]
}
EOF
)
```

* Submit the request
```bash
curl -X POST \
  https://api.squareroute.io/api/v1/ro/calculate \
  -H 'accept: application/json' \
  -H 'content-type: application/json' \
  -H "client-id: $clientID" \
  -H "client-secret: $clientSecret" \
  -d "{
    "data": {
        "callback_url": "https://api.example.com/api/squareroute/ro-event/callback",
        "include_ro_result_in_callback": false,
        "task": $task
  }
}"
```

