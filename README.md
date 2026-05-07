# [📈 Live Status](https://status.neuroon.ai): <!--live status--> **🟢 All systems operational**

This repository contains the open-source uptime monitor and status page for [**Neuroon**](https://neuroon.ai), powered by [Upptime](https://upptime.js.org).

[![Uptime CI](https://github.com/Neuroon-ai/status/actions/workflows/uptime.yml/badge.svg)](https://github.com/Neuroon-ai/status/actions/workflows/uptime.yml)
[![Response Time CI](https://github.com/Neuroon-ai/status/actions/workflows/response-time.yml/badge.svg)](https://github.com/Neuroon-ai/status/actions/workflows/response-time.yml)
[![Graphs CI](https://github.com/Neuroon-ai/status/actions/workflows/graphs.yml/badge.svg)](https://github.com/Neuroon-ai/status/actions/workflows/graphs.yml)
[![Static Site CI](https://github.com/Neuroon-ai/status/actions/workflows/static-site.yml/badge.svg)](https://github.com/Neuroon-ai/status/actions/workflows/static-site.yml)
[![Summary CI](https://github.com/Neuroon-ai/status/actions/workflows/summary.yml/badge.svg)](https://github.com/Neuroon-ai/status/actions/workflows/summary.yml)

<!--start: status pages-->
<!--end: status pages-->

<sub>Last updated: <!--start: last-updated-->Initial setup<!--end: last-updated--></sub>

## How does this work?

We use a [GitHub Action](https://upptime.js.org/docs/run-on-actions) to ping our health endpoints every 5 minutes. Results are committed to this repo and rendered as a static site on GitHub Pages, served at [status.neuroon.ai](https://status.neuroon.ai).

If a check fails, an issue is opened in this repo and the team gets notified. Once the service is back, the issue closes automatically.

## What is monitored?

| Component | Endpoint | Healthy = |
|---|---|---|
| API HTTP (production) | `https://api.neuroon.ai/actuator/health` | HTTP 200 + `{"status":"UP"}` |
| API HTTP (development) | `https://dev-api.neuroon.ai/actuator/health` | HTTP 200 + `{"status":"UP"}` |
| Widget CDN | `https://cdn.neuroon.ai/versions.json` | HTTP 200 |
| Documentation | `https://docs.neuroon.ai/` | HTTP 200 |
| Dashboard | `https://neuroon.ai/dashboard` | HTTP 200/302/308 |

## License

- Code: [MIT](./LICENSE) © Neuroon AI
- Powered by [Upptime](https://github.com/upptime/upptime)
