# Proyecto 5 - API REST con Django

**Programa:** Ingeniería de Sistemas  
**Materia:** Programación Avanzada  
**Semestre:** 7 - Jornada Nocturna  
**Docente:** Fredy Jacanamijoy  

---

## Descripción

API REST desarrollada con Django y Django REST Framework. Gestiona Proyectos, Usuarios y Tareas con base de datos MySQL.

## Requisitos previos

- Python 3.12
- MySQL o MariaDB instalado
- pip actualizado

## Instalación

### 1. Clonar el repositorio

```bash
git clone https://github.com/jhorch1/proyecto_5.git
cd proyecto_5
```

### 2. Crear y activar entorno virtual

```bash
python -m venv env
# Windows:
env\Scripts\activate
# macOS/Linux:
source env/bin/activate
```

### 3. Instalar dependencias

```bash
pip install django==4.2
pip install djangorestframework==3.14.0
pip install mysqlclient
pip install pymysql
```

> **Nota:** Se usa Django 4.2 LTS porque MariaDB 10.4 no es compatible con Django 5.2 (requiere 10.5+).

### 4. Crear la base de datos en MySQL

```sql
CREATE DATABASE tareas_db;
```

### 5. Configurar contraseña en settings.py

Editar `tareas_project/settings.py` y ajustar el campo `PASSWORD` según tu MySQL:

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': 'tareas_db',
        'USER': 'root',
        'PASSWORD': '',  # Cambia esto si tu MySQL tiene contraseña
        'HOST': 'localhost',
        'PORT': '3306',
        'OPTIONS': {
            'init_command': "SET sql_mode='STRICT_TRANS_TABLES'"
        }
    }
}
```

### 6. Aplicar migraciones

```bash
python manage.py migrate
```

### 7. Crear superusuario

```bash
python manage.py createsuperuser
```

### 8. Iniciar el servidor

```bash
python manage.py runserver
```

---

## Endpoints disponibles

| URL | Descripción |
|-----|-------------|
| http://localhost:8000/admin/ | Panel de administración Django |
| http://localhost:8000/api/ | Raíz de la API REST |
| http://localhost:8000/api/proyectos/ | CRUD de Proyectos |
| http://localhost:8000/api/usuarios/ | CRUD de Usuarios |
| http://localhost:8000/api/tareas/ | CRUD de Tareas |

## Estructura del proyecto

```
proyecto_5/
├── manage.py
├── tareas_project/
│   ├── settings.py
│   └── urls.py
└── tareas_app/
    ├── models.py       # Modelos: Proyecto, Usuario, Tarea
    ├── serializers.py  # Serializers DRF
    ├── views.py        # ViewSets
    ├── urls.py         # Rutas de la API
    └── admin.py        # Registro en panel admin
```
