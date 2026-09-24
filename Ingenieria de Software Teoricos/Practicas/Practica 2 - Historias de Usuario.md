# Formato
Historias de Usuario
Para cada Historia de Usuario se deben indicar los siguientes ítems:

[[Formato Historias de Usuario]]

### Ejercitación Práctica

Para cada problema planteado realice las tarjetas completas de todas las historias de usuario identificadas.

#### Problema 1: Alquiler de mobiliario​

Suponga que trabaja en una consultora la cual ha sido recientemente contactada por una empresa de alquiler de mobiliario para eventos para la realización de una app.

De las diferentes entrevistas se ha obtenido la siguiente información:

El gerente nos dijo que resulta fundamental tener una aplicación móvil que nos permita manejar la agenda de la empresa, sabiendo qué disponibilidad tenemos y permitiendo que nuestros clientes alquilen a través de la app. Para esta primera versión de la app, el gerente nos pidió que sea posible ==dar de alta los diferentes mobiliarios==, así como la posibilidad de que los ==usuarios puedan realizar una reserva de alquiler desde sus dispositivos.== Para el detalle de cómo se realiza la carga de los muebles, el gerente nos sugirió hablar con el encargado del departamento de mobiliario. El encargado de mobiliario nos comentó que ==de cada mueble se debe cargar código de inventario, tipo de mueble, fecha de creación, fecha de último mantenimiento, estado (libre, de baja, alquilado) y el precio de alquiler.== Además, ==no pueden existir códigos repetidos.== Para que el ==encargado pueda dar de alta el mobiliario debe autenticarse en el sistema. El registro de los usuarios de carga no debe modelarse.==

El encargado del departamento de alquileres no comentó acerca de las reservas de los alquileres. Por una política comercial de la marca una ==reserva tiene que incluir como mínimo 3 muebles. La reserva debe tener una fecha, lugar del evento, cantidad de días y mobiliario junto a su cantidad. Para realizar una reserva se debe abonar el 20% del total del alquiler. El pago de la reserva se realiza únicamente con tarjeta de crédito validando número de tarjeta y fondos a través de un servicio del banco. Luego de efectuado el pago, se emite un número de reserva único que será luego utilizado por el cliente para hacer efectivo el alquiler.==
 

- **ID:** Registrar mobiliario
- **TÍTULO:** Como encargado de mobiliario quiero registrar un nuevo mueble para que esté disponible para el alquiler.
- **REGLAS DE NEGOCIO:**
    - No pueden existir códigos de inventario repetidos.

 
**CRITERIOS DE ACEPTACIÓN: 
(revisión: Por cada uno de los tipos debo dar un ejemplo )**
Escenario 1: Registro exitoso
Dado un código de inventario "001" que no existe en el sistema, tipo de mueble "Silla", fecha de creación "16/9/2026", fecha de ultimo mantenimiento "16/9/2026", estado "libre" y precio de alquiler $1500
Cuando se ingresan los datos del mobiliario y se intenta guardar,
Entonces se muestra un mensaje de éxito indicando que el mueble está disponible para alquilar.

**Escenario 2: Error por código repetido**
**Dado** un código de inventario "001" que no existe en el sistema, tipo de mueble "Sillón", fecha de creación "16/9/2026", fecha de ultimo mantenimiento "16/9/2026", estado "libre" y precio de alquiler $3000
**Cuando** se ingresan los datos del mobiliario y se intenta guardar,
**Entonces** se muestra un mensaje de error indicando que el codigo ingresado ya existe

**Escenario 3: Registro fallido por datos incompletos.** 
**Dado** un codigo de inventario "002" que no existe en el sistema, tipo de mueble "Mesa", fecha de creacion "16/9/2026", fecha de ultimo manteminimiento "16/9/2026", estado "libre" , dejando el campo de precio de alquiler vacio 
**Cuando** se intenta guardar el mobiliario, 
**Entonces** se muestra un mensaje indicando que el precio de alquiler es un campo obligatorio.


- **ID:** Reservar mobiliario
- **TÍTULO:** Como cliente del sistema quiero realizar una reserva de alquiler de un mueble para asegurarlo para mi evento.
- **REGLAS DE NEGOCIO:**
	 - La reserva debe incluir como mínimo tres muebles
	 - La reserva se realiza abonando el 20% del total del alquiler
	 - El pago se realiza únicamente con tarjeta de crédito 
	 - Se debe validar tarjeta y fondos a través de un servicio del bando
	 - El numero de reserva es único y se crea obligatoriamente para cada reserva para hacer efectivo el alquiler ???

**CRITERIOS DE ACEPTACIÓN: 
tres muebles de que tipo que tienen disponibilidad para las fechas 
**Escenario 1: Reserva y pago exitoso
**Dado** una seleccion de 4 muebles (3 sillas, 1 mesa), fecha de evento "20/10/2026", lugar "Salon de las rosas", cantidad de dias "2" y una tarjeta de credito valida y con fondos suficientes
**Cuando** se ingresan los datos de tarjeta para pagar el 20% y confirmar la reserva,
**Entonces** se muestra un mensaje de pago exitoso junto a un numero de reserva unico.
(el sistema conecta con el banco, cobra el 20% de su reserva y emite un numero de reserva único para que el cliente haga efectivo su alquiler y se lo muestra)???

**Escenario 2: Pago rechazado por falta de fondos
**Dado** una seleccion de 5 muebles (3 sillas, 1 mesa, 1 sillon), fecha de evento "29/11/26", lugar "Salon dorado", cantidad de dias "2" y una tarjeta de credito valida con fondos insuficientes,
**Cuando** se ingresan los datos de la tarjeta para pagar el 20% y confirmar la reserva,
**Entonces** se muestra un mensaje informando que el pago fue rechazado por falta de fondos.
(el sistema recibe el rechazo del banco, se da de baja la reserva debido a falta y se lo informa al cliente)???

**Escenario 3: Cantidad mínima no alcanzada 
**Dado** una seleccion de 2 muebles (2 sillones), fecha de evento "20/10/26", lugar "Salon de las rosas", cantidad de dias "2" y una tarjeta de credito valida y con fondos suficientes,
**Cuando** se intenta confirmar la reserva para proceder con el pago
**Entonces** se muestra un mensaje indicando que el mínimo requerido son tres muebles.

**Escenario 4: Datos obligatorios no ingresados 
**Dado** una seleccion de 4 muebles (2 sillones, 2 sillas), fecha de evento "20/10/26", lugar "Salon de las rosas" y una tarjeta de crédito valida y con fondos suficientes, dejando el campo cantidad de días vacío
**Cuando** se quiere confirmar la reserva y proceder con el pago
**Entonces** se muestra un mensaje indicando que los datos del evento son obligatorios.

#### Problema 2: Cadena hotelera
Se desea automatizar parte del trabajo que se realiza en una cadena hotelera. La empresa ya cuenta con un módulo de registro y seguridad que se encarga del registro de usuarios y del inicio de sesiones por lo que no deben modelarse.
Para que un usuario pueda reservar un hospedaje debe ingresar la fecha de ingreso, la cual debe estar dentro de los 90 días a partir de la fecha actual y la fecha de egreso. Las estadías no pueden durar más de 15 días. También debe
ingresar el hotel elegido y la cantidad de personas que desean hospedarse. Una vez realizada la reserva, el sistema envía un correo electrónico con un código de reserva y un enlace para continuar con el pago.
Para realizar el check in, todos los hoteles cuentan con terminales en las cuales el usuario debe ingresar el código de reserva. Si el código ingresado tiene una reserva para la fecha actual el sistema informa la habitación asignada y manda
un mensaje a alguno de los conserjes del hotel para que guíen al usuario hasta la habitación asignada y otro mensaje a los botones para que se hagan cargo de las valijas. Si el código ingresado no es válido, se informará dicha situación. Los
check in pueden realizarse después de las 10 am y hasta las 23:59 pm; fuera de ese horario, el sistema debe informar que aún no se encuentran habilitados los ingresos al hotel.
Por último los conserjes son los que realizan el check out, para lo cual deben ingresar un número de habitación. Solo se puede realizar check out de habitaciones sin gastos, de lo contrario el sistema deberá informar al conserje que no puede hacerse el check out hasta que no se abonen los gastos realizados. El registro de pago de gastos de una habitación no deberá modelarse en esta etapa. Cuando una habitación es liberada el sistema debe enviar un mensaje a las
mucamas del hotel avisando que la habitación puede limpiarse.

- **ID:** Reservar hospedaje
- **TÍTULO:** Como cliente del sistema quiero realizar una reserva para asegurar mi estadía en el hotel
- **REGLAS DE NEGOCIO:**
	 - La fecha de ingreso debe estar dentro del plazo de los siguientes 90 días a partir de la fecha actual
	 - La estadía no puede durar mas de 15 días

**CRITERIOS DE ACEPTACIÓN: 

**Escenario 1: Reserva y pago exitoso
**Dado** un cliente que selecciono una fecha valida "20/10/26" (Dentro de los próximos 90 días a partir de la fecha actual), con su fecha de egreso "25/10/26"  (sin superar los 15 días de estadía) , el hotel "Hotel Arena Blanca" y la cantidad de personas "4"
**Cuando** se intenta confirmar la reserva
**Entonces** se muestra un mensaje confirmando la reserva y avisando que se ha enviado un correo electronico con el codigo y enlace de pago.

**Escenario 2: Reserva fallida por fecha de ingreso excedida 
**Dado** una fecha de ingreso "1/10/27" (superior a 90 dias), una fecha de egreso "5/10/27", el hotel "Gran hotel La Plata", con cantidad de personas "2"
**Cuando** se quiere confirmar la reserva
**Entonces** se muestra un mensaje de error indicando que la fecha de ingreso supera el plazo de 90 días a partir de la fecha actual. 

**Escenario 3: Reserva fallida por estadía prolongada. 
**Dado** una fecha de ingreso "1/11/26", una fecha de egreso "3/1/27", el hotel "Gran hotel La Plata", cantidad de personas "3"
**Cuando** se quiere confirmar la reserva
**Entonces** se muestra un mensaje de error indicando que la estadia maxima permitida es de 15 dias.

- **ID:** Realizar Chek-in
- **TÍTULO:** Como cliente del sistema quiero realizar una reserva para asegurar mi estadía en el hotel
- **REGLAS DE NEGOCIO:**
	 - Deben realizarse a partir de las 10am hasta las 23:59pm.
	 - El código de reserva debe ser valido y tener una reserva para la fecha actual

**CRITERIOS DE ACEPTACIÓN: 

**Escenario 1: Chek-in exitoso. 
**Dado** un codigo de reserva "0001" correspondiente a la fecha actual y la hora "15:00"
**Cuando** se ingresa el codigo en la terminal
**Entonces** se muestra en pantalla la habitacion asignada "104" junto con un mensaje informando que el conserje y el botones van en camino

**Escenario 2: Chek-in fallido por código invalido. 
**Dado** un codigo de reserva "023412" (inexistente o de otra fecha), la hora "12:00 pm"
**Cuando** se ingresa el codigo en la terminal
**Entonces** se informa en pantalla que el codigo ingresado no es valido o no corresponde al dia de hoy.

**Escenario 3: Chek-in fallido por horario no habilitado
**Dado** un codigo de reserva "012334" y la hora "8:15"
**Cuando** se ingresa el codigo en la terminal
**Entonces** se muestra en pantalla un mensaje informando que aun no se encuentran habilitados los ingresos al hotel

- **ID:** Realizar Check-out
- **TÍTULO:** Como conserje quiero realizar el check out de una habitación para liberarla y habilitar su limpieza.
- **REGLAS DE NEGOCIO:**
	 - Solo se puede realizar check out de habitaciones sin gastos pendientes.

**CRITERIOS DE ACEPTACIÓN: 

**Escenario 1: Check-out exitoso. 
**Dado** el numero de habitacion "104", con $0 en gastos pendientes, 
**Cuando** se ingresa el numero de habitacion para efectuar la salida, 
**Entonces** se muestra un mensaje confirmando que la habitacion fue liberada y que se envio el aviso de limpieza a las mucamas

**Escenario 2: Check-out fallido por gastos pendientes.**

**Dado** el numero de habitacion "100" con $400 en gastos pendientes, 
**Cuando** se ingresa el numero de habitacion para efectuar la salida 
**Entonces** se muestra un mensaje advirtiendo que no se puede realizar el check-out hasta que se abonen los gastos pendientes.

#### Problema 3: Venta de bebidas
Se desea modelar un sistema para el manejo de venta de bebidas alcohólicas en línea. Para poder empezar a comprar en el sitio, es necesario que las personas se registren ingresando nombre, apellido, mail (será utilizado como nombre de
usuario por lo tanto debe ser único) y edad. Solo se permite que se registren al sitio personas mayores a 18 años, de lo contrario el sistema debe mostrar en pantalla el texto de la ley que impide la venta de bebidas alcohólicas a menores. Si
el registro es exitoso el sistema genera una contraseña que es enviada al email ingresado en el registro.
Para comprar el usuario debe iniciar sesión y una vez logueado el sistema muestra una lista de bebidas, una vez que el usuario selecciona todos los productos que desea comprar, si el usuario es premium se le hace un descuento del 20%
y se informa en pantalla el total menos el 20%. Además si el usuario seleccionó productos por un monto superior a los $4500 se le hace un 10% de descuento y se informa en pantalla el total menos el 10%. Tenga en cuenta que si el usuario
es premium y compra por un monto superior a $4500 se deben aplicar ambos descuentos.


- **ID:** Realizar registro
- **TÍTULO:** Como usuario quiero realizar el registro en el sitio para poder realizar compras
- **REGLAS DE NEGOCIO:**
	 - El usuario debe tener mas de 18 años.
	 - Si la persona es menor, el sistema debe mostrar en pantalla el texto de la ley que impide la venta de bebidas alcohólicas a menores.==????==
	 
**CRITERIOS DE ACEPTACIÓN: 

**Escenario 1: Registro exitoso. 
**Dado** el nombre "Pepito", apellido "Gomez", mail  "pepitogomez@gmail.com", edad 36 años.
**Cuando** se ingresan los datos para realizar el registro, 
**Entonces** se informa que el registro ha sido exitoso y que se ha enviado un mail a "pepitogomez@gmail.com" con la contraseña generada.

**Escenario 2: Registro fallido por minoría de edad.**

**Dado** el nombre "juan", apellido "perez", mail "juanperez@hotmail.com", edad 17 años 
**Cuando**  se ingresan los datos para realizar el registro, 
**Entonces** Se muestra en pantalla un mensaje de error de registro por edad insuficiente y el texto de la ley que impide la venta de bebidas alcohólicas a menores.

%%**Dado** una edad de 17 años 
**Cuando**  se ingresan los datos  nombre "juan", apellido "perez", mail "juanperez@hotmail.com",  para realizar el registro, 
**Entonces** Se muestra en pantalla un mensaje de error de registro por edad insuficiente y el texto de la ley que impide la venta de bebidas alcohólicas a menores.
en los errores en el cuando se dan los datos? y dado el error?
%%

**Escenario 3: Registro fallido por mail ya existente.**
**Dado** el nombre "pepito", apellido "gomez catan", con el email "pepitogomez@gmail.com" (que ya se encuentra registrado), con la edad 23 años
**Cuando** se ingresan los datos para realizar el registro,
**Entonces** se informa en pantalla que el nombre de usuario(email) ya se encuentra registrado.


- **ID:** Comprar bebidas
- **TÍTULO:** Como usuario registrado en el sitio quiero ver la lista de productos para realizar compras
- **REGLAS DE NEGOCIO:**
	 - Si el usuario es premium se le hace un descuento del 20% y se informa en pantalla el total menos el 20%.
	 - Si el usuario selecciono un monto superior a los $4500 se le debe realizar un 10% de descuento e informar el monto a pagar menos el 10% en pantalla.
	 - Si el usuario es premium y realizo una compra mayor a $4500 deben aplicarse ambos descuentos

**CRITERIOS DE ACEPTACIÓN: 

**Escenario 1: Compra sin descuentos.**
**Dado** un usuario regular (no-premium) logueado en el sistema con una compra de $3000 
**Cuando** se quiere proceder al pago, 
**Entonces** se informa en pantalla que el total a pagar es $3000.

**Escenario 2: Compra con descuento de usuario premium**
**Dado** un usuario premium logueado en el sistema, con un carrito de compra con un monto de $3000
**Cuando** se quiere proceder al pago, 
**Entonces** muestra en pantalla el monto final (descuento del 20% al monto de su compra ).

**Escenario 3: Compra con descuento por superar los $4500**
**Dado** un usuario regular (no-premium) logueado en el sistema,  con un carrito de compra por $5000
**Cuando** se quiere proceder con el pago
**Entonces** se muestra en pantalla el monto total con el descuento del 10% y se informa que las compras con un monto superior a $4500 tienen el 10% de descuento

**Escenario 4: Compra con ambos descuentos**
**Dado** un usuario premium logueado en el sistema con un carrito de compra por $5000
**Cuando** se quiere proceder con el pago
**Entonces** se muestra en pantalla el monto final ( monto total aplicando 10% por compra superior a $4500 y 20% por usuario premium).


### Problema 4: Préstamos de Kits​
El área de Tics de la facultad dispone de kits multimedia (cámara, micrófono y trípode) que estudiantes y docentes pueden solicitar para grabar presentaciones, entrevistas o material audiovisual para trabajos académicos.
Actualmente, los préstamos se coordinan de manera informal por mensajería instantánea, lo que provoca superposiciones, olvidos y dificultad para saber qué kits están disponibles.
Se desea desarrollar una aplicación web que permita a los usuarios gestionar estos préstamos de manera autónoma.
Para utilizar el sistema, las personas deben estar previamente registradas y autenticadas (el registro y la autenticación no deben modelarse).
Para solicitar un kit, el usuario debe indicar: tipo de kit (básico o avanzado), día, hora de retiro y duración del préstamo en horas. Los préstamos no pueden durar más de 3 horas.
Un usuario no puede solicitar un préstamo si tiene algún préstamo anterior activo.

Por otro lado, los administradores deben tener la posibilidad de agregar nuevos elementos que formarán parte de un kit (el armado del kit es otra funcionalidad que no debe modelarse). De cada elemento se registra número de serie (es único
por elemento), tipo de elemento (cámara, micrófono o trípode), precio de compra (no puede superar el millón de pesos), origen de fabricación del elemento y fecha de alta. Si el elemento no es nacional, entonces el sistema deberá guardar un impuesto adicional del 10% calculado sobre el precio de compra.

- **ID:** Solicitar préstamo
- **TÍTULO:** Como usuario quiero realizar un préstamo de un equipo multimedia en el sitio de Tics para poder grabar material audiovisual
- **REGLAS DE NEGOCIO:**
	 - Los prestamos no pueden durar mas de 3 horas
	 - Un usuario no puede efectuar un préstamo con otro en curso.

**CRITERIOS DE ACEPTACIÓN: 

**Escenario 1: Préstamo realizado con éxito.**
**Dado** día "16/9/16", hora de retiro 15hs, duracion de prestamo 1.30hs y tipo de kit básico, sin prestamos activos
**Cuando** cuando se ingresan los datos y se quiere confirmar la solicitud,
**Entonces** se informa que el kit fue reservado con exito.

**Escenario 2: Préstamo rechazado por tener préstamo activo
**Dado**  día "16/9/16", hora de retiro 15hs, duración de prestamo 1.30hs, tipo de kit básico, con un préstamo activo en el sistema
**Cuando** se ingresan los datos y se quiere confirmar la solicitud, 
**Entonces** se informa que no puede realizar el préstamo hasta finalizar el activo.

**Escenario 3: Prestamo rechazado por exceso de duración maxima
**Dado** día "16/9/16", hora de retiro 15hs, duración de prestamo 4.30hs, tipo de kit básico, sin préstamos activos en el sistema
**Cuando** se ingresan los datos y se intenta confirmar la solicitud, 
**Entonces** se informa que no se puede realizar el prestamo debido a que excede de la duración maxima del mismo


- **ID:** Registrar elementos
- **TÍTULO:** Como administrador quiero agregar nuevos elementos al sistema para que posteriormente puedan formar parte de un kit.
- **REGLAS DE NEGOCIO:**
	 - El precio de compra no puede superar el millón de pesos.
	 - Si el elemento no es nacional se debe cargar un impuesto del 10% calculado sobre el precio de compra.

**CRITERIOS DE ACEPTACIÓN: 
 
**Escenario 1: Registro exitoso elemento nacional.**
**Dado** un numero de serie "001" no registrado, tipo de elemento "camara", un valor de compra "600.000", de origen nacional, con fecha de alta "16/9/26"
**Cuando** se ingresan los datos requeridos y se quiere proceder con el registro ,
**Entonces** se informa que el registro ha sido exitoso sin aplicar ningún impuesto.

**Escenario 2: Registro exitoso elemento importado.**
**Dado** un numero de serie "002" no registrado, tipo de elemento "tripode", un valor de "500.000", de origen importado, con fecha de alta "16/9/26",
**Cuando** se ingresan los datos requeridos y se quiere proceder con el registro,
**Entonces** se informa que el registro ha sido exitoso y se ha aplicado un impuesto del 10% por origen importado "550.000".

**Escenario 3: Registro fallido por numero de serie duplicado.**
**Dado** un número de serie "001" que ya se encuentra registrado en el inventario, tipo de elemento "microfono", con un valor de compra de "400.00", de origen nacional con fecha de alta "16/9/26"
**Cuando** se ingresan los datos requeridos y se quiere proceder con el registro, 
**Entonces** se informa que no se ha podido registrar correctamente ya el número de serie ya existe y este debe ser único.

**Escenario 4: Registro fallido por valor de compra superior al precio máximo.**
**Dado** un numero de serie "003" no registrado, tipo de elemento "camara", de origen nacional, con fecha de alta "16/9/26", con un valor de compra "1.200.000"
**Cuando**  se ingresan los datos requeridos y se quiere proceder con el registro, 
**Entonces** se informa no se ha podido realizar correctamente el registro ya que el precio de compra no puede superar el millón de pesos.


#### Problema 5: Manejo de licencias
Se desea modelar un sistema para el seguimiento de pedidos de licencias médicas por parte de los empleados de la Provincia de Buenos Aires. Para solicitar una licencia el empleado debe estar registrado y correctamente autenticado en
el sistema.
Cuando un empleado quiere solicitar una licencia debe ingresar el tipo de licencia (presencial o telemedicina), la fecha de inicio de reposo, la matrícula de su médico personal, el diagnóstico y si es para el titular o para un familiar enfermo. Para poder solicitar una licencia el empleado debe tener más de 1 mes de antigüedad, de lo contrario el sistema debe informar el rechazo de la licencia.
Además podrá solicitar una licencia un empleado que no tenga una licencia vigente.
Para registrar una licencia, el sistema genera un código de licencia y lo envía vía mail a la casilla del empleado con la confirmación de la licencia y los días otorgados.
Por otro lado, un administrativo podrá consultar las licencias solicitadas para lo cual ingresa el Cuil del empleado y un rango de fechas y el sistema imprime un informe de las licencias solicitadas. Tenga en cuenta que por una cuestión de
costos se podrá imprimir un informe por mes para cada empleado.

- **ID:** Registrar empleado
- **TÍTULO:** Como empleado  de la Provincia de Buenos Aires quiero registrarme en el sistema para solicitar una licencia medica
- **REGLAS DE NEGOCIO:**
????

**CRITERIOS DE ACEPTACIÓN: 

**Escenario 1: Registro exitoso.**
**Dado** un CUIL "20-2345678-2" no registrado en el sistema, que pertenece a un empleado de la Provincia de Buenos Aires y un email no registrado en el sistema "pepitoperez@gmail.com"
**Cuando** El empleado ingresa nombre "Pepito", apellido "Perez", cuil  "20-2345678-2", email pepitoperez@gmail.com, contraseña "123456" y presiona el boton registrar
**Entonces** Se registra a la persona y muestra el mensaje "Se ha registrado con exito" 

**Escenario 2: Registro fallido por cuil ya registrado**
**Dado** Un cuil "20-2345678-2" ya registrado en el sistema
**Cuando** el empleado ingresa nombre "Pepito", apellido "Perez", cuil  "20-2345678-2", email pepitoperez@gmail.com, contraseña "123456" y presiona el boton registrar
**Entonces** se informa que el Cuil ya se encuentra registrado en el sistema

**Escenario 3: Registro fallido por email ya registrado**
**Dado** Un email "pepitoperez@gmail.com" ya registrado en el sistema
**Cuando** el empleado ingresa el nombre "Pepito", apellido "Perez" cuil "20-2345678-2", contrasenia "123456" y presiona el boton registrar
**Entonces** el sistema informa que el mail ya se encuentra registrado en el sistema

- **ID**: Iniciar sesion
- **Titulo**: Como empleado de la provincia de buenos aires quiero inicar sesion en el sistema para solicitar una licencia medica

**CRITERIOS DE ACEPTACION**:

**Escenario 1: Inicio de sesion exitoso**
**Dado** un  email registrado en el sistema "pepitoperez@gmail.com" y una contraseña correcta "123456"
**Cuando**el empleado ingresa los datos y presiona iniciar sesion
**Entonces** el sistema abre sesion y redirige a la pantalla de inicio de sesion del sistema

**Escenario 2: Inicio de sesion fallido por falta de registro**
**Dado** un email no registrado en el sistema "pablodiaz@gmail.com" 
**Cuando** se ingresan los datos mail "pablodiaz@gmail.com", contraseña "654321" y se presiona inicar sesion
**Entonces** el sistema informa "Los datos ingresados son incorrectos"

**Escenario 3:  Inicio de sesion fallido por datos incorrectos**
**Dado** un email registrado en el sistema "tomasramirez@gmail.com"
**Cuando** se ingresa el mail y la contraseña "1234555" (incorrecta) y se presiona iniciar sesion
**Entonces** El sistema informa "Los datos ingresados son incorrectos"

- **ID**: Cerrar sesion
- **Titulo:** Como usuario quiero cerrar sesión para salir del sistema

Escenario 1: Cierre de sesion exitoso
**Dado** Un usuario autenticado del sistema "pepitogomez@gmail.com"
**Cuando** presiona el botón "cerrar sesion"
**Entonces** el sistema cierra la sesión del usuario y lo redirige a la pagina de inicio de sesion


- **ID:** Solicitar licencia
- **TÍTULO:** Como empleado quiero solicitar una licencia medica para justificar mi reposo y obtener los días correspondientes
- **REGLAS DE NEGOCIO:**
	 - El empleado debe tener mas de un mes de antigüedad
	 - El empleado no debe tener una licencia vigente
	- El sistema genera un código de licencia y lo envía vía mail con la confirmación y los días otorgados.???????????

**CRITERIOS DE ACEPTACIÓN: 

**Escenario 1: Solicitud de licencia exitosa.**
**Dado** un empleado con cuit "bla" con más de 1 mes de antigüedad (sin licencias vigentes),
**Cuando** se ingresan los datos:  el tipo "presencial", fecha de inicio "16/09/2026", matrícula "MS-3024", diagnóstico "esguince de tobillo" y se procede con la solicitud
**Entonces** se muestra en pantalla un mensaje informando solicitud exitosa, informando que por vía mail se ha enviado el código de licencia y los días otorgados, se registra correctamente en el sistema la licencia .

**Escenario 2: Solicitud de licencia fallida por falta de antigüedad.**
**Dado** una cuenta con menos de 1 mes de antigüedad  **????????????????? o dado que falla doy ejemplo de que es lo que falla y en el cuando pongo el resto de los datos exitosos**
**Cuando** se ingresan los datos , el tipo "presencial", fecha de inicio "16/09/2026", matrícula "MS-3024", diagnóstico "esguince de tobillo" y se presiona solicitar,
**Entonces** se informa en pantalla un mensaje de "solicitud rechazada debido a que no cumple con la cantidad de antigüedad requerida".

**Escenario 3: Solicitud de licencia fallida por licencia vigente.**
**Dado** una cuenta que actualmente posee una licencia médica vigente, el tipo "presencial", fecha de inicio "16/09/2026", matrícula "MS-3024", diagnóstico "esguince de tobillo"
**Cuando** se ingresan los datos y se procede con la solicitud, 
**Entonces** se informa en pantalla que se rechazo la solicitud ya que no puede solicitar una licencia con otra vigente.

**?????????????modelo registro e inicio de sesion con el cuil?????**

- **ID:** Consultar licencias
- **TÍTULO:** Como administrativo quiero consultar licencias medica solicitadas por un empleado para imprimir el informe correspondiente
- **REGLAS DE NEGOCIO:**
	 - Solo puede imprimirse un informe por mes de cada empleado
	 

**CRITERIOS DE ACEPTACIÓN: 

**Escenario 1: Consulta e impresión exitosa.
- El sistema imprime un informe de las licencias solicitadas.**
**Dado** el cuil de un empleado "2345678664-2" al cual no se ha impreso ningún informe en el mes actual y un rango de fechas valido "17/9/26"-"23/9/26"
**Cuando** se ejecuta la consulta
**Entonces** se imprime el informe con las licencias solicitadas por el empleado informando un mensaje de exito en pantalla.

**Escenario 2: Consulta fallida por limite de impresión mensual excedido .**
**Dado** el cuil de un empleado "2345678664-2" al cual ya se ha impreso un informe en el mes actual y un rango de fechas valido "17/9/26"-"23/9/26"
**Cuando** se ejecuta la consulta,
**Entonces** se informa en pantalla que se ha alcanzado el limite de un informe por mes para dicho empleado.

**Escenario 3: Consulta fallida por cuil no registrado en el sistema**
**Dado**: un CUIL "25-23455654-2" que no pertenece a un usuario registrado
**Cuando** el administrador ingresa el cuil "25-23455654-2", rango de fechas "4/6/2026"- "30/6/2026" y presiona consultar
**Entonces**El sistema informa que el CUIL ingresado no pertenece a un usuario registrado en el sitema
### Problema 6: Pago Electrónico
Se desea modelar un sistema de pago electrónico de impuestos y servicios en efectivo.
Cuando un cliente llega para realizar un pago, el empleado o el gerente de la sucursal ingresa el código de pago electrónico y el sistema se conecta con la central de cobro para recuperar los datos de la factura (empresa, nro de cliente, 1era fecha de vencimiento, 2da fecha de vencimiento, recargo, y monto original). Una vez recuperados los datos, el sistema debe verificar los vencimientos para determinar el monto a cobrar. Teniendo esto en cuenta, cuando el 2do vencimiento está vencido se debe informar que la factura no se puede cobrar por dicho motivo. Cuando el 1er vencimiento está vencido hay que aplicar el recargo al monto original. Si la factura no está vencida, se cobra el monto original.
Una vez al día, el gerente de la sucursal debe registrar en la central de cobros los pagos que hicieron los clientes. Para esto el sistema requiere la clave maestra y de ser correcta, recupera las transacciones de los impuestos y servicios cobrados en el día, se conecta a la central de cobro y se las envía. Cuando la central confirma la recepción exitosa, el sistema las registra como enviadas. Este último paso es importante porque no deben enviarse dos veces las transacciones. Si el gerente intenta enviar una segunda vez, el sistema no debe permitirlo.
Finalmente el Gerente puede ver las estadísticas de los impuestos y servicios cobrados. Para esto, se ingresa la clave maestra, un rango de fechas sobre las cuales debe calcularse las estadísticas y el sistema debe mostrar los montos y la
cantidad de cobros realizados, agrupando por empresa.
Tenga en cuenta que cada vez que el sistema debe conectarse a la central, debe enviarle un token (código que identifica al sistema). Una vez que la central valida el token, el sistema envía el requerimiento para recuperar los datos de la factura o el requerimiento para registrar los pagos del día según corresponda.


- **ID:** Cobrar factura
- **TÍTULO:** Como empleado quiero ingresar el código de pago electrónico para consultar la factura y cobrar el monto correspondiente al cliente. 
- **REGLAS DE NEGOCIO:**
	 - Cuando el 2do vencimiento está vencido se debe informar que la factura no se puede cobrar por dicho motivo. 
	 - Cuando el 1er vencimiento está vencido hay que aplicar el recargo al monto original. 
	 - Si la factura no está vencida, se cobra el monto original.
	 - Toda conexión con la central requiere el envió de un token identificador


**CRITERIOS DE ACEPTACIÓN: 

**Escenario 1: Cobro exitoso sin vencimientos.**
**Dado** el codigo de pago "1234" correspondiente a la empresa "Camuzzi", nro de cliente "98", 1era fecha de vencimiento "30/9/26", 2da fecha de vencimiento "15/10/26", recargo "500" y monto original "5000"
**Cuando** se ingresa el codigo de pago
**Entonces** se muestra en pantalla el monto original a cobrar de $5000.

**Escenario 2: Cobro exitoso con recargo (primer vencimiento vencido)**
**Dado** el codigo de pago "5546" correspondiente a la empresa "Edelap", nro de cliente "233", 1er vencimiento "10/9/26" (vencida), 2do vencimiento "25/9/26" (aun vigente), recargo "$500" y monto original "5000"
**Cuando** se ingresa el codigo de pago
**Entonces** se muestra en pantalla que debido al primer vencimiento vencido se cobrara el recargo de $500 resultando en un monto total de $5500.

**Escenario 3: Cobro fallido por segundo vencimiento vencido**
**Dado** el codigo de pago "4234" correspondiente a "Edelap", nro de cliente "142", 1er vencimiento "1/9/26" (vencida), 2do vencimiento "15/9/26"(vencida), con un recargo de $500 y monto original $5000
**Cuando** se ingresa el código de pago
**Entonces** se muestra en pantalla un mensaje informando que no se puede cobrar la factura debido a que ha expirado el segundo vencimiento

- **ID:** Registrar pagos diarios
- **TÍTULO:** Como gerente quiero registrar en la central los pagos que hicieron los clientes para asentar las transacciones realizadas
- **REGLAS DE NEGOCIO:**
	- Toda conexión con la central requiere el envió de un token identificador.
	- El sistema no debe permitir que las transacciones se envíen dos veces.

**CRITERIOS DE ACEPTACIÓN: 

**Escenario 1: Registro y envió exitoso de transacciones.**
**Dado** un lote de "45" transacciones de impuestos y servicios cobrados el dia "16/9/26" que aun no han sido enviadas,
**Cuando** se intenta registrar los pagos diarios
**Entonces**se muestra un mensaje de exito indicando que las 45 
transacciones fueron registradas y enviadas correctamente a la central

**Escenario 2: Envío fallido por transacciones ya registradas.**
**Dado** un lote de "45" transacciones de impuestos y servicios cobrados el dia "16/9/26" que ya figuran como enviadas exitosamente, 
**Cuando** se intenta registrar los pagos diarios, 
**Entonces** se muestra un mensaje de error indicando que las transacciones ya fueron enviadas y no pueden registrarse duplicadas

- **ID:** Consultar estadísticas
- **TÍTULO:** Como gerente de sucursal quiero ver las estadísticas de los pagos para analizar los montos y cobros realizados agrupados por empresa.
- **REGLAS DE NEGOCIO:**
    - El sistema debe mostrar los montos y la cantidad de cobros realizados, agrupando la información por empresa.

**CRITERIOS DE ACEPTACIÓN:**

**Escenario 1: Consulta de estadísticas exitosa.** 
**Dado** un rango de fechas desde "01/09/2026" hasta "15/09/2026", 
**Cuando** se ejecuta la consulta de estadísticas, 
**Entonces** se muestra en pantalla una lista indicando "$150.000" en "30" cobros para la empresa "EDELAP" y "$80.000" en "15" cobros para la empresa "ABSA".



==CONSULTAR SI SE MODELA EL REGISTRO LA VERIFICACION ETC==

### Problema 7: Transferencias vehiculares
Se desea modelar un sistema para el manejo de transferencias de vehículos de forma remota. Para poder transferir un vehículo se debe estar registrado en el sistema e iniciar sesión (tanto el registro como la autenticación forman parte de
otro módulo que no debe modelarse). Para iniciar el trámite de transferencia se debe ingresar la patente, el dni del
vendedor y el dni del comprador. Para que una transferencia se lleve a cabo con éxito, la patente ingresada no debe
tener deudas y tanto el vendedor como el comprador deben ser mayores de 18 años. Si la transferencia puede realizarse
con éxito, se le envía al mail del comprador un código para que realice el pago, caso contrario el sistema debe informar el
motivo del rechazo.
Por otro lado el sistema debe permitir consultar el estado de una transferencia, para lo cual se debe ingresar una
patente y el sistema informa el estado de la transferencia. Tenga en cuenta que se pueden hacer hasta tres consultas por
mes.

- **ID :** Iniciar tramite
- **Titulo:** : como usuario autenticado del sistema quiero iniciar un tramite para transferir mi vehiculo
- **REGLAS DE NEGOCIO:**
	- La patente no debe tener deudas
	- El vendedor y el comprador deben ser mayores de 18 años

**CRITERIOS DE ACEPTACION**

**Escenario 1 : Incio de tramite exitoso**
**Dado** Una patente "ARG 333" libre de deuda, de vendedor al cual pertenece el auto  un dni 25678345 con una edad de 49 y un dni de comprador 26567456 con una edad de 48
**Cuando** se ingresan los datos **poner patente dnis**   y se presiona "Aceptar"
**Entonces** El sistema informa "Inicio de tramite exitoso, se le enviara al mail del comprador un codigo para que realice el pago" envia un mail y inicia el tramite 



**Escenario 2: Inicio de tramite fallido por comprador menor de edad** 
**Dado** Un dni de comprador 49345345 con una edad de 17 años
**Cuando** se ingresan los datos patente "RBG 123" libre de deuda, un dni de vendedor 25642345 con edad de 49 y se presiona "Aceptar"
**Entonces** El sistema informa "Inicio de tramite fallido, el comprador no puede ser menor de 18 años"
en error no el sistema rechaza registra o no inicia, entonces de error solo lo que hace ,muestro mensaje


**Escenario 3: Inicio de tramite fallido por vendedor menor de edad**
**Dado** Un dni de vendedor 49234532 con una edad de 17 años
**Cuando** se ingresan los datos patente "TGH 682" libre de deuda, dni de comprador 34876142 con una edad de 39 años y se presiona "Aceptar"
**Entonces** el sistema informa "Inicio de tramite fallido, el vendedor no puede ser menor de 18 años"

**Escenario 4: Inicio de tramite fallido por patente con deuda**
**Dado** Una patente "PBT 163" que tiene deudas
**Cuando** se ingresan los datos dni de vendedor 3464234 de 38 años, dni de comprador 43567456 con edad de 25 años y se presiona "Aceptar"
**Entonces** El sistema informa "Inicio de tramite fallido, la patente ingresada tiene deudas"


CUANDO: TODOS LOS DATOS QUE TIENE QUE INGRESAR LA PERSONA
ENTONCES: EN CASO DE EXITO QUE ES LO QUE HACE EL SISTEMA
EN CASO DE ERROR QUE ES LO QUE MUESTRA, NO LO QUE NO HACE

