# Laboratorio #2 — Implementación del Login en Laravel

 **Universidad Tecnológica de Panamá**  
 Facultad de Ingeniería en Sistemas Computacionales — Campus Victor Levis Sasso  
 Curso: Desarrollo Web VII | Instructor: Ing. Irina Fong  
 Unidad I: Patrón Modelo–Vista–Controlador (MVC)



##  Objetivo del Laboratorio

Implementar un sistema de autenticación (Login y Registro) en Laravel, explorando la estructura del framework bajo el patrón **Modelo–Vista–Controlador (MVC)** y comprendiendo la organización de carpetas y componentes del proyecto.


## Introducción — Arquitectura MVC en Laravel

Laravel organiza el código bajo el patrón **Modelo–Vista–Controlador (MVC)**, que separa las responsabilidades en tres capas:


LABORATORIO2/
├── app/
│   ├── Http/
│   │   └── Controllers/    ← CONTROLADORES: lógica de la aplicación
│   └── Models/             ← MODELOS: interacción con la base de datos
├── resources/
│   └── views/              ← VISTAS: lo que ve el usuario (Blade templates)
├── routes/
│   └── web.php             ← RUTAS: definen las URLs de la aplicación
├── database/
│   └── migrations/         ← MIGRACIONES: estructura de la base de datos
└── .env                    ← Variables de entorno (configuración)
```

| Capa | Carpeta | Función |
|---|---|---|
| **Modelo** | `app/Models/` | Representa los datos y se comunica con la BD |
| **Vista** | `resources/views/` | Muestra la interfaz al usuario (HTML + Blade) |
| **Controlador** | `app/Http/Controllers/` | Recibe peticiones, procesa lógica y responde |
| **Rutas** | `routes/web.php` | Define qué URL llama a qué controlador |


##  Secuencia de Comandos Utilizados

### 1. Instalación del instalador de Laravel
```bash
composer global require laravel/installer
```

### 2. Crear el proyecto
```bash
cd C:\wamp64\www
laravel new LABORATORIO2
```

### 3. Configurar el archivo `.env`
```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=laboratorio2
DB_USERNAME=root
DB_PASSWORD=
```

### 4. Ejecutar migraciones
```bash
php artisan migrate
```

### 5. Instalar paquete de autenticación (Laravel/UI)
```bash
composer require laravel/ui
php artisan ui bootstrap --auth
```

### 6. Instalar dependencias y compilar assets
```bash
npm install
npm run dev
```

### 7. Levantar el servidor
```bash
php artisan serve
```



## Base de Datos

### Configuración del entorno
La conexión a la base de datos se configura en el archivo `.env` con las credenciales de MySQL local (WampServer). La base de datos utilizada se llama `laboratorio2`.

### Tablas generadas por las migraciones

| Tabla | Descripción |
|---|---|
| `users` | Almacena los usuarios registrados (nombre, email, contraseña) |
| `migrations` | Registro de migraciones ejecutadas por Laravel |
| `cache` | Almacenamiento temporal de caché |
| `jobs` | Cola de trabajos en segundo plano |

### Comandos de migración utilizados

```bash
php artisan migrate           # Ejecuta todas las migraciones pendientes
php artisan migrate:fresh     # Borra todo y recrea las tablas desde cero
php artisan config:clear      # Limpia la caché de configuración
php artisan config:cache      # Regenera la caché de configuración
```

>  El backup de la base de datos se encuentra en el archivo `backup_laboratorio2.sql` en este repositorio.

---

##  Resultado del Laboratorio

Al finalizar el laboratorio, se obtuvo Laravel corriendo exitosamente con el sistema de autenticación funcional:

- Pantalla de bienvenida de Laravel en `http://127.0.0.1:8000`
- Botones **Login** y **Register** disponibles
- Registro e inicio de sesión de usuarios funcionando correctamente
- Dashboard accesible tras autenticarse
  
 ![image alt]( https://github.com/CristianG0311/Laboratorio-2/blob/81844f889d0ddac577ca58a54552bf59fed4bca8/Captura%20de%20pantalla%202026-04-12%20192815.png
)


##  Dificultades y Soluciones

| Dificultad | Solución Aplicada |
|---|---|
| `Nothing to migrate` al correr `php artisan migrate` | No era un error — las migraciones ya habían sido ejecutadas previamente. Las tablas ya existían en la base de datos. |
| Página sin estilos CSS al abrir el navegador | Vite estaba en modo desarrollo. Se solucionó corriendo `npm run dev` en una terminal paralela mientras corre `php artisan serve`. |
| Pregunta al correr `php artisan ui bootstrap --auth` sobre reemplazar `Controller.php` | Se respondió `yes` para reemplazar el archivo y continuar con la generación del scaffolding. |


##  Referencias

1. Laravel Documentation — *Installation and Authentication*  
   https://laravel.com/docs/12.x

2. Laravel UI Package — *GitHub laravel/ui*  
   https://github.com/laravel/ui

3. WampServer — *Entorno de desarrollo local para Windows*  
   https://www.wampserver.com

4. Composer — *Dependency Manager for PHP*  
   https://getcomposer.org

5. Vite + Laravel — *Frontend Tooling*  
   https://laravel.com/docs/12.x/vite



  **Nombre:** Cristian Gonzalez  
  **Correo:** cristia.gonzalez7@utp.ac.pa  
  **Curso:** Desarrollo de Software 7  
  **Instructor del Laboratorio:** Ing. Irina Fong
