# Introducción:

Agrecol es una innovadora aplicación web enfocada en la venta y distribución de productos orgánicos. Esta plataforma permite a los usuarios comprar productos orgánicos de alta calidad, fomentando un estilo de vida saludable y sostenible. Agrecol ofrece una experiencia de compra fácil y eficiente, alentando a los consumidores a elegir opciones más ecológicas y naturales para sus necesidades diarias.
# Descripción del proyecto
Agrecol es una solución tecnológica sólida y fácil de usar, diseñada para facilitar el acceso a productos orgánicos. Nuestro objetivo es incrementar la conciencia sobre la alimentación saludable y promover prácticas de consumo sostenibles. La aplicación facilita la compra de productos orgánicos, ofreciendo una experiencia de usuario intuitiva y gratificante.
# Integrantes y Roles del Proyecto
- Diego Emerson Salvatierra Berrios: Como único integrante y desarrollador del proyecto, [Nombre] ha sido responsable de todas las fases del desarrollo, desde la conceptualización hasta la implementación. Se encargó de la arquitectura del software, la programación, el diseño de la interfaz, y la gestión de la base de datos, asegurando la funcionalidad eficiente y la experiencia de usuario óptima de Agrecol.
# Arquitectura del software
La aplicación está construida sobre Next.js 13, un framework de JavaScript basado en React 18. Esta elección de tecnología permite una generación eficiente de sitios estáticos y un renderizado en el servidor de páginas web de React, garantizando una carga rápida y un alto rendimiento. La estética y el diseño del sitio se implementan a través de Tailwind CSS 3, un framework de CSS de bajo nivel que permite a los desarrolladores crear diseños personalizados y adaptables. Se ha empleado el patrón de diseño MVC, facilitando así la organización y mantenimiento del código.
# Requisitos del sistema:
- Hardware (cliente): Dispositivo con conexión a internet y Chrome para la instalacion de la aplicación por medio de PWA, que esla aplicación del proyecto que se instala por medio de Chrome.
  
- Software (cliente): Navegador web Chrome.
   
- Hardware (servidor/hosting/BD): No es necesario un equipo físico debido al uso de hosting en Vercel y la base de datos en MongoDB.
   
- Software (servidor/hosting/BD): Node.js, npm, MongoDB.
  
En cuanto al servidor, hosting y la base de datos, estos se gestionan a través de Vercel y MongoDB, por lo que no se necesita un equipo físico. En términos de software, se requiere Node.js, npm y MongoDB.
# Instalación y configuración:
Para el proceso de instalación y configuración, se debe clonar el repositorio, instalar las dependencias, configurar las variables de entorno y arrancar el servidor de desarrollo. Todos estos pasos están detallados en la documentación del repositorio.
# PROCEDIMIENTO DE HOSTEADO / HOSTING (configuración)
El procedimiento de hosteado se realiza a través de Vercel, que es un servicio en la nube para el despliegue de aplicaciones web. Los tutoriales detallados para la creación de la base de datos y la obtención de las APIs están disponibles en los enlaces proporcionados.
# GIT:
El proyecto se encuentra en la siguiente dirección de Git:

[https://github.com/sbd0029992/agrecol](https://github.com/sbd0029992/agrecol)

El proyecto ya está en ejecución y funcionando con la opción de ser instalado como aplicación en teléfonos Android

[www.agrecol.vercel.app](http://www.agrecol.vercel.app/)
# Personalización y configuración:
La personalización y configuración del software depende de las necesidades específicas del usuario. Por ejemplo, para agregar nuevas páginas, se pueden crear en la ruta:

“src/pages”

Para nuevas APIs y consultas a la base de datos, se puede agregar una nueva carpeta a:

“src/api”

Y para crear nuevos modelos, se pueden hacer en:

“src/models”

Esto para crear nuevos documentos/tablas en la base de datos en mongodb.
# Seguridad:
En cuanto a la seguridad, se utilizan variables de entorno para asegurar la protección de datos sensibles. Además, el proyecto incluye un sistema de autenticación para los usuarios. Este sistema limita el acceso a ciertas páginas según el tipo de usuario. Por ejemplo, si un usuario no está registrado completamente, su acceso está limitado hasta que complete su registro.
# Depuración y solución de problemas:
La depuración y la solución de problemas se realizan a través de varias herramientas y técnicas. Se utiliza el sistema de commits convencionales, que ayuda a prevenir errores y facilita la identificación de problemas. También se utilizan los toast para notificar a los usuarios si hay algún error durante el funcionamiento de la aplicación.
# Glosario de términos:
- Next.js: Un framework de JavaScript basado en React para el desarrollo de aplicaciones web.
  
- React: Una biblioteca de JavaScript para construir interfaces de usuario.
   
- Tailwind CSS: Un framework de CSS de bajo nivel que permite a los desarrolladores crear diseños personalizados.
  
- Commits convencionales: Una convención para los mensajes de commit que facilita la lectura y la comprensión de la historia del proyecto.
   
- API: Interfaz de Programación de Aplicaciones. Un conjunto de reglas y protocolos que se utiliza para definir cómo deberían interactuar diferentes piezas de software.
  
- Model: En el contexto de MVC (Modelo-Vista-Controlador), un model representa los datos y la lógica de negocio de una aplicación.
   
- Toast: Un mensaje de alerta o notificación que aparece temporalmente para informar al usuario sobre alguna acción o evento.
# Referencias y recursos adicionales:
Documentación de Next.js: https://nextjs.org/docs

Documentación de React: https://reactjs.org/docs/getting-started.html

Documentación de Tailwind CSS: https://tailwindcss.com/docs
# Consideraciones finales:
Al concluir este manual técnico, es importante destacar la relevancia de Agrecol en el contexto actual, donde la demanda por productos orgánicos y sostenibles está en aumento. Esta aplicación no solo ofrece una solución tecnológica avanzada para facilitar la compra de estos productos, sino que también representa un paso adelante hacia un futuro más consciente y responsable.

Esperamos que Agrecol sirva como un catalizador para el cambio, inspirando a individuos y comunidades a tomar decisiones más informadas sobre su alimentación y su impacto en el planeta. Estamos comprometidos con la mejora continua de Agrecol, buscando siempre innovar y ofrecer la mejor experiencia posible a nuestros usuarios.