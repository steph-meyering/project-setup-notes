## Setup

In new project folder

```bash
pipenv install Flask~=1.1 
pipenv install python-dotenv~=0.13 # allows the use of .flaskenv file for enverionment variables
```

```bash
pipenv run flask run # start server
pipenv run flask run -p 5001 # specify port to run on
```
- .flaskenv
```
FLASK_APP=myapp.py
FLASK_ENV=development
SECRET_KEY=super-secret-stuff
```


- config.py
```python
import os


class Config(object):
    GREETING = 'Hey there, humans!'
    SECRET_KEY = os.environ.get('SECRET_KEY') or 'default-key-for-devs'

```


- app.py

```python
from flask import Flask
from config import Config

app = Flask(__name__)

app.config.from_object(Config)
# print("SECRET KEY IS: ", app.config["SECRET_KEY"])


```
