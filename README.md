# To contribute

```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```


# To consume template locally

If you have cloned this repository and want to test the Cookiecutter template from your local checkout, you can run:

```bash
pip install cookiecutter
cookiecutter .
cd django_project  # or the project_name you choose
./install.sh
docker compose up -d
docker compose run web pytest
```

This will generate a project from the local template, build the Docker environment and run the test suite.

## Cookiecutter configuration

When you run `cookiecutter` (either against GitHub or locally), you will be asked for the following variables:

- **project_name**: name of the Django project that will be generated (default: `root`).
- **template_name**: name of the template folder (default: `django_project`).
- **database_engine**: database engine used by Django in `config/settings/local.py`:
  - `postgresql` (default): uses `django.db.backends.postgresql` and the variables `DB_HOST`, `DB_NAME`, `DB_USER`, `DB_PASSWORD`, `DB_PORT` from `.env`. This option matches the provided `docker-compose.yml` (Postgres `database` service).
  - `sqlite`: uses `django.db.backends.sqlite3` and a local `db.sqlite3` file. Does not require any database container, ideal for quick tests without Docker.
