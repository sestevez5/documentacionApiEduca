# Descripción general

ApiEduca es un ApiREST de carácter interno de La Consejería de Educación, Formación Profesional, Actividad Física y Deportes del Gobierno de Canarias que expone las entidades que forman parte del dominio de Pincel (aplicación de gestión académica y administrativa de centros educativos). No obstante, con carácter temporal, también ofrece entidades de dominios externos como, por ejemplo, entidades del dominio del Directorio de Centros o el Plan de Estudio de Canarias.

# Seguridad

En líneas generales, el consumo de los endpoints publicados en este API requiere de una autenticación previa. Es requisito indispensable para su consumo disponer de un ApiKey que será gestionada por el servicio. Además, puede requerirse, adicionalmente, la autenticación adicional de una persona registrada en el servicio de autenticación.

# Parámetros
Pueden ser comunes o específicos de cada opción.

## Parámetros comunes
* **posicionInicial**: número de página a partir de la que se recuperarán los datos. Si no se indica, su valor por defecto será 0.
* **tamanyoBloque**: número de páginas que se recuperarán. Si no se indica, su valor por defecto será 100.
* **opcion**: 1, 2, 3, 4, 5. Se deberá escoger uno obligatoriamente.
* **cursoEscolar**: Obligatorio (Ej. 2023).
* **codigoCentro**: Obligatorio (Ej. 38010773).
* **fechaReferenciaHorario**: Si se especifica, se muestran las actividades de la semana en la que se encuentra la fecha indicada.
* **horarioCompleto**: Si se selecciona, se muestran todas las actividades, tanto para cualquier periodo de vigencia como para una colección de fechas.

**Observaciones**:
>* Si no se indican posicionInicial ni tamanyoBloque, el número máximo de páginas a recuperar es 100 (posicionInicial = 0, tamanyoBloque = 100).
>* En todas las opciones los campos _cursoEscolar_ y _codigoCentro_ son obligatorios.
>* Opción 1: Proporciona las actividades-horario del alumnado. Además del cursoEscolar y codigoCentro, será necesario indicar nifNieAlumnado o cialAlumnado (uno solo de los dos) e idEstudioSC.
>* Opción 2: Proporciona las actividades-horario del docente. Además del cursoEscolar y codigoCentro, será necesario indicar el nifNieDocente.
>* Opción 3: Proporciona las actividades-horario del personal de administración y servicios. Además del cursoEscolar y codigoCentro, será necesario indicar el nifNiePas.
>* Opción 4: Proporciona las actividades-horario de un grupo. Además del cursoEscolar y codigoCentro, será necesario indicar el codigoGrupo.
>* Opción 5: Proporciona las actividades-horario de una dependencia. Además del cursoEscolar y codigoCentro, será necesario indicar el codigoDependencia.

## Parámetros específicos

### Opción 1
* **nifNieAlumnado**: NIF o NIE del alumnado.
* **cialAlumnado**: CIAL del alumnado.
* **fechaReferenciaMatricula**:
* **idEstudioSC**: Obligatorio (Ej. 3206).

**Observaciones**: No están permitidos en esta opción los campos _nifNieDocente_, _fechaReferenciaServicioDocente_, _nifNiePas_, _fechaReferenciaServicioPas_, _codigoGrupo_, _codigoDependencia_.

### Opción 2
* **nifNieDocente**: NIF o NIE del docente.
* **fechaReferenciaServicioDocente**:

**Observaciones**: No están permitidos en esta opción los campos _nifNieAlumnado_, _cialAlumnado_, _fechaReferenciaMatricula_, _idEstudioSC_, _nifNiePas_, _fechaReferenciaServicioPas_, _codigoGrupo_, _codigoDependencia_.

### Opción 3
* **nifNiePas**: NIF o NIE del personal de administración y servicios.
* **fechaReferenciaServicioPas**:

**Observaciones**: No están permitidos en esta opción los campos _nifNieAlumnado_, _cialAlumnado_, _fechaReferenciaMatricula_, _idEstudioSC_, _nifNieDocente_, _fechaReferenciaServicioDocente_, _codigoGrupo_, _codigoDependencia_.

### Opción 4
* **codigoGrupo**: Obligatorio (Ej. ESO1A).

**Observaciones**: No están permitidos en esta opción los campos _nifNieAlumnado_, _cialAlumnado_, _fechaReferenciaMatricula_, _idEstudioSC_, _nifNieDocente_, _fechaReferenciaServicioDocente_, _nifNiePas_, _fechaReferenciaServicioPas_ , _codigoDependencia_.

### Opción 5
* **codigoDependencia**: Obligatorio (Ej. A10).

**Observaciones**: No están permitidos en esta opción los campos _nifNieAlumnado_, _cialAlumnado_, _fechaReferenciaMatricula_, _idEstudioSC_, _nifNieDocente_, _fechaReferenciaServicioDocente_, _nifNiePas_, _fechaReferenciaServicioPas_ , _codigoGrupo_.

# Ejemplos.
### A) Solicitud del horario completo de un alumno para un estudio concreto y un curso escolar determinado.
> * ?opcion=1 & cursoEscolar=2023 & codigoCentro=35010488 & horarioCompleto=true & cialAlumnado=A95F0610K & idEstudioSC=3206

### B) Solicitud del horario de un docente para un curso escolar determinado.
> * ?opcion=2 & cursoEscolar=2023 & codigoCentro=35010488 & nifNieDocente=00000001R

### C) Solicitud de datos con niveDetalle medio de los estudios de una enseñanza concreta del centro con código "35010488" en el curso 2023. 
> * ?opcion=1 & cursoEscolar=2023 & codigoCentro=35010488 & idEnsenyanza=737B55AB-E9C8-4EF0-A923-21B7E63C6F6B & idEstudio=016FE156-2D80-44BC-AA11-00652E182F90 & nivelDetalle=m

### D) Solicitud de datos con niveDetalle medio de los estudios de una enseñanza concreta del centro con código "35010488" en el curso 2023. 
> * ?opcion=1 & cursoEscolar=2023 & codigoCentro=35010488 & idEnsenyanza=737B55AB-E9C8-4EF0-A923-21B7E63C6F6B & idEstudio=016FE156-2D80-44BC-AA11-00652E182F90 & nivelDetalle=m

### E) Solicitud de datos con niveDetalle medio de los estudios de una enseñanza concreta del centro con código "35010488" en el curso 2023. 
> * ?opcion=1 & cursoEscolar=2023 & codigoCentro=35010488 & idEnsenyanza=737B55AB-E9C8-4EF0-A923-21B7E63C6F6B & idEstudio=016FE156-2D80-44BC-AA11-00652E182F90 & nivelDetalle=m
