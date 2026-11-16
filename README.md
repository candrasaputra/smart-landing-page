# SMART — Landing Page

Landing page statis (Bahasa Indonesia) untuk aplikasi **SMART**, alarm peringatan dini Gunung Merapi dari BPPTKG.

## Halaman

| URL | File |
| --- | --- |
| `/` | `public/index.html` |
| `/kebijakan-privasi` (juga `/privacy`, `/privacy-policy`) | `public/kebijakan-privasi.html` |
| `/healthz` | health check (Nginx) |

## Menjalankan dengan Docker

```bash
docker compose up -d --build      # http://localhost:8080
PORT=80 docker compose up -d --build
```

Tanpa compose:

```bash
docker build -t smart-landing-page .
docker run -d -p 8080:80 --name smart-landing-page --restart unless-stopped smart-landing-page
```

## Sebelum rilis

- Ganti `PRIVACY_EMAIL_HERE` di `public/kebijakan-privasi.html` dengan email kontak resmi.
- Pastikan tautan Google Play di `public/index.html` (`com.bpptkg.smart`) sudah aktif.
- Untuk HTTPS, letakkan container di belakang reverse proxy (Nginx/Traefik/Caddy) atau load balancer.
