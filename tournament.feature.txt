# language: es

Característica: Gestión de Torneos de Videojuegos
  Como plataforma de e-sports
  Quiero exponer una API para gestionar torneos, tickets, vistas y usuarios
  Para administrar de forma segura los torneos de videojuegos y su audiencia

  Antecedentes:
    Dado que la API de Torneo de Videojuegos está desplegada en AWS API Gateway
    Y el cliente está autenticado correctamente con AWS Signature v4
    Y existe conectividad con los servicios Lambda y DynamoDB

  @GetTournamentById
  Escenario: Obtener un torneo por su ID
    Dado que existe un torneo con un ID válido
    Cuando el cliente realiza un GET a /tournaments/{tournamentId}
    Entonces la API responde con el detalle del torneo solicitado
    Y la respuesta tiene el código de estado 200

  @UpdateTournament
  Escenario: Actualizar un torneo existente por su ID
    Dado que existe un torneo con un ID válido
    Y el cliente tiene información actualizada del torneo
    Cuando el cliente realiza un PUT a /tournaments/{tournamentId} con el cuerpo válido
    Entonces el torneo se actualiza correctamente en la base de datos
    Y la respuesta tiene el código de estado 200

  @DeleteTournament
  Escenario: Eliminar un torneo existente por su ID
    Dado que existe un torneo con un ID válido
    Cuando el cliente realiza un DELETE a /tournaments/{tournamentId}
    Entonces el torneo se elimina correctamente
    Y la respuesta tiene el código de estado 204

  @ListTournaments
  Escenario: Obtener la lista de torneos disponibles
    Dado que existen torneos registrados en el sistema
    Cuando el cliente realiza un GET a /tournaments
    Entonces la API responde con la lista de torneos disponibles
    Y la respuesta tiene el código de estado 200

  @CreateTournament
  Escenario: Crear un nuevo torneo
    Dado que el cliente tiene información válida para crear un torneo
    Cuando el cliente realiza un POST a /tournaments con el cuerpo de la solicitud válido
    Entonces el torneo se crea correctamente en la base de datos
    Y la respuesta tiene el código de estado 201

  @PublishTournament
  Escenario: Publicar un torneo para hacerlo visible a los usuarios
    Dado que existe un torneo en estado BORRADOR
    Cuando el cliente realiza un POST a /tournaments/{tournamentId}/publish
    Entonces el torneo cambia a estado PUBLICADO
    Y la respuesta tiene el código de estado 200

  @AssignSubadmins
  Escenario: Asignar subadministradores a un torneo
    Dado que existe un torneo publicado
    Y el cliente tiene una lista de subadministradores válidos
    Cuando el cliente realiza un POST a /tournaments/{tournamentId}/subadmins
    Entonces los subadministradores quedan asociados al torneo
    Y la respuesta tiene el código de estado 200

  @SendTournamentNotifications
  Escenario: Enviar notificaciones a los participantes de un torneo
    Dado que existe un torneo con participantes registrados
    Y el cliente define un mensaje de notificación
    Cuando el cliente realiza un POST a /tournaments/{tournamentId}/notifications
    Entonces las notificaciones se envían a los destinatarios configurados
    Y la respuesta tiene el código de estado 202

  @SellTicket
  Escenario: Realizar la venta de un ticket para un torneo
    Dado que existe un torneo con cupos disponibles
    Y el cliente tiene información válida del comprador
    Cuando el cliente realiza un POST a /tournaments/{tournamentId}/tickets
    Entonces se genera un ticket asociado al torneo y al usuario
    Y la respuesta tiene el código de estado 201

  @GetTicketById
  Escenario: Consultar un ticket por su ID
    Dado que existe un ticket con un ID válido
    Cuando el cliente realiza un GET a /tickets/{ticketId}
    Entonces la API responde con la información del ticket
    Y la respuesta tiene el código de estado 200

  @ValidateTicket
  Escenario: Validar un ticket de acceso a un torneo
    Dado que existe un ticket emitido en estado ACTIVO
    Cuando el cliente realiza un POST a /tickets/{ticketId}/validate
    Entonces el ticket se marca como USADO o VALIDADO según la regla de negocio
    Y la respuesta tiene el código de estado 200

  @CreateView
  Escenario: Registrar una vista (acceso) a un torneo
    Dado que existe un torneo publicado
    Y un usuario tiene permiso para acceder al torneo (gratuito o de pago)
    Cuando el cliente realiza un POST a /tournaments/{tournamentId}/views
    Entonces se registra una vista asociada al torneo y al usuario
    Y la respuesta tiene el código de estado 201

  @ListViewsByTournament
  Escenario: Consultar las vistas de un torneo
    Dado que existe un torneo con vistas registradas
    Cuando el cliente realiza un GET a /tournaments/{tournamentId}/views
    Entonces la API responde con la lista de vistas del torneo
    Y la respuesta tiene el código de estado 200

  @JoinView
  Escenario: Un usuario se une a una vista específica
    Dado que existe una vista configurada para un torneo
    Y el usuario tiene los permisos para unirse
    Cuando el cliente realiza un POST a /views/{viewId}/join
    Entonces el usuario queda registrado como participante de la vista
    Y la respuesta tiene el código de estado 200

  @CreateUser
  Escenario: Registrar un nuevo usuario en la plataforma
    Dado que el cliente tiene información válida del usuario
    Cuando el cliente realiza un POST a /users con el cuerpo válido
    Entonces el usuario queda registrado en la plataforma
    Y la respuesta tiene el código de estado 201

  @GetUserById
  Escenario: Consultar un usuario por su ID
    Dado que existe un usuario con un ID válido
    Cuando el cliente realiza un GET a /users/{userId}
    Entonces la API responde con la información del usuario
    Y la respuesta tiene el código de estado 200
