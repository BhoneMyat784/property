# Property Portal

The Property Portal helps people find homes, land, and commercial spaces to buy or rent in Yangon and Mandalay. Owners and agents can create listings, buyers and renters can explore properties, and staff can review listing quality.

The web portal is the first experience. The Expo mobile app is planned as a later client.

## Try the local demo

Start the API in one terminal:

```powershell
cd api
npm install
npm run dev
```

Start the web app in another:

```powershell
cd app
npm install
npm run dev
```

Open [http://localhost:5173](http://localhost:5173). The API is available at [http://localhost:4000/api/v1](http://localhost:4000/api/v1).

Use password `demo1234` with one of these local demo accounts:

| Role | Email |
| --- | --- |
| Owner | `owner@example.com` |
| Agent | `agent@example.com` |
| Buyer/renter | `buyer@example.com` |
| Staff | `staff@example.com` |
| Admin | `admin@example.com` |

Demo listings created through the owner or agent form are held in memory and clear when the API restarts.

## Projects

- [`api/README.md`](./api/README.md) — API setup, available endpoints, and demo access.
- [`app/README.md`](./app/README.md) — web portal setup and current user workflows.
- [`mobile/README.md`](./mobile/README.md) — Expo mobile app setup and planned capabilities.

## Project documents

- [`AGENTS.md`](./AGENTS.md) — stable engineering boundaries and stack decisions.
- [`CLAUDE.md`](./CLAUDE.md) — Claude-specific pointer to repository guidance.
- [`SPEC.md`](./SPEC.md) — product features and user workflows.
