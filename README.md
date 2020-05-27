# Back-End
For back end Node/Java Devs


BW SiTC Back End
Overview

School in The Cloud is a full-stack web application that was built during a "build week" by Lambda School students. Each student fulfills a role in the project to collectively build the application.
Authentication

Users are authenticated via JSON Web Tokens
Error Codes

400, 404, 401, 500
Rate limit

There should not be a rate limit unless Postgres or Heroku set one themselves

Server
GET Base URL
localhost:6660


Example Request
Default

GET / HTTP/1.1
Host: localhost:6660


API
GET /api
localhost:6660/api


Example Request
/api

GET /api HTTP/1.1
Host: localhost:6660


Student
POST /register
localhost:6660/api/student/register

add a new student to the database
BODY raw

{
	"username": "peruStu",
	"password": "test",
	"forename": "Estaban",
	"surname": "Julio Roberto Montoya Dela Rosa Ramirez",
	"country": "Peru",
	"volunteerId": 4
}



Example Request
/register

POST /api/student/register HTTP/1.1
Host: localhost:6660


{
	"username": "peruStu",
	"password": "test",
	"forename": "Estaban",
	"surname": "Julio Roberto Montoya Dela Rosa Ramirez",
	"country": "Peru",
	"volunteerId": 4
}

POST /login
localhost:6660/api/student/login

obtain an authorization token using student credentials
BODY raw

{
	"username": "peruStu",
	"password":"test"
}



Example Request
/login

POST /api/student/login HTTP/1.1
Host: localhost:6660


{
	"username": "peruStu",
	"password":"test"
}

GET /users
localhost:6660/api/student/users/

While authenticated, retrieve a lists of all students and the teachers above them
HEADERS
authorization
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWJqZWN0Ijo3LCJ1c2VybmFtZSI6InBlcnVTdHUiLCJuYW1lIjoiRXN0YWJhbiBKdWxpbyBSb2JlcnRvIE1vbnRveWEgRGVsYSBSb3NhIFJhbWlyZXoiLCJjb3VudHJ5IjoiUGVydSIsImlhdCI6MTU5MDUyMzQxNSwiZXhwIjoxNTkwNjA5ODE1fQ.xcmDW9q-joCb7mA6fQim_3WV_0OmdGTM7TIcK36bGm4


Example Request
/users

GET /api/student/users/ HTTP/1.1
Host: localhost:6660
authorization: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWJqZWN0Ijo3LCJ1c2VybmFtZSI6InBlcnVTdHUiLCJuYW1lIjoiRXN0YWJhbiBKdWxpbyBSb2JlcnRvIE1vbnRveWEgRGVsYSBSb3NhIFJhbWlyZXoiLCJjb3VudHJ5IjoiUGVydSIsImlhdCI6MTU5MDUyMzQxNSwiZXhwIjoxNTkwNjA5ODE1fQ.xcmDW9q-joCb7mA6fQim_3WV_0OmdGTM7TIcK36bGm4

GET /profile
localhost:6660/api/student/profile/

while authenticated, get user specific information
HEADERS
authorization
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWJqZWN0Ijo3LCJ1c2VybmFtZSI6InBlcnVTdHUiLCJuYW1lIjoiRGlubyBNdXJhdG92aWMiLCJjb3VudHJ5IjoiU3BhaW4iLCJpYXQiOjE1OTA2MDg0OTgsImV4cCI6MTU5MDY5NDg5OH0.AhGd3Y5ZdZF2rSmUIYgBB08kH8PjjHZ7t8N2cwZLmuI
BODY raw

{
	"forename": "Dino",
	"surname": "Muratovic",
	"country": "Spain"
}



Example Request
/profile

GET /api/student/profile/ HTTP/1.1
Host: localhost:6660
authorization: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWJqZWN0Ijo3LCJ1c2VybmFtZSI6InBlcnVTdHUiLCJuYW1lIjoiRGlubyBNdXJhdG92aWMiLCJjb3VudHJ5IjoiU3BhaW4iLCJpYXQiOjE1OTA2MDg0OTgsImV4cCI6MTU5MDY5NDg5OH0.AhGd3Y5ZdZF2rSmUIYgBB08kH8PjjHZ7t8N2cwZLmuI

{
	"forename": "Dino",
	"surname": "Muratovic",
	"country": "Spain"
}

GET /profile/country
localhost:6660/api/student/profile/country

while authenticated, retrieve a list of students who share a country with user, including the user themself
HEADERS
authorization
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWJqZWN0Ijo3LCJ1c2VybmFtZSI6InBlcnVTdHUiLCJuYW1lIjoiRGlubyBNdXJhdG92aWMiLCJjb3VudHJ5IjoiU3BhaW4iLCJpYXQiOjE1OTA2MDg0OTgsImV4cCI6MTU5MDY5NDg5OH0.AhGd3Y5ZdZF2rSmUIYgBB08kH8PjjHZ7t8N2cwZLmuI


Example Request
/profile/country

GET /api/student/profile/country HTTP/1.1
Host: localhost:6660
authorization: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWJqZWN0Ijo3LCJ1c2VybmFtZSI6InBlcnVTdHUiLCJuYW1lIjoiRGlubyBNdXJhdG92aWMiLCJjb3VudHJ5IjoiU3BhaW4iLCJpYXQiOjE1OTA2MDg0OTgsImV4cCI6MTU5MDY5NDg5OH0.AhGd3Y5ZdZF2rSmUIYgBB08kH8PjjHZ7t8N2cwZLmuI

PUT /profile/edit
localhost:6660/api/student/profile/edit

edit minor information about the user
HEADERS
authorization
eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWJqZWN0Ijo3LCJ1c2VybmFtZSI6InBlcnVTdHUiLCJuYW1lIjoiRGlubyBNdXJhdG92aWMiLCJjb3VudHJ5IjoiU3BhaW4iLCJpYXQiOjE1OTA2MDg0OTgsImV4cCI6MTU5MDY5NDg5OH0.AhGd3Y5ZdZF2rSmUIYgBB08kH8PjjHZ7t8N2cwZLmuI
BODY raw

{
	"forename": "Dino",
	"surname": "Muratovic",
	"country": "Spain"
}



Example Request
/profile/edit

PUT /api/student/profile/edit HTTP/1.1
Host: localhost:6660
authorization: eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWJqZWN0Ijo3LCJ1c2VybmFtZSI6InBlcnVTdHUiLCJuYW1lIjoiRGlubyBNdXJhdG92aWMiLCJjb3VudHJ5IjoiU3BhaW4iLCJpYXQiOjE1OTA2MDg0OTgsImV4cCI6MTU5MDY5NDg5OH0.AhGd3Y5ZdZF2rSmUIYgBB08kH8PjjHZ7t8N2cwZLmuI

{
	"forename": "Dino",
	"surname": "Muratovic",
	"country": "Spain"
}

BW SiTC Back End

    Introduction
        Overview
        Authentication
        Error Codes
        Rate limit
    Server
    API
    Student

