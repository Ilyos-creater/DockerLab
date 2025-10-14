## 🧩 Anforderungen des ersten Projekts

### 1️⃣ Warm-up: Offizielles Image anpassen (sehr leicht)

Ziel dieses Projekts ist es, mit dem offiziellen `nginx`-Image zu arbeiten und erste eigene Anpassungen vorzunehmen.

**Aufgaben:**
- `nginx` starten und eine eigene `index.html` **per Bind-Mount** serven.  
- Anschließend ein **Mini-Dockerfile** erstellen, das die `index.html` **ins Image kopiert**.  
- Container **mit Port-Mapping** starten, um die Seite im Browser aufzurufen.  

**Ergebnis:**
Am Ende solltest du deine `index.html` auf **zwei Arten** im Browser erreichen können:
1. Über den Container, der deine Datei **per Bind-Mount** lädt.  
2. Über den Container, der aus dem **neu gebauten Image (Dockerfile)** erstellt wurde.  

Ziel ist es, den Unterschied zwischen *dynamischen Bind-Mounts* und *fest eingebauten Dateien im Image* zu verstehen.

