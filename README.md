# Gydmation AI

Turn plain English into working n8n workflows.

## Before you start

You need **Docker Desktop**, installed and running.
Don't have it? → [docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)

That's the only requirement. Nothing else to install.

## Set up (one time)

1. Save `docker-compose.yml` (from this same folder) anywhere you like.
2. Open a terminal **in that folder** and run two commands:

```
docker compose pull
docker compose up -d
```

The first run also downloads and sets up an AI model in the background — this takes a few minutes. It happens again briefly every time you restart Gydmation (not just the very first time) — that's expected, and only takes 30–60 seconds. Your account, conversations, and settings are never affected by it.

## Open it

```
http://localhost:8080
```

## Every time after that

```
docker compose up -d
```

Same address, same command. Docker remembers everything.

## Stopping it

```
docker compose down
```

Your account, conversations, and settings are all saved — `docker compose up -d` picks up right where you left off.

## Checking on it

```
docker compose logs -f
```

Shows what Gydmation is doing right now. Press `Ctrl+C` to stop watching — this doesn't stop the app.

## Using a different port

Already have something running on 8080? Two ways:

**Quick, one-time:**
```
$env:GYDMATION_PORT=3000
docker compose up -d
```

**Permanent:** open `docker-compose.yml`, find this line, and change the **first** number:
```yaml
ports:
  - "${GYDMATION_PORT:-8080}:8080"
```
for example `"${GYDMATION_PORT:-3000}:8080"` — then open `http://localhost:3000` instead.

## Getting an update

When a new version is out, same two commands:

```
docker compose pull
docker compose up -d
```

Nothing you've built or saved is touched.

## Something not working?

```
docker compose logs -f
```

almost always shows exactly what's wrong. If you're stuck, send that output — it's the single most useful thing for figuring out what happened.

