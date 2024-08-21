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
>* Opción 1: Además del codigoCentro, será necesario indicar nifnie o pasaporte.
>* Opción 2: Además del codigoCentro, opcionalmente se podrá seleccionar tieneServicioEnElCentro y/o tieneServicioEnElCurso.

## Parámetros específicos

### Opción 1
* **nifnie**: NIF o NIE del docente.
* **pasaporte**: Pasaporte del docente.

**Observaciones**: Debe cumplimentarse solamente uno de ellos.

### Opción 2
* **tieneServicioEnElCentro**: Booleano que permite seleccionar a los docentes que tienen o han tenido algún servicio en el centro. Si no se indica, se seleccionan todos los docentes del centro.
* **tieneServicioEnElCurso**: Cuando se ha seleccionado la opción anterior, permite indicar el curso escolar en el que ha tenido servicio un docente (Ej. 2023).


**Observaciones**: Ambos son opcionales.


# Ejemplos.
### A) Solicitud de datos con nivelDetalle extendido del docente con nif = 00000001R en el centro con código "35010488".
> * ?opcion=1 & codigoCentro=35010488 & nifnie=00000001R & nivelDetalle=e

### B) Solicitud de datos con nivelDetalle reducido de todos los docentes del centro con código "35010488".
> * ?opcion=2 & codigoCentro=35010488

### C) Solicitud de datos con nivelDetalle medio de los docentes del centro con código "35010488" y servicio en el curso 2023. 
> * ?opcion=2 & codigoCentro=35010488 & tieneServicioEnElCentro=true & tieneServicioEnElCurso=2023 & nivelDetalle=m

