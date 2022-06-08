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
### Basic Static Site With Flask
```bash

from flask import Flask

app = Flask(__name__)

@app.route("/")
def Home():
    return 'This is Homepage'

@app.route("/About")
def About():
    return 'This is About Section'

@app.route("/Services")
def Service():
    return 'We Provide Following Services in Our Website'

app.run(debug=True)

# debug=True detects any change in code and restart the server automatically just like nodemon in Node and Express JS
```
