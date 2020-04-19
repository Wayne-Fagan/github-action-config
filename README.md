# Github Action Workflow - Targeting Django App With Postgres DB

Taken from my own custom cookiecutter.

### Database configuration - settings.py 

```
DATABASES = {
    "default": {
        "ENGINE": "django.db.backends.postgresql",
        "NAME": "{{ cookiecutter.repo }}",
        "USER": env("DATABASE_USER"),
        "PASSWORD": env("DATABASE_PASSWORD"),
        "HOST": "localhost",
        "PORT": "5432",
    }
}
```

To link the postgres `service` with the job of the workflow, the *host* must be defined in the above, as follows:

1. *Virtual machine* - set it to `localhost`
2. *In a container* - set it to the `name of the service` as defined in `docker-compose.yml`