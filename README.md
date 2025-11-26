# 🎮 Plataforma API – Torneo de Videojuegos  
Arquitectura Serverless en AWS

---

# 📘 1. Descripción del Proyecto  
Este proyecto implementa una plataforma serverless para la gestión completa de torneos de videojuegos, incluyendo:

- Torneos (creación, publicación, administración)
- Tickets (venta, consulta, validación)
- Vistas del torneo (acceso de espectadores)
- Usuarios (registro y consulta)

Todo construido con una arquitectura basada en **AWS Lambda, API Gateway, DynamoDB e IAM**.

---

# 🏛️ 2. Arquitectura (Serverless + AWS)
![Arquitectura API](./torneovideojuegos.drawio.svg)

> Arquitectura serverless con API Gateway → Lambda → DynamoDB, con seguridad IAM SigV4 y monitoreo CloudWatch.

---

# 🟪 3. Domain Driven Design (DDD)
El proyecto está dividido en **4 Bounded Contexts**:

| Dominio | Responsabilidad | APIs |
|--------|----------------|------|
| **Torneos** | Crear, publicar, administrar, notificar | /tournaments |
| **Tickets** | Vender, consultar, validar | /tickets |
| **Vistas** | Registrar vista, unirse, consultar | /views |
| **Usuarios** | Registrar, consultar | /users |

> Esta separación permite una arquitectura modular, escalable y alineada al dominio del negocio.

---

# 🧪 4. Behavior Driven Development (BDD)
Los comportamientos del sistema están definidos mediante archivos `.feature` usando lenguaje Gherkin (Dado–Cuando–Entonces):

📄 **Archivo BDD:**  
👉 [🧪 tournament.feature](./tournament.feature)

Ejemplo:

```gherkin
Escenario: Obtener un torneo por su ID
Dado que existe un torneo con un ID válido
Cuando el cliente realiza un GET a /tournaments/{id}
Entonces la API responde con estado 200

📄 5. Contrato de la API (OpenAPI – YAML)

El contrato completo de la API está definido con OpenAPI 3.0, documentando:

Endpoints

Modelos

Validaciones

Ejemplos

Respuestas y códigos HTTP

Las 15 operaciones del dominio

📘 Contrato OpenAPI:
👉 tomeovideojuegos.yaml

🗂️ 6. Modelo de Base de Datos (DynamoDB)

El diseño de la base de datos está representado en el siguiente diagrama:

📊 Modelo BD:


Incluye las tablas:

Tournaments

Tickets

Views

Users

Organizadas según los bounded contexts del modelo DDD.

🛠️ 7. Tecnologías Utilizadas

AWS Lambda (lógica de negocio serverless)

AWS API Gateway (exposición de endpoints REST)

AWS DynamoDB (base de datos NoSQL)

AWS IAM (seguridad y accesos)

AWS CloudWatch (monitoreo, logs y trazabilidad)

Node.js

OpenAPI (YAML)

Gherkin (BDD)

GitHub (control de versiones)

🧪 8. Pruebas Unitarias (TDD)

El proyecto implementa TDD (Test Driven Development):

🔴 Red → Se escribe primero una prueba que falla

🟢 Green → Se desarrolla el código mínimo para pasar la prueba

🔵 Refactor → Se mejora el código sin romper nada

Ejemplo de prueba:

it("debe crear un torneo correctamente", () => {
  const result = handler(requestValida);
  expect(result.statusCode).toBe(201);
});


Esto asegura calidad, estabilidad y mantenibilidad en las funciones Lambda.

👤 9. Autor

Miguel
Arquitectura • Backend • DevOps • Serverless • AWS
