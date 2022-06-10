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
if __name__ == "__main__":
    app.run(debug=True, port=8000) 

# port is not mandetory, Flask gives us a default port 5000
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
### Render Templates in Flask
- Make a Folder 'Templates'
- Create a HTML file like 'index.html' in it
```bash
@app.route("/Flask-Tutorial")
def Render():
    return render_template('index.html')
```
- Passing Variables in Templates
```bash
def Render():
    name = "Bishnudev Khutia"
    return render_template('index.html',myName = name)
```
### Render Image in Flask
- Make a Static Folder in the main directory
- Put any jpg or png image like 'image.jpg'
```bash
@app.route("/Render-Image")
def RenderImage():
    return render_template('Image.html')
```
## Jinja Template in Flask
- You can reuse Templates with Jinja just like we do in it React JS (Reuse Components).
- Make a "general.html" and add Navbar and Footer in it.
```bash
<!-- Navbar Code -->
    {% block body %} {% endblock body %}
<!-- Footer Code -->
```
- Import it in another file like "index.html"
```bash
{% extends 'general.html' %}
{% block body %}
<!-- Body of "index.html" -->
{% endblock body %}
```
## Connecting to Database with Flask
### SQLite Database in Flask
- Installing The SQLAlchemy Module
```bash
pip install SQLAlchemy
```
- Importing The SQLAlchemy Module
```bash
from flask_sqlalchemy import SQLAlchemy
```
- If We Want to Create a Database Named "todo"
```bash
app.config['SQLALCHEMY_DATABASE_URI'] = "sqlite:///todo.db"
app.config['SQLALCHEMY_TRACK_MODIFICATIONS'] = False
```
- To Create The "todo" Database Hit Below Commands in Your Python Terminal
```bash
python
from python import db
db.create_all()
exit()
```
- Initialize The Database
```bash
db = SQLAlchemy(app)
```
- Creating The Dababase Class & Tables
```bash
class Todo(db.Model):
    sno = db.Column(db.Integer, primary_key=True)
    # Nullable False User Can't Blank This Field
    title = db.Column(db.String(200), nullable=False)
    desc = db.Column(db.String(500), nullable=False)
    date_created = db.Column(db.DateTime, default=datetime.utcnow)
 ```
 - Commiting The Post Request 
 ```bash
 @app.route('/',methods=['GET','POST'])
def todo():
    if request.method == 'POST':
        # todoTitle will the title value from "index.html" which has title name attribute
        todoTitle = request.form['title']
        todoDesc = request.form['desc']
        # Storing The title and desc value from "index.html" to Todo Class
        todo = Todo(title=todoTitle,desc=todoDesc)
        # Storing The values to "todo" DB from Todo Class
        db.session.add(todo)
        # Pushing The Data
        db.session.commit()
    return render_template('index.html',allTodo = allTodo)
 ```
 - In HTML Set Method to Post and Action to it's Path
 ```bash
 <form class="container my-4" method="POST" action="/">
<!-- Form Body -->
 </form>
 ```
