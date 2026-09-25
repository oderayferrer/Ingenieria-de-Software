# Reglas que me dijeron en la consulta


En el **dado** debe ponerse las condiciones ya sean de falla o de éxito, es decir que es lo que dictamina que ese caso funcione(o no)
Por ejemplo: tenemos un cliente que debe ser mayor de 18 años y no adeudar nada, de ese cliente tenemos dni nombre apellido, el dado deberia decir: Dado un cliente de 20 años (mayor de 18) que no adeuda
En el dado de las fallas hay que poner solo lo que genera la falla

En el **cuando** deben ir los tipos que ingresa el usuario, siguiendo el ejemplo anterior, el cuando deberia decir: Cuando se ingresan los datos del cliente con dni 123455678 nombre "Pepe", apellido "Gomez" y se selecciona "CONTINUAR"
En el cuando siempre debe decirse que datos ingresa el usuario y donde aprieta para seguir

En el **entonces** de los casos de éxito debe ponerse además de lo que se muestra en pantalla lo que el sistema hace en ese caso de exito
En el **entonces** de los casos de error debe ponerse lo que se muestra en pantalla
==NUNCA lo que NO hace el sistema==


# FORMATO
[[Formato Historias de Usuario]] 
**ID:**

**TÍTULO:** Como  quiero para .

**REGLAS DE NEGOCIO:** Conjunto de reglas, normas, políticas, leyes, etc.
que condicionan el modo de operación (Requisitos no funcionales).

**CRITERIOS DE ACEPTACION:**

**Escenario :**
**Dado**
**Cuando** 
**Entonces** 



# Problema 1: Alquiler de mobiliario 
Suponga que trabaja en una consultora la cual ha sido recientemente contactada por una empresa de alquiler de mobiliario para eventos para la realización de una app. De las diferentes entrevistas se ha obtenido la siguiente información: El gerente nos dijo que resulta fundamental tener una aplicación móvil que nos permita manejar la agenda de la empresa, sabiendo qué disponibilidad tenemos y permitiendo que nuestros clientes alquilen a través de la app. Para esta primera versión de la app, el gerente nos pidió que sea posible dar de alta los diferentes mobiliarios, así como la posibilidad de que los usuarios puedan realizar una reserva de alquiler desde sus dispositivos. Para el detalle de cómo se realiza la carga de los muebles, el gerente nos sugirió hablar con el encargado del departamento de mobiliario. El encargado de mobiliario nos comentó que de cada mueble se debe cargar código de inventario, tipo de mueble, fecha de creación, fecha de último mantenimiento, estado (libre, de baja, alquilado) y el precio de alquiler. Además, no pueden existir códigos repetidos. Para que el encargado pueda dar de alta el mobiliario debe ==autenticarse en el sistema==. El registro de los usuarios de carga no debe modelarse. El encargado del departamento de alquileres no comentó acerca de las reservas de los alquileres. Por una política comercial de la marca una reserva tiene que incluir como mínimo 3 muebles. La reserva debe tener una fecha, lugar del evento, cantidad de días y mobiliario junto a su cantidad. Para realizar una reserva se debe abonar el 20% del total del alquiler. El pago de la reserva se realiza únicamente con tarjeta de crédito validando número de tarjeta y fondos a través de un servicio del banco. Luego de efectuado el pago, se emite un número de reserva único que será luego utilizado por el cliente para hacer efectivo el alquiler

**Usuario/Cliente:**
	Debe poder alquilar mobiliario desde la app en sus dispositivos
	Datos para alquilar: fecha, lugar del evento, cantidad de dias, mobiliario junto a su cantidad
	Regla: 
	una reserva tiene mínimo tres muebles
	
- **Pagos:**
	Se realiza unicamente con tarjeta de credito validando  el numero de tarjeta y fondos a traves de un servicio de banco
	Regla:
	Se debe abonar el 20 % del total del alquiler
	La tarjeta debe ser valida
	La tarjeta debe tener fondos suficientes para pagar el monto a abonar
	Unicamente con tarjeta de credito
	Recibe: numero de reserva unico

**Encargado de mobiliario**
	Debe poder dar de alta/cargar los diferentes mobiliarios
	Datos: código de inventario, tipo de mueble, fecha de creación, fecha de último mantenimiento, estado (libre, de baja, alquilado) y el precio de alquiler.
	Reglas:
	No pueden existir dos codigos repetidos
	el encargado de mobiliario debe autenticarse en el sistema


**ID**: Iniciar sesion.

**TÍTULO:** Como encargado de mobiliario quiero iniciar sesion
para poder acceder al sistema.

**CRITERIOS DE ACEPTACION:**

**Escenario 1: Inicio de sesion exitoso**
**Dado** un encargado de mobiliario registrado en el sistema con nombre de usuario/mail "carlosramirez@gmail.com", y contraseña 12345 correspondiente al usuario
**Cuando** el encargado de mobiliario ingresa su mail "carlosramirez@gmail.com" y contraseña 12345 y presiona "Iniciar sesion"
**Entonces** el sistema inicia la sesión del usuario y lo redirige a la pagina principal.

**Escenario 2: Inicio de sesion fallido por usuario inexistente**
**Dado** el nombre de usuario/mail "pabloperez@gmail.com" 
**Cuando** el encargado de mobiliario ingresa el mail "pabloperez@gmail.com" y la contraseña 54321 y presiona "Iniciar Sesion"
**Entonces** el sistema informa "Los datos ingresados son incorrectos"

**Escenario 3: Inicio de sesion fallido por contraseña incorrecta**
**Dado**  el nombre de usuario/mail "lisandromartinez@gmail.com" con una contraseña incorrecta 444444
**Cuando** el encargado ingresa sus datos mail "lisandromartinez@gmai.com" y la contraseña 444444 y presiona "Iniciar sesion"
**Entonces** el sistema informa "Los datos ingresados son incorrectos"

**ID**: Cerrar sesion.

**TITULO**: Como encargado de mobiliario quiero cerrar sesion para salir del sistema

**Escenario 1: cierre de sesion exitoso**
**Dado** un encargado que se encuentra autenticado en la aplicación con el usuario "carlosramirez@gmail.com"
**Cuando** el encargado de mobiliario presiona "Cerrar sesion"
**Entonces** el sistema cierra la sesion del usuario y redirige a la pagina de inicio de sesion

**ID: Cargar mobiliario** 

**TÍTULO:** Como encargado autenticado de mobiliario quiero dar de alta muebles para que se vean reflejados en el sistema.

**REGLAS DE NEGOCIO:** 
No pueden existir códigos repetidos

**CRITERIOS DE ACEPTACION:**

**Escenario 1: Carga exitosa**
**Dado**  el código de inventario 00001 no existente en el sistema
**Cuando**  ingresa los datos: código 0001, tipo de mueble "Sillon",fecha de creación "26/6/2026", fecha de ultimo mantenimiento "26/6/2026", estado "libre" y precio de alquiler $3000 y presiona "Cargar mobiliario"
**Entonces** la aplicacion carga el mobiliario en el sistema e informa "Mueble cargado con exito"

**Escenario 2: Carga fallida por codigo repetido**
**Dado**  el código de inventario 00001 que ya se encuentra registrado
**Cuando** el encargado ingresa los datos: código de mobiliario 00001, tipo de mueble "Estantería", fecha de creación "27/6/2026", fecha de ultimo mantenimiento "24/6/2026", estado "libre" y precio de alquiler $2000 "Cargar mobiliario"
**Entonces** la aplicación informa "No se ha podido realizar la carga ya que el codigo de mobiliario ya existe"

**Escenario 2: Carga fallida por datos incompletos**
**Dado** el dato faltante de estado
**Cuando** el encargado ingresa los datos: codigo de mobiliario 02345, tipo de mueble "Silla", fecha de creacion "27/6/2026", fecha de ultimo mantenimiento "23/5/2026", precio de alquiler $1000 y el campo de estado vacio y presiona "Cargar mobiliario"
**Entonces** la aplicación informa "No se han ingresado todos los datos requeridos"

**ID: Realizar reserva**

**TÍTULO:** Como cliente de la empresa quiero realizar una reserva de mobiliario para asegurar su disponibilidad en la fecha de mi evento.

**REGLAS DE NEGOCIO:** 
Una reserva debe que incluir al menos 3 muebles.


**CRITERIOS DE ACEPTACION:**

**Escenario 1: Reserva  exitosa**
**Dado** una selección por parte de un usuario de 3 muebles con estado libre disponibles de tipo "mesa" cargados en el sistema, con una fecha 28/9/2026, lugar "Salón las rosas", cantidad de días 2
**Cuando** el cliente ingresa la fecha 28/9/2026, lugar del evento "Salón las rosas", cantidad de días 2, tipo de mobiliario "mesa" con una cantidad seleccionada de 3,  y presiona "Reservar mobiliario"
**Entonces** la aplicación da de alta la reserva 1232 con estado "pendiente de pago" y redirige al cliente a la pantalla de pago para confirmar. 

**Escenario 2: Reserva fallida por cantidad mínima no alcanzada**
**Dado** una selección de dos muebles con estado "libre" de tipo "silla" disponibles cargados en el sistema
**Cuando** el cliente ingresa los datos con una fecha 28/9/2026, lugar "Salón las rosas", cantidad de días 2, mobiliario tipo "silla" con cantidad seleccionada de 2 y presiona "Reservar mobiliario"
**Entonces** el sistema informa "La reserva debe incluir un mínimo de 3 muebles para poder continuar"

**Escenario 3: Reserva fallida por falta de stock de muebles**
**Dado** el catalogo de mobiliario que cuenta con el tipo "mesa" cantidad de mobiliario 1 disponible en estado libre
**Cuando**  el cliente ingresa los datos con una fecha 28/9/2026, lugar "Salón las rosas", cantidad de días 2, mobiliario tipo "mesa" con cantidad seleccionada de 4 y presiona "Reservar mobiliario"
**Entonces** el sistema informa "No hay stock suficiente para los muebles seleccionados"


**ID: Pagar reserva**

**TÍTULO:** Como cliente de la empresa de alquiler de mobiliario quiero realizar una reserva de mobiliario para asegurar su disponibilidad en la fecha de mi evento.

**REGLAS DE NEGOCIO:** 
Se debe abonar el 20 % del total del alquiler
La tarjeta debe ser valida
La tarjeta debe tener fondos suficientes para pagar el monto a abonar
Únicamente con tarjeta de crédito

**CRITERIOS DE ACEPTACION:**



**Escenario 1: Pago exitoso**
**Dado** la reserva de mobiliario 1234 pendiente de pago, una tarjeta de crédito con un numero valido "4545 1234 5678 9012" valida con fondos suficientes de $10000 (referente al 20% del alquiler)
**Cuando** el cliente ingresa la tarjeta de crédito "4545 1234 5678 9012" y presiona el botón "Pagar"
**Entonces** el sistema valida y realiza el cobro del 20% del monto total e informa "Pago realizado" e informa al cliente su numero de reserva 1234

**Escenario 2: Reserva fallida por pago rechazado**
**Dado** la reserva de mobiliario 3452 pendiente de pago, una tarjeta de crédito con numero "4545 1234 5678 9012" valida que no cuenta con fondos suficientes $50 (referente al 20% de alquiler)
**Cuando** el cliente ingresa los datos  "4545 1234 5678 9012" con fondos insuficientes y presiona "Pagar"
**Entonces** el sistema informa "No se ha podido realizar la reserva por fondos insuficientes"

**Escenario 3: Pago fallido por tarjeta incorrecta** 
**Dado** la reserva de mobiliario 1234 pendiente de pago, una tarjeta de crédito con número incorrecto 1234 5678 9123 4569  
**Cuando** el cliente ingresa la tarjeta de crédito 1234 5678 9123 4569 y presiona el botón “Pagar” 
**Entonces** la aplicación informa “No se ha podido realizar el pago, la tarjeta ingresada no es válida”

**Escenario 4: Reserva fallida por intento de pago con tarjeta de debito**
**Dado** la reserva 6524 pendiente de pago, una tarjeta de debito con numero "6432 2345 1246 8253" con fondos suficientes
**Cuando**  el cliente ingresa los datos de una tarjeta de debito con numero "6432 2345 1246 8253" y presiona "Reservar mobiliario"
**Entonces** el sistema informa "Solo puede abonarse con tarjeta de credito"

**Escenario 5: Pago fallido por error de conexión con el servidor del banco** 
**Dada** la conexión con el servidor del banco fallida 
**Cuando** el cliente ingresa un número de tarjeta y presiona “Pagar” 
**Entonces** el sistema retorna un error por conexión no establecida. 



# ==Debería hacer realizar reserva y pago de reserva junto o separado?==
### RTA DE LA PROFE: SI, REVISAR EJEMPLO DE LA PRACTICA DE HU
## (SPOILER: ESTA MAL) Por que lo hice así: lo hice todo junto ya que la reserva y el generar el código único de reserva depende estrictamente de que se haya efectuado el pago con éxito, el pago es un sub-paso obligatorio de que la reserva ha sido realizada con éxito, el flujo de aceptación de la reserva explícitamente depende de tener mínimo 3 muebles y una tarjeta valida con fondos suficientes 

# Problema 2: Cadena hotelera
Se desea automatizar parte del trabajo que se realiza en una cadena hotelera. La empresa ya cuenta con un módulo de registro y seguridad que se encarga del registro de usuarios y del inicio de sesiones por lo que no deben modelarse.
Para que un usuario pueda reservar un hospedaje debe ingresar la fecha de ingreso, la cual debe estar dentro de los 90 días a partir de la fecha actual y la fecha de egreso. Las estadías no pueden durar más de 15 días. También debe
ingresar el hotel elegido y la cantidad de personas que desean hospedarse. Una vez realizada la reserva, el sistema envía un correo electrónico con un código de reserva y un enlace para continuar con el pago.
Para realizar el check in, todos los hoteles cuentan con terminales en las cuales el usuario debe ingresar el código de reserva. Si el código ingresado tiene una reserva para la fecha actual el sistema informa la habitación asignada y manda
un mensaje a alguno de los conserjes del hotel para que guíen al usuario hasta la habitación asignada y otro mensaje a los botones para que se hagan cargo de las valijas. Si el código ingresado no es válido, se informará dicha situación. Los
check in pueden realizarse después de las 10 am y hasta las 23:59 pm; fuera de ese horario, el sistema debe informar que aún no se encuentran habilitados los ingresos al hotel.
Por último los conserjes son los que realizan el check out, para lo cual deben ingresar un número de habitación. Solo se puede realizar check out de habitaciones sin gastos, de lo contrario el sistema deberá informar al conserje que no puede hacerse el check out hasta que no se abonen los gastos realizados. El registro de pago de gastos de una habitación no deberá modelarse en esta etapa. Cuando una habitación es liberada el sistema debe enviar un mensaje a las
mucamas del hotel avisando que la habitación puede limpiarse.

**Usuario**
	Debe poder reservar hospedaje (HU)
	Datos: 
	ingresar la fecha de ingreso, y la fecha de egreso, hotel elegido y la cantidad de personas que desean hospedarse
	Reglas:
	 la cual debe estar dentro de los 90 días a partir de la fecha actual 
	 Las estadías deben durar a lo sumo 15 días
	Recibe: por correo electrónico un código de reserva y un enlace para realizar el pago
	- Realizar check in:
	Datos: código de reserva
	Reglas: 
	el código ingresado debe ser de la fecha actual 
	debe ser correcto
	y deben ser entre las 10 am y 23.59 pm

**Conserje**
	Realizar check out:
	Datos: numero de habitacion
	Reglas:
	Solo check out de habitaciones sin gastos pendientes
	Recibe: Cuando una habitación es liberada el sistema debe enviar un mensaje a las mucamas del hotel avisando que la habitación puede limpiarse.

**ID: Realizar reserva**

**TÍTULO:** Como usuario del sistema quiero realizar una reserva de hospedaje para asegurar mi estadía en el hotel.

**REGLAS DE NEGOCIO:** 
	La fecha de ingreso debe estar dentro de los 90 días a partir de la fecha actual
	La estadía no puede durar mas de 15 días 

**CRITERIOS DE ACEPTACION:**

**Escenario 1: Reserva exitosa**
**Dado** la fecha actual "23/9/2026", fecha de ingreso "27/9/2026", fecha de egreso "1/10/2026", hotel "Gran hotel La Plata", cantidad de personas 2
**Cuando** el usuario ingresa la fecha de ingreso "27/9/2026", fecha de egreso "1/10/2026", hotel "Gran hotel La Plata", cantidad de personas 2 y presiona "Reservar"
**Entonces** el sistema da de alta la reserva, envía un correo electrónico con el código de reserva y una enlace para que el usuario realice el pago e informa "El código de reserva y el link de pago han sido enviados al email"

**Escenario 2: Reserva fallida por estadía superior a 15 días**
**Dado** Una fecha de ingreso "23/9/2026", una fecha de egreso "20/10/2026"
**Cuando** el usuario ingresa la fecha de ingreso "23/9/2026", fecha de egreso "20/10/2026", hotel "Gran hotel La Plata", cantidad de personas 2 y presiona "Reservar"
**Entonces** el sistema informa "El tiempo máximo de estadía es de 15 días"

**Escenario 3: Reserva fallida por fecha de ingreso fuera del rango de 90 dias**
**Dado** una fecha actual 23/9/2026 y una fecha de ingreso "20/10/2027"
**Cuando**  el usuario ingresa la fecha de ingreso "20/10/2027", fecha de egreso "25/10/2027", hotel "Gran hotel La Plata", cantidad de personas 2 y presiona "Reservar"
**Entonces** el sistema informa "La fecha de ingreso debe encontrarse dentro de los 90 días a partir de la fecha actual"


**ID: Check in**

**TÍTULO:** Como usuario del sistema quiero realizar el check in para poder ingresar a mi habitacion.

**REGLAS DE NEGOCIO:** 
	El código de reserva debe ser de la fecha actual
	El código ingresado debe ser correcto
	El horario de check in es a partir de las 10am hasta las 23.59 pm

**CRITERIOS DE ACEPTACION:**

**Escenario 1: Check in exitoso**
**Dado** Una fecha actual "23/9/2026" un código de reserva correcto 12345 para el día de la fecha "23/9/2026" en el horario 12.30 pm
**Cuando** el usuario ingresa su código de reserva 12345 y presiona "Realizar check-in"
**Entonces**  el sistema informa "Check-in realizado con exito, su habitacion es la 120" y manda un mensaje a alguno de los conserjes del hotel para que guíen al usuario hasta la habitación asignada y otro mensaje a los botones para que se hagan cargo de las valijas. 

**Escenario 2: Check-in fallido por fecha incorrecta**
**Dado** Una fecha actual "23/9/2026" y un código de reserva correcto para la fecha "24/9/2026"
**Cuando** el usuario ingresa su código de reserva 12356 y presiona "Realizar el check-in"
**Entonces** el sistema informa "El código de reserva no corresponde a una reserva realizada para el día de la fecha" 


**Escenario 3: Check-in fallido por horario fuera de rango**
**Dado** una fecha actual "23/9/2026" a las 8:30 am 
**Cuando** el usuario ingresa su código de reserva 3421 y presiona "Realizar check-in"
**Entonces** El sistema informa "El horario de ingreso es de 10 am a 23.59pm"

**ID: Check-out**

**TÍTULO:** Como conserje quiero realizar el check-out para liberar la habitacion.

**REGLAS DE NEGOCIO:** 
La habitacion no debe tener gastos pendientes

**CRITERIOS DE ACEPTACION:**

**Escenario 1: Check-out exitoso**
**Dado** una habitación ocupada con numero 120, la cual no adeuda pagos
**Cuando** el conserje ingresa el numero de una habitación  120 y presiona "Realizar check-out"
**Entonces** el sistema informa "Check-out realizado con éxito" y envía un mensaje a las mucamas del hotel avisando que la habitación 120 puede limpiarse.

**Escenario 2: Check-out fallido por falta de pago**
**Dado** una habitación con numero 303 ocupada que adeuda pagos
**Cuando** el conserje ingresa el numero de habitación 303 y presiona "Realizar check-out" 
**Entonces** el sistema informa "No puede hacerse el check out hasta que no se abonen los gastos realizados" 

**Escenario 3: Check-out fallido por numero de habitacion sin ocupar**
**Dado** una habitación con numero 105 sin ocupar
**Cuando** el conserje ingresa el numero de habitación 105 y presiona "Realizar check-out"
**Entonces** el sistema informa "No se puede realizar check-out a una habitación no ocupada"

# Problema 3: Venta de bebidas
Se desea modelar un sistema para el manejo de venta de bebidas alcohólicas en línea. Para poder empezar a comprar en el sitio, es necesario que las personas se registren ingresando nombre, apellido, mail (será utilizado como nombre de
usuario por lo tanto debe ser único) y edad. Solo se permite que se registren al sitio personas mayores a 18 años, de lo contrario el sistema debe mostrar en pantalla el texto de la ley que impide la venta de bebidas alcohólicas a menores. Si
el registro es exitoso el sistema genera una contraseña que es enviada al email ingresado en el registro.
Para comprar el usuario debe iniciar sesión y una vez logueado el sistema muestra una lista de bebidas, una vez que el usuario selecciona todos los productos que desea comprar, si el usuario es premium se le hace un descuento del 20%
y se informa en pantalla el total menos el 20%. Además si el usuario seleccionó productos por un monto superior a los $4500 se le hace un 10% de descuento y se informa en pantalla el total menos el 10%. Tenga en cuenta que si el usuario
es premium y compra por un monto superior a $4500 se deben aplicar ambos descuentos.

**Usuarios**
- Tienen que registrarse
	- Datos: nombre, apellido, mail (se usa como nombre de usuario único), edad
	- Requisitos:
		Deben ser mayores a 18 años
		Si es mayor de edad recibe la contraseña por mail 
		De lo contrario devuelve mensaje con la ley que impide la venta de bebidas alcohólicas a menores 

- Para comprar
	- debe iniciar sesión (por lo tanto poder cerrar sesion)
	- si el usuario es premium 20% de descuento
	- si el usuario gasta mas de $4500 se le hace 10% de descuento
	- si es premium y gasta mas de $4500 se aplican el del 20% y el del 10%
	- Devuelve: 
		- si aplica descuento se informa en pantalla el total menos el descuento

**ID: Registro de Usuario**

**TÍTULO:** Como persona quiero registrarme al sistema para comprar bebidas alcohólicas.

**REGLAS DE NEGOCIO:** 
Los clientes deben ser mayores de 18 años
El email debe ser unico

**CRITERIOS DE ACEPTACION:**

**Escenario 1: Registro exitoso**
**Dado** un nombre "Pedro", apellido "Diaz", email "pdiaz@gmail.com", con una edad de 43 años
**Cuando** el usuario ingresa los datos nombre "Pedro", apellido "Diaz", email "pdiaz@gmail.com", edad 43 años y presiona "Registrarse"
**Entonces** el sistema registra al usuario y lo redirige a la pagina de inicio del sistema, envía la contraseña al email "pdiaz@gmail.com" e informa "Se ha enviado la contraseña al email ingresado"


**Escenario 2: Registro fallido por mail existente en el sistema**
**Dado** Un email "pdiaz@gmail.com" ya existente en el sistema
**Cuando** el usuario ingresa nombre "Pedro", apellido "Diaz", email "pdiaz@gmail.com" edad 43 y presiona "Registrar"
**Entonces** el sistema informa "El email ingresado ya se encuentra registrado en el sistema"

**Escenario 3: Registro fallido por minoría de edad**
**Dado** Una edad de 17 años
**Cuando** el usuario ingresa nombre "Diego", apellido "Gomez", email "dgomez@gmail.com", edad 17 años y presiona "Registrar"
**Entonces** el sistema informa "Debe ser mayor de edad para registrarse en el sistema según la Ley 24.788 Prohíbase en todo el territorio nacional, el expendio a menores de dieciocho años, de todo tipo de bebidas alcohólicas. Créase el Programa Nacional de Prevención y Lucha contra el Consumo Excesivo de Alcohol." 

**ID: Iniciar sesión**

**TÍTULO:** Como usuario del sistema quiero iniciar sesión para comprar bebidas alcohólicas.

**CRITERIOS DE ACEPTACION:**

**Escenario 1: Inicio de sesión exitoso**
**Dado** un email "pdiaz@gmail.com" registrado en el sistema y una contraseña correcta "abc23653"
**Cuando** el usuario ingresa su mail "pdiaz@gmail.com" y su contraseña "abc23653" y presiona "Iniciar sesión"
**Entonces** el sistema abre la sesión y redirige al listado de bebidas alcohólicas


**Escenario 2: Inicio de sesión fallido por email incorrecto**
**Dado** un mail "tgutierrez@gmail.com" no registrado en el sistema
**Cuando** se ingresa el mail "tgutierrez@gmail.com" y la contraseña valida "ert1234" y se presiona "Iniciar sesión"
**Entonces** el sistema informa "Los datos ingresados son incorrectos"

**Escenario 3: Inicio de sesión fallido por contraseña incorrecta**
**Dado** un mail registrado "pdiaz@gmail.com" y una contraseña "34fasd" incorrecta
**Cuando** se ingresa el mail "pdiaz@gmail.com" y la contraseña "34fasd" y se presiona "Iniciar sesión"
**Entonces** el sistema informa "Los datos ingresados son incorrectos"

**ID: Cerrar sesión**

**TÍTULO:** Como usuario del sistema quiero cerrar sesión para salir del sitio.


**CRITERIOS DE ACEPTACION:**

**Escenario 1: Cierre de sesión exitoso**
**Dado** un usuario autenticado en el sistema con una sesión activa con el mail "pdiaz@gmail.com"
**Cuando** el usuario presione "Cerrar sesion"
**Entonces** el sistema cierra la sesión del usuario y lo redirige a la pagina de inicio de sesión 


**ID: Compra de bebidas**

**TÍTULO:** Como cliente quiero comprar bebidas para consumirlas.

**REGLAS DE NEGOCIO:** 
Si el usuario es premium se le aplica un 20% de descuento
Si el usuario gasta mas de $4500 se le aplica un 10% de descuento
Si el usuario es premium y gasta mas de $4500 se le aplican ambos descuentos

**CRITERIOS DE ACEPTACION:**

**Escenario 1: Compra exitosa sin descuentos**
**Dado** un usuario "cgalindez@gmail.com" que no es premium y una bebida "Cerveza" con un precio de $3000
**Cuando** se selecciona "Cerveza" con un monto de $3000 y se presiona "Aceptar"
**Entonces** el sistema muestra en pantalla "Monto total: $3000"


**Escenario 2: Compra exitosa con descuento premium**
**Dado** un usuario "pdiaz@gmail.com" que es premium y una bebida "Fernet" con un precio de $4000
**Cuando** se selecciona "Fernet" con un precio de $4000 y se presiona "Aceptar"
**Entonces** el sistema le aplica el 20% de descuento al monto total e informa "Monto total: 3200"


**Escenario 3: Compra exitosa con descuento de 10%**
**Dado** un usuario "cgalindez@gmail.com" que no es premium y una bebida "Gin" con un precio de $5000
**Cuando** se selecciona "Gin" con un precio de $5000 y se presiona "Aceptar"
**Entonces** el sistema le aplica el 10% de descuento al monto total e informa "Monto total: 4500"


**Escenario 4: Compra exitosa con ambos descuentos**
**Dado** un usuario "pdiaz@gmail.com" que es premium y una bebida "Gin" con un precio de $5000
**Cuando** se selecciona "Gin" con un precio de 5000 y se presiona "Aceptar"
**Entonces** el sistema le aplica el 30% de descuento al monto total e informa "Monto total: 3500"

# Problema 4: Préstamos de Kits​
El área de Tics de la facultad dispone de kits multimedia (cámara, micrófono y trípode) que estudiantes y docentes pueden solicitar para grabar presentaciones, entrevistas o material audiovisual para trabajos académicos.
Actualmente, los préstamos se coordinan de manera informal por mensajería instantánea, lo que provoca superposiciones, olvidos y dificultad para saber qué kits están disponibles.
Se desea desarrollar una aplicación web que permita a los usuarios gestionar estos préstamos de manera autónoma.
Para utilizar el sistema, las personas deben estar previamente registradas y autenticadas (el registro y la autenticación no deben modelarse).
Para solicitar un kit, el usuario debe indicar: tipo de kit (básico o avanzado), día, hora de retiro y duración del préstamo en horas. Los préstamos no pueden durar más de 3 horas.
Un usuario no puede solicitar un préstamo si tiene algún préstamo anterior activo.

Por otro lado, los administradores deben tener la posibilidad de agregar nuevos elementos que formarán parte de un kit (el armado del kit es otra funcionalidad que no debe modelarse). De cada elemento se registra número de serie (es único
por elemento), tipo de elemento (cámara, micrófono o trípode), precio de compra (no puede superar el millón de pesos), origen de fabricación del elemento y fecha de alta. Si el elemento no es nacional, entonces el sistema deberá guardar un impuesto adicional del 10% calculado sobre el precio de compra.

**Usuarios**
	Deben estar registrados y autenticados (no debe modelarse registro y autenticación)
	Datos: tipo de kit (básico o avanzado), día, hora de retiro y duración del préstamo en horas.
	Reglas:
		 El prestamo no puede durar mas de 3 horas
		No puede realizarse un prestamo con otro en curso

**Administradores**
	Pueden agregar nuevos elementos que formaran parte de un kit (el armado del kit es otra funcionalidad que no debe modelarse).
	Datos: 
		número de serie (es único por elemento), tipo de elemento (cámara, micrófono o trípode), precio de compra (no puede superar el millón de pesos), origen de fabricación del elemento y fecha de alta.
	Reglas:
	Precio de compra no puede superar el millón de pesos
	Si el origen de fabricacion no es nacional debe  guardar un impuesto adicional del 10% calculado sobre el precio de compra.
	El numero de serie es unico por elemento

**ID:**

**TÍTULO:** Como usuario del sistema quiero realizar un prestamo para utilizar los kits.

**REGLAS DE NEGOCIO:** 
El prestamo no puede durar mas de 3 horas
Puede solicitarse un prestamo a la vez

**CRITERIOS DE ACEPTACION:**

# ==CORRECCION DE LA PROFE: TIENE QUE DECIR LA DISPONIBILIDAD Y HACER ESCENARIO DE FALTA DE STOCK ==

**Escenario 1: Prestamo exitoso**
**Dado** una duración del prestamo de 2 horas, de tipo de kit básico que esta disponible para el día "3/10/2026" hora de retiro 13hs y duración de 2hs,el usuario no tiene prestamos al momento de la solicitud 
**Cuando** se selecciona tipo de kit básico, día "3/10/2026", hora de retiro 13hs y duración de 2hs y se presiona "Aceptar"
**Entonces** el sistema da de alta el prestamo y registra el kit en uso e informa "Solicitud del kit realizada con exito"

**Escenario 2: Prestamo fallido por duracion mayor a 3 horas**
**Dado** una duración de prestamo ingresada de 5 horas
**Cuando** se selecciona tipo de kit avanzado, día "3/10/2026", hora de retiro 13hs y duración de 5hs y se presiona "Aceptar"
**Entonces** el sistema informa "El prestamo no puede superar las 3 horas"

**Escenario 3: Prestamo fallido por tener otro activo**
**Dado** un usuario autenticado en el sistema con un prestamo activo
**Cuando** se selecciona tipo de kit básico, día "3/10/2026", hora de retiro 15hs y duración de 1hs y se presiona "Aceptar"
**Entonces** el sistema informa "No se puede realizar un prestamo con otro activo"

**Escenario 4: Solicitud fallida por falta de stock** 
**Dado** un kit de tipo “avanzado” sin stock en el sistema  
**Cuando** el usuario selecciona  tipo de kit “avanzado”, ingresa el día 13/08/2026, hora de retiro “18:45”, duración del préstamo en horas “2” y presiona el botón “Solicitar” 
**Entonces** el sistema informa “No hay stock disponible para el kit seleccionado”
 
 **ID: Agregar elementos**

**TÍTULO:** Como administrador quiero agregar elementos para que queden disponibles para su prestamo.

**REGLAS DE NEGOCIO:** 
El precio de compra no puede superar el millón de pesos
Si el origen de fabricación no es nacional debe guardar un impuesto adicional del 10% calculado sobre el precio de compra.
El numero de serie es único por elemento

**CRITERIOS DE ACEPTACION:**

**Escenario 1: Elemento nacional agregado con éxito**
**Dado** un código único de producto "F-3098" no registrado, tipo de elemento "cámara", precio de compra $500.000, origen nacional, fecha de alta "23/9/2026"
**Cuando** se ingresan los datos código único de producto "F-3098", tipo de elemento "cámara", precio de compra $500.000, origen nacional, fecha de alta "23/9/2026" y se presiona "Aceptar"
**Entonces** el sistema guarda el elemento e informa "Elemento agregado con exito"


**Escenario 2: Elemento importado agregado con éxito**
**Dado** un código único de producto "F-4598" no registrado, tipo de elemento "cámara", precio de compra $500.000, origen importado, fecha de alta "23/9/2026"
**Cuando** se ingresan los datos código único de producto "F-4598", tipo de elemento "cámara", precio de compra $500.000, origen importado, fecha de alta "23/9/2026" y se presiona "Aceptar"
**Entonces** el sistema calcula un 10% sobre el precio de compra, guarda el elemento con el impuesto adicional e informa "Elemento agregado con exito"

**Escenario 3: Elemento no agregado por código repetido**
**Dado** un código de producto "F-3098" el cual ya se encuentra registrado en el sistema
**Cuando** se ingresan los datos código de producto "F-3098", tipo de elemento "cámara", precio de compra $500.000, origen nacional, fecha de alta "23/9/2026" y se presiona "Aceptar"
**Entonces** el sistema informa "Error: el código del elemento ya se encuentra registrado en el sistema"

**Escenario 4: Elemento no agregado por precio de compra superior al millón de pesos**
**Dado** un precio de compra de $1.500.000
**Cuando** se ingresa un código único de producto "F-9335" no registrado, tipo de elemento "microfono", precio de compra $1.500.000, origen nacional, fecha de alta "23/9/2026" y se presiona "Aceptar"
**Entonces** el sistema informa "El precio de compra no puede superar el millon de pesos"

# Problema 5: Manejo de licencias
Se desea modelar un sistema para el seguimiento de pedidos de licencias médicas por parte de los empleados de la Provincia de Buenos Aires. Para solicitar una licencia el empleado debe estar registrado y correctamente autenticado en
el sistema.
Cuando un empleado quiere solicitar una licencia debe ingresar el tipo de licencia (presencial o telemedicina), la fecha de inicio de reposo, la matrícula de su médico personal, el diagnóstico y si es para el titular o para un familiar enfermo. Para poder solicitar una licencia el empleado debe tener más de 1 mes de antigüedad, de lo contrario el sistema debe informar el rechazo de la licencia.
Además podrá solicitar una licencia un empleado que no tenga una licencia vigente.
Para registrar una licencia, el sistema genera un código de licencia y lo envía vía ==mail a la casilla del empleado== con la confirmación de la licencia y los días otorgados.
Por otro lado, un administrativo podrá consultar las licencias solicitadas para lo cual ingresa el ==Cuil== del empleado y un rango de fechas y el sistema imprime un informe de las licencias solicitadas. Tenga en cuenta que por una cuestión de
costos se podrá imprimir un informe por mes para cada empleado.

**Empleado**
- Debe estar registrado y autenticado en el sistema
	Dato: cuil, mail

- Solicitar licencia
	- Datos:  tipo de licencia (presencial o telemedicina), la fecha de inicio de reposo, la matrícula de su médico personal, el diagnóstico y si es para el titular o para un familiar enfermo
	- Reglas:
		- Para poder solicitar una licencia el empleado debe tener más de 1 mes de antigüedad
	- Recibe: 
		- Para registrar una licencia, el sistema genera un código de licencia y lo envía vía mail a la casilla del empleado con la confirmación de la licencia y los días otorgados.


**Administrativo**
	Para consultar las licencias solicitadas
	Datos: 
		Cuil del empleado y un rango de fechas 
	Reglas:
		Limite de una impresión de informe por mes
	Recibe:
		Se imprime un informe de las licencias solicitadas 


**ID: Registrar empleado**

**TÍTULO:** Como empleado quiero registrarme en el sistema para solicitar licencias.


**CRITERIOS DE ACEPTACION:**

**Escenario 1: Registro exitoso**
**Dado** un CUIL no registrado en el sistema "23-56724534-2" perteneciente a un empleado de la Provincia de Buenos Aires y un email "pdiaz@gmail.com" no registrado en el sistema
**Cuando** se ingresa el mail "pdiaz@gmail.com", el CUIL "23-56724534-2", contraseña "abc123" y se presiona "Registrarse"
**Entonces** el sistema da de alta el nuevo usuario informa "Registro exitoso" y redirige a la pagina de inicio del sistema

**Escenario 2: Registro fallido por CUIL ya registrado**
**Dado** un CUIL  "23-56724534-2" ya registrado en el sistema
**Cuando** se ingresa el mail "pdiaz@gmail.com", el CUIL "23-56724534-2", contraseña "abc123" y se presiona "Registrarse"
**Entonces** el sistema informa "Ya existe un usuario con los datos ingresados"

**Escenario 3: Registro fallido por email ya registrado**
**Dado** un email "pdiaz@gmail.com" ya registrado en el sistema
**Cuando** se ingresa el mail "pdiaz@gmail.com", el CUIL "23-56724534-2", contraseña "abc123" y se presiona "Registrarse"
**Entonces** el sistema informa "Ya existe un usuario con los datos ingresados"

**Escenario 4: Registro fallido por no ser empleado de la Provincia de Buenos Aires**
**Dado** un CUIL "20-12344763-2" no registrado en el sistema, que no pertenece a un empleado de la Provincia de Buenos Aires
**Cuando** el empleado ingresa el mail "cgomez@gmail.com", el CUIL "20-12344763-2", contraseña "1234art" y presiona "Registrarse"
**Entonces** el sistema informa "El CUIL ingresado no pertenece a un empleado de la Provincia de Buenos aires"

# ==Modelo un escenario 4 de fallido para verificar que el usuario sea un empleado de la PBA o con haberlo puesto de condición en el id basta ???== SI!!! QUE NO PERTENECE

**ID: Iniciar sesión**

**TÍTULO:** Como empleado de la Provincia de Buenos Aires quiero iniciar sesión para pedir una licencia medica.

**CRITERIOS DE ACEPTACION:**

**Escenario 1: Inicio de sesión exitoso**
**Dado** un email "pdiaz@gmail.com" registrado en el sistema, con contraseña "abc123"
**Cuando** se ingresan los datos email "pdiaz@gmail.com", contraseña "abc123" y se presiona "Iniciar sesión" 
**Entonces** el sistema da de alta la sesión y redirige al usuario a la pantalla de inicio

**Escenario 2: Inicio de sesion fallido por email incorrecto**
**Dado** un email "pdiax@gmail.com" no registrado en el sistema
**Cuando** se ingresan los datos email "pdiax@gmail.com", contraseña "abc123" y se presiona "Iniciar sesión" 
**Entonces** el sistema informa "Los datos ingresados son incorrectos"

**Escenario 3: Inicio de sesion fallido por contraseña incorrecta**
**Dado** un email "pdiaz@gmail.com" registrado en el sistema con una contraseña erronea "acb123" 
**Cuando** se ingresan los datos email "pdiaz@gmail.com", contraseña "acb123" y se presiona "Iniciar sesión" 
**Entonces** el sistema informa "Los datos ingresados son incorrectos"

**ID: Cerrar sesion**

**TÍTULO:** Como usuario del sistema quiero cerrar sesión de mi cuenta para salir del sistema.

**CRITERIOS DE ACEPTACION:**

**Escenario 1: Cierre de sesión exitoso**
**Dado** un mail "pdiaz@gmail.com" con una sesión activa
**Cuando** se presiona "Cerrar sesión"
**Entonces** el sistema cierra la sesión del usuario y lo redirige a la pagina de inicio de sesión


**ID: Solicitar Licencia**

**TÍTULO:** Como empleado de la Provincia de Buenos Aires quiero solicitar una licencia medica para obtener los días de reposo.

**REGLAS DE NEGOCIO:** 
El empleado debe tener al menos un mes de antiguedad
Puede tener una sola licencia activa

**CRITERIOS DE ACEPTACION:**

==Misma pregunta, en el dado solo pongo un empleado de PBA con mas de un mes de antigüedad sin licencias activas o también ejemplifico los tipos ??? o solo pongo los tipos en el cuando==
**Escenario 1: Solicitud de licencia exitosa**
**Dado** un mail "pdiaz@gmail.com" autenticado en el sistema con diez años de antigüedad sin licencias vigentes 
**Cuando** se ingresan los datos tipo de licencia presencial, fecha de inicio "27/9/2026", matricula "MR-236324" diagnostico "esguince de tobillo" para "titular" y se presiona "Aceptar"
**Entonces** el sistema da de alta la solicitud, envía un mail a "pdiaz@gmail.com" informando el código de licencia 151456, confirmando la licencia con 2 semanas de reposo, muestra en pantalla "Solicitud registrada, enviamos un mail con la información de la licencia"

**Escenario 2: Solicitud de licencia rechazada por falta de antigüedad**
**Dado** un mail "cbenitez@gmail.com" autenticado en el sistema con 2 semas de antigüedad
**Cuando** se ingresan los datos tipo de licencia presencial, fecha de inicio "27/9/2026", matricula "MR-917424" diagnostico "gripe" para "titular" y se presiona "Aceptar"
**Entonces** el sistema informa "Debe poseer mas de un mes de antigüedad para poder solicitar licencias"

**Escenario 3: Solicitud de licencia rechazada por tener una activa**
**Dado** un mail "pdiaz@gmail.com" autenticado en el sistema con una licencia vigente
**Cuando** se ingresan los datos tipo de licencia presencial, fecha de inicio "2/10/2026", matricula "MR-73384" diagnostico "Laringitis" para "familiar" y se presiona "Aceptar"
**Entonces** el sistema informa "No se pueden solicitar licencias con una licencia activa"


**ID: Consultar licencias**

**TÍTULO:** Como administrativo quiero consultar licencias para imprimir informe de licencias solicitadas.

**REGLAS DE NEGOCIO:** 
Solo puede imprimirse un informe por mes por empleado

**CRITERIOS DE ACEPTACION:**
	Para consultar las licencias solicitadas
	Datos: 
		Cuil del empleado y un rango de fechas 
	Reglas:
		Limite de una impresión de informe por mes
	Recibe:
		Se imprime un informe de las licencias solicitadas 

**Escenario 1: Consulta exitosa**
**Dado** un Cuil "23-56724534-2" correspondiente a un usuario registrado, y el rango de fechas "23/9/2026"-"23/10/2026"
**Cuando** se ingresan los datos CUIL "23-56724534-2", rango de fechas "23/9/2026"-"23/10/2026" y se presiona "Consultar"
**Entonces** el sistema informa "Consulta exitosa" y manda a imprimir el informe de licencias solicitadas en el rango de fechas

**Escenario 2: Consulta fallida por limite excedido**
**Dado** un CUIL "23-56724534-2" el cual ya se ha hecho su informe mensual
**Cuando** se ingresan los datos CUIL "23-56724534-2",  rango de fechas "23/9/2026"-"23/10/2026" y se presiona "Consultar"
**Entonces** el sistema informa "Ya ha solicitado el informe mensual para este usuario"

**Escenario 3: Consulta fallida por cuil no registrado en el sistema**
**Dado**: un CUIL "25-23455654-2" que no pertenece a un usuario registrado
**Cuando** se ingresa el cuil "25-23455654-2", rango de fechas "4/6/2026"- "30/6/2026" y presiona consultar
**Entonces**El sistema informa que "El CUIL ingresado no pertenece a un usuario registrado en el sitema"


# Problema 6: Pago Electrónico
Se desea modelar un sistema de pago electrónico de impuestos y servicios en efectivo.
Cuando un cliente llega para realizar un pago, el empleado o el gerente de la sucursal ingresa el código de pago electrónico y el sistema se conecta con la central de cobro para recuperar los datos de la factura (empresa, nro de cliente, 1era fecha de vencimiento, 2da fecha de vencimiento, recargo, y monto original). Una vez recuperados los datos, el sistema debe verificar los vencimientos para determinar el monto a cobrar. Teniendo esto en cuenta, cuando el 2do vencimiento está vencido se debe informar que la factura no se puede cobrar por dicho motivo. Cuando el 1er vencimiento está vencido hay que aplicar el recargo al monto original. Si la factura no está vencida, se cobra el monto original.
Una vez al día, el gerente de la sucursal debe registrar en la central de cobros los pagos que hicieron los clientes. Para esto el sistema requiere la clave maestra y de ser correcta, recupera las transacciones de los impuestos y servicios cobrados en el día, se conecta a la central de cobro y se las envía. Cuando la central confirma la recepción exitosa, el sistema las registra como enviadas. Este último paso es importante porque no deben enviarse dos veces las transacciones. Si el gerente intenta enviar una segunda vez, el sistema no debe permitirlo.
Finalmente el Gerente puede ver las estadísticas de los impuestos y servicios cobrados. Para esto, se ingresa la clave maestra, un rango de fechas sobre las cuales debe calcularse las estadísticas y el sistema debe mostrar los montos y la
cantidad de cobros realizados, agrupando por empresa.
Tenga en cuenta que cada vez que el sistema debe conectarse a la central, debe enviarle un token (código que identifica al sistema). Una vez que la central valida el token, el sistema envía el requerimiento para recuperar los datos de la factura o el requerimiento para registrar los pagos del día según corresponda.

**Empleado/Gerente**
1. PAGOS ELECTRONICOS DE CLIENTES
	Ingresa: ingresa el código de pago electrónico
	El sistema se conecta con la central de cobro para recuperar los datos de la factura
	Datos: empresa, nro de cliente, 1era fecha de vencimiento, 2da fecha de vencimiento, recargo, y monto original
	Reglas: cuando el 2do vencimiento está vencido se debe informar que la factura no se puede cobrar por dicho motivo. Cuando el 1er vencimiento está vencido hay que aplicar el recargo al monto original. Si la factura no está vencida, se cobra el monto original.
2. REGISTRAR LOS COBROS DE LOS PAGOS AL SISTEMA
	Datos: Clave maestra (DEBE SER CORRECTA)
	Recibe: Transacciones de los impuestos y servicios cobrados en el dia
	Se conecta con la central de cobro y los registra
	Reglas: NO DEBEN ENVIARSE DOS VECES LAS TRANSACCIONES
3. VER ESTADISTICAS DE IMPUESTOS Y SERVICIOS COBRADOS
	Datos: Clave maestra, rango de fechas sobre las cuales debe calcularse las estadísticas
	El sistema muestra los montos y la cantidad de cobros realizados agrupando por empresa
	

> [!NOTE]
> Tenga en cuenta que cada vez que el sistema debe conectarse a la central, debe enviarle un token (código que identifica al sistema). Una vez que la central valida el token, el sistema envía el requerimiento para recuperar los datos de la factura o el requerimiento para registrar los pagos del día según corresponda.



**ID: Cobrar factura**

**TÍTULO:** Como ==empleado/gerente== del sistema quiero saber los montos de la factura para cobrarle al cliente. ==????==

**REGLAS DE NEGOCIO:**
Si la factura no esta vencida se cobra el monto original
Si la factura tiene vencido el 1er vencimiento se le cobra un recargo sobre el monto original
Si la factura tiene vencido el 2do vencimiento no se puede cobrar


código de pago electrónico empresa, nro de cliente, 1era fecha de vencimiento, 2da fecha de vencimiento, recargo, y monto original
**CRITERIOS DE ACEPTACION:**

# ==!!!! ACA COMO LO QUE SE INGRESA ES EL CODIGO DEL CLIENTE ESO ES LO UNICO QUE SE PONE EN EL CUANDO Y EN EL ENTONCES SE PONE QUE EL SISTEMA DEVUELVEN LOS DATOS ASI??? ESTA BIEN PERO EN EL DADO HAY QUE ACLARAR QUE EL TOKEN ES VALIDO Y QUE LA CONEXION CON LA CENTRAL ES EXITOSA==
**Escenario 1: Cobro exitoso sin vencimientos**
**Dado** la fecha actual 10/9/2026, el envió de token correcto, la conexión con la central de cobro exitosa, con un codigo de pago electronico 32543632 existente en el servidor y con primer fecha de vencimiento "28/9/2026"
**Cuando** se ingresa el código de pago electrónico 32543632  y se presiona "Consultar"
**Entonces** el sistema se conecta con la central y devuelve los datos empresa "Camuzzi", nro de cliente 6902, 1era fecha de vencimiento "28/9/2026", segunda fecha de vencimiento "8/10/2026", recargo $500, monto original $1000, y se muestra en pantalla los datos de la factura junto con el mensaje "El monto a cobrar es $1000", y se registra el pago correctamente

**Escenario 2: Cobro exitoso con primer vencimiento vencido (monto con recargo)** **Dado** la fecha actual "22/9/2026", el envió de token correcto, la conexión con la central de cobro exitosa, un código de pago electrónico 4520 cuya factura asociada superó el primer vencimiento de la fecha "20/9/2026" pero aún no el segundo "30/9/2026"
**Cuando** se ingresa el código de pago electrónico 4520 y se presiona "Consultar". 
**Entonces** el sistema valida el token, se conecta a la central, recupera los datos (empresa "Edelap", nro de cliente 1122, 1era fecha "20/9/2026", 2da fecha "30/9/2026", recargo $200, monto original $800), calcula el nuevo total aplicando el recargo, y se muestran en pantalla los datos junto con el mensaje "El monto a cobrar es $1000 (incluye recargo)".

**Escenario 3: Falla por segundo vencimiento vencido** 
**Dado** la fecha actual "22/9/2026"  el envió de token correcto, la conexión con la central de cobro exitosa, un código de pago electrónico "9988" cuya factura asociada ya ha superado su segunda fecha límite de vencimiento "20/9/2026. 
**Cuando** se ingresa el código de pago electrónico "9988" y se presiona "Consultar". 
**Entonces**  se conecta con la central, se recuperan los datos (empresa "Edelap", nro de cliente 1122, 1era fecha "10/9/2026", 2da fecha "20/9/2026", recargo $200, monto original $800) se muestra en pantalla un mensaje de error informando "La factura no se puede cobrar ya que el segundo vencimiento se encuentra vencido".

**Escenario 4: Cobro fallido por token rechazado**
**Dado** el envío de token vencido 
**Cuando** el empleado de la sucursal ingresa el código de pago 22223333 y presiona el botón "Cobrar" 
**Entonces** el sistema falla en la conexión con la central e informa "hubo un error en la autenticación en la central de cobro". 

**Escenario 5: Cobro fallido por error de conexión con la central**
**Dado** el envio del token correcto
**Cuando** el empleado de la sucursal ingresa el código de pago 98765432 y presiona el botón "Cobrar"
**Entonces** el sistema falla en la conexión con la central e informa "No se pude establecer la conexión con la central de cobro"

 **ID:** Registrar pagos diarios
 
 **TÍTULO:** Como gerente quiero registrar en la central los pagos que hicieron los clientes para asentar las transacciones realizadas
 
 **REGLAS DE NEGOCIO:**
	- Toda conexión con la central requiere el envió de un token identificador.
	- El sistema no debe permitir que las transacciones se envíen dos veces.

**CRITERIOS DE ACEPTACIÓN: 

**Escenario 1: Registro y envió exitoso de transacciones.**
**Dado** Un token valido, una conexión con la central de cobro exitosa, una clave maestra correcta "JAC8992" y un lote de "45" transacciones de cobros del día que aún no han sido enviadas. 
**Cuando** se ingresa la clave maestra "JAC8992" y presiona "Registrar"
**Entonces** el sistema recupera las transacciones de los impuestos y servicios cobrados en el día, se conecta a la central de cobro y se las envía, la central confirma la recepción exitosa, el sistema las registra como enviadas, e informa "Las 45 transacciones han sido enviadas y registradas con exito"

**Escenario 2: Falla por intento de envío duplicado** 
**Dado** una clave maestra "JAC8992" correcta, un token correcto, una conexion exitosa con la central, un lote de transacciones del día "20/9/2026" que ya se encuentran registradas previamente como enviadas en el sistema.
**Cuando** se ingresa la clave maestra "JAC8992" y se presiona "Registrar". **Entonces** se muestra en pantalla un mensaje advirtiendo "Las transacciones del día ya han sido enviadas anteriormente y no se permite un segundo envío".

**Escenario 3: Falla por clave maestra incorrecta** 
**Dado** una clave maestra ingresada "ERR000" que resulta ser incorrecta. 
**Cuando** se ingresa la clave maestra "ERR000" y se presiona "Registrar". 
**Entonces** se muestra en pantalla un mensaje indicando "La clave maestra ingresada es incorrecta".

**Escenario 4: Registro fallido por conexión fallida con la central**
**Dado** el envió correcto de un token valido y la clave maestra "JAC8992"
**Cuando** se ingresa la clave maestra "JAC8992" y se presiona "Registrar". 
**Entonces** el sistema recupera las transacciones del día, intenta conectarse con la central de cobros, falla e informa "Hubo un error en la conexión con la central de cobros"

**Escenario 5: Registro fallido por token inválido**
**Dado** que existe una clave maestra 33333 habilitada para operar en el sistema y un token incorrecto 
**Cuando** el gerente de la sucursal ingresa la clave maestra 33333 y presiona el botón "Registrar pagos del día" 
**Entonces** el sistema recupera las transacciones del día, se conecta con la central de cobros, la autenticación falla, y el sistema informa que hubo un error en la autenticación con la central de cobros 

**ID:** Consultar estadísticas

**TÍTULO:** Como gerente quiero consultar las estadísticas de los impuestos y servicios cobrados para analizar la información.

**REGLAS DE NEGOCIO:**
- El sistema debe mostrar los montos y la cantidad de cobros realizados, agrupando la información por empresa.
    

**CRITERIOS DE ACEPTACIÓN:**

**Escenario 1: Consulta exitosa de estadísticas con resultados.**
**Dado** una clave maestra "JAC8992" válida y un rango de fechas "01/09/2026 al 15/09/2026" que posee cobros de impuestos y servicios registrados.
**Cuando** se ingresa la clave maestra "JAC8992", el rango de fechas "01/09/2026 al 15/09/2026" y se presiona "Consultar estadísticas".
**Entonces** el sistema recupera los cobros de ese período, calcula los montos y cantidades agrupando por empresa, y muestra en pantalla el listado informando: "Camuzzi: 30 cobros, Monto total: $150.000 | Edelap: 15 cobros, Monto total: $80.000".

**Escenario 2: Falla por clave maestra incorrecta.**
**Dado** una clave maestra "ERR000" que resulta ser incorrecta.
**Cuando** se ingresa la clave maestra "ERR000", el rango de fechas "01/09/2026 al 15/09/2026" y se presiona "Consultar estadísticas".
**Entonces** se muestra en pantalla un mensaje indicando "La clave maestra ingresada es incorrecta, no se pueden visualizar las estadísticas".

**Escenario 3: Consulta exitosa pero sin registros en el rango de fechas.**
**Dado** un rango de fechas "01/01/2026 al 15/01/2026" en el cual no existen cobros registrados en el sistema.
**Cuando** se ingresa la clave maestra "JAC8992", el rango de fechas "01/01/2026 al 15/01/2026" y se presiona "Consultar estadísticas".
**Entonces** el sistema procesa la búsqueda sin encontrar coincidencias y muestra en pantalla un mensaje informando "No existen cobros registrados para el rango de fechas seleccionado".

### Problema 7: Transferencias vehiculares
Se desea modelar un sistema para el manejo de transferencias de vehículos de forma remota. Para poder transferir un vehículo se debe estar registrado en el sistema e iniciar sesión (tanto el registro como la autenticación forman parte de
otro módulo que no debe modelarse). Para iniciar el trámite de transferencia se debe ingresar la patente, el dni del vendedor y el dni del comprador. Para que una transferencia se lleve a cabo con éxito, la patente ingresada no debe
tener deudas y tanto el vendedor como el comprador deben ser mayores de 18 años. Si la transferencia puede realizarse con éxito, se le envía al mail del comprador un código para que realice el pago, caso contrario el sistema debe informar el motivo del rechazo.
Por otro lado el sistema debe permitir consultar el estado de una transferencia, para lo cual se debe ingresar una patente y el sistema informa el estado de la transferencia. 
Tenga en cuenta que se pueden hacer hasta tres consultas por
mes.

- **ID :** Iniciar tramite
- **Titulo:** : como usuario autenticado del sistema quiero iniciar un tramite para transferir mi vehiculo
- **REGLAS DE NEGOCIO:**
	- La patente no debe tener deudas
	- El vendedor y el comprador deben ser mayores de 18 años

**CRITERIOS DE ACEPTACION**

**Escenario 1 : Incio de tramite exitoso**
**Dado** Una patente "ARG 333" libre de deuda, perteneciente al auto del vendedor con dni 25678345 con una edad de 49 y un dni de comprador 26567456 con una edad de 48
**Cuando** se ingresan los datos patente "ARG 333", dni del vendedor 25678345, dni del comprador 26567456 y se presiona "Aceptar"
**Entonces** El sistema informa "Inicio de tramite exitoso, se le enviara al mail del comprador un codigo para que realice el pago" envia un mail e inicia el tramite 

**Escenario 2: Inicio de tramite fallido por comprador menor de edad** 
**Dado** Un dni de comprador 49345345 con una edad de 17 años
**Cuando** se ingresan los datos patente "RBG 123" libre de deuda, un dni de vendedor 25642345 con edad de 49 y se presiona "Aceptar"
**Entonces** El sistema informa "Inicio de tramite fallido, el comprador no puede ser menor de 18 años"

**Escenario 3: Inicio de tramite fallido por vendedor menor de edad**
**Dado** Un dni de vendedor 49234532 con una edad de 17 años
**Cuando** se ingresan los datos patente "TGH 682" libre de deuda, dni de comprador 34876142 con una edad de 39 años y se presiona "Aceptar"
**Entonces** el sistema informa "Inicio de tramite fallido, el vendedor no puede ser menor de 18 años"


**Escenario 4: Inicio de tramite fallido por patente con deuda**
**Dado** Una patente "PBT 163" que tiene deudas
**Cuando** se ingresan los datos dni de vendedor 3464234 de 38 años, dni de comprador 43567456 con edad de 25 años y se presiona "Aceptar"
**Entonces** El sistema informa "Inicio de tramite fallido, la patente ingresada tiene deudas"


Por otro lado el sistema debe permitir consultar el estado de una transferencia, para lo cual se debe ingresar una patente y el sistema informa el estado de la transferencia. 
Tenga en cuenta que se pueden hacer hasta tres consultas por
mes.

**ID: Consultar estado**

**TÍTULO:** Como cliente quiero consultar el estado de la transferencia para saber como va el proceso.

**REGLAS DE NEGOCIO:** 
Se pueden hacer hasta tres consultas por mes por patente

**CRITERIOS DE ACEPTACION:**

**Escenario 1: Consulta exitosa**
**Dado** una patente "ARG 333" valida que no fue consultada en el ultimo mes
**Cuando** se ingresa patente "ARG 333" y se presiona "Consultar"
**Entonces** el sistema informa "La patente esta en proceso"

**Escenario 2: Consulta fallida por exceso de consultas**
**Dado** una patente "ABC 123" valida que ya fue consultada 3 veces en el ultimo mes
**Cuando** se ingresa patente "ABC 123" y se presiona "Consultar"
**Entonces** el sistema informa "No se puede realizar mas de 3 consultas mensuales"

**Escenario 3: Consulta fallida por patente inexistente**
**Dado** una patente "NNN 000" que no esta registrada en el sistema
**Cuando** se ingresa patente "NNN 000" y se presiona "Consultar"
**Entonces** el sistema informa "La patente ingresada es inexistente"

# Problema 8: Concursos

Suponga que el área para la cual trabaja fue contactada para implementar un sistema para el manejo de concursos de los docentes de la Facultad de Informática.

El DOCENTE que quiera inscribirse a un concurso deberá registrarse previamente en el sistema. Para esto deberá ingresar los siguientes datos: Dni, nombre, apellido y dirección de mail. Una vez completado los datos el sistema mandará a la casilla de correo ingresada la contraseña asignada automáticamente. El mail debe ser único y será utilizado como nombre de usuario. Según el estatuto de la UNLP los dni permitidos para concursar son aquellos menores a 55 millones y mayores a 12 millones.

Una vez registrado el docente USUARIO puede inscribirse al concurso, para lo cual, una vez que haya ingresado al sistema, deberá seleccionar la materia a la cual desea inscribirse. Según el reglamento interno de la Facultad de informática que nos facilitó el jefe del área de personal, el docente no podrá inscribirse a más de 3 concursos. Cuando el docente acepta la inscripción el sistema deberá imprimir un comprobante.

Por último, para cumplir con la ordenanza número 123/19 de la UNLP, el JEFE DEL ÁREA DE CONCURSOS, el cual ya cuenta con un nombre de usuario y contraseña, deberá poder imprimir un listado con los inscriptos a una materia determinada para poder enviar dicho listado al secretario administrativo quien lo firma y eleva al decano de la Facultad. Suponga que el sistema Siu-Guaraní realiza una tarea similar a la solicitada y que puede consultar su implementación y registros.

Docente
	- Registrarse: 
		datos: dni (MENOR A 55 millones, MAYOR a 12 millones), nombre, apellido, mail (UNICO ya que es nombre de usuario)
		reglas: dni (MENOR A 55 millones, MAYOR a 12 millones),mail (UNICO ya que es nombre de usuario)
		RECIBE: en el correo contraseña

Usuario (ya registrado):
	inscribirse: 
	datos: materia
	reglas: no mas de 3 concursos
	recibe: impresion de comprobante

Jefe del area de concursos:
	ya tiene usuario y contraseña
	imprimir:
		listado con los inscriptos a la materia 
	debe enviar el listado al secretario administrativo quien lo firma y eleva al decano de la facultad
	Suponga que el sistema Siu-Guaraní realiza una tarea similar a la solicitada y que puede consultar su implementación y registros.

**ID: Registro**

**TÍTULO:** Como usuario quiero registrarme para usar el sistema.

**REGLAS DE NEGOCIO:** 
DNI debe estar entre 12 y 55 millones

**CRITERIOS DE ACEPTACION:**

**Escenario 1: Registro exitoso**
**Dado** un dni 23543345 (mayor a 12 millones, menor a 55 millones), un mail "jperez@gmail.com" no registrado 
**Cuando** se ingresa el nombre "Juan", apellido "Perez", mail "jperez@gmail.com", dni 23543345 y se presiona "Registrarse"
**Entonces** el sistema da de alta al usuario, genera una contraseña y la envía por mail e informa "Se le ha enviado un mail con la contraseña"

**Escenario 2: Registro fallido por email existente**
**Dado** un email "jperez@gmail.com" ya registrado en el sistema
**Cuando** se ingresa el nombre "Juan", apellido "Perez", mail "jperez@gmail.com", dni 23543345 y se presiona "Registrarse"
**Entonces** el sistema informa "Ya existe un usuario con los datos ingresados"

**Escenario 3: Registro fallido por dni fuera de rango**
**Dado** un dni 10567890 fuera del rango
**Cuando** se ingresan los datos nombre "Tomas", apellido "Dente", mail "tdente@gmail.com" dni 10567890 y se presiona "Registrarse"
**Entonces** el sistema informa "El dni debe ser mayor a 12 millones y menor a 55 millones"

**ID: Iniciar sesion**

**TÍTULO:** Como usuario quiero ingresar al sistema para inscribirme a concursos.


**CRITERIOS DE ACEPTACION:**

**Escenario 1: Inicio de sesión exitoso**
**Dado** un mail registrado en el sistema "jperez@gmail.com", con una contraseña valida para el usuario "abc123"
**Cuando** se ingresa el mail "jperez@gmail.com", contraseña "abc123" y se presiona "Iniciar sesión"
**Entonces** el sistema da de alta la sesión y redirige al usuario a la pagina de inicio

**Escenario 2: Inicio de sesión fallido por contraseña invalida**
**Dado** un mail registrado "jperez@gmail.com", con una contraseña incorrecta "acb123"
**Cuando** se ingresa el mail "jperez@gmail.com" contraseña "acb123" y se presiona "iniciar sesión"
**Entonces** el sistema informa "Los datos ingresados son incorrectos"

**Escenario 3: Inicio de sesión fallido por usuario no registrado**
**Dado** un mail no registrado "pdiaz@gmail.com" 
**Cuando** se ingresa el mail "pdiaz@gmail.com", contraseña "ytu123" y se presiona "Iniciar sesión"
**Entonces** el sistema informa "Los datos ingresados son incorrectos"

**ID: Cerrar sesion.**

**TITULO**: Como usuario del sistema quiero cerrar sesión para salir del sistema

**Escenario 1: cierre de sesion exitoso**
**Dado** un mail "carlosramirez@gmail.com" con una sesion activa
**Cuando** se presiona "Cerrar sesion"
**Entonces** el sistema cierra la sesion del usuario y redirige a la pagina de inicio de sesion


**ID: Realizar inscripción**

**TÍTULO:** Como docente quiero inscribirme a un concurso para postularme para un cargo.

**REGLAS DE NEGOCIO:** 
No puede inscribirse a mas de 3 concursos

**CRITERIOS DE ACEPTACION:**

**Escenario 1: Inscripción exitosa**
**Dado** el mail "pdiaz@gmail.com" de un usuario que no registra mas de 3 inscripciones a concursos
**Cuando** selecciona la materia "Matemática" y presiona "Inscribirse"
**Entonces** el sistema registra la inscripción, genera el comprobante e informa "Inscripción realizada con éxito"

**Escenario 2: Inscripción fallida por materia ya inscrita**
**Dado** el mail "pdiaz@gmail.com" de un usuario que ya se encuentra inscripto al concurso de "Matemática"
**Cuando** selecciona la materia "Matemática" y presiona "Inscribirse"
**Entonces** el sistema informa "Usted ya se encuentra inscripto en esta materia"

**Escenario 3: Inscripción fallida por superar cantidad maxima**
**Dado** el mail "pdiaz@gmail.com" de un usuario que ya se encuentra inscripto a 3 concursos
**Cuando** selecciona la materia "CADP" y presiona "Inscribirse"
**Entonces** el sistema informa "Ya ha superado el limite de 3 concursos por usuario"



Jefe del area de concursos:
	ya tiene usuario y contraseña
	imprimir:
		listado con los inscriptos a la materia 
	debe enviar el listado al secretario administrativo quien lo firma y eleva al decano de la facultad
	Suponga que el sistema Siu-Guaraní realiza una tarea similar a la solicitada y que puede consultar su implementación y registros.

**ID: Imprimir listado**

**TÍTULO:** Como jefe del área de concursos quiero imprimir el listado con los inscriptos para enviarlo al secretario administrativo.


**CRITERIOS DE ACEPTACION:**

**Escenario 1: Impresión exitosa (No vacía)**
**Dado** la materia "Matemática" que cuenta con 5 inscriptos
**Cuando** se selecciona "Matemática" y presiona "Imprimir listado"
**Entonces** el sistema imprime un listado con los datos (nombre, apellido, dni) de los 5 inscriptos a la materia

**Escenario 2: Impresión fallida por no tener inscriptos**
**Dado** la materia "Filosofía" que no cuenta con inscriptos
**Cuando** se selecciona "Filosofía" y presiona "Imprimir listado"
**Entonces** el sistema informa "La materia no cuenta con inscriptos"



# Problema 9: Créditos bancarios

Se desea modelar el manejo de créditos otorgados por un banco a sus clientes.

Los CLIENTES que desean pedir un crédito, deben iniciar un trámite a través de un sitio web del banco ingresando dni, nombre, apellido, mail, tipo de crédito (personal, vivienda, etc.) y monto solicitado. El sistema acepta el inicio de trámite si el dni ingresado corresponde a un cliente del banco y si el crédito solicitado no supera los $400.000. En caso de que no sea cliente del banco el sistema deberá enviar un correo electrónico al email ingresado con un instructivo para hacerse cliente del banco. Si el monto supera los $400.000 el sistema rechaza el inicio de trámite y muestra el mensaje “El monto solicitado excede el límite permitido”. Si los datos son correctos, el sistema almacena el trámite para que sea analizado por el área económica e imprime un número de comprobante para el cliente.

Por otro lado, los clientes pueden consultar el estado de un trámite, para esto es necesario que se ingrese un número de comprobante. Si el número de comprobante es válido, el sistema retorna un informe con el estado del mismo, de lo contrario mostrará un mensaje “trámite inexistente”. Si el cliente ingresa tres veces un código inexistente el sistema bloquea la ip (dirección de red de la máquina que efectúa la consulta) del cliente por 24 horas mostrando un mensaje “Usted ha excedido el número de consultas inválidas”.

Por último, el GERENTE del banco puede pedir un listado de créditos aprobados entre fechas. Si las fechas ingresadas son válidas, el sistema mostrará un listado con los créditos aprobados, de lo contrario mostrará un mensaje “las fechas ingresadas no son válidas”. El sistema utiliza un sistema de autenticación general del banco, por lo que no es necesario modelar el iniciar y cerrar sesión. Si no hay créditos aprobados para las fechas ingresadas el sistema mostrará el siguiente mensaje: ”No hay créditos aprobados en las fechas ingresadas”.


Usuario:
	Datos: ingresando dni, nombre, apellido, mail, tipo de crédito (personal, vivienda, etc.) y monto solicitado
	Reglas: dni ingresado corresponde a un cliente del banco y si el crédito solicitado no supera los $400.000
	Recibe:
		Si es < 400mil el sistema almacena el trámite para que sea analizado por el área económica e imprime un número de comprobante para el cliente.
		Si es > 400mil “El monto solicitado excede el límite permitido”
		Si no pertenece a cliente del banco "Los datos ingresados no pertenecen a un cliente del banco"
Consultar estado de tramite:
	Datos: Numero de comprobante
	Reglas: Si se ingresa 3 veces un código existente se bloquea la ip por 24 horas
	Recibe:
		Numero de comprobante:
			Si es valido retorna informe con el estado del mismo
			de lo contrario "Tramite inexistente"
		Bloqueo de ip:
			 “Usted ha excedido el número de consultas inválidas”.
Gerente:
	Datos: Fecha desde, fecha hasta
	Recibe
		Si son validas las fechas:
			 Listado de creditos aprobados
		Si no son validas:
			"Las fechas ingresadas no son validas"
	Reglas:
		 Si no hay créditos aprobados para las fechas ingresadas el sistema mostrará el siguiente mensaje: ”No hay créditos aprobados en las fechas ingresadas”.
**El sistema utiliza un sistema de autenticación general del banco, por lo que no es necesario modelar el iniciar y cerrar sesión.**



**ID: Solicitar crédito**

**TÍTULO:** Como cliente quiero iniciar la solicitud de un crédito para contar con el dinero.

**REGLAS DE NEGOCIO:**
El dni debe corresponder a un cliente del banco
El crédito solicitado no debe superar los $400.000



**CRITERIOS DE ACEPTACION:**

**Escenario 1: Solicitud exitosa**
**Dado** Un dni 43516523 perteneciente a un cliente del banco y un credito solicitado de $200000
**Cuando** se ingresan los datos dni 43516523, nombre oderay, apellido ferrer, mail "oferrer@gmail.com", crédito de tipo "personal", monto $200000 y presiona "Solicitar"
**Entonces** el sistema almacena el tramite, imprime el numero de comprobante del cliente e informa "Solicitud realizada con éxito"

**Escenario 2: Solicitud fallida por monto superior a 400000**
**Dado** un dni 43516523 perteneciente a un cliente del banco y un credito solicitado de $500000
**Cuando** se ingresan los datos dni 43516523, nombre "oderay", apellido "ferrer", mail "oferrer@gmail.com", crédito de tipo "personal", monto $500000 y presiona "Solicitar"
**Entonces** el sistema informa “El monto solicitado excede el límite permitido”

**Escenario 3: Solicitud fallida por no ser usuario del  banco**
**Dado** un dni 23542345 que no pertenece a un cliente del banco
**Cuando** se ingresan los datos dni 23542345, nombre "Roberto", apellido "Funes", dni "rfunes@gmail.com", credito tipo "vivienda", monto $300000 y presiona "Solicitar"
**Entonces** el sistema informa "Los datos ingresados no pertenecen a un cliente del banco"


**ID:**

**TÍTULO:** Como usuario quiero consultar el estado del tramite para saber como viene el proceso.

**REGLAS DE NEGOCIO:** 
Si supera en 3 veces el ingreso de código inexistente el sistema bloquea la ip por 24 horas

**CRITERIOS DE ACEPTACION:**

**Escenario 1: Consulta exitosa**
**Dado** un numero de comprobante 345124123 existente 
**Cuando** ingresa el numero de comprobante 345124123 y presiona "Consultar"
**Entonces** el sistema informa "En revisión"

**Escenario 2: Consulta fallida por numero de comprobante inexistente**
**Dado** un numero de comprobante 123456 inexistente,  sin ingreso previo de código inexistente
**Cuando** se ingresa el numero de comprobante 123456 y se presiona "Consultar"
**Entonces** el sistema informa "Tramite inexistente" y suma 1 intento fallido al contador

**Escenario 3: Consulta fallida por numero de comprobante inexistente + bloqueo** 
**Dado** un numero de comprobante 654321 inexistente, habiéndose ingresado previamente 2 veces un código inexistente
**Cuando** se ingresa el numero de comprobante 654321 y se presiona "Consultar"
**Entonces** el sistema bloquea la ip de la maquina que efectua la consulta por 24 horas e informa “Usted ha excedido el número de consultas inválidas”.

**Escenario 4: Consulta fallida por usuario bloqueado**
**Dado** una ip "265.252.452.33" bloqueada por exceder los 3 intentos
**Cuando** se ingresa el numero de comprobante 6534532 y se presiona "Consultar"
**Entonces** el sistema informa "Usuario bloqueado"


**ID: Listar créditos**

**TÍTULO:** Como gerente del banco quiero consultar el listado de créditos aprobados entre fechas para saber cuantos créditos se aprobaron.


**CRITERIOS DE ACEPTACION:**
Gerente:
	Datos: Fecha desde, fecha hasta
	Recibe
		Si son validas las fechas:
			 Listado de créditos aprobados
		Si no son validas:
			"Las fechas ingresadas no son validas"
	Reglas:
		 Si no hay créditos aprobados para las fechas ingresadas el sistema mostrará el siguiente mensaje: ”No hay créditos aprobados en las fechas ingresadas”.


**Escenario 1: Listado exitoso**
**Dado** un rango de fechas "1/9/2026" "15/9/2026" donde se han aprobado 10 créditos 
**Cuando** se ingresa el rango de fechas "1/9/2026" "15/9/2026" y se presiona "Listar"
**Entonces** el sistema devuelve un listado con los 10 créditos aprobados en el rango de fechas y lo informa en pantalla 

**Escenario 2: Listado fallido por fechas invalidas**
**Dado** una fecha actual "24/9/2026" y un rango de fechas invalido "1/11/2026" "1/12/2026" 
**Cuando** se ingresa el rango de fechas  "1/11/2026" "1/12/2026"  y se presiona "Listar"
**Entonces** el sistema informa "Las fechas ingresadas no son validas"

**Escenario 3: Listado fallido por no tener créditos aprobados**
**Dado**un rango de fechas "1/9/2026" "15/9/2026" donde no se han aprobado créditos 
**Cuando** se ingresa el rango de fechas "1/9/2026" "15/9/2026" y se presiona "Listar"
**Entonces** el sistema informa ”No hay créditos aprobados en las fechas ingresadas”.



# Problema 10: Manejo de canchas de tenis

Problema 10: Manejo de canchas de tenis
Suponga que la consultora para la cual trabaja ha sido contactada para realizar un sistema para el manejo de turnos en canchas de tenis.
Luego de varias reuniones con el cliente se ha concluido que es necesario la realización de un sistema web donde las personas interesadas puedan obtener turnos en diferentes canchas de tenis de un complejo. Para esto las personas
deben registrarse en la plataforma indicando nombre, apellido, mail (será utilizado como nombre de usuario), edad y domicilio. El cliente nos ha indicado que solo quiere que se registren personas mayores de edad (18 años o más). Una vez
que la persona se registra con éxito el sistema genera una contraseña que será enviada al correo que ha sido ingresado.
Una vez registrada la persona puede solicitar turnos en una cancha del complejo, para esto debe iniciar sesión previamente. El cliente desea que si un usuario falla tres veces al iniciar sesión su cuenta sea bloqueada.
Para solicitar un turno, el usuario ingresa cancha, fecha y hora. Si la cancha está libre el turno se le asigna al usuario informando “Su turno ha sido registrado con éxito”, si la cancha está ocupada se le informará “Cancha ocupada, por favor
seleccione otro día y horario”, dándole la posibilidad de volver a seleccionar un turno nuevo. El sistema no debe permitir dar turno con menos de 2 días a la fecha en que se solicita.

Usuario:
	- Deben registrarse:
		Datos:  nombre, apellido, mail (será utilizado como nombre de usuario), edad y domicilio. 
		Reglas: 
			Mail único
			Solo mayores de 18
		Recibe:
			Contraseña por correo electrónico
	-Debe iniciar sesión
	-Debe poder cerrar sesión
	- Solicitar turnos:
		Datos: cancha,fecha, hora
		Recibe:
			Si la cancha esta libre: “Su turno ha sido registrado con éxito”
			Si la cancha esta ocupada: “Cancha ocupada, por favor seleccione otro día y horario”
		Reglas: 
			El sistema no debe permitir dar turno con menos de 2 días a la fecha en que se solicita.

**ID: Registro**

**TÍTULO:** Como cliente quiero registrarme para utilizar el sistema.

**REGLAS DE NEGOCIO:** 
Solo pueden registrarse mayores de 18 años
Mail unico

**CRITERIOS DE ACEPTACION:**

**Escenario 1: Registro exitoso**
**Dado** una edad de 46 años y un mail no registrado "pdiaz@gmail.com"
**Cuando** se ingresan los datos nombre "Pedro", apellido "Diaz", edad 46, mail "pdiaz@gmail.com", domicilio "Calle falsa 123", una contraseña "abc123" y presiona "Registrarse"
**Entonces** el sistema da de alta al usuario, envía un mail con la contraseña e informa "La contraseña se ha enviado al mail ingresado"

**Escenario 2: Registro fallido por mail ya registrado**
**Dado** un mail ya registrado en el sistema "pdiaz@gmail.com"
**Cuando** se ingresan los datos nombre "Pedro", apellido "Diaz", edad 46, mail "pdiaz@gmail.com", domicilio "Calle falsa 123", una contraseña "abc123" y presiona "Registrarse"
**Entonces** el sistema informa "Ya existe un usuario con los datos ingresados"

**Escenario 3: Registro fallido por minoría de edad**
**Dado** una edad de 17 años 
**Cuando** se ingresan los datos nombre "Jose", apellido "Rodriguez", edad 17, mail "jrodriguez@gmail.com", domicilio "Calle falsa 123", una contraseña "abc123" y presiona "Registrarse"
**Entonces** el sistema informa "Error: Debe ser mayor de 18 para poder registrarse"

**ID: Iniciar sesion**

**TÍTULO:** Como usuario quiero ingresar al sistema para inscribirme a concursos.


**CRITERIOS DE ACEPTACION:**

**Escenario 1: Inicio de sesión exitoso**
**Dado** un mail registrado en el sistema "jperez@gmail.com", con una contraseña valida para el usuario "abc123"
**Cuando** se ingresa el mail "jperez@gmail.com", contraseña "abc123" y se presiona "Iniciar sesión"
**Entonces** el sistema da de alta la sesión y redirige al usuario a la pagina de inicio

**Escenario 2: Inicio de sesión fallido por contraseña invalida**
**Dado** un mail registrado "jperez@gmail.com", con una contraseña incorrecta "acb123"
**Cuando** se ingresa el mail "jperez@gmail.com" contraseña "acb123" y se presiona "iniciar sesión"
**Entonces** el sistema informa "Los datos ingresados son incorrectos"

**Escenario 3: Inicio de sesión fallido por usuario no registrado**
**Dado** un mail no registrado "pdiaz@gmail.com" 
**Cuando** se ingresa el mail "pdiaz@gmail.com", contraseña "ytu123" y se presiona "Iniciar sesión"
**Entonces** el sistema informa "Los datos ingresados son incorrectos"

**ID: Cerrar sesion.**

**TITULO**: Como usuario del sistema quiero cerrar sesión para salir del sistema

**Escenario 1: cierre de sesion exitoso**
**Dado** un mail "carlosramirez@gmail.com" con una sesion activa
**Cuando** se presiona "Cerrar sesion"
**Entonces** el sistema cierra la sesion del usuario y redirige a la pagina de inicio de sesion



**ID: Solicitar turnos**

**TÍTULO:** Como usuario del sistema quiero solicitar un turno para jugar en una cancha.

**REGLAS DE NEGOCIO:** 
El sistema no debe permitir dar turno con menos de 2 días a la fecha en que se solicita.

**CRITERIOS DE ACEPTACION:**

**Escenario 1: Solicitud de turno exitosa**
**Dado** una fecha actual "24/9/2026", una fecha para turno "1/10/2026", hora "16:00hs" cancha 1 (la cual esta libre para ese día y horario)
**Cuando** se ingresan los datos fecha para turno "1/10/2026", hora "16:00hs" cancha 1 y presiona "Solicitar turno"
**Entonces** el sistema da de alta el turno e informa “Su turno ha sido registrado con éxito”

**Escenario 2: Solicitud fallida por limite de fechas**
**Dado** una fecha actual "1/10/2026", una fecha para turno "1/10/2026"
**Cuando** se ingresan los datos fecha para turno "1/10/2026", hora "15:00hs" cancha 2 y presiona "Solicitar turno"
**Entonces** el sistema informa "No es posible solicitar un turno con menos de dos días de anticipación"

**Escenario 3: Solicitud fallida por cancha ocupada**
**Dado** una selección de cancha 2 que se encuentra ocupada para la fecha "28/9/2026" en el horario "14:00hs"
**Cuando** se ingresan los datos fecha "28/9/2026", hora "14:00hs", cancha 2 y presiona "Solicitar turno"
**Entonces** el sistema informa “Cancha ocupada, por favor seleccione otro día y horario” y le permite al usuario volver a seleccionar los datos del turno


# Problema 11: Autenticación OTP

Se desea modelar, a través de historias de usuario, un módulo de autenticación mediante códigos de un solo uso (OTP) para una aplicación web. Este módulo debe permitir que los usuarios inicien sesión de forma segura utilizando un código
enviado a su correo electrónico.​
El proceso de autenticación consta de dos pasos: la solicitud del código OTP y la validación del código.​
En la solicitud del código, el usuario debe ingresar su dirección de correo electrónico. El sistema verificará que el correo corresponda a un usuario previamente registrado y cuya cuenta se encuentre activa. Si la verificación es correcta, se generará un código OTP numérico de seis dígitos, aleatorio y de un único uso, con una vigencia máxima de cinco minutos.
El código será enviado al correo electrónico del usuario.​
Durante la vigencia del código, el usuario podrá solicitar un nuevo OTP. En ese caso, el código anteriormente generado perderá inmediatamente su validez y únicamente el último código enviado podrá ser utilizado para autenticarse.​
Para completar el inicio de sesión, el usuario deberá ingresar el código recibido por correo electrónico. Luego de realizar las verificaciones correspondientes, el sistema permitirá el acceso a la aplicación y registrará la fecha y hora del inicio de
sesión.

Solicitud del Código OTP:
	Datos: Mail
	Reglas: 
		El sistema verificará que el correo corresponda a un usuario previamente registrado y cuya cuenta se encuentre activa.
		Durante la vigencia del código, el usuario podrá solicitar un nuevo OTP. En ese caso, el código anteriormente generado perderá inmediatamente su validez y únicamente el último código enviado podrá ser utilizado para autenticarse.​
	Si la verificación es correcta, se generará un código OTP numérico de ==seis dígitos, aleatorio y de un único uso, con una vigencia máxima de cinco minutos. ==El código será enviado al correo electrónico del usuario.​


Validación del Código OTP:
	Para completar el inicio de sesión, el usuario deberá ingresar el código recibido por correo electrónico. Luego de realizar las verificaciones correspondientes, el sistema permitirá el acceso a la aplicación y registrará la fecha y hora del inicio de sesión.


**ID: Solicitar Codigo**

**TÍTULO:** Como usuario del sistema quiero solicitar un codigo para iniciar sesion.

**REGLAS DE NEGOCIO:** 
	La cuenta del usuario que solicita el codigo debe estar activa
	Cada código tiene vigencia de 5 minutos
	Solicitar un nuevo codigo invalida al anterior

**CRITERIOS DE ACEPTACION:**

**Escenario 1: Solicitud de codigo exitosa**
**Dado** un mail "pdiaz@gmail.com" previamente registrado, con su cuenta activa y sin codigos vigentes al momento de la solicitud
**Cuando** se ingresa el mail "pdiaz@gmail.com" y se presiona "Solicitar codigo"
**Entonces** el sistema genera un codigo OTP de seis digitos, aleatoreo, de unico uso con vigencia de 5 minutos y lo envía por correo electrónico e informa "Codigo enviado al correo electronico"

**Escenario 2: Solicitud de código exitosa con otro vigente**
**Dado** un mail "pdiaz@gmail.com" previamente registrado, con su cuenta activa y que cuenta con un codigo 735124 vigente al momento de la solicitud 
**Cuando** se ingresa el mail "pdiaz@gmail.com" y se presiona "Solicitar codigo"
**Entonces** el sistema invalida el código anterior 735124 y genera un codigo OTP de seis digitos, aleatoreo, de unico uso con vigencia de 5 minutos y lo envía por correo electrónico e informa "Codigo enviado al correo electronico"

**Escenario 3: Solicitud de codigo fallida por no pertenecer a una cuenta activa**
**Dado** un mail "oferrer@gmail.com" perteneciente a un usuario registrado con su cuenta inactiva
**Cuando** se ingresa el mail "oferrer@gmail.com" y se presiona "Solicitar codigo"
**Entonces** el sistema  informa "El mail ingresado no corresponde a una cuenta activa"

**Escenario 4: Solicitud de codigo fallida por mail  no registrado**
**Dado** un mail "msantamaria@gmail.com" no registrado en el sistema
**Cuando** se ingresa el mail "msantamaria@gmail.com" y se presiona "Solicitar codigo"
**Entonces** el sistema informa "El mail ingresado no corresponde a un usuario registrado"


**ID: Validar codigo**

**TÍTULO:** Como usuario del sistema quiero validar mi código para ingresar a mi cuenta.

**REGLAS DE NEGOCIO:** 
Cada código tiene vigencia de 5 minutos

**CRITERIOS DE ACEPTACION:**

**Escenario 1: Validacion exitosa**
**Dado** un código OTP 735124 con dos minutos pasados desde su creación correcto para el mail "pdiaz@gmail.com" 
**Cuando** se ingresa el código 735124 y se presiona "Iniciar sesión" 
**Entonces** el sistema permite el acceso a la aplicación y registra la fecha y hora del inicio de sesión.

**Escenario 2: Validacion fallida por codigo OTP expirado**
**Dado** un código OTP 735124 expirado
**Cuando** se ingresa el codigo 735124 y se presiona "Iniciar sesión" 
**Entonces** el sistema informa "El codigo ingresado ha expirado, solicite uno nuevo"

**Escenario 2: Validacion fallida por codigo OTP incorrecto**
**Dado** un código OTP 000000 incorrecto
**Cuando** se ingresa el codigo 735124 y se presiona "Iniciar sesión" 
**Entonces** el sistema informa "El código ingresado es incorrecto"










correcto / incorrecto no valido/invalido