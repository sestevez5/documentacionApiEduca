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
* **tieneMatriculaEnElCentro**: selecciona al alumnado que está matriculado al menos en un curso escolar.
* **conMatriculaEnElCurso**: selecciona al alumnado que está matriculado en el curso escolar indicado como cadena de texto.
* **nivelDetalle**: r, m, e (reducido, medio, extendido). Si no se indica, su valor por defecto será r.
* **tieneMatriculaActiva**: selecciona al alumnado con matrícula activa en el centro.

**Observaciones**:
>* Si no se indican posicionInicial ni tamanyoBloque, el número máximo de páginas a recuperar es 100 (posicionInicial = 0, tamanyoBloque = 100).
>* Opción 1: Sólo es obligatorio el codigoCentro.
>* Opción 2: Sólo es obligatorio el cial, nifnie o pasaporte (uno solo).

## Parámetros específicos

### Opción 1
* **cursoEscolar**: Obligatorio (Ej. 2024)
* **codigoCentro**: Obligatorio (Ej. 38010773)
* **nifNieResponsable**: NIF o NIE del responsable del alumnado.
* **pasaporteResponsable**: Pasaporte del responsable del alumnado.

### Opción 2

* **cial**: CIAL del alumnado.
* **nifnie**: NIF o NIE del alumnado.
* **pasaporte**: Pasaporte del alumnado.

**Observaciones**: Los campos nifNieResponsable y pasaporteResponsable no están permitidos en ninguna de las opciones.

# Ejemplos.
### A) Solicitud de datos con nivelDetalle extendido del alumno con cial B00P08015J.
> * ?opcion=2 & cial=B00P08015J & nivelDetalle=e

### B) Solicitud de datos con nivelDetalle reducido de todo el alumnado del centro con código "35010488".
> * ?opcion=1 & codigoCentro=35010488

### C) Solicitud de datos con nivelDetalle medio del alumnado del centro con código "35010488" y matrícula en el curso 2023. 
> * ?opcion=1 & codigoCentro=35010488 & conMatriculaEnElCurso=2023 & nivelDetalle=m
