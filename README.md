# tt-node-final-2025

Una API REST moderna para la gestión de productos en una aplicación de ecommerce, desarrollada con Node.js y Express. Incluye autenticación JWT y almacenamiento en Firebase Firestore.

## 📋 Descripción

Este proyecto es el trabajo final del curso de Node.js de Talento Tech 2025. Se trata de una API backend que permite gestionar productos de un ecommerce, con funcionalidades de autenticación para proteger las operaciones de creación y eliminación de productos.

### Características principales
- 🚀 **API RESTful** con endpoints limpios y estructurados
- 🔐 **Autenticación JWT** para operaciones sensibles
- 🔥 **Firebase Firestore** como base de datos NoSQL
- 📧 **Nodemailer** integrado para notificaciones (futuro)
- 🛡️ **CORS configurado** para desarrollo y producción
- 📝 **Logging middleware** para monitoreo de requests

## 🛠️ Tecnologías utilizadas

- **Backend**: Node.js con Express.js
- **Base de datos**: Firebase Firestore
- **Autenticación**: JSON Web Tokens (JWT)
- **Correo**: Nodemailer
- **Configuración**: dotenv para variables de entorno
- **Seguridad**: CORS para control de orígenes

## 📦 Instalación

### Prerrequisitos
- Node.js versión 18 o superior
- Cuenta de Firebase con proyecto configurado
- Variables de entorno configuradas

### Pasos de instalación

1. **Clona el repositorio**
   ```bash
   git clone https://github.com/Anita-Llanes/tt-node-final-2025.git
   cd tt-node-final-2025
   ```

2. **Instala las dependencias**
   ```bash
   npm install
   ```

3. **Configura las variables de entorno**

   Crea un archivo `.env` en la raíz del proyecto con las siguientes variables:

   ```env
   # Puerto del servidor
   PORT=3000

   # JWT Secret Key (genera una clave segura)
   JWT_SECRET_KEY=tu_clave_secreta_jwt_aqui

   # Configuración de Firebase
   FIREBASE_API_KEY=tu_api_key_firebase
   FIREBASE_AUTH_DOMAIN=tu_proyecto.firebaseapp.com
   FIREBASE_STORAGE_BUCKET=tu_proyecto.appspot.com
   FIREBASE_APP_ID=tu_app_id_firebase
   ```

4. **Configura Firebase**
   - Ve a [Firebase Console](https://console.firebase.google.com/)
   - Crea un proyecto o selecciona uno existente
   - Habilita Firestore Database
   - Obtén las credenciales de configuración

## 🚀 Uso

### Iniciar el servidor
```bash
npm start
```

El servidor se ejecutará en `http://localhost:3000` (o el puerto configurado en `.env`).

### Endpoints de la API

#### 🔐 Autenticación
- `POST /api/login` - Iniciar sesión
  - **Body**: `{ "email": "test@gmail.com", "password": "123456" }`
  - **Respuesta**: `{ "token": "jwt_token_aqui" }`

#### 📦 Productos
- `GET /api/products` - Obtener todos los productos
- `GET /api/products/:id` - Obtener producto por ID
- `POST /api/products/create` - Crear nuevo producto (requiere autenticación)
  - **Headers**: `Authorization: Bearer <token>`
  - **Body**: `{ "name": "Producto", "price": 100, ... }`
- `DELETE /api/products/:id` - Eliminar producto (requiere autenticación)
  - **Headers**: `Authorization: Bearer <token>`

### Ejemplo de uso con cURL

```bash
# Login
curl -X POST http://localhost:3000/api/login \
  -H "Content-Type: application/json" \
  -d '{"email":"test@gmail.com","password":"123456"}'

# Obtener productos
curl http://localhost:3000/api/products

# Crear producto (con token)
curl -X POST http://localhost:3000/api/products/create \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer TU_TOKEN_AQUI" \
  -d '{"name":"Nuevo Producto","price":50}'
```

## 🔧 Configuración adicional

### CORS
La aplicación está configurada para aceptar requests desde:
- `http://localhost:5173` (desarrollo con Vite)
- `https://midominio.com` (producción)

Para modificar los orígenes permitidos, edita el archivo `index.js`.

### Base de datos
Los productos se almacenan en Firebase Firestore. La estructura de datos esperada para un producto incluye campos como `name`, `price`, `description`, etc.

## 📁 Estructura del proyecto

```
tt-node-final-2025/
├── src/
│   ├── controllers/     # Controladores de la API
│   ├── data/           # Configuración de BD y tokens
│   ├── middleware/     # Middlewares personalizados
│   ├── models/         # Modelos de datos
│   ├── routes/         # Definición de rutas
│   └── services/       # Lógica de negocio
├── index.js            # Punto de entrada
├── package.json        # Dependencias y scripts
├── vercel.json         # Configuración de despliegue
└── README.md           # Este archivo
```

## 🧪 Pruebas

Actualmente no hay pruebas automatizadas configuradas. Para probar manualmente:

1. Inicia el servidor
2. Usa herramientas como Postman o cURL para probar los endpoints
3. Verifica la autenticación y operaciones CRUD

## 🚀 Despliegue

### Vercel
El proyecto incluye configuración para despliegue en Vercel. Asegúrate de configurar las variables de entorno en el dashboard de Vercel.

### Otros proveedores
Para otros proveedores de hosting, configura las variables de entorno y ajusta la configuración de CORS según sea necesario.

## 🤝 Contribución

Este es un proyecto educativo. Para mejoras:

1. Fork el proyecto
2. Crea una rama para tu feature (`git checkout -b feature/nueva-funcionalidad`)
3. Commit tus cambios (`git commit -am 'Agrega nueva funcionalidad'`)
4. Push a la rama (`git push origin feature/nueva-funcionalidad`)
5. Abre un Pull Request

## 📄 Licencia

Este proyecto está bajo la Licencia ISC. Ver el archivo `LICENSE` para más detalles.

## 👤 Autor

**Ana Llanes** - Proyecto final para Talento Tech 2025

---

⭐ Si te gusta este proyecto, ¡dale una estrella en GitHub!
