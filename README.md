# semana-3
Requerimientos
1. La interfaz debe contar con un campo para el nombre de usuario, otro campo para contraseña y un botón para realizar la acción de inicio de sesión, al ingresar deberá mostrar un escritorio para el usuario en donde se visualicen su nombre y correo. En caso de fallar, se debe indicar que hubo un error en el inicio de sesión.
2. Cuando el usuario se loguea exitosamente ,debe responder con un status 200 y propiedad accessToken.
3. El usuario no existe en la bases de dato, debe responder con un status 404.
4. El usuario ingresa una contraseña inválida, debe responder con un status 401.
5. Queda de elección de cada grupo utilizar la bases de datos localmente que deseen ya sea la predeterminada en el archivo o utilizar mysql.
6. La modificacion en la base de datos solo se deben realizar en el objeto “development”, las otras opciones de test y production por ningún motivo deben ser modificadas esto podría alterar el resultado de la prueba y por ende su calificación.
7. El modelo se debe realizar en sequelize cli con los atributos obligatorios: name, email , password de tipo string.

Historia de usuario: 
El cliente desea un pagina que pueda validar el correo electronico y la contraseña de sus empleados, y que les informe si la informacion que ingresan es incorrecta, si la informacion es correcta que les muestre el nombre y el correo electronico.

Product Backlog
1. Validar en una pagina el nombre y correo de la persona para dejarlo ingresar a la siguiente pagina
2. Que sea intuitivo para el empleado donde debe ingresar esa información, tanto el email como la contraseña
3. Informar al empleado cuando la informacion no es correcta pero no decirle si el error esta en el usuario o en la contraseña
4. Que le permita hacer los intentos que desee
5. Si todo es correcto permitirle ingresar a la siguiente pagina
6. En la pagina despues de loguearse debe aparecer el nombre y el correo y un boton para salir de la pagina
7. El boton de salir, lo debe enviar nuevamente a la pagina inicial donde se logueo.
