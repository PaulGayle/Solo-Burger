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
