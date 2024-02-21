# Setup

```console
darwin@LAPTOP-MMLBEP53:~$ sudo apt-get upgrade -y && sudo apt-get update -y
...

darwin@LAPTOP-MMLBEP53:~$ sudo apt install python3
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
python3 is already the newest version (3.10.6-1~22.04).
python3 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 99 not upgraded.

darwin@LAPTOP-MMLBEP53:~$ python3
Python 3.10.6 (main, Mar 10 2023, 10:55:28) [GCC 11.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> exit()

darwin@LAPTOP-MMLBEP53:~$ python3 --version
Python 3.10.6
```

# Create a Virtual Environment

```console
darwin@LAPTOP-MMLBEP53:~$ cd temp/
darwin@LAPTOP-MMLBEP53:~/temp$ mkdir myproject
darwin@LAPTOP-MMLBEP53:~/temp$ cd myproject/
darwin@LAPTOP-MMLBEP53:~/temp/myproject$ python -m venv venv
Command 'python' not found, did you mean:
  command 'python3' from deb python3
  command 'python' from deb python-is-python3

darwin@LAPTOP-MMLBEP53:~/temp/myproject$ grep -qxF 'alias python='\''python3'\''' ~/.bashrc || echo "alias python='python3'" >> ~/.bashrc && source ~/.bashrc

darwin@LAPTOP-MMLBEP53:~/temp/myproject$ tail ~/.bashrc
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if ! shopt -oq posix; then
  if [ -f /usr/share/bash-completion/bash_completion ]; then
    . /usr/share/bash-completion/bash_completion
  elif [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
  fi
fi
alias python='python3'

darwin@LAPTOP-MMLBEP53:~/temp/myproject$ python -m venv venv
The virtual environment was not created successfully because ensurepip is not
available.  On Debian/Ubuntu systems, you need to install the python3-venv
package using the following command.

    apt install python3.10-venv

darwin@LAPTOP-MMLBEP53:~/temp/myproject$ sudo apt install python3.10-venv -y
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  libpython3.10 libpython3.10-minimal libpython3.10-stdlib python3-distutils python3-lib2to3 python3-pip-whl python3-setuptools-whl python3.10 python3.10-minimal
  ...

darwin@LAPTOP-MMLBEP53:~/temp/myproject$ ls venv -la
total 0
drwxr-xr-x 1 darwin darwin 4096 Feb 21 10:51 .
drwxr-xr-x 1 darwin darwin 4096 Feb 21 10:51 ..
drwxr-xr-x 1 darwin darwin 4096 Feb 21 10:59 bin
drwxr-xr-x 1 darwin darwin 4096 Feb 21 10:51 include
drwxr-xr-x 1 darwin darwin 4096 Feb 21 10:51 lib
lrwxrwxrwx 1 darwin darwin    3 Feb 21 10:51 lib64 -> lib
-rw-r--r-- 1 darwin darwin   71 Feb 21 10:59 pyvenv.cfg

darwin@LAPTOP-MMLBEP53:~/temp/myproject$ source venv/bin/activate
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject$
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject$ deactivate
darwin@LAPTOP-MMLBEP53:~/temp/myproject$ source venv/bin/activate
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject$ pip list
Package    Version
---------- -------
pip        22.0.2
setuptools 59.6.0
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject$ python -m pip install --upgrade pip
Requirement already satisfied: pip in ./venv/lib/python3.10/site-packages (22.0.2)
Collecting pip
  Downloading pip-24.0-py3-none-any.whl (2.1 MB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 2.1/2.1 MB 9.8 MB/s eta 0:00:00
Installing collected packages: pip
  Attempting uninstall: pip
    Found existing installation: pip 22.0.2
    Uninstalling pip-22.0.2:
      Successfully uninstalled pip-22.0.2
Successfully installed pip-24.0
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject$ pip list
Package    Version
---------- -------
pip        24.0
setuptools 59.6.0
```

# Installating Packages

```console
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject$ python -m pip install pandas
Collecting pandas
  Downloading pandas-2.2.0-cp310-cp310-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (19 kB)
Collecting numpy<2,>=1.22.4 (from pandas)
  Downloading numpy-1.26.4-cp310-cp310-manylinux_2_17_x86_64.manylinux2014_x86_64.whl.metadata (61 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 61.0/61.0 kB 2.4 MB/s eta 0:00:00
Collecting python-dateutil>=2.8.2 (from pandas)
  Downloading python_dateutil-2.8.2-py2.py3-none-any.whl (247 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 247.7/247.7 kB 6.5 MB/s eta 0:00:00
Collecting pytz>=2020.1 (from pandas)
  Downloading pytz-2024.1-py2.py3-none-any.whl.metadata (22 kB)
Collecting tzdata>=2022.7 (from pandas)
  Downloading tzdata-2024.1-py2.py3-none-any.whl.metadata (1.4 kB)
Collecting six>=1.5 (from python-dateutil>=2.8.2->pandas)
  Downloading six-1.16.0-py2.py3-none-any.whl (11 kB)
Downloading pandas-2.2.0-cp310-cp310-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (13.0 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 13.0/13.0 MB 32.6 MB/s eta 0:00:00
Downloading numpy-1.26.4-cp310-cp310-manylinux_2_17_x86_64.manylinux2014_x86_64.whl (18.2 MB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 18.2/18.2 MB 34.0 MB/s eta 0:00:00
Downloading pytz-2024.1-py2.py3-none-any.whl (505 kB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 505.5/505.5 kB 31.5 MB/s eta 0:00:00
Downloading tzdata-2024.1-py2.py3-none-any.whl (345 kB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 345.4/345.4 kB 42.3 MB/s eta 0:00:00
Installing collected packages: pytz, tzdata, six, numpy, python-dateutil, pandas
Successfully installed numpy-1.26.4 pandas-2.2.0 python-dateutil-2.8.2 pytz-2024.1 six-1.16.0 tzdata-2024.1
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject$
```

Si on souhaite une version spécifique :

```console
(env) $ python -m pip install pandas==1.1.1
```

Si l'on souhaite n'importe quelle version avant 1.2

```console
(env) $ python -m pip install 'pandas<1.2'
```

Si l'on souhaite n'importe quelle version après 0.25.3

```console
(env) PS> python -m pip install 'pandas>0.25.3'
```

```console
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject$ pip list
Package         Version
--------------- -------
numpy           1.26.4
pandas          2.2.0
pip             24.0
python-dateutil 2.8.2
pytz            2024.1
setuptools      59.6.0
six             1.16.0
tzdata          2024.1
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject$
```


# Reproducing a Python Virtual Environment

```console
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject$ pip list
Package         Version
--------------- -------
numpy           1.26.4
pandas          2.2.0
pip             24.0
python-dateutil 2.8.2
pytz            2024.1
setuptools      59.6.0
six             1.16.0
tzdata          2024.1
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject$ pip freeze > requirements.txt
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject$ cat requirements.txt
numpy==1.26.4
pandas==2.2.0
python-dateutil==2.8.2
pytz==2024.1
six==1.16.0
tzdata==2024.1
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject$ pip install -r requirements.txt
Requirement already satisfied: numpy==1.26.4 in ./venv/lib/python3.10/site-packages (from -r requirements.txt (line 1)) (1.26.4)
Requirement already satisfied: pandas==2.2.0 in ./venv/lib/python3.10/site-packages (from -r requirements.txt (line 2)) (2.2.0)
Requirement already satisfied: python-dateutil==2.8.2 in ./venv/lib/python3.10/site-packages (from -r requirements.txt (line 3)) (2.8.2)
Requirement already satisfied: pytz==2024.1 in ./venv/lib/python3.10/site-packages (from -r requirements.txt (line 4)) (2024.1)
Requirement already satisfied: six==1.16.0 in ./venv/lib/python3.10/site-packages (from -r requirements.txt (line 5)) (1.16.0)
Requirement already satisfied: tzdata==2024.1 in ./venv/lib/python3.10/site-packages (from -r requirements.txt (line 6)) (2024.1)
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject$
darwin@LAPTOP-MMLBEP53:~/temp/myproject$ git clone git@github.com:heg-web/algopy-darwinamelihearc.git
Cloning into 'algopy-darwinamelihearc'...
remote: Enumerating objects: 27, done.
remote: Counting objects: 100% (27/27), done.
remote: Compressing objects: 100% (24/24), done.
remote: Total 27 (delta 0), reused 23 (delta 0), pack-reused 0
Receiving objects: 100% (27/27), 7.90 KiB | 1.58 MiB/s, done.
darwin@LAPTOP-MMLBEP53:~/temp/myproject$ cd algopy-darwinamelihearc/
darwin@LAPTOP-MMLBEP53:~/temp/myproject/algopy-darwinamelihearc$ source ~/temp/myproject/venv/bin/activate
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject/algopy-darwinamelihearc$ pip install -r requirements.txt
Collecting pytest==7.2.1 (from -r requirements.txt (line 1))
  Downloading pytest-7.2.1-py3-none-any.whl.metadata (7.8 kB)
Collecting pytest-html==3.2.0 (from -r requirements.txt (line 2))
  Downloading pytest_html-3.2.0-py3-none-any.whl.metadata (3.1 kB)
Collecting pytest-json-report==1.5.0 (from -r requirements.txt (line 3))
  Downloading pytest_json_report-1.5.0-py3-none-any.whl (13 kB)
Collecting attrs>=19.2.0 (from pytest==7.2.1->-r requirements.txt (line 1))
  Downloading attrs-23.2.0-py3-none-any.whl.metadata (9.5 kB)
Collecting iniconfig (from pytest==7.2.1->-r requirements.txt (line 1))
  Downloading iniconfig-2.0.0-py3-none-any.whl.metadata (2.6 kB)
Collecting packaging (from pytest==7.2.1->-r requirements.txt (line 1))
  Downloading packaging-23.2-py3-none-any.whl.metadata (3.2 kB)
Collecting pluggy<2.0,>=0.12 (from pytest==7.2.1->-r requirements.txt (line 1))
  Downloading pluggy-1.4.0-py3-none-any.whl.metadata (4.3 kB)
Collecting exceptiongroup>=1.0.0rc8 (from pytest==7.2.1->-r requirements.txt (line 1))
  Downloading exceptiongroup-1.2.0-py3-none-any.whl.metadata (6.6 kB)
Collecting tomli>=1.0.0 (from pytest==7.2.1->-r requirements.txt (line 1))
  Downloading tomli-2.0.1-py3-none-any.whl (12 kB)
Collecting py>=1.8.2 (from pytest-html==3.2.0->-r requirements.txt (line 2))
  Downloading py-1.11.0-py2.py3-none-any.whl (98 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 98.7/98.7 kB 3.3 MB/s eta 0:00:00
Collecting pytest-metadata (from pytest-html==3.2.0->-r requirements.txt (line 2))
  Downloading pytest_metadata-3.1.1-py3-none-any.whl.metadata (8.6 kB)
Downloading pytest-7.2.1-py3-none-any.whl (317 kB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 317.1/317.1 kB 10.7 MB/s eta 0:00:00
Downloading pytest_html-3.2.0-py3-none-any.whl (16 kB)
Downloading attrs-23.2.0-py3-none-any.whl (60 kB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 60.8/60.8 kB 6.8 MB/s eta 0:00:00
Downloading exceptiongroup-1.2.0-py3-none-any.whl (16 kB)
Downloading pluggy-1.4.0-py3-none-any.whl (20 kB)
Downloading iniconfig-2.0.0-py3-none-any.whl (5.9 kB)
Downloading packaging-23.2-py3-none-any.whl (53 kB)
   ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 53.0/53.0 kB 1.6 MB/s eta 0:00:00
Downloading pytest_metadata-3.1.1-py3-none-any.whl (11 kB)
Installing collected packages: tomli, py, pluggy, packaging, iniconfig, exceptiongroup, attrs, pytest, pytest-metadata, pytest-json-report, pytest-html
Successfully installed attrs-23.2.0 exceptiongroup-1.2.0 iniconfig-2.0.0 packaging-23.2 pluggy-1.4.0 py-1.11.0 pytest-7.2.1 pytest-html-3.2.0 pytest-json-report-1.5.0 pytest-metadata-3.1.1 tomli-2.0.1
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject/algopy-darwinamelihearc$
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject/algopy-darwinamelihearc$ git add .
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject/algopy-darwinamelihearc$ git commit -m "add sol"
[main 02fbed8] add sol
 4 files changed, 35 insertions(+), 17 deletions(-)
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject/algopy-darwinamelihearc$ git push
Enumerating objects: 15, done.
Counting objects: 100% (15/15), done.
Delta compression using up to 8 threads
Compressing objects: 100% (7/7), done.
Writing objects: 100% (8/8), 1.18 KiB | 301.00 KiB/s, done.
Total 8 (delta 5), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (5/5), completed with 5 local objects.
To github.com:heg-web/algopy-darwinamelihearc.git
   a3d001d..02fbed8  main -> main
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject/algopy-darwinamelihearc$ pytest
========================================= test session starts ==========================================
platform linux -- Python 3.10.12, pytest-7.2.1, pluggy-1.4.0
rootdir: /home/darwin/temp/myproject/algopy-darwinamelihearc
plugins: html-3.2.0, json-report-1.5.0, metadata-3.1.1
collected 54 items

src/algopy/test/test_chunk_array_in_groups.py .......                                            [ 12%]
src/algopy/test/test_diff_array.py ....                                                          [ 20%]
src/algopy/test/test_find_secret.py ..                                                           [ 24%]
src/algopy/test/test_franken_splice.py ....                                                      [ 31%]
src/algopy/test/test_golf_score.py ...........                                                   [ 51%]
src/algopy/test/test_multiply.py ........                                                        [ 66%]
src/algopy/test/test_my_replace.py ......                                                        [ 77%]
src/algopy/test/test_palindrome.py ............                                                  [100%]

========================================== 54 passed in 0.15s ==========================================
(venv) darwin@LAPTOP-MMLBEP53:~/temp/myproject/algopy-darwinamelihearc$
```
