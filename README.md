# Verlichting demo UI

Simpele web-app om de drie lampen (host / sub1 / sub2) van de PoC aan te sturen
via dezelfde publieke MQTT-broker als de firmware. Stuurt platte-tekst commando's;
aan de board-/verlichtingskant verandert niets.

## Gebruik
1. Open `index.html` in een browser (desktop of telefoon). Dubbelklikken volstaat.
2. De app verbindt automatisch met `broker.hivemq.com` over WebSockets.
3. Sliders versturen **pas bij loslaten** een commando (live waarde tijdens slepen).

## Bediening
- **Host / Sub 1 / Sub 2** sliders → `host=<v>` / `sub1=<v>` / `sub2=<v>`
- **Alle lampen** slider → `all=<v>` (zet ook de drie sliders mee)
- **Sync** → `sync` (subs gelijk aan host)
- **Status** → `status` (antwoord verschijnt onderin bij "Berichten")

## Configuratie (matcht de firmware)
| | Waarde |
|---|---|
| Broker (WebSocket) | `ws://broker.hivemq.com:8000/mqtt` |
| Commando-topic (publish) | `devacademy/naar_nrf54_cmd/topic` |
| Status-topic (subscribe) | `devacademy/vanafnrf54_pub/topic` |

Staat bovenin het `<script>`-blok in `index.html`.

## Hosten op een https-pagina (bijv. GitHub Pages)
Vanaf `https://` mag een onbeveiligde `ws://` niet. Zet dan in `index.html`:
`const BROKER_URL = "wss://broker.hivemq.com:8884/mqtt";`
