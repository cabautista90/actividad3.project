# actividad3.project
actividad3 programacion espe

# Sistema de Gestión de Proyectos y Participantes
Este proyecto es una aplicación web que gestiona la relación entre **proyectos** y **participantes** utilizando **Custom Elements** para el frontend y **Express** con **MySQL** para el backend. Permite agregar, actualizar y eliminar proyectos, participantes y las relaciones entre ellos, todo a través de una interfaz interactiva.

## Características

- **Frontend**: Utiliza **Custom Elements** para crear componentes reutilizables y encapsulados mediante **Shadow DOM**.
- **Backend**: Implementado con **Express** y **MySQL**, ofreciendo una API REST para realizar operaciones CRUD sobre proyectos y participantes.
- **Interactividad**: La interfaz permite gestionar proyectos y participantes, mostrando una tabla dinámica que permite agregar, actualizar y eliminar registros.

## Componentes del Proyecto

1. **Menú de Navegación**: Permite alternar entre las vistas de gestión de proyectos y participantes.
2. **Encabezado**: Muestra información del usuario actual (nombre, rol y fecha).
3. **Tabla de Visualización**: Muestra las relaciones entre proyectos y participantes con opciones para registrar, actualizar y eliminar datos.
4. **Pie de Página**: Muestra información adicional, como derechos de autor o enlaces de contacto.
5. **Contenedor Principal**: Gestiona la estructura global de la aplicación.

## Tecnologías Utilizadas

- **Frontend**:
  - HTML5
  - CSS3
  - JavaScript (Custom Elements, Shadow DOM)
- **Backend**:
  - Node.js
  - Express
  - MySQL
- **Otros**:
  - CORS (para permitir las solicitudes entre el frontend y backend)

## Estructura del Proyecto

## directorio endpoints

/project-directory 

├── /backend │

├── server.js # Configuración de Express y rutas de la API │

└── db.js # Conexión a la base de datos MySQL ├── /frontend │ 

├── /components │ 

│ ├── menu-nav.js # Componente del menú de navegación │ 

│ ├── header.js # Componente del encabezado │ 

│ ├── table-view.js # Componente de la tabla de visualización │ 

│ ├── footer.js # Componente del pie de página │

│ └── container.js # Componente contenedor principal │ 

├── index.html # Estructura principal de la página │ 

└── style.css # Estilos globales de la aplicación 

└── package.json # Dependencias y scripts del proyecto

2. CREAR LA BD EN MYSQL

CREATE DATABASE PROYECTO_JS;

USE PROYECTO_JS;

CREATE TABLE projects (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(255) NOT NULL,
  description TEXT
);

CREATE TABLE participants (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(255) NOT NULL,
  role VARCHAR(100) NOT NULL
);

CREATE TABLE project_participants (
  id INT AUTO_INCREMENT PRIMARY KEY,
  project_id INT,
  participant_id INT,
  FOREIGN KEY (project_id) REFERENCES projects(id),
  FOREIGN KEY (participant_id) REFERENCES participants(id)
);

Configurar el archivo de conexión de base de datos (db.js)
En el archivo backend/db.js,
como el nombre de usuario, 
la contraseña
el nombre de la base de datos.

const mysql = require('mysql2');

const db = mysql.createConnection({
  host: 'localhost',
  user: 'root',
  password: '',  // Tu contraseña de MySQL
  database: 'projects_db'  // Nombre de la base de datos
});

module.exports = db;

Acceder al frontend
Abre el archivo frontend/index.html aplicación a través de la interfaz de usuario. Los datos de los proyectos y participantes se gestionan a través de la API REST.

Rutas de la API
Proyectos:
GET /projects: Obtiene todos los proyectos.
POST /projects: Crea un nuevo proyecto (requiere name y description).
PUT /projects/:id: Actualiza un proyecto existente (requiere name y description).
DELETE /projects/:id: Elimina un proyecto por su id.

