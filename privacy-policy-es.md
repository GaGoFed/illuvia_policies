# Illuvia — Política de privacidad

**Última actualización: 6 de agosto de 2026 · Aplica a Illuvia 1.0.0 para Windows**

## En resumen

Illuvia no recoge nada. No tiene servidores, ni cuentas, ni herramientas de
analítica, y no abre ninguna conexión de red por su cuenta. Todo lo que escribes
permanece en archivos de tu PC, bajo tu cuenta de Windows.

## Qué guarda Illuvia, y dónde

Todo lo que introduces — tareas, listas, transacciones, cuentas, planes de pago,
deseos, vehículos, ajustes — se escribe en archivos dentro de tu propia carpeta
de usuario:

```
%APPDATA%\Gagofed\Illuvia\database\
```

Esa es la carpeta tanto si Illuvia viene de la Microsoft Store como si se
ejecuta desde una compilación normal: los datos no viven dentro del paquete
instalado.

Esos archivos están **cifrados en disco** con AES-256. La clave se genera en tu
PC la primera vez que se ejecuta Illuvia y se guarda en el Administrador de
credenciales de Windows, protegida para tu cuenta de Windows (DPAPI). Nunca
deriva de tu PIN o contraseña, y nunca sale del equipo. Quien copiara los
archivos a otro PC, o intentara leerlos desde otra cuenta de Windows, no podría
descifrarlos.

Illuvia también escribe un registro de diagnóstico en texto plano:

```
%APPDATA%\Gagofed\Illuvia\logs\illuvia.log
```

Anota lo que hizo la aplicación — qué módulo se cargó, cuántos registros leyó,
qué decía un error — para poder entender un problema a posteriori. Está limitado
a 5 MB con hasta tres archivos rotados, no se envía a ninguna parte y puedes
borrarlo cuando quieras. No está cifrado: si lo envías para pedir ayuda, léelo
antes.

## Qué no hace Illuvia

- **Ninguna recogida de datos.** Sin estadísticas de uso, sin informes de
  errores, sin analítica, sin publicidad, sin perfilado, sin identificadores de
  ningún tipo.
- **Ninguna cuenta.** No hay nada que registrar y no hace falta una dirección de
  correo para usar la aplicación.
- **Ninguna red.** El paquete de la aplicación no declara ninguna capacidad de
  conexión a Internet y la aplicación no realiza peticiones. Funciona con el
  cable de red desconectado.
- **Ningún tercero.** Nada de lo que introduces se comparte con nadie, porque no
  hay nadie con quien compartirlo.

## Las dos veces en que algo sale de la aplicación

**Abrir un enlace.** Si guardas el enlace de una tienda en un deseo, o usas el
enlace de donación, al tocarlo la dirección pasa a tu navegador predeterminado.
A partir de ahí estás en ese sitio web, bajo su política de privacidad, no bajo
esta. Illuvia no descarga la página.

**Hacer una copia de seguridad.** Una copia es un único archivo con todo dentro,
guardado donde tú elijas. Cómo sale del ordenador lo decides tú:

- **Exportar sin contraseña** (opción predeterminada). El archivo se escribe como JSON
  legible. Es la única manera de inspeccionar una copia o de abrirla con algo que
  no sea Illuvia, y es tan privado como el sitio donde lo pongas. Si has guardado
  las credenciales de un servicio en un plan de pago (ver más abajo), Illuvia te
  avisa antes de escribirlo: ahí están en claro.
- **Exportar con contraseña.** El archivo se sella con AES-256, con una clave
  derivada de tu contraseña (Argon2id). Puede restaurarse en cualquier máquina, y
  sin esa contraseña no se abre: nadie puede recuperarla por ti.

Las copias que Illuvia escribe para sí misma — las automáticas, y la copia de
seguridad tomada antes de una restauración o de una importación — están siempre
selladas con la clave de este PC. Se quedan en la carpeta de Illuvia, y
desinstalar la aplicación las deja ahí junto con todo lo demás.

## Las contraseñas que guardas para otros servicios

Un plan de pago puede contener el usuario y la contraseña del servicio que paga
— tu cuenta de la luz, una suscripción — porque es ahí donde los buscas. Se
guardan como cualquier otro campo: en la base de datos, cifrados en reposo y solo
en este PC. Nunca se envían a ninguna parte, e Illuvia no tiene forma de usarlos.

De ahí se siguen dos cosas. Viajan dentro de una copia de seguridad, que es lo
que permite que una restauración devuelva tus datos tal como estaban; y por eso
una **exportación sin contraseña** los contiene en claro, que es la razón por la que
Illuvia avisa antes de escribirla.

## El bloqueo de la aplicación

El PIN o la contraseña que abren Illuvia son otra cosa, y nunca se almacenan. Lo que se almacena es
un hash Argon2id con una sal aleatoria, en el Administrador de credenciales de
Windows, junto a la clave de cifrado. Windows Hello, si lo activas, lo gestiona
Windows por completo: Illuvia solo recibe un sí o un no y nunca ve datos
biométricos.

## Borrar tus datos

Ajustes → Seguridad → *Vaciar todos los módulos* elimina todo lo que has
introducido. Al lado, *Borrar todos los datos* elimina además la clave de cifrado y la
credencial: es lo que hace el flujo «he olvidado mi PIN».

**Desinstalar Illuvia no borra tus datos.** Windows elimina la aplicación y deja
las carpetas indicadas arriba donde están, de modo que al reinstalar lo
encuentras todo como lo dejaste. Si quieres que desaparezcan también los datos,
usa antes uno de los dos comandos, o borra tú la carpeta `%APPDATA%\Gagofed\Illuvia\`: ahí
están la base de datos, el registro y las copias automáticas.

Las copias de seguridad que hayas exportado no se ven afectadas por ninguna de
estas operaciones: solo tú sabes dónde están.

## Menores

Illuvia es un organizador personal de uso general. No está dirigida a menores y
no recoge información de nadie, de ninguna edad.

## Cambios en esta política

Si una versión futura de Illuvia cambiara lo que hace con tus datos, esta página
se actualizará antes de publicar esa versión, y el cambio se describirá en las
notas de la versión.

## Contacto

Preguntas sobre esta política: **illuvia.dev@gmail.com**
