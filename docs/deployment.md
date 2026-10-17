# Manual Deployment M03

- Application path: `/srv/cc-m03`
- Service: `cc-m03.service`
- Backend: `127.0.0.1:8000`
- Public endpoint: `http://20.194.24.209/`

## Update Procedure

```bash
cd /srv/cc-m03
git pull
source .venv/bin/activate
python -m pip install -r requirements.txt
sudo systemctl restart cc-m03
sudo systemctl status cc-m03 --no-pager
curl -fsS http://127.0.0.1:8000/health
curl -fsS http://127.0.0.1/health
```

## Catatan Konfigurasi
API key layanan AI (saat fitur diintegrasikan) disimpan sebagai environment
variable pada service systemd, bukan di repository.
