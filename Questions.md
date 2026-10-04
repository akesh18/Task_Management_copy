## Did you use ChatGPT/AI to build this?
**Ans:** Yes, I used AI tools as a development assistant for faster debugging and understanding error logs, just like referencing documentation. But I made sure to understand the root cause of the schemas and authentication flow myself before implementing the fix.

## What does this project does?
**Ans:** In this project, a user can create their account then create their tasks inside that account. They can add, edit and delete their tasks. They can also delete their account if they want.
- There is also a "Admin" role who can view usernames of all the registered users and how many tasks they have created. But, obviously for privacy reason the admin can't see the contents of their tasks.
The admin can also delete accounts of users.

## Features of this project:
- User can create, edit and delete tasks in their account and they can also delete their account.
  
- Before deleting a account by user or admin, a confirmation gets asked so that user account doesn't accidently gets deleted.
  
- After a task gets deleted, it moves to recycle bin before getting permanently deleted so that user doesn't accidently deletes a task.
  
- Admin can view registered usernames and how many tasks each have created and can delete any user account.

- It is ensured that every username should remain unique and no username should be repeated.
  
- No user can create account with "admin" username and there is a seperate login page for admin and admin can't login from user login page.

## Can you walk me through the high-level architecture of your project?

Here are 5 common ways interviewers ask the exact same high-level architecture question:

1. **"How does data flow in your application from the frontend to the database?"**
*(They want you to trace a user request from UI click $\rightarrow$ API $\rightarrow$ validation $\rightarrow$ DB $\rightarrow$ response.)*

2. **"Can you explain the design and component breakdown of this system?"**
*(They want to hear about the moving parts: UI layer, FastAPI backend, database, and auth layer.)*

3. **"If you had a whiteboard right now, how would you sketch out this project?"**
*(They are testing if you can visualize the blocks and the communication lines between them.)*

4. **"Walk me through the overall tech stack and how these pieces communicate with each other."**
*(They want the technologies named alongside the protocol connecting them, like REST/HTTP).*

5. **"What happens under the hood when a user clicks 'Create Task' on the screen?"**
*(A scenario-based trigger asking for the exact same end-to-end architecture story.)*

**Ans:** My project follows a standard client-server architecture. The frontend is built with responsive HTML and Tailwind CSS, communicating via HTTP requests with a FastAPI backend server hosted on Render.

The backend exposes RESTful endpoints, handles data validation using Pydantic, and enforces security through JWT authentication. Finally, it interacts with a cloud-hosted PostgreSQL database on Render using SQLAlchemy to securely execute CRUD operations.

**Client-Server Architecture:** A system design split into two parts: the **client** (the user's browser/UI) that requests data, and the **server** (backend and database) that processes the logic and returns the response.

**Responsive HTML:** Web page structure designed to automatically adjust its layout, elements, and sizing to look good and function properly on any screen size, from mobile phones to desktops.
  
**HTTP Requests:** Standardized messages sent by the client to the server over the internet using methods like `GET` to fetch data, `POST` to save data, `PUT` to update data and `DELETE` to remove data.

**FastAPI** is a modern, high-performance Python web framework for building RESTful APIs. It provides native asynchronous support (i.e. `async`/`await`) for handling concurrent requests, uses Pydantic for automatic data validation, and auto-generates interactive Swagger documentation out of the box.

*Asynchronous Support:* The ability of the server to process other incoming user requests while waiting for slow operations (like database read/write) to finish, preventing the app from freezing.

*Swagger documentation* is an auto-generated, interactive web UI (at /docs) that lists all API endpoints, models, and parameters, letting developers test requests directly from the browser.
  
**RESTful Endpoints:** Specific web URLs exposed by the backend API (such as `/api/tasks`) that follow REST architectural rules to perform operations on resources using standard HTTP methods.

### **Restful API**

You already know that, **API** (Application programming Interface) is a set of rules and protocols that lets different software applications communicate with each other.

**Restful API** is a API that follows REST(Representational State Transfer) architectural rules and standard HTTP methods.

In practice, following REST architectural rules means:

- **Resource-Based URLs:** Endpoints represent objects (nouns), not actions—for example, `/tasks`, not `/getTasks` or `/deleteTask`.
  
- **Standard HTTP Methods:** Actions are performed using standard HTTP methods:
- `GET` (fetches/read data)
- `POST` (creates data)
- `PUT` / `PATCH` (updates data)
- `DELETE` (removes data)

- **Statelessness:** The server never stores client session state between requests. Every request carries all required data (such as the JWT token in headers) to complete the action.
  
- **Standard Representation:** Resources are exchanged in a standard data format, usually **JSON**.

**Pydantic** is a data validation and parsing library for Python. In my project, it defines schemas to validate incoming request data—like task titles and user credentials. It ensures the inputs match expected types, rejects invalid requests with automatic 422 errors, and formats outgoing data into clean JSON.

**SQLAlchemy** is an Object-Relational Mapping (ORM) library for Python. In my project, it connects FastAPI to PostgreSQL. Instead of writing raw SQL queries, I define tables as Python classes. SQLAlchemy translates my Python code into database commands to execute secure CRUD operations and manage transactions smoothly.

**ORM (Object-Relational Mapping)** is a programming technique that connects object-oriented code with relational databases. It maps database tables to programming classes and rows to objects, enabling developers to query, insert, and update data using native code without writing raw SQL.

**OAuth2** is an industry-standard authorization framework. It allows applications to securely access user resources using scoped access tokens (like JWTs) without exposing raw user credentials on every request.

A **JSON Web Token (JWT)** is a compact, URL-safe token used for stateless authentication. It consists of three dot-separated Base64Url-encoded parts: the **Header** (algorithm), the **Payload** (user claims and expiry), and the **Signature** (verifies token integrity).

## What is the tech stack used in this project?
**Ans:** The tech stack used in this project are:

* For **backend**, FastAPI which is python web framework 

* For **Database** PostgreSQL on render.com & for ORM (Object-Relational Mapping) SQLAlchemy is getting used. 
  
* For **Data Validation**, Pydantic which is Python data validation and parsing library
  
* For **Authentication & Security**, OAuth2 with JWT tokens and Bcrypt password hashing

* For **Frontend**, HTML5, Vanilla JavaScript and Tailwind CSS
  
* For **Server**, Uvicorn (ASGI)

*Bcrypt* is a method that scrambles plain passwords into a one-way secure code before saving them in the database. It adds random data (salt) to stop hackers from guessing or decrypting passwords.

A *server* handles network requests and returns responses; *Uvicorn* is the lightning-fast ASGI web server that runs FastAPI applications asynchronously to handle concurrent traffic.

## Why you have choosen this technology for your project?
**Ans:** - I chose **FastAPI** and **PostgreSQL** because their native async support and robust relational integrity handle concurrent operations efficiently. 

- **JWT and Bcrypt** provide industry-standard authentication without server overhead. 
 
- **Tailwind CSS** enabled rapid, lightweight responsive UI development, while 

- **Render** offered seamless, zero-config automated CI/CD directly from GitHub.
  
**Terms used above:**
  
- **Relational Integrity:** Rules in a database (like Foreign Keys) that keep data accurate and consistent—for example, ensuring a task cannot belong to a non-existent user.
  
- **Server Overhead:** Extra load, memory, or CPU usage placed on the server—like having to store and manage thousands of active user sessions in server RAM.
  
- **Zero-Config:** Setting up or deploying a service without writing complex build scripts, server configs, or Docker files; the platform detects your setup and runs it automatically.

## GitHub pe kaise upload kiya?

```
1> git init
- (Configured .gitignore file)
2> git add .
3> git commit -m "Commit Message"
4> git branch -M main
5> git remote add origin https://github.com/username/repo-name.git
6> git push -u origin main
```

- First I opened "Git Bash" in my local project directory, then I initialized Git using `git init`
  command. 
   
- Then I configured `.gitigonre` in my folder to exclude unnecessary files like `__pycache__`, virtual environment and `.db` files. 

- Then I staged (ready to upload) all files in my current folder using `git add .`
  (Here, `.` means all files of current folder).

- Then I created a save point of all my staged files using command 
  `git commit -m "Commit Message"`

- Then I changed my current branch name to "main" using command
  `git branch -M main`
  
- Then I created a empty repositry on Github and linked my local project folder with that repositry 
  using command `git remote add origin <repo-url>` 

- Finally, I pushed my entire codebase to Github using command `git push -u origin main`.
  (`-u` - This is upstream flag that binds your local "main" branch with remote "main" branch on github, that's why for subsequent updates you only need to write `git push` command on your Git Bash).

## Render pe kaise deploy kiya?

1. First I went to render.com then signed up with my github account, then from Render Dashboard I     created a new **Web Service** and since I signed up with my github account, all my repositiries starts showing up there so I selected the "Task_Manager" repositry that i had to deploy.
  
2. Then I setted up the configuration settings:
- I entered **Build Command:** `pip install -r requirements.txt` to install all the dependencies that are required to run my project.

- And entered **Start Command:** `uvicorn app.main:app --host 0.0.0.0 --port $PORT` to run the production server.
 
3. Then for database, I setted up **PostgreSQL instance** and then pasted it's connection string
   into Web Service **Environment Varables** `DATABASE_URL` field.

4. Then finally I deployed the webservice. Render automatically run my project build and my website got live. As Continous Deployment is enabled on render so with every new Github Push, render automatically deploys my updated code. 

## How registration and login are working in this web application (while maintaining security)?

**Ans:** In this application, authentication is handled using **FastAPI, OAuth2, and JWT tokens**:

1. **Registration (`/signup`)**:
* The client sends the `username` and `password`.
* Input is validated via **Pydantic** schemas.
* The backend hashes the plain password using **Bcrypt** and added some salt (extra characters that are not in the original password) in it for security and saves the new user record into the database with a default non-admin role.

2. **Login (`/login`)**:
* The user submits their credentials.
* The backend queries the user from the database and verifies the incoming plain password against the stored hash using Bcrypt.
* If valid, it generates a signed **JWT Access Token** with an expiration time, encoding the user's identity.

3. **Protected Routes & Session**:
* For subsequent requests, the frontend includes this token in the `Authorization: Bearer <token>` header.
* FastAPI's dependency injection (`get_current_user`) decodes and verifies the token on protected routes (like CRUD operations and admin views) to authenticate and authorize the user.
  
**Terms description used above:**
  
* **`Authorization: Bearer <token>` Header**: It is an HTTP request header used to authenticate the client. The prefix `Bearer` indicates that the sender holds an access token (like a JWT) granting protected resource access.

In FastAPI, **Dependency Injection** uses `Depends()` to automatically plug shared tools—like a database connection or user authentication—directly into your API functions. Instead of writing the same setup code repeatedly, FastAPI manages it for you, keeping endpoints clean, modular, and easy to test.

## How are CRUD operations and data validation handled in FastAPI?
**Ans:** CRUD routes use standard HTTP methods (GET, POST, PUT, DELETE). Pydantic schemas automatically validate incoming request data types and reject invalid inputs with a 422 Unprocessable Entity error before saving them to the database.

## How does deployment and CI/CD work on Render?
**Ans:** My GitHub repository is linked directly to Render. Every git push to main triggers an automatic build (pip install -r requirements.txt) and starts the server via uvicorn, securely connecting to a hosted PostgreSQL database using a DATABASE_URL environment variable.

## Can we check/retrieve information using POST instead of GET?
**Ans:**
Yes, technically we can. While **GET** is the standard HTTP method for retrieving data, **POST** is often used when query parameters are too large for URL limits or contain sensitive credentials that shouldn't appear in browser history, logs, or URLs, such as complex search filters or authentication checks.

## What is the diffrence between Authentication and Authorization?

**Authentication** verifies **who you are** by checking your identity, whereas **authorization** determines **what you are allowed to do** by verifying your permissions. Authentication always takes place first; authorization follows once your identity is confirmed.

**Example:**

Logging into a company portal using your corporate username and password is **authentication**. Once logged in, a regular employee viewing payroll data gets blocked while HR can edit it—that access control decision is **authorization**.

## How "admin" role is working in your project?
i.e. How "admin" is able to view all the registered users, number of tasks created by them and delete
user account?
**Ans:**
I implemented Role-Based Access Control using FastAPI dependencies. When a user logs in, their role is encoded into the JWT. For admin endpoints, a dependency verifies the token and checks the admin flag. Then, SQLAlchemy executes aggregate queries to fetch all users with their task counts and safely handles user deletion.