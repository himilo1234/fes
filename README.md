# AutoSender Frontend

This repository contains the standalone AutoSender dashboard. It is a static site and can be deployed independently from the FastAPI backend in the sibling `be` repository.

## Local setup

Run a static file server from this folder:

```powershell
python -m http.server 5173
```

Open `http://127.0.0.1:5173`. The dashboard uses same-origin API requests when the `api-base-url` metadata is empty. For local development against the separate backend, set it in `index.html`:

```html
<meta name="api-base-url" content="http://127.0.0.1:3002">
```

## Deploy

Deploy this repository as a static site. Set the `api-base-url` metadata in `index.html` to the public base URL of the deployed FastAPI backend, with no trailing slash. On the backend service, set `FRONTEND_ORIGINS` to the frontend's exact public origin (scheme and hostname, without a path or trailing slash).

The backend is a separate repository and service. Configure its database and admin secrets in the backend host; do not put those secrets in this frontend repository.
