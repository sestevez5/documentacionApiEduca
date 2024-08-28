# Descripción general

Este endpoint proporciona datos de actividades susceptibles de disponer de horario:
* Matrículas (alumnado),
* Docentes-servicio (docentes),
* Pas-servicio (personal de administración y servicios),
* Grupos,
* Dependencias

## Parámetros comunes
* **opcion**: 1, 2, 3, 4, 5. Se deberá escoger uno obligatoriamente.
* **cursoEscolar**: Obligatorio (Ej. 2023).
* **codigoCentro**: Obligatorio (Ej. 38010773).
* **fechaReferenciaHorario**: Si se especifica, se muestran las actividades semanales en la fecha indicada.
* **horarioCompleto**: Si se selecciona, se muestran todas las actividades, tanto para cualquier periodo de vigencia como para una colección de fechas.

**Observaciones**:
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
