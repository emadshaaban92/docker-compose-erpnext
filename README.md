# Important Update

This repo isn't maintained anymore because I stopped using ERPNext long time ago, luckily there's a working (and much better) alternative [Monogramm/docker-erpnext](https://github.com/Monogramm/docker-erpnext)

# Docker ERPNext (Multi-container) Example

Frappe, ERPNext - Dockerized on Alpine

Follow the steps below to run your own local installation of ERPNext.

## Perequisites

1. **install docker** as per these instructions https://docs.docker.com/engine/installation/
2. **install docker compose** with `sudo apt install docker-compose` (debian/ubuntu)

## Clone this repository and move into it

1. `git clone https://github.com/emadshaaban92/docker-compose-erpnext.git`  
2. `cd docker-compose-erpnext`

## Start a local version of ERPNext

1. First we need to bootstrap the installation, run: `docker-compose -f manage.yml run setup`
2. Enter `y` and enter, when asked to reset the database _(be patient. This may take quite a while)_
3. Start the containers: `docker-compose up -d`
4. Watch the container logs: `docker-compose logs -f`

You should be able to log in to the server at `http://localhost`. The username is `Administrator` and the password is `frappe`. Follow the prompts to complete the initial setup.


## Update

1. Stop & remove the containers: `docker-compose down`
2. Change ERPNEXT_VERSION in .env file
3. Update database (run patches & migrations): `docker-compose -f manage.yml run update`
4. Start the containers: `docker-compose up -d`
5. Watch the container logs: `docker-compose logs -f`


## Backup

Run : `docker-compose -f manage.yml run backup`

You can find your new created backup inside `sites/localhost/private/backups`


## Restore

Run : `docker-compose -f manage.yml run restore`

This will prompt you to choose form previous backups in `sites/localhost/private/backups`


## Migrate

Run : `docker-compose -f manage.yml run migrate`
