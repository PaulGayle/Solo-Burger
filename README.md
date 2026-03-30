🔐 Flask Authentication App

A simple authentication system built with Flask that allows users to register, log in, access a protected dashboard, and log out.

This project is designed as a beginner-friendly foundation for learning how authentication works in web applications.

📌 Features
User Registration
User Login
Session Management
Protected Dashboard
Logout Functionality
SQLite Database (auto-created)
🛠️ Technologies Used
Python
Flask
SQLite
HTML/CSS
📁 Project Structure
flask_auth_app/
│
├── app.py
├── users.db
├── requirements.txt
└── templates/
    ├── layout.html
    ├── login.html
    ├── register.html
    └── dashboard.html
⚙️ Installation
1. Clone the Repository
git clone https://github.com/your-username/flask-auth-app.git
cd flask-auth-app
2. Create a Virtual Environment (Recommended)
python -m venv venv

Activate it:

Windows (PowerShell):

venv\Scripts\activate

Mac/Linux:

source venv/bin/activate
3. Install Requirements

If you don’t have a requirements.txt, create one with:

flask

Then install:

pip install -r requirements.txt
▶️ Running the Application
python app.py

Then open your browser and go to:

http://127.0.0.1:5000


Comprehension questions
Q1. What does @app.route('/login', methods=['GET', 'POST']) do? Why both methods?”
   @app.route('/login', methods=['GET', 'POST']) is a Flask route decorator that tells your app:

“When someone goes to /login, run this function—and allow both GET and POST requests.”

🔹 What it does
@app.route('/login') → maps the URL /login to a specific Python function (your login view).
methods=['GET', 'POST'] → allows that route to handle both types of HTTP requests.
🔹 Why use BOTH GET and POST?

Because login pages typically need to do two different things:

1. GET request (when user first visits the page)
Happens when you go to /login in the browser.
The server returns the login form (HTML page).

2. POST request (when user submits the form)
Happens when the user clicks “Login”.
The browser sends form data (username/password) to the server.
The server processes it (checks credentials).

Q2. “Walk me through what happens from the moment a user clicks ‘Login’ to when they see the dashboard.”
    🔹 1. User fills out the form

On your login.html page
The key part is method="POST"
When the user clicks Login, the browser prepares to send data to the server
🔹 2. Browser sends a POST request

When the button is clicked:
The browser sends an HTTP POST request to /login
It includes the form data:

🔹 3. Flask route receives the request
@app.route('/login', methods=['GET', 'POST'])
def login():
Flask sees:
URL = /login
Method = POST
So it runs this function
🔹 4. Your code checks the request method
if request.method == 'POST':
Since this is a form submission, it enters the POST block
🔹 5. Extract form data
username = request.form['username']
password = request.form['password']
Flask pulls the data sent from the browser
🔹 6. Validate the user

This is where you check credentials:
if username == "admin" and password == "1234":
In real apps:
You check a database
Compare hashed passwords
🔹 7. Create a session (log the user in)
session['user'] = username
Flask stores user info in a session
This is how the app remembers the user is logged in
🔹 8. Redirect to dashboard
return redirect(url_for('dashboard'))

Flask sends a response telling the browser:

“Go to /dashboard instead”

🔹 9. Browser makes a new GET request

Now the browser:

Automatically sends a GET request to /dashboard
🔹 10. Dashboard route runs
@app.route('/dashboard')
def dashboard():
    if 'user' in session:
        return render_template('dashboard.html')
    else:
        return redirect(url_for('login'))
Flask checks if the user is logged in via session
If yes → show dashboard
If no → send them back to login
🔹 11. Dashboard is displayed
Flask returns dashboard.html
The browser renders it
✅ User sees the dashboard
