# sqlite3

```console
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject$ cd guestbook-src/02_mvp_modules_sqlite3
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject/guestbook-src/02_mvp_modules_sqlite3$ tree
.
├── app.py
├── gbmodel
│   ├── __init__.py
│   ├── model.py
│   ├── model_pylist.py
│   ├── model_sql_postgres.py
│   └── model_sqlite3.py
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

3 directories, 14 files
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject/guestbook-src/02_mvp_modules_sqlite3$ pip install -r requirements.txt
Requirement already satisfied: flask in /home/darwin/temp/myproject/venv/lib/python3.10/site-packages (from -r requirements.txt (line 1)) (3.0.2)
Collecting python-dotenv (from -r requirements.txt (line 3))
  Downloading python_dotenv-1.0.1-py3-none-any.whl.metadata (23 kB)
Collecting psycopg[binary] (from -r requirements.txt (line 2))
  Downloading psycopg-3.1.18-py3-none-any.whl.metadata (4.2 kB)
Requirement already satisfied: Werkzeug>=3.0.0 in /home/darwin/temp/myproject/venv/lib/python3.10/site-packages (from flask->-r requirements.txt (line 1)) (3.0.1)
Requirement already satisfied: Jinja2>=3.1.2 in /home/darwin/temp/myproject/venv/lib/python3.10/site-packages (from flask->-r requirements.txt (line 1)) (3.1.3)
Requirement already satisfied: itsdangerous>=2.1.2 in /home/darwin/temp/myproject/venv/lib/python3.10/site-packages (from flask->-r requirements.txt (line 1)) (2.1.2)
Requirement already satisfied: click>=8.1.3 in /home/darwin/temp/myproject/venv/lib/python3.10/site-packages (from flask->-r requirements.txt (line 1)) (8.1.7)
Requirement already satisfied: blinker>=1.6.2 in /home/darwin/temp/myproject/venv/lib/python3.10/site-packages (from flask->-r requirements.txt (line 1)) (1.7.0)
Collecting typing-extensions>=4.1 (from psycopg[binary]->-r requirements.txt (line 2))
  Downloading typing_extensions-4.9.0-py3-none-any.whl.metadata (3.0 kB)
Collecting psycopg-binary==3.1.18 (from psycopg[binary]->-r requirements.txt (line 2))
  Downloading psycopg_binary-3.1.18-cp310-cp310-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (2.8 kB)
Requirement already satisfied: MarkupSafe>=2.0 in /home/darwin/temp/myproject/venv/lib/python3.10/site-packages (from Jinja2>=3.1.2->flask->-r requirements.txt (line 1)) (2.1.5)
Downloading psycopg_binary-3.1.18-cp310-cp310-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (3.3 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 3.3/3.3 MB 20.9 MB/s eta 0:00:00
Downloading python_dotenv-1.0.1-py3-none-any.whl (19 kB)
Downloading typing_extensions-4.9.0-py3-none-any.whl (32 kB)
Downloading psycopg-3.1.18-py3-none-any.whl (178 kB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 178.1/178.1 kB 12.4 MB/s eta 0:00:00
Installing collected packages: typing-extensions, python-dotenv, psycopg-binary, psycopg
Successfully installed psycopg-3.1.18 psycopg-binary-3.1.18 python-dotenv-1.0.1 typing-extensions-4.9.0
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject/guestbook-src/02_mvp_modules_sqlite3$
```

# Run

```console
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject/guestbook-src/02_mvp_modules_sqlite3$ python app.py
 * Serving Flask app 'app'
 * Debug mode: on
WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
 * Running on all addresses (0.0.0.0)
 * Running on http://127.0.0.1:5000
 * Running on http://157.26.104.158:5000
Press CTRL+C to quit
 * Restarting with stat
 * Debugger is active!
 * Debugger PIN: 714-352-544
127.0.0.1 - - [21/Feb/2024 14:14:39] "GET / HTTP/1.1" 200 -
127.0.0.1 - - [21/Feb/2024 14:14:39] "GET /static/style.css HTTP/1.1" 200 -
127.0.0.1 - - [21/Feb/2024 14:14:39] "GET /static/sign_here.png HTTP/1.1" 200 -
127.0.0.1 - - [21/Feb/2024 14:15:23] "GET /sign HTTP/1.1" 200 -
127.0.0.1 - - [21/Feb/2024 14:15:23] "GET /static/style.css HTTP/1.1" 304 -
127.0.0.1 - - [21/Feb/2024 14:15:50] "POST /sign HTTP/1.1" 302 -
127.0.0.1 - - [21/Feb/2024 14:15:50] "GET / HTTP/1.1" 200 -
127.0.0.1 - - [21/Feb/2024 14:15:50] "GET /static/style.css HTTP/1.1" 304 -
127.0.0.1 - - [21/Feb/2024 14:15:50] "GET /static/sign_here.png HTTP/1.1" 304 -
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
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject/guestbook-src/02_mvp_modules_sqlite3$ python app.py
```

# sqlite3 database

```console
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject/guestbook-src/02_mvp_modules_sqlite3$ sudo apt-get install sqlite3 libsqlite3-dev
[sudo] password for darwin:
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  libsqlite3-0

(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject/guestbook-src/02_mvp_modules_sqlite3$ sqlite3 guestbook.db
SQLite version 3.37.2 2022-01-06 13:25:41
Enter ".help" for usage hints.
sqlite> .tables
entries
sqlite> .schema entries
CREATE TABLE entries (name text, email text, signed_on timestamp, message text);
sqlite> select * from entries
   ...> ;
Darwin Ameli|darwin.ameli@he-arc.ch|2024-02-21 14:15:50.520863|python/flask MVP sqlite3 #1
Darwin Ameli|darwin.ameli@he-arc.ch|2024-02-21 14:20:08.139516|python/flask MVP sqlite3 #2
sqlite> select rowid, * from entries;
1|Darwin Ameli|darwin.ameli@he-arc.ch|2024-02-21 14:15:50.520863|python/flask MVP sqlite3 #1
2|Darwin Ameli|darwin.ameli@he-arc.ch|2024-02-21 14:20:08.139516|python/flask MVP sqlite3 #2
sqlite> UPDATE entries SET email = 'test@test.com' WHERE rowid = 1;
sqlite> select rowid, * from entries;
1|Darwin Ameli|test@test.com|2024-02-21 14:15:50.520863|python/flask MVP sqlite3 #1
2|Darwin Ameli|darwin.ameli@he-arc.ch|2024-02-21 14:20:08.139516|python/flask MVP sqlite3 #2
sqlite> .quit
```
