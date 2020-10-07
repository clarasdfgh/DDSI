# Prácticas DDSI: torneo de tenis

## Subsistemas requeridos

### 1. Jugadores/Entrenadores

- Insertar jugador en BD
  - Nombre (30 caracteres)
  - Apellidos (60 caracteres)
  - Tfno (hasta 12 caracteres numericos menos el primero que puede ser +) 
  - E-mail (50 caracteres debe contener @)
- Insertar entrenador en BD
  - Nombre (30 caracteres)
  - Apellidos (60 caracteres)
  - Tfno (hasta 12 caracteres numericos menos el primero que puede ser +) 
  - E-mail (50 caracteres debe contener @)

- Inscribir pareja de jugadores en una edición de torneo

- Asignar entrenador a pareja de jugadores en una  edición de torneo

- Asignar posición en el ranking a una pareja de jugadores en una edición de torneo

- Registrar entrenadores y parejas a las que entrenan en una edición. Un entrenador puede entrenar más de una pareja

- Consultar los jugadores que no están inscritos en una edición
- Cambiar entrenador asociado a una pareja en una edición
- Mostrar las parejas de jugadores por ranking en una edición
- Mostrar las parejas en un rango del ranking en una edición

#### Condiciones

- Un entrenador puede entrenar varias parejas en una misma edición. 
  - No es así al contrario: una pareja sólo puede tener un entrenador en una edición
- No es obligatorio que la pareja tenga entrenador
- No puede haber dos parejas con la misma posición en el ranking en la misma edición
- Un jugador no puede pertenecer a dos parejas distintas en la misma edición



### 2. Usuarios/Entradas

- Insertar nuevo usuario
  - Nombre 
  - Apellidos
  - E-mail
  - Contraseña (30 caracteres)
  - Notificaciones (Si/No)
- Insertar nuevo tipo de entrada (entrada de la final, entrada semifinal, pase de temporada...)
  - Nombre/Tipo
- Asignar una cantidad de tipo de entrada a una edición
- Asignar un precio a un tipo de entrada en una edición
- Iniciar una compra
  - Usuario
  - Edición (Nombre a cada edición, o año) ((seguramente luego sea una entidad))
  - Fecha (DD-MM-AAAA HH:MM:SS)
- Añadir entradas a una compra
  - Tipo
  - Cantidad
- Finalizar una compra
  - Finalizada
  - Fecha
  - Identificador entrada
  - Tipo
  - Cantidad
  - Total a pagar
- Pagar una compra
  - Pagada
  - Fecha
  - Identificador compra
  - Dinero pagado por cada tipo de entrada
  - Total
- Consultar el dinero obtenido en una edición por venta de entradas
- Mostrar compras finalizadas de un usuario en una edición (pagadas o no)
  - Fecha inicio
  - Fecha fin
  - Tipo
  - Cantidad
  - Pagada
    - Fecha pago
    - Total

#### Condiciones

- No se puede finalizar una compra no iniciada
- No se puede pagar una compra no finalizada
- Un usuario no puede iniciar una nueva compra si tiene otra iniciada sin finalizar
- Un usuario solo puede pagar una compra por día



### 3. Árbitros/Contratación

- Insertar nuevo árbitro
  - Nombre
  - Apellidos
  - E-mail
  - Tfno
- Hacer una oferta monetaria a un árbitro en una edición
  - Árbitro
  - Edición
  - Oferta
  - Fecha
- Aceptar oferta
  - Árbitro
  - Edición
  - Oferta
  - Fecha
- Rechazar oferta
  - Fecha
- Contraoferta
  - Fecha
  - Cantidad
- Aceptar una contraoferta
  - Fecha
- Rechazar una contraoferta
  - Fecha
- Retirar oferta
- Mostrar las ofertas realizadas a un árbitro en una edición
  - Fecha
  - Oferta
  - Aceptada
    - Fecha
  - Rechazada
    - Fecha
  - Contraoferta
    - Cantidad
    - Fecha
- Mostrar las ofertas aceptadas en una edición
  - Fecha
  - Árbitro
  - Oferta
  - Fecha aceptación

#### Condiciones

- No puedo retirar una oferta si esta ha sido aceptada, rechazada o contraofertada
- No le puedo realizar una nueva oferta a un árbitro que ya ha aceptado o rechazado alguna oferta en esta edición
- Sólo puedo realizar una oferta si no hay ninguna contraoferta realizada o si todas las ofertas tienen contraoferta
- No se puede contraofertar dos veces la misma oferta
- El árbitro no me puede hacer contraoferta si ya he aceptado o rechazado una oferta anterior



### 4. Pistas/Partidos

- Insertar nueva pista
  - Nombre (30 caracteres)
  - Capacidad
- Insertar nuevo partido
  - Edición
  - Ambas parejas de jugadores
  - Fecha
  - Pista
  - Árbitro
- Añadir resultado a partido
  - Número de sets ganado por cada pareja
- Mostrar partidos que hay en una fecha (DD-MM-AAAA)
  - Partidos
  - Resultado
- Partidos que se juegan en una pista concreta en una edición
  - Partidos
- Mostrar los partidos finalizados de una edición (partidos finalizados = aquellos que tengan un resultado)
- Modificar el árbitro de un partido
- Mostrar los partidos asignados a un árbitro en una edición
- Mostrar las pistas sin ningún partido asignado en esta edición

#### Condiciones

- No se pueden solapar los horarios de dos partidos en una misma pista con menos de 3 horas de diferencia
- En una misma pista no se pueden jugar más de dos partidos en el mismo día
- Sólo puedo asignar árbitros que hayan aceptado una oferta en esta edición
- Un árbitro no puede llevar más de un partido por día
- No se puede añadir un resultado a un partido cuya fecha de inicio es posterior a la fecha actual



### 5. Personal/Horarios

- Insertar un nuevo personal
  - Nombre
  - Apellidos
  - E-mail
  - Tfno
- Asignar personal a edición
  - Salario/hora
- Asignar horario a personal de edición
  - Fecha inicio
  - Fecha fin
  - Pista
- Mostrar trabajadores libres de una edición (personal asignado a la edición sin horario de trabajo asignado)
- Mostrar el horario de trabajo de un trabajador (ordenado por días)
  - Hora inicio
  - Hora fin
  - Pista
- Modificar el salario/hora de un trabajador en una edición
- Mostrar el personal que no trabaja en una edición
- Mostrar el total de dinero pagado en salarios en una edición
- Mostrar los trabajadores de una edición ordenados por horas trabajadas
  - Nombre
  - Apellidos
  - Salario
  - Horas
  - Salario total

#### Condiciones

- No se pueden solapar los horarios de un trabajador con menos de una hora de diferencia
- No se puede asignar a un trabajador la misma pista más de dos veces el mismo día
- No se puede trabajar más de 8 horas el mismo día
- No puedo modificar el salario de un trabajador si ya ha realizado algún trabajo



### 6. Patrocinadores/Colaboradores

- Insertar una nueva entidad
  - Nombre
  - Persona de contacto (80 caracteres)
  - E-mail
  - Tfno
- Registrar colaborador en edición
  - Entidad
  - Cantidad monetaria
- Registrar patrocinador en edición
  - Entidad
  - Cantidad monetaria
- Mostrar entidades que ni patrocinan ni colaboran en una edición
- Dinero total obtenido en una edición
- Modificar el dinero aportado por un colaborador en una edición
- Mofidicar el dinero aportado por un patrocinador en una edición
- Mostrar entidades ordenadas por el dinero total aportado en todas las ediciones
- Eliminar colaborador de una edición
- Eliminar patrocinador de una edición

#### Condiciones

- Una entidad no puede colaborar y patrocinar en la misma edición
- No se puede modificar el dinero aportado por un colaborador o patrocinador si ya ha comenzado el torneo
- No se puede eliminar un patrocinador o colaborador si ya ha comenzado el torneo



### 7. Materiales/Pedidos

- Insertar nuevo material para una edición
  - Nombre (30 caracteres)
  - Patrocinador que lo suministra
  - Cantidad
- Realizar un pedido de material en una edicióno
  - Patrocinador
  - Material
  - Cantidad
  - Recibo
    - Número de pedido
    - Patrocinador
    - Materiales
    - Cantidad
- Asignar un pedido a un trabajador
  - Trabajador
  - Fecha
  - Pista de recogida
- Consultar trabajadores que tienen asignado un pedido un día concreto
  - Nombre
  - Apellidos
  - Número de pedido
  - Pista de recogida
  - Hora
- Cancelar asignación de un pedido
- Mostrar pedidos de una pista en una edición
  - Número de pedido
  - Material
  - Cantidad
  - Patrocinador
  - Trabajador
  - Fecha
- Mostrar trabajadores y número de pedidos asignados y ordenarlos por nº de pedidos en una edición
- Recibir pedido
- Cancelar pedido
- Mostrar los pedidos realizados a un patrocinador en una edición
  - Número de pedido
  - Materiales
  - Cantidad
  - Trabajador

#### Condiciones

- Un pedido solo puede contener materiales del mismo patrocinador
- No puedo asignar un pedido a un trabajador que no está trabajando a esa hora en esa pista
- No se puede cancelar un pedido que ya esté asignado a un trabajador
- No puedo cancelar la asignación de un pedido a un trabajador el mismo día en el que se va a entregar
- No puedo asignar un nuevo pedido al mismo trabajador con menos de una hora de diferencia
- Sólo se puede marcar un pedido como recibido después de la fecha en la que estaba prevista la entrega



> GRUPOS DE 5: 
>
> - 3 subsistemas a elegir 
> - 2 asignados 
> - 5 funcionalidades de cada uno

