# SMART — Landing Page

Landing page statis (Bahasa Indonesia) untuk aplikasi **SMART**, alarm peringatan dini Gunung Merapi dari BPPTKG.

## Halaman

| URL | File |
| --- | --- |
| `/` | `public/index.html` |
| `/kebijakan-privasi` (juga `/privacy`, `/privacy-policy`) | `public/kebijakan-privasi.html` |
| `/healthz` | health check (Nginx) |

## Deploy di Easypanel

**Opsi A — App service (disarankan)**
1. Buat service **App** → Source: GitHub/Git repo (atau upload).
2. Build: pilih **Dockerfile** (path `Dockerfile`), bukan Nixpacks/Buildpacks.
3. Tab **Domains** → tambahkan domain, set **Port = 13006**.
4. Deploy.

**Opsi B — Compose service**
Gunakan `docker-compose.yml` apa adanya (tanpa `ports`/`container_name`), lalu di tab Domains
pilih service `smart-landing` dan **Port = 13006**.

## Menjalankan lokal

```bash
docker compose -f docker-compose.yml -f docker-compose.local.yml up -d --build   # http://localhost:8080
```

## Sebelum rilis

- Ganti `PRIVACY_EMAIL_HERE` di `public/kebijakan-privasi.html` dengan email kontak resmi.
- Pastikan tautan Google Play di `public/index.html` (`com.bpptkg.smart`) sudah aktif.
- Untuk HTTPS, letakkan container di belakang reverse proxy (Nginx/Traefik/Caddy) atau load balancer.
