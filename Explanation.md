## Folder Structre

**Task_Managment_app**
|-----------------*git/*
                    |
|-----------------*app/*
                    |---*__pycache__/*
                    |---__init__.py (typed)
                    |---auth.py (typed)
                    |---database.py (typed)
                    |---main.py (typed)
                    |---models.py (typed)
                    |---schemas.py (typed)
|-----------------*static/*
                    |--tailwind.js
|-----------------*venv/*
                    |---*Include/*
                    |---*Lib/*
                    |---*Scripts/*
                    |---.gitignore
                    |---pyvenv.cfg
|--create_admin.py (typed)
|--Procfile (typed)
|--requirements.txt (typed)
|--tasks.db

## Manually typed files that are not automatically generated

**Task_Managment_app**
|-----------------*app/*
                |---__init__.py 
                |---auth.py 
                |---database.py
                |---main.py 
                |---models.py 
                |---schemas.py
|--.gitignore 
|--create_admin.py  
|--Procfile 
|--requirements.txt

## The tech stack used in this project are:

* For **backend**, FastAPI which is python web framework. 

* For **Database** PostgreSQL on render.com & for ORM (Object-Relational Mapping) SQLAlchemy is getting used.
  
* For **Data Validation**, Pydantic which is Python data validation and parsing library
  
* For **Authentication & Security**, OAuth2 with JWT tokens (`python-jose`) and Bcrypt password hashing (`passlib`)

* For **Frontend**, HTML5, Vanilla JavaScript and Tailwind CSS
  
* For **Server**, Uvicorn (ASGI)

### **FastAPI** 
Ek web framework hai joh Python ke zariye fast aur scalable RESTful APIs banane ke liye use hota hai.

- High speed: yeh high performance deta hai kyunki yeh Starlette aur Uvicorn (ASGI) par built hai
- Type Hints & Pydantic: Standard python type annotations use karta hai jisse data automatic validate ho jaata hai
- Auto Documentation: Swagger UI ke zariye live, interactive API documentation (/docs) automatically generate kar deta hai
- Async Support: Concurrency aur asynchronous programming (async/await) ko natively support karta hai

### **Restful API**

**API** (Application programming Interface): Do alag softwares yaa systems ke biich baat karne kaa zariya

Restful API ek aisi API hai jo REST(Representational State Transfer) ke architectural rules aur standard HTTP methods ko follow karti hai:

- GET: Data read/fetch karne ke liye
- POST: Naya data create karne ke liye
- PUT/ PATCH: Data update karne ke liye
- DELETE: Date remove karne ke liye

*Key Rule:* Yeh stateless hoti hai yaani ki har request complete aur independent hoti hai, server user ka koi session state save nahi karta. Data aam taur par JSON format mein exchange hota hai.

*API Documentation:* Yeh ek instruction manual yaa guide hota hai joh batata hai ki kisi API ko kaisi use aur integrate karna hai.

### PostgreSQL, ORM (Object-Relational Mapping) and SqlAlchemy

Mere project mein dono (PostgreSQL aur SQLAlchemy) use ho rahe hain, kyunki dono alag-alag cheezein hain aur milkar kaam karti hain.

**PostgreSQL**: Yeh mera actual database engine hai (Render ke cloud server par). Yeh tables ke form mein data (users, tasks) ko hard drive/disk par physically store karta hai.

**SQLAlchemy**: Yeh mere Python backend (FastAPI) ke andar ek library (ORM) hai. Yeh Python code ko SQL queries mein translate karke PostgreSQL tak pahunchata hai.

**ORM (Object-Relational Mapping)**: ORM (Object-Relational Mapping) is a programming technique that connects object-oriented code with relational databases. It maps database tables to programming classes and rows to objects, enabling developers to query, insert, and update data using native code without writing raw SQL.

