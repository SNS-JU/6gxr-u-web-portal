Unified & North Web Portals Deployment Guide

This repository contains two Django-based web applications (Unified and North) with their own frontends, connected to a PostgreSQL database and served with gunicorn and nginx. Systemd unit files are provided to simplify deployment.

**UI Template Notice**:

As the frontend application, we use the *Material Kit React* template provided by the `minimal-ui-kit` team.
This UI template is licensed under the **MIT License**, which allows free use, modification, and distribution, including for commercial purposes.
You can find the original template and license information here:  
https://github.com/minimal-ui-kit/material-kit-react

## Project Structure

```text
6G-XR/
├── Unified/               # Django backend for Unified
├── North/                 # Django backend for North
├── Unified_front/         # Frontend for Unified (Vite + React)
├── north_front/           # Frontend for North (Vite + React) 
├── services/              # Systemd service files
├── Nginx/                 # Nginx configuration files
├── Unified APIs/          # Unified API documentation
├── North APIs/            # North API documentation
├── Grafana.ini            # Grafana configuration file
├── Slice1-dashboard/      # Grafana dashboard configuration for slice 1
├── Slice2-dashboard/      # Grafana dashboard configuration for slice 2
├── LICENSE                # MIT License
└── README.md              # This guide
```

**Port Mapping:**
| **Service**               | **Description**                  | **Port** |
| ------------------------- | -------------------------------- | -------- |
| **Unified Backend**       | Django via Gunicorn              | `8000`   |
| **North Backend**         | Django via Gunicorn              | `8080`   |
| **Unified Frontend**      | React served via Nginx           | `8087`   |
| **North Frontend**        | React served via Nginx           | `8086`   |
| **South Service Manager** | Internal service proxy via Nginx | `4040`   |


**Prerequisites**:

Python 3.10+

Node.js 18+

PostgreSQL

nginx

systemd (Linux)


**Installation Instructions**
1. Clone the Repository
git clone https://your.git.repo/6g-xr.git
cd 6g-xr

2. Setup Python Virtual Environment (Unified)
cd Unified
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python manage.py collectstatic

3. Use this command to generate a secret key, and use it in the settings file of both projects:
python -c "from django.core.management.utils import get_random_secret_key; print(get_random_secret_key())"

# Setup database
4. Go to the settings file and set your Database parameters.
python manage.py makemigrations
python manage.py migrate
python manage.py createsuperuser


5. Repeat the same for North portal:
cd ../../North
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python manage.py collectstatic

**6. Use the unified secret key in the settings file of North portal.**

# Setup database
7. Go to settings file and set your Database parameters.
python manage.py makemigrations
python manage.py migrate
python manage.py createsuperuser

8. Build Frontend (React + Vite)
# Unified frontend
cd ../../Unified_front
npm install
npm run build

# North frontend
cd ../../north_front
npm install
npm run build

9. nginx Configuration
cd ../../nginx
copy 'nextjs' and 'portals' files to your server at the following path: /etc/nginx/sites-available/

10. systemd Service Setup
cd ../../services
copy all service files to your server at the following path: /etc/systemd/system/
Enable & Start Services:
sudo systemctl daemon-reload
sudo systemctl enable <name>.service
sudo systemctl start <name>.service


**Troubleshooting**:
Backend logs: journalctl -u <name>.service


## License

This project is licensed under the [MIT License](./LICENSE).

