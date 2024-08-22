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
* **fechaReferencia**: Si se indica, muestra las matrículas del curso hasta esta fecha (Ej. 2023-08-31)

**Observaciones**:
>* Si no se indican posicionInicial ni tamanyoBloque, el número máximo de páginas a recuperar es 100 (posicionInicial = 0, tamanyoBloque = 100).
>* Opción 1: Los campos obligatorios son el cursoEscolar y el codigoCentro.
>* Opción 2: El campo idCursoCentro es obligatorio.
>* Los campos _idAlumnadoCentro_, _cial_, _nifNie_, _pasaporte_, _nifNieResponsable_ y _pasaporteResponsable_ no están permitidos en ninguna de las opciones.

## Parámetros específicos

### Opción 1
* **cursoEscolar**: Obligatorio (Ej. 2024)
* **codigoCentro**: Obligatorio (Ej. 38010773)
* **idEstudioSC**: Si no se indica, se muestran las matrículas de todos los estudios (Ej. 344).
* **codigoGrupo**: Si no se indica, se muestran las matrículas de todos los grupos (Ej. 1ESOB).

### Opción 2

* **idCursoCentro**: Obligatorio (Ej. E480D237-EC8C-4AFF-A870-01C277A3D712).
* **idEstudio**: Si no se indica, se muestran las matrículas de todos los estudios (Ej. 6701A4CA-1008-4A91-A2F7-6B68F3A0B360).
* **idGrupo**: Si no se indica, se muestran las matrículas de todos los grupos (Ej. 0a606f79-6f58-4adb-9d8a-6061f38b20ba).

**Observaciones**: 

# Ejemplos.
### A) Solicitud de datos con nivelDetalle extendido del alumno con cial B00P08015J.
> * ?opcion=2 & cial=B00P08015J & nivelDetalle=e

### B) Solicitud de datos con nivelDetalle reducido de todo el alumnado del centro con código "35010488".
> * ?opcion=1 & codigoCentro=35010488

### C) Solicitud de datos con nivelDetalle medio del alumnado del centro con código "35010488" y matrícula en el curso 2023. 
> * ?opcion=1 & codigoCentro=35010488 & conMatriculaEnElCurso=2023 & nivelDetalle=m
