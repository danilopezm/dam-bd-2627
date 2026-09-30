---
unit_title: "Unidad 1. Sistemas de información."
---
[Volver a Inicio](../README.md)

1. [FICHEROS](#1-ficheros)
   - [TIPOS DE FICHEROS Y FORMATOS](#11-tipos-de-ficheros-y-formatos)
2. [BASES DE DATOS](#2-bases-de-datos)
   - [TIPOS DE BASES DE DATOS](#21-tipos-de-bases-de-datos)
3. [BASES DE DATOS RELACIONALES](#3-bases-de-datos-relacionales)
   - [CONCEPTOS](#31-conceptos)
   - [SISTEMAS GESTORES DE BASES DE DATOS](#32-sistemas-gestores-de-bases-de-datos)

## 1. FICHEROS

Un ordenador almacena distintos tipos de información en sus dispositivos de almacenamiento. Para organizar esa información se utilizan **ficheros** o **archivos**.

Un fichero es una unidad de información almacenada en un dispositivo, identificada normalmente por un nombre. Su contenido está formado por bits (ceros y unos) y debe interpretarse según un formato determinado.

Un fichero puede tener una **extensión**, como `.txt`, `.pdf`, `.jpg` o `.mp3`, que orienta al sistema operativo y al usuario sobre el tipo de contenido y la aplicación con la que puede abrirse. Sin embargo, la extensión no garantiza el formato real del fichero.

### 1.1. TIPOS DE FICHEROS Y FORMATOS

El formato de un fichero determina cómo se organizan e interpretan los datos que contiene. Como todos los ficheros son secuencias de bits, es necesario conocer su formato para dar significado a la información almacenada.

#### 1.1.1. SEGÚN EL CONTENIDO

- **Ficheros de texto**: almacenan caracteres, letras, números y símbolos que pueden interpretarse mediante una codificación de caracteres, como UTF-8. Se pueden leer y editar con un editor de texto.  
  - Ejemplos: `.txt`, `.csv`, `.html`, `.json` y `.py`.

- **Ficheros binarios**: almacenan datos en un formato que no está pensado para ser leído directamente como texto. Para interpretarlos correctamente se necesita un programa compatible con su formato.  
  - Ejemplos: imágenes, archivos de audio, vídeos, documentos PDF, hojas de cálculo, programas ejecutables y archivos de bases de datos.

#### 1.1.2. SEGÚN LA ORGANIZACIÓN

La organización de un fichero indica cómo se estructuran sus registros y cómo se puede acceder a ellos:

- **Secuencial**: los registros se almacenan uno detrás de otro. Para llegar a un registro concreto suele ser necesario recorrer los anteriores.
   Ejemplo: leer línea a línea un fichero de texto.

- **Directa o aleatoria**: permite acceder a un registro concreto sin recorrer necesariamente todos los anteriores. Normalmente se utiliza una posición, una dirección o una clave para localizarlo.  

- **Indexada**: utiliza un índice que relaciona una clave con la posición de los registros dentro del fichero. Facilita la búsqueda rápida, de forma similar al índice de un libro.  

> ⚠️ Atención: existen variantes que combinan distintas formas de organización y acceso para optimizar el rendimiento según el uso previsto del fichero.

#### 1.1.3. SEGÚN LA UTILIDAD

Según su finalidad dentro de un sistema de información, los ficheros pueden clasificarse en:

- **Maestros**: contienen los datos principales y relativamente estables de una organización.
   Ejemplo: el fichero con los datos de los alumnos de un instituto.

- **De movimientos**: contienen las operaciones que se realizan sobre los datos maestros, como altas, bajas, modificaciones, ventas, matrículas o pagos.  

- **Históricos**: almacenan datos antiguos que ya no se usan en los procesos cotidianos, pero que se conservan para consultas, auditorías, estadísticas o motivos legales.

#### 📝 Actividades

> **Actividad 1. Abrir un fichero**.
> 1. Busca en tu ordenador un fichero con extensión '.docx'.
> 2. Ábrelo con el Bloc de notas.
> 3. Responde: ¿por qué no se ve bien el contenido del fichero?

> **Actividad 2. Tabla de códigos ASCII**. 
> La tabla ASCII es un conjunto estandarizado de códigos numéricos que representan caracteres que una computadora puede entender.
> - Caracteres de control (0–31 y 127): No se imprimen; se usaban para controlar dispositivos, como el retorno de carro CR o salto de línea LF.
> - Símbolos y signos de puntuación: Por ejemplo !, @, #, $, %.
> - Números (48–57): Los dígitos del 0 al 9.
> - Letras mayúsculas (65–90): A a Z.
> - Letras minúsculas (97–122): a a z.
> - Caracteres extendidos (128–255, en ASCII extendido): Permiten letras acentuadas, símbolos gráficos y otros caracteres especiales.
> 
> Conéctate a Internet y busca una tabla de códigos ASCII de 8 bits. Traduce el texto "Bases de Datos" a binario.

> **Actividad 3. Identificación de ficheros**. 
> Observa la siguiente captura de una carpeta en Windows:
> ![Lista de ficheros](img/Lista.png)
> Indica para cada fichero su tipo y qué contiene o para qué se usa.


## 2. BASES DE DATOS

Una **Base de Datos (BD)** es un conjunto organizado de datos relacionados entre sí, almacenados de forma estructurada y pertenecientes a un mismo contexto. Una BD permite conservar, consultar y compartir información de manera eficiente.

Para definir, crear, consultar, modificar y administrar una BD se utiliza un **Sistema Gestor de Bases de Datos (SGBD)**.

Antes de utilizar bases de datos, era habitual almacenar la información mediante sistemas de ficheros tradicionales. A continuación se muestran las principales diferencias:

- **Ficheros tradicionales:**  
  - Almacenan los datos en archivos independientes, normalmente creados para una aplicación concreta.  
  - Cada aplicación suele gestionar sus propios ficheros, por lo que los datos pueden quedar aislados y ser difíciles de compartir con otras aplicaciones.  
  - Es habitual que existan **datos redundantes**, es decir, que la misma información se repita en varios archivos.  
  - Actualizar un dato puede requerir modificar varios ficheros, lo que aumenta el tiempo de mantenimiento y el riesgo de inconsistencias.  
  - Existe una fuerte dependencia entre los programas y la estructura de los ficheros.

- **Bases de datos:**  
  - Los datos se almacenan de forma organizada, con una estructura o esquema definido, y son gestionados por un **SGBD**.  
  - Permiten que varias aplicaciones y usuarios accedan a los mismos datos de forma controlada.  
  - Reducen la redundancia de datos y ayudan a mantener su consistencia.  
  - Facilitan la consulta, actualización, seguridad, recuperación y control del acceso a la información.  
  - Separan, en cierta medida, los datos de las aplicaciones que los utilizan.

> ⚠️ Atención:  
> En un sistema tradicional de ficheros, la información puede estar dispersa en varios archivos. Las relaciones entre esos archivos y la recuperación conjunta de los datos deben ser programadas y controladas por cada aplicación. En una base de datos, el SGBD centraliza la gestión, el acceso y las reglas de integridad de la información.

### 2.1. TIPOS DE BASES DE DATOS

Las bases de datos se pueden clasificar según distintos criterios. Uno de los más habituales es el **modelo de datos**, es decir, la forma en que organizan y representan la información.

#### 2.1.1. EVOLUCIÓN HISTÓRICA DE LOS MODELOS DE BASES DE DATOS

**1. Primeros sistemas (años 60–70)**

- BD jerárquicas  
  - Organizan los datos en una estructura de árbol formada por registros padre e hijo.  
  - Cada registro hijo depende normalmente de un único registro padre.  
  - Ejemplo: IMS de IBM.

- BD en red  
  - Organizan los registros mediante una red de relaciones, de forma que un registro puede estar relacionado con varios registros.  
  - El modelo fue definido por el grupo CODASYL.

**2. BD relacionales (desde los años 70)**

- Organizan los datos en tablas, formadas por filas (registros) y columnas (campos o atributos).
- Las tablas se relacionan mediante claves primarias y claves foráneas.
- Utilizan principalmente el lenguaje SQL (*Structured Query Language*) para definir estructuras y consultar o modificar datos.
- Ejemplos de SGBD relacionales: Oracle Database, MySQL, PostgreSQL y Microsoft SQL Server.

**3. BD orientadas a objetos (desde los años 80)**

- Almacenan los datos como objetos, que pueden incluir atributos y métodos.
- Resultan adecuadas para determinados ámbitos con estructuras complejas, como aplicaciones CAD, multimedia o científicas.
- Ejemplos: ObjectDB y db4o.

**4. BD NoSQL (desde los años 2000)**

- No se basan necesariamente en tablas relacionales ni requieren un esquema rígido.
- Se utilizan cuando se necesita flexibilidad, escalabilidad horizontal o un modelo de datos especializado.
- Principales tipos:  
  - Clave-valor: almacenan pares formados por una clave y un valor.  
    - Ejemplos: Redis y Amazon DynamoDB.  
  - Documentales: almacenan documentos, habitualmente con estructuras similares a JSON.  
    - Ejemplos: MongoDB y CouchDB.  
  - Columnas anchas: organizan los datos en familias de columnas y están orientadas a grandes volúmenes distribuidos.  
    - Ejemplos: Apache Cassandra y HBase.  
  - Grafos: almacenan nodos y relaciones, llamados aristas.  
    - Ejemplos: Neo4j y OrientDB.

**5. BD modernas y emergentes**

- NewSQL: combinan SQL y transacciones consistentes con arquitecturas distribuidas y escalables.  
  - Ejemplos: Google Cloud Spanner y VoltDB.

- En memoria: mantienen una parte importante de los datos en memoria RAM para ofrecer gran velocidad de acceso.  
  - Ejemplo: SAP HANA.

- Multimodelo: permiten utilizar más de un modelo de datos dentro del mismo sistema.  
  - Ejemplos: ArangoDB y Azure Cosmos DB.

- Vectoriales: almacenan y buscan vectores numéricos, utilizados especialmente en sistemas de IA, búsqueda semántica y aplicaciones con modelos de lenguaje.  
  - Ejemplos: Pinecone y Milvus.

#### 2.1.2. CLASIFICACIÓN DE LAS BASES DE DATOS SEGÚN SU UBICACIÓN

Otra forma de clasificar las bases de datos es según dónde se almacenan y desde dónde se accede a ellas. Las principales son las siguientes:

**1. BD locales**

En una base de datos local, los datos y la aplicación que los utiliza se encuentran normalmente en el mismo ordenador o dispositivo.

* Son adecuadas para aplicaciones personales, educativas, de escritorio o móviles, especialmente cuando el número de usuarios concurrentes es reducido.
* Ejemplo: **Microsoft Access**, que permite crear y gestionar bases de datos de forma relativamente sencilla.
* **SQLite** es otro ejemplo habitual: se utiliza en muchas aplicaciones móviles y de escritorio, ya que se integra dentro de la propia aplicación y almacena la base de datos en un archivo local.
* Otros ejemplos históricos son **dBase** y **Paradox**.

**2. BD centralizadas**

En los sistemas centralizados, la base de datos se administra desde un **servidor central**, al que acceden los usuarios y las aplicaciones a través de una red.

* Que la base de datos esté centralizada no significa que se guarde en un único archivo o en un solo disco: internamente puede usar múltiples ficheros, discos o sistemas de almacenamiento.
* En una arquitectura **cliente/servidor**, el SGBD se ejecuta en el servidor y los clientes se conectan a él mediante una red local o Internet.
* El servidor puede atender a varios usuarios y aplicaciones de forma simultánea.
* Es un modelo muy habitual en organizaciones y empresas.
* Ejemplos de SGBD utilizados en este modelo: **PostgreSQL**, **Oracle Database**, **Microsoft SQL Server**, **IBM Db2** y **MySQL**.

**3. BD distribuidas**

En una base de datos distribuida, los datos se almacenan o replican en varios nodos conectados mediante una red. Los nodos pueden encontrarse en ubicaciones geográficas diferentes.

* El sistema gestor coordina los distintos nodos para que los usuarios puedan trabajar con los datos como si formaran parte de una única base de datos lógica.
* Los datos pueden estar **fragmentados**, es decir, repartidos entre varios nodos, o **replicados**, es decir, copiados en varios nodos para mejorar la disponibilidad.
* Este modelo puede aumentar la disponibilidad, la tolerancia a fallos y la cercanía de los datos a los usuarios, pero también hace más compleja la sincronización y el mantenimiento de la consistencia.
* Ejemplos: **Google Cloud Spanner**, **CockroachDB**, **Apache Cassandra** y algunos servicios de bases de datos distribuidas en la nube.

#### 📝 Actividades

> **Actividad 4. Comparativa de sistemas**.
> 
> Elabora un esquema o mapa conceptual sobre los tipos de bases de datos estudiados.

> **Actividad 5. Tipos de datos en BD**.
> 
> Investiga sobre los tipos de datos más comunes en las bases de datos relacionales. Puedes utilizar PostgreSQL como referencia, ya que será el sistema gestor de bases de datos que emplearemos. Incluye una breve descripción y un ejemplo de uso para cada tipo de dato. En próximas sesiones profundizaremos en estos conceptos.


## 3. BASES DE DATOS RELACIONALES

### 3.1. CONCEPTOS

- **Datos:** hechos conocidos que se pueden registrar y que tienen un significado.  

- **Tipo de dato:** indica la naturaleza de un dato y los valores que puede almacenar un campo.  
   - Ejemplos: texto, número, fecha, valor lógico o decimal.

- **Entidad:** todo aquello sobre lo que interesa almacenar información.  
   - Ejemplos: 'Persona', 'Producto', 'Animal', 'Cliente' o 'Vehiculo'.

- **Atributo o campo:** característica o propiedad de una entidad. En una tabla relacional, se representa mediante una columna.  
   - Ejemplo: para la entidad 'CLIENTE', algunos atributos pueden ser 'nif', 'nombre', 'apellidos', 'direccion' y 'telefono'.  

- **Tabla o relación:** conjunto de datos organizados en filas y columnas, identificado mediante un nombre. Normalmente representa una entidad.
   - Ejemplo: la información de todos los clientes de una BD se puede guardar en la tabla 'CLIENTES'.

- **Registro, fila o tupla:** cada una de las filas de una tabla. Contiene los valores de todos los campos correspondientes a un elemento concreto.  
   - Ejemplo: en la tabla 'CLIENTES', un registro puede contener la información de una persona, como Pedro Picapiedra.

- **Clave primaria:** campo, o conjunto de campos, que identifica de forma única cada registro de una tabla. No puede repetirse ni tener un valor nulo.  
   - Ejemplo: el 'nif' puede ser la clave primaria de la tabla 'CLIENTES', ya que es único para cada persona.

- **Clave foránea o clave ajena:** campo de una tabla que contiene valores de la clave primaria de otra tabla. Permite establecer relaciones entre ambas tablas.  
   - Ejemplo: el campo 'codCliente' de la tabla 'VEHICULOS' puede ser una clave foránea que hace referencia a la clave primaria 'codCliente' de la tabla 'CLIENTES'.

- **Relación:** vínculo establecido entre dos tablas mediante una clave primaria y una clave foránea.  
   - Ejemplo: un cliente puede tener varios vehículos. Las tablas 'CLIENTES' y 'VEHICULOS' se relacionan mediante el campo 'codCliente'.

- **Integridad referencial:** regla que garantiza que toda clave foránea tenga un valor válido en la clave primaria de la tabla relacionada. Evita referencias a registros inexistentes.  
   - Ejemplo: no se puede registrar un vehículo con un 'codCliente' que no exista previamente en la tabla 'CLIENTES'. La integridad referencial sirve precisamente para que las referencias entre tablas sean consistentes.

- **Metadatos:** son datos que describen otros datos y la estructura de la BD.  

### 3.2. SISTEMAS GESTORES DE BASES DE DATOS

Un **Sistema Gestor de Bases de Datos (SGBD)** es un software que permite a los usuarios definir, crear, consultar, modificar y administrar una base de datos, proporcionando un acceso controlado a la información.

Entre los principales servicios que proporciona un SGBD se encuentran los siguientes:

- **Definición de datos (DDL, Data Definition Language):**  
  Permite definir y modificar la estructura de la base de datos. Con DDL se crean, alteran o eliminan objetos como bases de datos, tablas, vistas, índices y restricciones.  
  - Ejemplos de sentencias: `CREATE`, `ALTER` y `DROP`.

- **Manipulación de datos (DML, Data Manipulation Language):**  
  Permite insertar, consultar, modificar y eliminar los datos almacenados en las tablas.  
  - Ejemplos de sentencias: `INSERT`, `SELECT`, `UPDATE` y `DELETE`.

- **Control de datos (DCL, Data Control Language):**  
  Permite controlar el acceso de los usuarios a la base de datos mediante permisos y privilegios.  
  - Ejemplos de sentencias: `GRANT` y `REVOKE`.

- **Control de transacciones (TCL, Transaction Control Language):**  
  Permite confirmar o deshacer grupos de operaciones para mantener la consistencia de los datos.  
  - Ejemplos de sentencias: `COMMIT`, `ROLLBACK` y `SAVEPOINT`.

- **Sistema de seguridad:**  
  Evita que usuarios no autorizados accedan, consulten o modifiquen la información de la base de datos.

- **Sistema de integridad:**  
  Garantiza que los datos sean válidos y coherentes mediante reglas y restricciones, como las claves primarias, las claves foráneas o los valores obligatorios.

- **Sistema de control de concurrencia:**  
  Permite que varios usuarios accedan a la base de datos al mismo tiempo, evitando conflictos e inconsistencias cuando intentan modificar los mismos datos.

- **Sistema de recuperación:**  
  Permite restaurar la base de datos a un estado coherente después de un fallo de hardware, software, alimentación eléctrica o una operación incorrecta.

- **Diccionario de datos o catálogo:**  
  Contiene los metadatos de la base de datos: información sobre las tablas, campos, tipos de datos, restricciones, relaciones, usuarios y permisos.

#### 🖥️ Hojas de ejercicios

> - Hoja de ejercicios 1
