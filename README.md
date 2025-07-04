# Products Backend

A simple Spring Boot API that serves products data from a PostgreSQL database.

---

##  Prerequisites

- **Java 17**  

- **Maven** 

- **PostgreSQL** 

## Database setup

1. Start PostgreSQL:

    - sudo service postgresql start

2.  Log in to psql as the postgres user:

    - sudo -u postgres psql

3. Inside psql, create a database and user:

    CREATE DATABASE products_db;
    CREATE USER interview_user WITH PASSWORD 'password';
    GRANT ALL PRIVILEGES ON DATABASE products_db TO interview_user;

4. Exit psql:

    - \q

In Application properties:

    - Edit your src/main/resources/application.properties:

        spring.datasource.url=jdbc:postgresql://localhost:5432/products_db
        spring.datasource.username=products_user
        spring.datasource.password=password

        spring.jpa.hibernate.ddl-auto=update
        spring.jpa.show-sql=true
        spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect

Set Up

1. Clone the repo:

    - git clone https://github.com/your-username/products-backend.git
    - cd products-backend

2.  Build the project:

    - mvn clean install

3.  Run the app:

    - mvn spring-boot:run

The API will be available at:

    - http://localhost:8080/api/products

Example CURL commands

    List all products:

        curl -X GET http://localhost:8080/api/products

    Add Product:

        curl -X POST http://localhost:8080/products \
        -H "Content-Type: application/json" \
        -d '{"name": "Test Product"}'

Example SQL script

If you want to manually insert some products in psql, run:

    \c products_db

    CREATE TABLE IF NOT EXISTS product (
        id BIGSERIAL PRIMARY KEY,
        name VARCHAR(255)
    );

    INSERT INTO product (name) VALUES
    ('Valve'),
    ('Screw'),
    ('Hat');
