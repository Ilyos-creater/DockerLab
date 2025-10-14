#FirstFive
Here I will built five projects, to go from almost no Docker knowledge to knowing how to work with docker regularly.

Those First Five are:
### 1) Warm-up: Offizielles Image anpassen (sehr leicht)

- `nginx` starten und eine eigene `index.html` **per Bind-Mount** serven.
- Danach ein **Mini-Dockerfile** bauen, das deine `index.html` ins Image kopiert.
- Mit Port-Mapping starten; kurzer **Screenshot/README** als Nachweis.

---

### 2) Kleine API containerisieren (leicht)

- Winzige HTTP-API (Python/Node, „/health“ reicht).
- **Dockerfile** bauen (Port, ENV, `.dockerignore`).
- Container lokal starten, **curl** gegen `/health`; **README** mit Befehlen.

---

### 3) Zwei Services mit Compose (mittel)

- Deine API + **Postgres oder Redis** via `docker-compose.yml`.
- **Environment-Variablen** aus `.env` laden; **named volumes** nutzen.
- Beide Services starten/stoppen; **Kurznotiz**, welche ENV du gesetzt hast.

---

### 4) Versionieren & Registry (mittel+)

- Dein API-Image **taggen** (`v1`, `latest`).
- In **Docker Hub oder GHCR** pushen (öffentlich oder privat).
- **Mini-Makefile** mit Targets: `build`, `tag`, `push`; Screenshot vom Registry-Eintrag.

---

### 5) Mini-Pipeline lokal (fortgeschritten, aber kompakt)

- **Tests** für deine API (sehr klein) im Container ausführen.
- **Trivy** einmal lokal gegen dein Image laufen lassen (Security-Scan).
- **Compose-Override** für „prod“ (keine Bind-Mounts, nur Image + ENV).
- Ergebnis dokumentieren: Test-Output, Scan-Summary, `docker compose up -d` (prod).
