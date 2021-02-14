# PixyShip

## Requirements
* Python 3.9
* NPM 7.5.0
* Docker

## Getting Started locally
1. Pip install the dev requirements: `pip install -r dev_reqs.txt`
2. Install npm packages: `fab npm_install`
2. Configure database access: 
    - `ln -s config/alembic_dev.ini alembic.ini`
    - `vim alembic.ini`
3. Create Postgres database :
    - in a container: `fab create_postgres`
    - OR juste create database: `alembic upgrade head`
4. Build the UI: `fab build_ui`
5. Initial data load: `fab update_data`
6. Initial data load of players: `python data_load.py`
7. Start the front-end dev environment: `fab ui`
8. Start the back end from the virtual environment (activate it) then `python run.py`

Access the web server at localhost:8080

## Deploying remotely
The deployment process targets a Ubuntu 16 server with ssh access.

First setup the remote from your local environment: 
`fab -h <host> setup`

Then the first and all subsequent deploys are done with: 
`fab -h <host> deploy`
