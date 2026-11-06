# VideoGrab — site statique responsive

## Lancer
Ouvrir `index.html` ou lancer `python -m http.server 8000` depuis ce dossier.

## Téléchargements réels
La partie front-end est fonctionnelle (détection, collage, états, rendu des métadonnées), mais ne peut pas télécharger des vidéos sans un service serveur autorisé. Par défaut, elle indique clairement que le serveur est absent.

Dans `assets/app.js`, renseigner `API_BASE` avec une URL HTTPS d’un backend que vous contrôlez. Contrat attendu :
- `POST /api/info` JSON `{ "url": "https://..." }` → `{ "title": "...", "thumbnail": "https://...", "formats": [{"id":"format_id","quality":"HD"},{"id":"sd_id","quality":"SD"},{"id":"audio_id","quality":"MP3"}] }`
- `POST /api/download` JSON `{ "url": "...", "format": "format_id" }` → `{ "downloadUrl": "https://..." }`
Le backend doit valider les URLs, protéger contre SSRF, limiter les requêtes, appliquer CORS de façon restrictive, ne servir que des médias autorisés, et ne pas contourner les restrictions des plateformes. Les capacités du serveur Render préexistant ne sont pas présumées compatibles.

## Avant publication
1. Remplacer `contact@example.com` dans les pages, `data-contact-email` et les pages légales.
2. Renseigner l’identité de l’éditeur et la juridiction; faire relire les pages légales.
3. Remplacer `https://example.com/` dans `sitemap.xml` par le domaine réel; ajouter des URL canoniques et OG URL après choix du domaine.
4. Ajouter une vraie solution de contact si l’envoi serveur est souhaité (actuellement `mailto:`).
5. Configurer une API et tester chaque plateforme avec des médias autorisés.
6. Avant toute publicité ou analytique, implémenter une gestion du consentement conforme à la région.
7. Les emplacements publicitaires sont des placeholders : aucune publicité ni AdSense n’est intégré. L’acceptation AdSense n’est jamais garantie.

## Arborescence
`index.html`, `instagram.html`, `facebook.html`, `snapchat.html`, `tiktok.html`, `x.html`, `about.html`, `contact.html`, `privacy.html`, `terms.html`, `dmca.html`, `faq.html`, `assets/style.css`, `assets/app.js`, `assets/placeholder.svg`, `robots.txt`, `sitemap.xml`.
