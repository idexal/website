# idexal.com — website

The official landing page for **Idexal Code**, served as a static site by nginx
and deployed via **Coolify**.

## What's here

| File | Purpose |
|---|---|
| `index.html` | The landing page (Aurora hero, features, install). |
| `install` | The public install script, served at `idexal.com/install`. |
| `nginx.conf` | nginx config (gzip, plain-text `/install`, SPA-style fallback). |
| `Dockerfile` | `nginx:alpine` image — Coolify auto-detects and builds it. |

## Deploy on Coolify

1. **New Resource → Application → Public/Private Git Repository** → select this repo.
2. Build pack: **Dockerfile** (auto-detected). Port: **80**.
3. **Domains**: add `https://idexal.com` (and `https://www.idexal.com`).
4. Point DNS for `idexal.com` (A/AAAA or CNAME) at your Coolify server, then
   enable **Let's Encrypt** in Coolify for automatic HTTPS.
5. Deploy. `idexal.com` serves the site and `idexal.com/install` serves the
   install script, so `curl -fsSL https://idexal.com/install | bash` works.

## Local preview

```bash
docker build -t idexal-site . && docker run --rm -p 8080:80 idexal-site
# open http://localhost:8080
```

## Keeping `install` in sync

The canonical install script lives in
[`idexal/idexal-code`](https://github.com/idexal/idexal-code). Copy it here when
it changes:

```bash
curl -fsSL https://raw.githubusercontent.com/idexal/idexal-code/main/install -o install
```

---

© 2026 Idexal · MIT licensed
