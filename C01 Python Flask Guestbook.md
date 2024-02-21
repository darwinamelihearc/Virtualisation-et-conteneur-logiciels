# Python Flask Guestbook

```console
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject$ git clone https://github.com/bfritscher/guestbook-src.git
Cloning into 'guestbook-src'...
remote: Enumerating objects: 1261, done.
remote: Counting objects: 100% (128/128), done.
remote: Compressing objects: 100% (57/57), done.
remote: Total 1261 (delta 77), reused 85 (delta 70), pack-reused 1133
Receiving objects: 100% (1261/1261), 442.83 KiB | 2.43 MiB/s, done.
Resolving deltas: 100% (628/628), done.
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject$ cd guestbook-src/
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject/guestbook-src$ ls
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject/guestbook-src$ tree 01_mvc_pylist/ -L 2
01_mvc_pylist/
├── Model.py
├── app.py
├── model_pylist.py
├── requirements.txt
├── static
│   └── style.css
└── templates
    ├── index.html
    └── layout.html

2 directories, 7 files
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject/guestbook-src$ cd 01_mvc_pylist/
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject/guestbook-src/01_mvc_pylist$ pip install -r requirements.txt
Collecting flask (from -r requirements.txt (line 1))
  Downloading flask-3.0.2-py3-none-any.whl.metadata (3.6 kB)
Collecting Werkzeug>=3.0.0 (from flask->-r requirements.txt (line 1))
  Downloading werkzeug-3.0.1-py3-none-any.whl.metadata (4.1 kB)
Collecting Jinja2>=3.1.2 (from flask->-r requirements.txt (line 1))
  Downloading Jinja2-3.1.3-py3-none-any.whl.metadata (3.3 kB)
Collecting itsdangerous>=2.1.2 (from flask->-r requirements.txt (line 1))
  Downloading itsdangerous-2.1.2-py3-none-any.whl (15 kB)
Collecting click>=8.1.3 (from flask->-r requirements.txt (line 1))
  Downloading click-8.1.7-py3-none-any.whl.metadata (3.0 kB)
Collecting blinker>=1.6.2 (from flask->-r requirements.txt (line 1))
  Downloading blinker-1.7.0-py3-none-any.whl.metadata (1.9 kB)
Collecting MarkupSafe>=2.0 (from Jinja2>=3.1.2->flask->-r requirements.txt (line 1))
  Downloading MarkupSafe-2.1.5-cp310-cp310-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (3.0 kB)
Downloading flask-3.0.2-py3-none-any.whl (101 kB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 101.3/101.3 kB 2.8 MB/s eta 0:00:00
Downloading blinker-1.7.0-py3-none-any.whl (13 kB)
Downloading click-8.1.7-py3-none-any.whl (97 kB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 97.9/97.9 kB 3.0 MB/s eta 0:00:00
Downloading Jinja2-3.1.3-py3-none-any.whl (133 kB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 133.2/133.2 kB 5.1 MB/s eta 0:00:00
Downloading werkzeug-3.0.1-py3-none-any.whl (226 kB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 226.7/226.7 kB 11.9 MB/s eta 0:00:00
Downloading MarkupSafe-2.1.5-cp310-cp310-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (25 kB)
Installing collected packages: MarkupSafe, itsdangerous, click, blinker, Werkzeug, Jinja2, flask
Successfully installed Jinja2-3.1.3 MarkupSafe-2.1.5 Werkzeug-3.0.1 blinker-1.7.0 click-8.1.7 flask-3.0.2 itsdangerous-2.1.2
```

# Run

```console
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject/guestbook-src/01_mvc_pylist$ python app.py
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
 
127.0.0.1 - - [21/Feb/2024 13:47:09] "GET / HTTP/1.1" 200 -
127.0.0.1 - - [21/Feb/2024 13:47:09] "GET /static/style.css HTTP/1.1" 200 -
127.0.0.1 - - [21/Feb/2024 13:47:10] "GET /favicon.ico HTTP/1.1" 404 -
```