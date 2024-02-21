# PostgreSQL

On va attendre le cours pour voir s'il n'y a pas besoin d'acheter de crédit google

```console
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject/guestbook-src/02_mvp_modules_sqlite3$ tree
.
├── __pycache__
│   ├── index.cpython-310.pyc
│   └── sign.cpython-310.pyc
├── app.py
├── gbmodel
│   ├── __init__.py
│   ├── __pycache__
│   │   ├── __init__.cpython-310.pyc
│   │   ├── model.cpython-310.pyc
│   │   └── model_sqlite3.cpython-310.pyc
│   ├── model.py
│   ├── model_pylist.py
│   ├── model_sql_postgres.py
│   └── model_sqlite3.py
├── guestbook.db
├── index.py
├── requirements.txt
├── sign.py
├── static
│   ├── sign_here.png
│   └── style.css
└── templates
    ├── index.html
    ├── layout.html
    └── sign.html

5 directories, 20 files

```

# Créating .env

```console
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject/guestbook-src/02_mvp_modules_sqlite3$ touch .env
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject/guestbook-src/02_mvp_modules_sqlite3$ nano .env
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject/guestbook-src/02_mvp_modules_sqlite3$ cat .env
DB_HOST=localhost
DB_PORT=5432 # Default PostgreSQL port
DB_NAME=guestbook
DB_USER=guestbook
DB_PASS=guestbook
GUESTBOOK_SERVICE=postgres
```

Il faut modifier DB_HOST par l'adresse publique google de notre instance


TODO Demande au prof si on peut self-host un psql à la place