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


---

# 🧪 4. Behavior Driven Development (BDD)
Los comportamientos del sistema están definidos en archivos `.feature`:

[🧪 Archivo BDD – tournament.feature](./tournament.feature)


