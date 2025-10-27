Crea un entorno virtual llamado venv

```bash
python -m venv venv
```
Activa el venv

```bash
venv\Scripts\activate.bat
```
Crea un archivo `requeriments.txt` para las dependencias de la aplicación

```txt
django
python-dotenv
gunicorn
psycopg2
```

```bash
python -m pip install -r requirements.txt
```
Crea el proyecto main en la raiz del repositorio

```bash
Django-admin startproject main .
```
Crea la app venta 

```bash
Django-admin startapp venta
``` 
Instalan la aplicacion venta en `main/setings.py`

```py
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'venta'
]
```

Configuramos la conexión a PostgresSQL en `main/setings.py`

```py
from dotenv import load_dotenv
import os
load_dotenv()
```

```py
DATABASES = {
    "default": {
        "ENGINE": "django.db.backends.postgresql",
        "NAME": os.getenv("dbname"),
        "USER": os.getenv("user"),
        "PASSWORD": os.getenv("password"),
        "HOST": os.getenv("host"),
        "PORT": os.getenv("port"),
    }
}
```

Ahora crear las variables de entorno en un nuevo archivo `.env`

```env
user=user
password=password
host=host
port=port
dbname=postgres
```