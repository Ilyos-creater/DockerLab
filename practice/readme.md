# 🧩 Docker – Phase 1: Container Basics

## 1️⃣ Hello Container
```bash
# Image starten
docker run nginx

# Kontrolle
docker ps
docker stop <id>

# Ergebnis:
# Container erfolgreich gestartet und gestoppt.



# Port-Mapping testen
docker run -p 8080:80 nginx

# Zugriff über Browser:
# http://localhost:8080

# Ergebnis:
# Standard-"Welcome to nginx!"-Seite wird angezeigt.



# Eigene index.html erstellen und mounten
docker run -v $(pwd):/usr/share/nginx/html:ro -p 8080:80 -d nginx

# Ergebnis:
# Eigene HTML-Seite im Browser sichtbar.
# Live-Änderungen auf dem Host sofort wirksam.


# Dockerfile
FROM nginx
COPY . /usr/share/nginx/html

# Image bauen
docker build -t my-nginx .

# Container starten
docker run -p 8080:80 -d my-nginx

# Ergebnis:
# Custom-HTML ist direkt im Image eingebettet.
# Läuft auch ohne Bind Mount.

