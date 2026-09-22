#### Did you use ChatGPT/AI to build this?
**Ans:** Yes, I used AI tools as a development assistant for faster debugging and understanding error logs, just like referencing documentation. But I made sure to understand the root cause of the schemas and authentication flow myself before implementing the fix.

### What does this project does?
**Ans:** In this project, a user can create their account then create their tasks inside that account. They can add, edit and delete their tasks. They can also delete their account if they want.
- There is also a "Admin" role who can view usernames of all the registered users and how many tasks they have created. But, obviously for privacy reason the admin can't see the contents of their tasks.
The admin can also delete accounts of users.

### Features of this project:
- User can create, edit and delete tasks in their account and they can also delete their account.
  
- Before deleting a account by user or admin, a confirmation gets asked so that user account doesn't accidently gets deleted.
  
- After a task gets deleted, it moves to recycle bin before getting permanently deleted so that user doesn't accidently deletes a task.
  
- Admin can view registered usernames and how many tasks each have created and can delete any user account.

- It is ensured that every username should remain unique and no username should be repeated.
  
- No user can create account with "admin" username and there is a seperate login page for admin and admin can't login from user login page.

### Can you walk me through the high-level architecture of your project?

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

The backend exposes RESTful endpoints, handles data validation using Pydantic, and enforces security through JWT authentication. Finally, it interacts with a cloud-hosted PostgreSQL database using SQLAlchemy to securely execute CRUD operations and manage persistent data transactions.

- **Client-Server Architecture:** A system design split into two parts: the **client** (the user's browser/UI) that requests data, and the **server** (backend and database) that processes the logic and returns the response.

- **Responsive HTML:** Web page structure designed to automatically adjust its layout, elements, and sizing to look good and function properly on any screen size, from mobile phones to desktops.
  
- **HTTP Requests:** Standardized messages sent by the client to the server over the internet (using methods like `GET`, `POST`, `PUT`, or `DELETE`) to fetch, send, update, or remove data.
  
- **RESTful Endpoints:** Specific web URLs exposed by the backend API (such as `/api/tasks`) that follow REST architectural rules to perform operations on resources using standard HTTP methods.

#### **Restful API**

You already know that, **API** (Application programming Interface) is a set of rules and protocols that lets different software applications communicate with each other.

**Restful API** is a API that follows REST(Representational State Transfer) architectural rules and standard HTTP methods.

**REST architectural rules** are a set of standard design guidelines that ensure APIs communicate predictably and efficiently.

In practice, following REST means:

- **Resource-Based URLs:** Endpoints represent objects (nouns), not actions—for example, `/tasks`, not `/getTasks` or `/deleteTask`.
  
- **Standard HTTP Verbs:** Actions are performed using standard HTTP methods:
- `GET` (fetches/read data)
- `POST` (creates data)
- `PUT` / `PATCH` (updates data)
- `DELETE` (removes data)

- **Statelessness:** The server never stores client session state between requests. Every request carries all required data (such as the JWT token in headers) to complete the action.
  
- **Standard Representation:** Resources are exchanged in a standard data format, usually **JSON**.

### What is the tech stack used in this project?
**Ans:** The tech stack used in this project are:

* For **backend**, FastAPI which is python web framework 

* For **Database** PostgreSQL on render.com & for ORM (Object-Relational Mapping) SQLAlchemy is getting used. 
  
* For **Data Validation**, Pydantic which is Python data validation and parsing library
  
* For **Authentication & Security**, OAuth2 with JWT tokens (`python-jose`) and Bcrypt password hashing (`passlib`)

* For **Frontend**, HTML5, Vanilla JavaScript and Tailwind CSS
  
* For **Server**, Uvicorn (ASGI)
  
### What is ORM (Object-Relational Mapping) ?
**Ans:** ORM (Object-Relational Mapping) is a programming technique that connects object-oriented code with relational databases. It maps database tables to programming classes and rows to objects, enabling developers to query, insert, and update data using native code without writing raw SQL.

### Why you have choosen this technology for your project?
**Ans:** - I chose **FastAPI** and **PostgreSQL** because their native async support and robust relational integrity handle concurrent operations efficiently. 

- **JWT and Bcrypt** provide industry-standard authentication without server overhead. 
 
- **Tailwind CSS** enabled rapid, lightweight responsive UI development, while 

- **Render** offered seamless, zero-config automated CI/CD directly from GitHub.
  
**Terms used above:**
- **Async Support:** The ability of the server to process other incoming user requests while waiting for slow operations (like database read/write) to finish, preventing the app from freezing.
  
- **Relational Integrity:** Rules in a database (like Foreign Keys) that keep data accurate and consistent—for example, ensuring a task cannot belong to a non-existent user.
  
- **Server Overhead:** Extra load, memory, or CPU usage placed on the server—like having to store and manage thousands of active user sessions in server RAM.
  
- **Zero-Config:** Setting up or deploying a service without writing complex build scripts, server configs, or Docker files; the platform detects your setup and runs it automatically.

### GitHub pe kaise upload kiya?

- "Maine local project directory mein Git initialize kiya using `git init`. 
- Unnecessary files (jaise `__pycache__`, virtual environment, aur `.db` files) ko exclude karne ke liye `.gitignore` configure kiya. 
- Uske baad saari source files ko stage kiya (`git add .`), initial commit create kiya (`git commit -m 'Initial commit'`), aur 
- GitHub par remote repository create karke local repo ko link kiya (`git remote add origin <repo-url>`). 
- Finally, `git push -u origin main` command se pura codebase GitHub par push kar diya.

### Render pe kaise deploy kiya?

1. Render Dashboard par jaakar naya **Web Service** create kiya aur apne GitHub repository ko link kiya.
  
2. Configuration settings set kiye:
* **Build Command:** `pip install -r requirements.txt` (dependencies install karne ke liye joh project ko run karne ke liye chahiye).

* **Start Command:** `uvicorn app.main:app --host 0.0.0.0 --port $PORT` (production server run karne ke liye).
 
3. Database ke liye Render par **PostgreSQL instance** setup kiya aur uska connection string web service ke **Environment Variables** mein `DATABASE_URL` ke taur par paste kiya.

4. Deploy trigger hote hi Render ne automated build run kiya aur service live ho gayi. Continuous deployment enable hone ki wajah se GitHub ke har push par yeh automatically redeploy ho jata hai."

### How registration and login are working in this web application?

**Ans:** In this application, authentication is handled using **FastAPI, OAuth2, and JWT tokens**:

1. **Registration (`/signup`)**:
* The client sends the `username` and `password`.
* Input is validated via **Pydantic** schemas.
* The backend hashes the plain password using **Bcrypt** (`passlib`) for security and saves the new user record into the database with a default non-admin role.

2. **Login (`/login`)**:
* The user submits their credentials.
* The backend queries the user from the database and verifies the incoming plain password against the stored hash using Bcrypt.
* If valid, it generates a signed **JWT Access Token** (using `python-jose`) with an expiration time, encoding the user's identity.

3. **Protected Routes & Session**:
* For subsequent requests, the frontend includes this token in the `Authorization: Bearer <token>` header.
* FastAPI's dependency injection (`get_current_user`) decodes and verifies the token on protected routes (like CRUD operations and admin views) to authenticate and authorize the user.
  
**Terms description used above:**

* **OAuth2**: Ek open-standard authorization framework/protocol hai jo define karta hai ki secure login aur token exchange ka flow kaise hona chahiye. FastAPI mein `OAuth2PasswordBearer` client se token extract karne ka standard tareeka provide karta hai.
  
* **JWT (JSON Web Token)**: Ek digitally signed, compact string hoti hai jisme user ki identity (jaise `username`, expiry time) securely encoded rehti hai. Client login ke baad ise save karta hai taaki baar-baar password na bhejna pade.

* **Bcrypt (`passlib`)**: Ek strong cryptographic password-hashing algorithm (aur Python library) hai. Yeh plain text password ko one-way encrypted hash mein convert karta hai aur salt add karta hai, taaki database leak hone par bhi original password reveal na ho sake.
  
* **`python-jose`**: Python ki ek library hai jo backend par JWT tokens ko generate (encode/sign) karne aur incoming requests par unhe verify (decode) karne ka kaam karti hai.
  
* **`Authorization: Bearer <token>` Header**: HTTP request ka ek metadata header. Jab frontend kisi protected endpoint (jaise tasks create karna) ko call karta hai, toh woh server ko proof dene ke liye JWT token ko is header format mein bhejta hai; server verify karta hai ki request authenticated user ki taraf se hai ya nahi.

### How are CRUD operations and data validation handled in FastAPI?
**Ans:** CRUD routes use standard HTTP methods (GET, POST, PUT, DELETE). Pydantic schemas automatically validate incoming request data types and reject invalid inputs with a 422 Unprocessable Entity error before saving them to the database.

### How does deployment and CI/CD work on Render?
**Ans:** My GitHub repository is linked directly to Render. Every git push to main triggers an automatic build (pip install -r requirements.txt) and starts the server via uvicorn, securely connecting to a hosted PostgreSQL database using a DATABASE_URL environment variable.