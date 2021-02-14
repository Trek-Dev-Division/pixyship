# PixyShip

## Requirements

* Python 3.9
* NPM 7.5.0
* Docker

## Getting Started locally

```bash

# Create virtualenv
python3 -m venv .venv
source .venv/bin/activate

# Install Python dependencies
pip install -r requirements.txt

# Install npm dependencies
(cd frontend/ && npm install)

# Configure database
ln -s config/alembic_dev.ini alembic.ini
${EDITOR} alembic.ini # update sqlalchemy.url

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
The deployment process targets a Ubuntu 16 server with ssh access.

First setup the remote from your local environment: 
`fab -h <host> setup`

Then the first and all subsequent deploys are done with: 
`fab -h <host> deploy`
