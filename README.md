# 📚 Gestión de Biblioteca (CRUD Hibernate)

## Resumen del Proyecto

Este proyecto es una implementación en **Java** utilizando el framework **Hibernate** para la gestión de una base de datos relacional de una **Biblioteca** (`MySQL`). El objetivo principal ha sido dominar las operaciones **CRUD** (Create, Read, Update, Delete) y la correcta gestión y mapeo de las tres principales tipos de **relaciones** entre entidades: **1:1, 1:M y N:M**.

El proyecto demuestra cómo modelar y persistir estructuras de datos complejas con la temática de una biblioteca, con usuarios, autores, libros y las relaciones entre ellos.

## 🛠️ Tecnología
* **Lenguaje:** Java (JDK 24)
* **Framework ORM:** Hibernate
* **Base de Datos:** MySQL
* **Conexión:** JDBC
* *Necesario un servidor MySQL funcionando*

## 📖 Relaciones

* **`Usuario`** y **`TarjetaUsuario`**: Relación 1:1.
* **`Autor`** y **`Libro`**: Relación 1:M (un autor puede tener muchos libros).
* **`Libro`** y **`Usuario`**: Relación M:1 (un libro puede estar prestado a un solo usuario a la vez y un usuario puede tener más de un libro).
* **`Usuario_Favorito`**: Tabla de enlace para la relación N:M entre `Usuario` y `Libro`.

## Funcionalidades Implementadas

### 1. Operaciones CRUD Estándar

Implementación de las operaciones Create, Read, Update y Delete para la entidad **Libro**.

### 2. Lectura Recursiva (1:M)

He implementado una opción de lectura recursiva para ver la relación 1:M entre `Autor` y `Libro`.

* **`muestra Autor`**: Lista todos los autores.
* **`muestra -r Autor`**: Muestra cada autor y **todos los libros asociados** a ese autor (muestra la colección relacionada).

### 3. Inserción de los campos relacionados

Al insertar un `Libro`, se maneja la asignación de su `Autor` de forma interactiva:

* **`añadir Libro`**: Inserta un libro nuevo dejando el campo `Autor` como `NULL`.
* **`añadir -r Libro`**: Permite seleccionar un autor existente de la BD. Además, te da la opción de **crear un nuevo `Autor`** si no existe y asignarlo inmediatamente al nuevo `Libro`. Ambas entidades se persisten en la base de datos en esta operación, pero no solo se aplica a estas 2:

* Todas las entidades de la Base de Datos funcionan de esta manera al ser modificadas, todo esta relacionado y **se pueden editar cualquier entidad desde el CRUD de `Libro` implementado**
* Por ejemplo, al crear un **`Libro`** podemos crear un **`Usuario nuevo`**, y a su vez **se nos creará automáticamente su respectiva `Tarjeta`**

## 🚀 Cómo Empezar

1.  **Clonar el Repositorio.**
2.  **Configurar MySQL:** Ejecutar el script SQL de la base de datos `Biblioteca` (incluido en el repositorio) para crear la estructura de la BD e insertar los datos de ejemplo.
3.  **Ejecución:** Ejecuta la clase principal e interactúa con el menú de la consola. Los logs y el SQL de Hibernate estan desactivados para una vista más limpia), se pueden reactivar desde el archivo de **logback.xml** y **persistence.xml** del proyecto.
