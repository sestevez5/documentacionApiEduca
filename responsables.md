# Descripción general

ApiEduca es un ApiREST de carácter interno de La Consejería de Educación, Formación Profesional, Actividad Física y Deportes del Gobierno de Canarias que expone las entidades que forman parte del dominio de Pincel (aplicación de gestión académica y administrativa de centros educativos). No obstante, con carácter temporal, también ofrece entidades de dominios externos como, por ejemplo, entidades del dominio del Directorio de Centros o el Plan de Estudio de Canarias.

# Seguridad

En líneas generales, el consumo de los endpoints publicados en este API requiere de una autenticación previa. Es requisito indispensable para su consumo disponer de un ApiKey que será gestionada por el servicio. Además, puede requerirse, adicionalmente, la autenticación adicional de una persona registrada en el servicio de autenticación.

# Parámetros
Pueden ser comunes o específicos de cada opción.

## Parámetros comunes
* **posicionInicial**: número de página a partir de la que se recuperarán los datos. Si no se indica, su valor por defecto será 0.
* **tamanyoBloque**: número de páginas que se recuperarán. Si no se indica, su valor por defecto será 100.
* **opcion**: 1, 2. Se deberá escoger uno obligatoriamente.
* **codigoCentro**: Obligatorio (Ej. 38010773)
* **nivelDetalle**: r, m, e (reducido, medio, extendido). Si no se indica, su valor por defecto será r.

**Observaciones**:
>* Si no se indican posicionInicial ni tamanyoBloque, el número máximo de páginas a recuperar es 100 (posicionInicial = 0, tamanyoBloque = 100).
>* Opción 1: El codigoCentro es obligatorio, además de uno solo de los campos nifNie o pasaporte.
>* Opción 2: Sólo es obligatorio el campo codigoCentro.

## Parámetros específicos

### Opción 1
* **nifNie**: NIF o NIE del responsable del alumnado.
* **pasaporte**: Pasaporte del responsable del alumnado.

**Observaciones**: Se debe escoger uno solo de los campos _nifNie_ o _pasaporte_.

### Opción 2

* **tieneTuteladoMatriculaEnElCentro**: si no se selecciona, proporciona todos los responsables del alumnado del centro.
* **tieneTuteladoMatriculaEnElCurso**: selecciona los responsables del alumnado que está matriculado en el curso escolar indicado (Ej. 2024).

**Observaciones**: Los campos nifNie y pasaporte no están permitidos en esta opción.

# Ejemplos.
### A) Solicitud de datos con nivelDetalle medio del responsable con dni = "12345678Z" del centro con código "35010488".
> * ?opcion=1 & codigoCentro=35010488 & nifNie=12345678Z & nivelDetalle=m
> * 
### B) Solicitud de datos con nivelDetalle extendido de todos  los responsables del centro con código "35010488".
> * ?opcion=2 & codigoCentro=35010488 & nivelDetalle=e

### C) Solicitud de datos con nivelDetalle reducido de los responsables con alumnado tutelado que esté matriculado en el curso 2022 en el centro con código "35010488". 
> * ?opcion=2 & codigoCentro=35010488 & tieneTuteladoMatriculaEnElCentro=true & tieneTuteladoMatriculaEnElCurso=2022
