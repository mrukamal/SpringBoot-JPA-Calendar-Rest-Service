# SpringBoot-JPA-Calendar-Rest-Service
Spring Boot JPA project that lets users create calendar events using a REST API.

Contents
* 	Eclipse Project
* 	All dependencies included in pom.xml
* 	The included project can be run using the built in H2 database (NO external database driver such as MySQL, SQL Server, and Oracle required!)

Required
* 	Eclipse Photon (or any Eclipse flavor that allows Java EE and Spring Boot projects)
* 	Maven.

Installation and setup
* 	In the Eclipse IDE, import the attached project as a Maven project.
* 	The included pom.xml will download and setup all dependencies.
* 	Once download is complete, run the project by right clicking and selecting either Run As or Debug As and selecting "Spring Boot App"
* 	Once the project is running in Eclipse, use a tool like Google Postman to call the API and create calendar and events.
* 	Once the project is running in Eclipse, the local (in memory) H2 database can be browsed using: http://localhost:8080/h2-console
* 	On the H2 Console leave all settings unchanged and ensure the JDBC URL is: jdbc:h2:mem:testdb
* 	Username and password are sa/sa (password can be left blank)

Sample API calls from Google Postman
Note: The API uses JSON as request body for any request allowed through it.

- Search calendar events using date range
Method: POST
URL: http://localhost:8080/v1/calendars/search
Request:
{
    "startDateTime": "2018-07-01 00:00:00",
    "endDateTime": "2018-07-04 00:00:00"
}

- Create a calendar
Method: POST
URL: http://localhost:8080/v1/calendars/add
Request:
{
    "name": "Calendar345",
    "user": {
        "id": 1,
        "name": "Uk1"
    },
    "events": [
        {
            "title": "event1",
            "eventDateTime": "2018-07-01 00:00:00",
            "location": "event location 1",
            "attendees": null,
            "reminderDateTime": null,
            "reminderSent": true
        },
        {
            "title": "event2",
            "eventDateTime": "2018-07-04 00:00:00",
            "location": "event location 2",
            "attendees": null,
            "reminderDateTime": null,
            "reminderSent": false
        },
        {
            "title": "event3",
            "eventDateTime": "2018-07-20 00:00:00",
            "location": "event location 3",
            "attendees": null,
            "reminderDateTime": null,
            "reminderSent": false
        }
    ]
}

- Retrieve all calendars
Method: GET
URL: http://localhost:8080/v1/calendars
Request (empty)
{
}
