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
* **idEnsenyanza**: Si no se indica, se muestran las evaluaciones de todas las enseñanzas.

**Observaciones**:
>* Si no se indican posicionInicial ni tamanyoBloque, el número máximo de páginas a recuperar es 100 (posicionInicial = 0, tamanyoBloque = 100).
>* Opción 1: Los campos obligatorios son el cursoEscolar y el codigoCentro.
>* Opción 2: El campo idCursoCentro es obligatorio.

## Parámetros específicos

### Opción 1
* **cursoEscolar**: Obligatorio (Ej. 2023).
* **codigoCentro**: Obligatorio (Ej. 38010773)
* **idCursoCentro**: Si no se indica, se muestran todas las evaluaciones para el curso y centro especificado (Ej. E480D237-EC8C-4AFF-A870-01C277A3D712).
* **idEnsenyanza**: Si no se indica, se muestran las evaluaciones de todas las enseñanzas del curso y centro especificado (Ej. FF31EB10-8792-4121-87C7-3076537F5822).

**Observaciones**: El campo idCursoCentro no se tienen en cuenta en esta opción, ya que queda determinado por los campos cursoEscolar y codigoCentro.

### Opción 2
* **idCursoCentro**: Obligatorio (Ej. E480D237-EC8C-4AFF-A870-01C277A3D712).
* **idEnsenyanza**: Si no se indica, se muestran todas las evaluaciones para el idCursoCentro introducido.

**Observaciones**: Los campos cursoEscolar y codigoCentro están permitidos en esta opción, pero no se tienen en cuenta ya que quedan determinados por el campo idCursoCentro.

# Ejemplos.
### A) Solicitud de las evaluaciones del curso 2019 para una enseñanza concreta del centro con código "35010488".
> * ?opcion=1 & cursoEscolar=2019 & codigoCentro=35010488 & idEnsenyanza=C3E9383D-03D9-4CD1-83CE-15DAF8BF3E1D

### B) Solicitud de todas las evaluaciones para el idCursoCentro especificado .
> * ?opcion=2 & idCursoCentro=E480D237-EC8C-4AFF-A870-01C277A3D712

### C) Solicitud de las evaluaciones de una enseñanza concreta para un idCursoCentro determinado.
> * ?opcion=2 & idCursoCentro=E480D237-EC8C-4AFF-A870-01C277A3D712 & idEnsenyanza=FF31EB10-8792-4121-87C7-3076537F5822
