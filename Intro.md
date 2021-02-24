### Dependencies

These distributions will be installed automatically when installing Flask.

- ```Werkzeug``` implements WSGI, the standard Python interface between applications and servers.

- ```Jinja``` is a template language that renders the pages your application serves.

- ```MarkupSafe``` comes with Jinja. It escapes untrusted input when rendering templates to avoid injection attacks.

- ```ItsDangerous``` securely signs data to ensure its integrity. This is used to protect Flask’s session cookie.

- ```Click``` is a framework for writing command line applications. It provides the flask command and allows adding custom management commands.

### Virtual Environment

What problem does a virtual environment solve? The more Python projects you have, the more likely it is that you need to work with different versions of Python libraries, or even Python itself. Newer versions of libraries for one project can break compatibility in another project.

Virtual environments are independent groups of Python libraries, one for each project. Packages installed for one project will not affect other projects or the operating system’s packages.



환경설정을 하면서부터 삽질을 많이 했는데

```python3 -m venv (니가 만들 directory name)```

이렇게 만들면 directory가 본인이 넣은 이름대로 생기는데 그 안에 bin, include, lib 라는 directory들이 생긴다. bin 안에 file들을 대충 살펴보면 activate 라는 file이 보이는데, 걔를 실행시키면 activate 할 수 있다.

가상환경을 activate 하는 마법의 주문은 아래와 같다.

```. (니가 만든 directory 이름)/bin/activate```

보통은 directory 이름을 ```venv```로 한다.

### Install Flask

```pip3 install Flask```

### directory tree

```
/home/user/Projects/flask-tutorial
├── flaskr/
│   ├── __init__.py
│   ├── db.py
│   ├── schema.sql
│   ├── auth.py
│   ├── blog.py
│   ├── templates/
│   │   ├── base.html
│   │   ├── auth/
│   │   │   ├── login.html
│   │   │   └── register.html
│   │   └── blog/
│   │       ├── create.html
│   │       ├── index.html
│   │       └── update.html
│   └── static/
│       └── style.css
├── tests/
│   ├── conftest.py
│   ├── data.sql
│   ├── test_factory.py
│   ├── test_db.py
│   ├── test_auth.py
│   └── test_blog.py
├── venv/
├── setup.py
└── MANIFEST.in
```

- `flaskr/`, a Python package containing your application code and files.

- `tests/`, a directory containing test modules.

- `venv/`, a Python virtual environment where Flask and other dependencies are installed.

### Application Setup

#### A Flask application is an instance of the **Flask class**

Instead of creating a Flask instance globally, you will create it inside a function. This function is known as the **application factory**. Any configuration, registration, and other setup the application needs will happen inside the function, then the application will be returned.

대충 global variable 쓰듯이 하지 말고 함수 내에서 만들라는 뜻, 그것을 application factory라고 하는 것 같다.

### Application Factory

The __init__.py serves double duty: it will contain the application factory, and it tells Python that the flaskr directory should be treated as a package.

```__init__.py```를 꼭 써야하는 이유!

위에 나와있듯이, package로서 기능을 하기 위해서이다.

### Run The Application

```
$ export FLASK_APP=(__init__.py가 들어있는 directory)
$ export FLASK_ENV=development
$ flask run
```
