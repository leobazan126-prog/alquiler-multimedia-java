# Bibliomedia - MULTIMEDIA RENTAL MANAGEMENT

A Java practice project designed to manage the loan of movies and video games between students and teachers.

It allows user registration, multimedia item queries, and return date tracking via both the command-line console and a basic web interface running in the browser.

---

## Tech Stack & Tools

* **Language:** Java (configured with Maven for automatic dependency management)
* **Recommended IDE:** IntelliJ IDEA (allows easy SDK and JVM configuration without Build Path conflicts)
* **Database:** MariaDB / MySQL managed locally using XAMPP and phpMyAdmin
* **Persistence Driver:** `mysql-connector-j` automatically downloaded by Maven via `pom.xml`
* **Web Interface:** Static HTML, CSS, and JavaScript pages connected to an internal server running on port `8080`

---

## Project Structure

```text
src/
|-- main/

|   |-- java/
|   |   `-- org/example/
|   |       |-- database/          # Database connection (ConexionDB)
|   |       |-- model/             # Domain classes and inheritance
|   |       |   |-- AbstractArticulo
|   |       |   |-- AbstractUsuario
|   |       |   |-- Alumno
|   |       |   |-- Docente
|   |       |   |-- Pelicula
|   |       |   |-- VideoJuego
|   |       |   `-- Prestamo
|   |       |-- repository/        # DAO Layer (SQL database queries)
|   |       |   |-- ArticuloDao
|   |       |   |-- UsuarioDao
|   |       |   |-- PrestamoDao
|   |       |   `-- Query
|   |       |-- service/           # Core logic and servers
|   |       |   |-- GestionAlquiler
|   |       |   |-- MenuConsola
|   |       |   `-- ServidorWeb
|   |       |-- utils/             # Data validation (ValidacionesUtil)
|   |       `-- Main.java          # Main execution file
|   |-- resources/                 # SQL Scripts (schema.sql, data.sql)
|   `-- webapp/                    # Web interface files (HTML, CSS, JS)
```

---

## Database

The project uses a database named `library_db` with three main tables:

1. **usuarios (users):** Stores students and teachers using their DNI/NIE as the primary identifier.
2. **articulos (items):** Stores video games and movies identified by their serial number.
3. **prestamos (loans):** Tracks which user borrowed which item, including the checkout date, return deadline, and the actual return date (to determine if it was returned on time or overdue).

---

## How to Run the Project

1. **Clone the repository:**
   ```bash
   git clone https://github.com/leobazan126-prog/alquiler-multimedia-java.git
   ```

2. **Initialize the database:**
   * Open the XAMPP Control Panel and start the **MySQL** module.
   * Go to phpMyAdmin in your browser (`http://localhost/phpmyadmin`).
   * Execute `src/main/resources/schema.sql` (this creates the `library_db` database and its table structure).
   * Execute `src/main/resources/data.sql` (this inserts the initial sample data).

3. **Open the project in your IDE:**
   * It is highly recommended to open the project folder directly with **IntelliJ IDEA**.
   * Wait for Maven to sync and automatically download the dependencies listed in the `pom.xml` file (no need to manually add `.jar` files).
   * Ensure that the Project SDK is properly assigned within the Project Structure settings.

4. **Execution:**
   * Run the `Main.java` file.
   * The application will launch the console-based menu and the web interface will also be accessible in your browser at `http://localhost:8080`.
