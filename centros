# Descripción general

ApiEduca es un ApiREST de carácter interno de La Consejería de Educación, Formación Profesional, Actividad Física y Deportes del Gobierno de Canarias que expone las entidades que forman parte del dominio de Pincel (aplicación de gestión académica y administrativa de centros educativos). No obstante, con carácter temporal, también ofrece entidades de dominios externos como, por ejemplo, entidades del dominio del Directorio de Centros o el Plan de Estudio de Canarias.

# Seguridad

En líneas generales, el consumo de los endpoints publicados en este API requiere de una autenticación previa. Es requisito indispensable para su consumo disponer de un ApiKey que será gestionada por el servicio. Además, puede requerirse, adicionalmente, la autenticación adicional de una persona registrada en el servicio de autenticación.

# Parámetros
Pueden ser comunes o específicos de cada opción.

## Parámetros comunes
* **posicionInicial**: número de página a partir de la que se recuperarán los datos. Si no se indica, su valor por defecto será 0.
* **tamanyoBloque**: número de páginas que se recuperarán. Si no se indica, su valor por defecto será 100.
* **codigoCentro**: Si no se indica, se muestran todos los centros (Ej. 38010773)
* **idCentroSC**: Si no se indica, se muestran todos los centros (Ej. 2250)
* **codEtapaCentro**: Si no se indica, se muestran todos los tipos de centros (Ej. IES).
* **isla**: Si no se indica, se muestran los centros de todas las islas (Ej. 3, muestra los centros de Gran Canaria).
* **naturaleza**: Si no se indica, se muestran los centros de cualquier naturaleza (Ej. 1, ofrece los centros públicos).
* **zonaInspeccion**: Si no se indica, se muestran los centros de todas las zonas de inspección (Ej. 305, ofrece los centros adscritos a esa zona).
* **cursoEscolarZonaInspeccion**: Si no se indica, se muestran los centros para todos los cursos (Ej. 2022, ofrece los centros de ese curso).
* **codigoMunicipio**: Si no se indica, se muestran los centros de todos los municipio (Ej. 38005, ofrece los centros con ese código)

**Observaciones**:
>* Todos los parámetros son opcionales.

# Ejemplos.
### A) Solicitud de datos del centro con código "38011108".
> * ?codigoCentro=38011108

### B) Solicitud de los centros públicos de la isla de Tenerife.
> * ?isla=7 & naturaleza=1

### C) Solicitud de los centros de la zona de inspección 401 en el curso 2021. 
> * ?zonaInspeccion=401 & cursoEscolarZonaInspeccion=2021
