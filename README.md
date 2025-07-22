# Chatbot Backend Microservice

Este microservicio contiene exclusivamente la **lógica del chatbot**, funcionando como backend y ejecutándose en el **puerto 8091**.

## Objetivo

Proveer la funcionalidad del chatbot a través de un servicio REST que permite registrar, consultar y administrar preguntas y respuestas, sin interfaz gráfica.

Este microservicio trabaja en conjunto con una aplicación web (frontend) que corre en el puerto 5001, encargada de mostrar una interfaz visual tipo chat para los usuarios.

## Funcionalidades principales

### Registro de preguntas
- Permite registrar preguntas enviadas desde el frontend.
- Si no existe respuesta, se guarda con estado `0` (pendiente o `false`).
- Si ya está respondida, se guarda con estado `1` (respondida o `true`).

### Consulta de preguntas
- Búsqueda exacta por pregunta completa.
- Búsqueda por palabras clave (keywords), retornando una o más coincidencias.
- Indica si la pregunta ya está respondida o pendiente.

### Escenarios contemplados
1. Pregunta nueva sin respuesta:  
   Se guarda con estado `0`. El sistema retorna un mensaje indicando que la pregunta fue registrada pero aún no tiene respuesta.

2. Pregunta ya registrada con respuesta:  
   Se retorna la respuesta junto con su estado `1`.

3. Pregunta registrada sin respuesta:  
   Se notifica que la pregunta existe, pero todavía no ha sido respondida.

4. Coincidencias por palabras clave:  
   Retorna una lista de preguntas similares y sus respectivos estados.
