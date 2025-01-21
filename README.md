**********************************************************************************FOROHUB*********************************************************************************************************************

Proyecto de creación de una API REST sencilla para gestionar un foro de tópicos. Acá podés listar, crear, actualizar y eliminar tópicos, todo de manera segura usando tokens JWT. Si sos nuevo en esto, no te preocupes, te voy a guiar paso a paso.

---

## Funcionalidades principales:

1. **Listar Tópicos**
   - Método: `GET`
   - Ruta: `/topicos`
   - Cuando hacés esta solicitud, la API te devuelve todos los tópicos que están en la base de datos. Es como ver una lista de los mensajes del foro.

2. **Crear un Tópico**
   - Método: `POST`
   - Ruta: `/topicos`
   - Para poder crear un tópico, necesitas estar autenticado. Primero, vas a obtener un token JWT (es como una especie de "llave" que te da acceso a ciertas funciones). Al crear un tópico, vas a tener que enviar información como:
     - `idUsuario`: ID del usuario que está creando el tópico.
     - `mensaje`: El mensaje que querés dejar en el foro.
     - `curso`: El curso al que se refiere el tópico.
     - `titulo`: El título de tu tópico.

3. **Autenticación**
   - Método: `POST`
   - Ruta: `/auth`
   - Acá podés registrarte o iniciar sesión con tu email y contraseña. Si todo está bien, la API te devuelve un token JWT que vas a necesitar para hacer otras acciones como crear o eliminar tópicos.

4. **Eliminar un Tópico**
   - Método: `DELETE`
   - Ruta: `/topicos/{id}`
   - Si querés eliminar un tópico, necesitás enviar una solicitud a esta ruta, pero solo lo podés hacer si tenés el token JWT. Recordá que necesitás el `id` del tópico que querés eliminar.

---

## Requisitos

- **Base de Datos**: Podés usar la base de datos que más te guste para almacenar los tópicos.
- **Autenticación**: Usamos JWT para autenticar a los usuarios.
- **Códigos de Estado HTTP**:
  - `200`: Todo salió bien.
  - `201`: Tópico creado con éxito.
  - `403`: No tenés permiso para hacer eso (falta autenticación).
  - Otros códigos de estado según la acción.

---

## ¿Cómo usar esta API?

1. **Autenticación**:
   - Primero, hacé un `POST` a `/auth` con tu email y contraseña. Vas a recibir un token JWT que vas a necesitar para las siguientes solicitudes.

2. **Usar el token en solicitudes**:
   - Una vez tengas tu token, cada vez que vayas a hacer algo como crear un tópico o eliminarlo, vas a tener que incluir el token. Normalmente, se hace como "Bearer Token" en las herramientas como Postman o tu cliente HTTP favorito.

3. **Ejemplo de creación de tópico**:
   - Si querés crear un tópico, hacé un `POST` a `/topicos` y enviá algo como esto:
     ```json
     {
       "idUsuario": 1,
       "mensaje": "Este es mi primer tópico",
       "curso": "Java Básico",
       "titulo": "Duda sobre variables"
     }
     ```
   - Si todo sale bien, vas a recibir un código `201`, que significa que se creó correctamente.

4. **Listar tópicos**:
   - Hacés un `GET` a `/topicos` para obtener todos los tópicos disponibles.

5. **Eliminar un tópico**:
   - Si querés eliminar un tópico, enviá un `DELETE` a `/topicos/{id}` con el ID del tópico que querés borrar.
