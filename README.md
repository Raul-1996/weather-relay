# weather-relay

Relays the Open-Meteo forecast via GitHub for irrigation controllers whose ISP
blocks the Open-Meteo datacenter IP (RF/RKN).

A cron on an ops host that *can* reach Open-Meteo fetches the forecast and pushes
the raw JSON here. Controllers pull the static JSON from `raw.githubusercontent.com`
(which stays reachable where `api.open-meteo.com` does not).

- `gub.json` — forecast for poliv-gub (Аэродром Губерля, 51.2664/58.5328).
  Raw: `https://raw.githubusercontent.com/Raul-1996/weather-relay/main/gub.json`

JSON is the verbatim Open-Meteo `/v1/forecast` response (same params the app uses),
so the controller's parser consumes it unchanged. Producer:
`shared/scripts/weather-relay-fetch.sh` on rauls-ubuntu-cl (cron */30).
