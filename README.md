# webdev-with-flask
Flask Documentation For Web Apps

## Creating Our First Flask App

- Import Flask Package
```bash
from flask import Flask
```
- Initialize Flask Package
```bash
app = Flask(__name__)
```
- Setting The Route
```bash
@app.route("/")
```
- Creating The Content
```bash
def Hello():
    return 'This is a Flask App'
```
- Run The Server
```bash
app.run()
```
