# semana-3
Requerimientos
1. La interfaz debe contar con un campo para el nombre de usuario, otro campo para contraseña y un botón para realizar la acción de inicio de sesión, al ingresar deberá mostrar un escritorio para el usuario en donde se visualicen su nombre y correo. En caso de fallar, se debe indicar que hubo un error en el inicio de sesión.
2. Cuando el usuario se loguea exitosamente ,debe responder con un status 200 y propiedad accessToken.
3. El usuario no existe en la bases de dato, debe responder con un status 404.
4. El usuario ingresa una contraseña inválida, debe responder con un status 401.
5. Queda de elección de cada grupo utilizar la bases de datos localmente que deseen ya sea la predeterminada en el archivo o utilizar mysql.
6. La modificacion en la base de datos solo se deben realizar en el objeto “development”, las otras opciones de test y production por ningún motivo deben ser modificadas esto podría alterar el resultado de la prueba y por ende su calificación.
7. El modelo se debe realizar en sequelize cli con los atributos obligatorios: name, email , password de tipo string.

Historia de usuario
El cliente desea un pagina que pueda validar el correo electronico y la contraseña de sus empleados, informando si se ingresan la informacion de forma incorrecta y solo dejando pasar a los empleados que tienen las credenciales correctas, si tanto el correo como el usuario si es el correcto y es el registrado en la base de datos debe ingresar a una pagina donde se presente el nombre del empleado y su correo electronico.


