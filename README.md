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
curl -X POST \
  https://api.squareroute.io/api/v1/ro/calculate \
  -H "accept: application/json" \
  -H "content-type: application/json" \
  -H "client-id: $clientID" \
  -H "client-secret: $clientSecret" \
  -d @data.json
```