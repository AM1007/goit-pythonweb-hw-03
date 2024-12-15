# Web Basics: Building a Simple HTTP Server

## Your goal is to implement the simplest web application.

### Technical task description:

Create a web application with routing for two HTML pages: `index.html` and `message.html`.

**Additionally:**

- Handle static resources such as `style.css` and `logo.png`.
- Implement functionality for working with a form on the `message.html` page.
- In the event of a `404 Not Found` error, return an `error.html` page.
- Your application should run on port `3000`.

When working with the form, the received byte string should be converted into a dictionary and stored in a JSON file, `data.json`, located in the `storage` directory.

The format for storing the `data.json` file is as follows:

```json
{
  "2022-10-29 20:20:58.020261": {
    "username": "krabaton",
    "message": "First message"
  },
  "2022-10-29 20:21:11.812177": {
    "username": "Krabat",
    "message": "Second message"
  }
}
```

Each message's key should be the time the message was received `datetime.now()`, meaning every new message from the web application is appended to the `storage/data.json` file along with the time it was received.

Add a route, `/read`, which generates an informational page. This page should use a Jinja2 template and display all saved notifications from the `data.json` file.

- Create a `Dockerfile` and run your application as a Docker container.
- Use the `volumes` mechanism to store the `storage/data.json` file outside the container.

#### Key requirements:

**1. Routing:**

- Two HTML pages are created: `index.html` and `message.html`.
- Static resources (e.g., `style.css` and `logo.png`) are handled appropriately.
- The web application runs on port 3000.

**2. Form handling:**

- The form on the `message.html` page works correctly and sends data (e.g., username and message).
- Data from the form is converted into a dictionary and written to the `data.json` file in the following format:

```json
{
  "%timestamp%": {
    "username": "example",
    "message": "example message"
  }
}
```

**3. The /read route:**

- When accessed, it returns a Jinja2 template-based page displaying all stored messages from the `data.json` file.

**4. Error handling:**

- If a 404 error occurs, an `error.html` page is returned.

**5. Message storage:**

- Messages are stored in the `storage/data.json` file in JSON format, where the key is the message's receipt time.

**6. Docker:**

- A Dockerfile is created to run the application as a Docker container.
- The volumes mechanism is used to ensure the `data.json` file is stored outside the container.
