# EmailConnect - Librería para Recuperación de Contraseña

**EmailConnect** es una librería en Java que facilita el proceso de recuperación de contraseñas mediante el envío de un código de verificación a través de un correo electrónico. La librería está diseñada para ser fácil de usar y se conecta a un servidor SMTP (por defecto, Gmail) para enviar los correos electrónicos con el código de recuperación.

## Características

- **Envío de correos electrónicos:** Utiliza SMTP para enviar correos electrónicos de recuperación de contraseñas.
- **Generación de código aleatorio:** Genera códigos de recuperación aleatorios que pueden ser enviados al usuario.
- **Verificación de códigos:** Permite verificar si el código ingresado por el usuario coincide con el código enviado.

## Requisitos

- Java 8 o superior.
- Acceso a un servidor SMTP (se utiliza Gmail por defecto).
- La clase `EmailConnect` está diseñada para ser utilizada de manera estática.

## Uso

### Enviar un código de recuperación

```java
// Parámetros:
// - emailEmpresa: El email de la empresa que enviará el correo.
// - clave: La contraseña de la cuenta de email de la empresa.
// - nombre: El nombre del destinatario.
// - contrasena: El código de recuperación generado.
// - emailTo: El email del destinatario.

String emailEmpresa = "tucorreo@empresa.com";
String clave = "tu_contraseña";
String nombre = "Juan Pérez";
String contrasena = EmailConnect.generarCodigoRandom();
String emailDestino = "destinatario@dominio.com";

try {
    EmailConnect.sendEmail(emailEmpresa, clave, nombre, contrasena, emailDestino);
} catch (MessagingException e) {
    e.printStackTrace();
}
////////////////////////////////////////////////////
Verificar un código de recuperación
Para verificar si el código ingresado por el usuario es correcto, utiliza el siguiente método:

boolean esCorrecto = EmailConnect.verificarCodigo("codigoIngresado", "codigoOriginal");

///////////////////////////////////////////////////
Generar un código aleatorio
La librería incluye una función para generar un código aleatorio de 6 caracteres, utilizando letras y números:

String codigo = EmailConnect.generarCodigoRandom();
