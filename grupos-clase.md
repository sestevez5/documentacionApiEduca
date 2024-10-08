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
* **nivelDetalle**: r, m (reducido, medio). Si no se indica, su valor por defecto será r.

**Observaciones**:
>* Si no se indican posicionInicial ni tamanyoBloque, el número máximo de páginas a recuperar es 100 (posicionInicial = 0, tamanyoBloque = 100).
>* Opción 1: Los campos obligatorios son el cursoEscolar y el codigoCentro.
>* Opción 2: El campo idCursoCentro es obligatorio.

## Parámetros específicos

### Opción 1
* **cursoEscolar**: Obligatorio (Ej. 2023).
* **codigoCentro**: Obligatorio (Ej. 38010773).
* **idEstudioSC**: Optativo. No se puede especificar simultáneamente con el campo *idEnsenyanzaSC* (Ej. 232)
* **idEnsenyanzaSC**: Optativo. No se puede especificar simultáneamente con el campo *idEstudioSC* (Ej. 26)

**Observaciones**: Los campos idCursoCentro, IdEstudio, IdEnsenyanza no están permitidos en esta opción.

### Opción 2
* **idCursoCentro**: Obligatorio (Ej. E480D237-EC8C-4AFF-A870-01C277A3D712).
* **idEstudio**: Optativo. No se puede especificar simultáneamente con el campo *idEnsenyanza* (Ej. FB122AE6-37F4-45AF-BED5-F401C0AB6E87)
* **idEnsenyanza**: Optativo. No se puede especificar simultáneamente con el campo *idEstudio* (Ej. 5FF2F0FD-02AD-44F0-8D39-EF37774F9569)

**Observaciones**: Los campos cursoEscolar, codigoCentro, idEstudioSC, idEnsenyanzaSC no están permitidos en esta opción.

# Ejemplos.
### A) Solicitud de todos los grupos clase con nivelDetalle medio del centro con código "38011327" en el curso 2022.
> * ?opcion=1 & cursoEscolar=2022 & codigoCentro=38011327 & nivelDetalle=m

### B) Solicitud de los grupos clase con nivelDetalle reducido de una enseñanza concreta del centro con código "35007374" en el curso 2021.
> * ?opcion=1 & cursoEscolar=2021 & codigoCentro=38011327 & idEnsenyanzaSC=9

### C) Solicitud de todos los grupos clase con nivelDetalle medio para un idCursoCentro determinado.
> * ?opcion=2 & idCursoCentro=D2F5FE18-A312-4939-B8CC-46D8E8EF46FF & nivelDetalle=m

### D) Solicitud de los grupos clase con nivelDetalle reducido de un estudio concreto para un idCursoCentro determinado.
> * ?opcion=2 & idCursoCentro=D2F5FE18-A312-4939-B8CC-46D8E8EF46FF & idEstudio=89FC278E-0BFF-4190-8197-2F18A0C07516
