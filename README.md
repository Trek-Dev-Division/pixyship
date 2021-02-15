# PixyShip

## Requirements

* Debian 10
* Python 3.7
* NPM 5.8.0

## Getting Started locally

```bash

# Create virtualenv
python3 -m venv .venv
source .venv/bin/activate

# Install Python dependencies
pip install wheel # not mandatory, but easier for installing modules
pip install -r requirements.txt

# Install npm dependencies
(cd frontend/ && npm install)

# Configure database
cp config/alembic_dev.ini alembic.ini
${EDITOR} alembic.ini # update sqlalchemy.url, user must be SUPERUSER

cp config/config_template.py config/config.py
${EDITOR} config/config.py # update DSN

# Create database
alembic upgrade head

# Build UI
(cd frontend/ && npm run build)

# Initial data load
python data_load.py --data
python data_load.py --players
```

Run :

```bash
# Frontend
(cd frontend/ && npm run dev)

# Backend
python run.py
```

Access the web server at localhost:8080

## Deploying remotely

**TODO: remove fab**

The deployment process targets a Ubuntu 16 server with ssh access.

First setup the remote from your local environment: 
`fab -h <host> setup`

Then the first and all subsequent deploys are done with: 
`fab -h <host> deploy`
