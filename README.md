# QR Redirect

Azure Static Web App som tar emot ett ID från en QR-kod och visar en landningssida.

## Struktur

```
src/
├── index.html              # Visas om ingen QR-kod anges
└── r/
    └── index.html          # Landningssida för /r/{id}
staticwebapp.config.json    # Azure routing-regler
```

## URL-format

```
https://<din-url>/r/{id}
```

## Deploy

Pushar till `main` triggar automatisk deploy via GitHub Actions.

## Fas 2 — BC-integration

När BC-uppslag ska läggas till:
1. Lägg till `/api`-mapp med en Azure Function
2. Uppdatera `staticwebapp.config.json` så `/r/*` routas till funktionen
3. Funktionen anropar BC OData/API med ID:t och returnerar redirect eller data
