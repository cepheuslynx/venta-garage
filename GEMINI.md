# Instrucciones del Proyecto: Venta de Garage / Catálogo Estático

## Contexto del Proyecto
Este repositorio/carpeta contiene un sitio web estático diseñado para vender artículos del hogar usados. El objetivo es mantener una página web liviana, responsiva y fácil de actualizar a partir de un listado de productos y sus imágenes asociadas.

## Estructura de Archivos Esperada
```text
/
├── GEMINI.md            <-- Este archivo de contexto e instrucciones
├── index.html           <-- Interfaz web estática (HTML + JS + Tailwind CSS via CDN)
├── productos.json       <-- Base de datos estática extraída del Excel/XML
└── fotos/               <-- Carpeta contenedora de las imágenes de los productos
    ├── foto1.jpg
    ├── foto2.jpg
    └── ...

Modelo de Datos (productos.json)

El archivo productos.json debe seguir estrictamente el siguiente esquema de arreglo de objetos JSON:
JSON

[
  {
    "id": "string_u_numero",
    "articulo": "Nombre del artículo",
    "valor": 00000,
    "descripcion": "Descripción detallada del estado o características",
    "foto": "fotos/nombre_archivo.jpg",
    "estado": "disponible | reservado | vendido"
  }
]

Reglas para los datos:

    valor: Debe ser un número entero (sin puntos, comas ni símbolos de moneda).

    foto: Debe apuntar a la ruta relativa en la carpeta fotos/. Si no hay foto definida, usar null o una cadena vacía.

    estado: Los valores permitidos son unicamente "disponible", "reservado" o "vendido". Por defecto, todo elemento nuevo ingresa como "disponible".

Requisitos de la Interfaz Web (index.html)

    Diseño:

        Estilizado utilizando Tailwind CSS cargado mediante CDN.

        Diseño tipo cuadrícula (Grid) responsivo de tarjetas (Cards) adaptables a móviles y escritorio.

        Indicadores visuales claros en las tarjetas según el estado:

            Disponible: Botón visible para consultar vía WhatsApp.

            Reservado: Etiqueta/Badge amarilla de "Reservado".

            Vendido: Tarjeta con opacidad reducida o escala de grises y etiqueta/badge roja de "Vendido".

    Funcionalidades requeridas:

        Carga dinámica de los datos desde productos.json mediante fetch.

        Buscador en tiempo real por nombre de artículo o descripción.

        Formateador automático de precios a moneda local (Peso Chileno CLP, sin decimales).

        Enlace directo de WhatsApp por producto prellenando el mensaje con el nombre del artículo.

Rol de la IA (Instrucciones para Gemini)

Cada vez que me comunique contigo en esta carpeta o chat de desarrollo, debes actuar como asistente y desarrollador de este proyecto siguiendo estas reglas:

    Conversión de datos: Cuando te proporcione un archivo Excel, XML, CSV o texto con nuevos artículos o actualizaciones, tu tarea principal es convertir esos datos al formato productos.json respectivo respetando el esquema.

    Generación/Actualización de código: Si te pido modificar la interfaz, debes entregar el código HTML/JS de index.html completo y funcional sin omitting partes clave.

    Nombrado de fotos: Si agrego una columna o listado de fotos, asegúrate de sanitizar los nombres de los archivos en el JSON (sin espacios ni caracteres especiales, ej: bicicleta-trek.jpg).
