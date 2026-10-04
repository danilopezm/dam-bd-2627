---
unit_title: "Unidad 2. Diseño lógico de la base de datos."
---
[Volver a Inicio](../README.md)

1. [MODELO DE DATOS](#1-modelo-de-datos)
2. [DIAGRAMAS E/R](#2-diagramas-er)
    - [ENTIDADES](#21-entidades)
    - [ATRIBUTOS Y TIPOS](#22-atributos)
    - [RELACIONES](#23-relaciones)
    - [CARDINALIDAD](#24-cardinalidad)
    - [TIPO DE CORRESPONDENCIA](#25-tipo-de-correspondencia)
    - [DEBILIDAD](#26-debilidad)
3. [EL MODELO E/R AMPLIADO](#3-el-modelo-er-ampliado)
4. [MODELO RELACIONAL](#4-modelo-relacional)
    - [ELEMENTOS DE UNA RELACIÓN](#41-elementos-de-una-relación)
    - [RESTRICCIONES DEL MODELO RELACIONAL](#42-restricciones-del-modelo-relacional)
    - [CLAVES PRIMARIAS Y CLAVES AJENAS](#43-claves-primarias-y-claves-ajenas)
    - [INTEGRIDAD REFERENCIAL](#44-integridad-referencial)
    - [REPRESENTACIÓN DEL MODELO RELACIONAL](#45-️representación-del-modelo-relacional)
6. [NORMALIZACIÓN](#6-normalización)
    - [1FN (PRIMERA FORMA NORMAL)](#61-1fn-primera-forma-normal)
    - [2FN (SEGUNDA FORMA NORMAL)](#62-2fn-segunda-forma-normal)
    - [3FN (TERCERA FORMA NORMAL)](#63-3fn-tercera-forma-normal)

## 1. Modelo de datos

Un modelo es una representación simplificada de la realidad que permite comprenderla, analizarla y trabajar con ella de una forma más sencilla.

Para construir un modelo se realiza una **abstracción de la realidad**, seleccionando los elementos, las características y las relaciones que resultan relevantes para el objetivo que se quiere alcanzar. Por tanto, un modelo no representa todos los detalles de la realidad, sino únicamente los que son necesarios.

Los modelos se utilizan en diferentes áreas de la informática. Algunos ejemplos son:

- **UML**, utilizado en ingeniería del software.
- **El modelo Entidad-Relación**, utilizado en el diseño de bases de datos.
- **Los diagramas de arquitectura**, utilizados para representar sistemas informáticos.

### 1.1. Definición de modelo de datos

Un modelo de datos es un conjunto de conceptos, estructuras, operaciones y reglas que permiten representar:

- los datos que se quieren almacenar;
- las relaciones entre los datos;
- las operaciones que pueden realizarse;
- las restricciones que deben cumplirse.

Por ejemplo, en una base de datos de un centro educativo se pueden representar los alumnos, los grupos, los módulos y las matrículas. También se pueden definir relaciones entre estos elementos y restricciones, como que un alumno no pueda matricularse dos veces en el mismo módulo.

### 1.2. Principales modelos de datos

Los principales modelos de datos son:

- **Modelo jerárquico:** organiza los datos en una estructura de árbol formada por relaciones padre-hijo.
- **Modelo en red:** permite que un registro esté relacionado con varios registros de otros conjuntos, por lo que puede representar relaciones más complejas que el modelo jerárquico.
- **Modelo relacional:** organiza los datos en tablas formadas por filas y columnas. Es el modelo más utilizado en las bases de datos tradicionales.
- **Modelo orientado a objetos:** representa la información mediante objetos con atributos y, en algunos casos, operaciones o métodos.
- **Modelo objeto-relacional:** combina las características principales del modelo relacional con algunas características propias de la orientación a objetos.
- **Modelos NoSQL:** incluyen modelos documentales, clave-valor, de columnas y de grafos, entre otros.

En esta unidad nos centraremos principalmente en el **modelo Entidad-Relación**, utilizado para el diseño conceptual, y en el **modelo relacional**, utilizado para representar lógicamente la base de datos.

### 1.3. Clasificación según el nivel de abstracción

Los modelos de datos también pueden clasificarse según el nivel de detalle o abstracción que presentan.

#### 1.3.1. Modelo conceptual

El modelo conceptual representa la información de una organización de forma general, sin depender de un SGBD concreto.

Se utiliza durante la fase de análisis y permite identificar:

- las entidades;
- los atributos;
- las relaciones;
- las restricciones principales.

El modelo Entidad-Relación es uno de los modelos más utilizados para representar esta fase. Permite describir, por ejemplo, que un alumno puede matricularse en varios módulos y que un módulo puede tener varios alumnos.

#### 1.3.2. Modelo lógico

El modelo lógico transforma el modelo conceptual en una estructura que puede ser interpretada por un tipo de SGBD.

En el caso del modelo relacional, el modelo lógico define:

- las tablas;
- las columnas;
- las claves primarias;
- las claves foráneas;
- las relaciones entre tablas;
- las restricciones de integridad.

Por ejemplo, una entidad `Alumno` del modelo Entidad-Relación puede transformarse en una tabla llamada 'ALUMNO', con columnas como 'id_alumno', 'nombre' y 'apellidos'.

#### 1.3.3. Modelo físico

El modelo físico describe cómo se implementa el modelo lógico en un SGBD concreto.

Puede incluir:

- los tipos de datos específicos del SGBD;
- los índices;
- las particiones;
- la organización de los archivos;
- los espacios de almacenamiento;
- las estrategias para mejorar el rendimiento;
- las medidas de seguridad y acceso.

El modelo físico depende del SGBD que se utilice. Algunos ejemplos de SGBD son:

- Microsoft Access;
- MySQL;
- PostgreSQL;
- Microsoft SQL Server;
- Oracle Database.

> **Importante:** estos productos no son modelos físicos, sino sistemas gestores de bases de datos en los que se puede implementar un modelo físico.

### 1.4. Proceso general de diseño

El diseño de una base de datos suele realizarse siguiendo varias fases:

1. **Análisis de requisitos:** se estudia qué información necesita la organización.
2. **Diseño conceptual:** se identifican las entidades, los atributos y las relaciones.
3. **Diseño lógico:** se transforma el modelo conceptual en tablas, claves y restricciones.
4. **Diseño físico:** se implementa el modelo lógico en un SGBD concreto.
5. **Creación y pruebas:** se crean las tablas, se introducen datos y se comprueba el funcionamiento.

En este tema se trabajarán principalmente las fases conceptual y lógica:

- el modelo Entidad-Relación;
- la transformación al modelo relacional.

### 1.5. Diferencia entre modelo de datos y SGBD

No debe confundirse un modelo de datos con un sistema gestor de bases de datos.

- El **modelo de datos** define cómo se representan, organizan y relacionan los datos.
- El **SGBD** es el programa que permite crear, gestionar, consultar y utilizar la base de datos.

Por ejemplo:

- El **modelo relacional** establece que los datos se organizan en tablas relacionadas.
- **MySQL**, **PostgreSQL** y **Oracle Database** son SGBD que permiten implementar bases de datos siguiendo ese modelo.

---

## Ejemplo completo

Supongamos que un centro educativo necesita gestionar su alumnado y sus módulos.

### Modelo conceptual

Se identifican las siguientes entidades:

- **Alumno**
- **Módulo**
- **Matrícula**

También se identifican las relaciones:

- Un alumno puede realizar varias matrículas.
- Un módulo puede tener muchos alumnos matriculados.
- Cada matrícula relaciona a un alumno con un módulo.

### Modelo lógico

El modelo conceptual puede transformarse en las siguientes tablas:

- `ALUMNO(id_alumno, nombre, apellidos)`
- `MODULO(id_modulo, nombre)`
- `MATRICULA(id_alumno, id_modulo, fecha)`

En este caso:

- 'id_alumno' es la clave primaria de 'ALUMNO'.
- 'id_modulo' es la clave primaria de 'MODULO'.
- En 'MATRICULA', 'id_alumno' y 'id_modulo' actúan como claves foráneas.
- La combinación de 'id_alumno' e 'id_modulo' puede formar la clave primaria de 'MATRICULA'.

### Modelo físico

Finalmente, estas tablas se implementan en un SGBD concreto, como PostgreSQL o MySQL. En esta fase se pueden definir:

- los tipos de datos concretos;
- los índices;
- las restricciones;
- los permisos de los usuarios;
- la ubicación y organización del almacenamiento.


## 2. Diagrama Entidad-Relación (DER)

El **Modelo Entidad-Relación (MER)** es un modelo conceptual que describe la estructura de los datos de un sistema. Permite representar:

- los conjuntos de entidades;
- los atributos de las entidades;
- las relaciones entre ellas;
- las restricciones que deben cumplirse.

El **Diagrama Entidad-Relación (DER)** es la representación gráfica concreta de un modelo Entidad-Relación. El DER es independiente del SGBD que se utilice posteriormente.

En un DER se representa gráficamente cómo se organiza la información de una base de datos. Sus elementos básicos son:

- entidades;
- atributos;
- relaciones.

Además, el diagrama puede representar restricciones como:

- claves;
- cardinalidades;
- participación mínima y máxima;
- atributos derivados;
- atributos multivaluados;
- entidades débiles.

De esta forma, el diagrama permite identificar de un vistazo:

- qué entidades forman parte del sistema;
- qué características tiene cada entidad;
- cómo se relacionan las entidades;
- qué restricciones deben cumplir esas relaciones.

En la siguiente imagen se muestra un ejemplo de Diagrama Entidad-Relación:

<div style="text-align: center;">
  <img src="img/esquemaER.png" alt="Ejemplo de Diagrama Entidad-Relación" width="500">
</div>

En los siguientes apartados se explican los elementos que componen un DER y el proceso básico para construirlo.

### 2.1. Entidades

Una **entidad** es un objeto, sujeto, lugar, acontecimiento o concepto sobre el que se desea almacenar información.

En el esquema anterior pueden identificarse las siguientes entidades:

- `ALUMNO`;
- `MÓDULO`;
- `PROFESOR`.

Una entidad representa un conjunto de elementos del mismo tipo. Por ejemplo, la entidad `ALUMNO` representa al conjunto de alumnos del centro educativo.

Cada entidad se representa mediante un rectángulo:

<div style="text-align: center;">
  <img src="img/entidades.png" alt="Representación de entidades" width="500">
</div>

Una **ocurrencia** de una entidad es un elemento concreto perteneciente a ese conjunto. Por ejemplo, Juan Pérez sería una ocurrencia de la entidad `ALUMNO`.

### 2.2. Atributos

Un **atributo** es una propiedad o característica de una entidad.

Por ejemplo, la entidad `ALUMNO` puede tener los siguientes atributos:

- `NumExpediente`;
- `Nombre`;
- `Apellidos`;
- `FechaNacimiento`.

> **Importante:** las relaciones también pueden tener atributos. Por ejemplo, una relación `MATRÍCULA` puede tener los atributos `FechaMatricula` y `Convocatoria`.

En la notación utilizada en estos apuntes, los atributos se representan mediante pequeños círculos unidos a la entidad por una línea. Junto a cada círculo se escribe el nombre del atributo:

<div style="text-align: center;">
  <img src="img/atributo2.png" alt="Representación de atributos" width="500">
</div>

#### 2.2.1. Dominio de un atributo

El **dominio** de un atributo es el conjunto de valores que puede tomar ese atributo.

Por ejemplo, el dominio del atributo `Nombre` podría ser el conjunto de cadenas de caracteres de una longitud máxima determinada.

Ejemplo de atributos y dominios de una entidad `EMPLEADO`:

| Atributo | Dominio |
|---|---|
| `DNI` | Cadena de caracteres de longitud 9 |
| `Nombre` | Cadena de caracteres de longitud máxima 20 |
| `Apellidos` | Cadena de caracteres de longitud máxima 30 |
| `FechaIncorporacion` | Fecha válida |
| `Antigüedad` | Número entero no negativo o intervalo de tiempo |
| `Salario` | Número real con dos decimales |
| `Categoría` | Valor perteneciente a un conjunto de categorías |
| `JornadaCompleta` | Verdadero o falso |

#### Actividad 1

Indica cuál podría ser el dominio de cada uno de los siguientes atributos de una entidad `PERSONA`:

- `FechaNacimiento`;
- `LocalidadNacimiento`;
- `Edad`;
- `EsMayorDeEdad`;
- `DNI`;
- `Teléfonos`;
- `Nombre`;
- `Apellidos`.

Considera que una persona puede tener varios teléfonos.

#### 2.2.2. Tipos de atributos

##### Atributos simples y compuestos

Un atributo es **simple** cuando no se considera dividido en partes.

Por ejemplo:

- `Nombre`;
- `DNI`;
- `Salario`.

Un atributo es **compuesto** cuando puede dividirse en varios componentes.

Por ejemplo, el atributo `Direccion` podría dividirse en:

- `Calle`;
- `Numero`;
- `CodigoPostal`;
- `Localidad`.

<div style="text-align: center;">
  <img src="img/atributo2.png" alt="Atributos simples y compuestos" width="500">
</div>

Aunque una fecha puede dividirse conceptualmente en día, mes y año, en una implementación concreta suele almacenarse como un único valor de tipo fecha.

##### Atributos monovaluados y multivaluados

Un atributo es **monovaluado** cuando cada ocurrencia de la entidad puede tener un único valor para ese atributo.

Por ejemplo, cada alumno puede tener un único número de expediente.

Un atributo es **multivaluado** cuando una ocurrencia de la entidad puede tener varios valores para ese atributo.

Por ejemplo, una persona puede tener varios teléfonos:

- teléfono personal;
- teléfono de trabajo;
- teléfono de contacto alternativo.

<div style="text-align: center;">
  <img src="img/atributo3.png" alt="Atributos monovaluados y multivaluados" width="500">
</div>

##### Atributos obligatorios y opcionales

Un atributo es **obligatorio** cuando todas las ocurrencias de una entidad deben tener un valor para ese atributo.

Un atributo es **opcional** cuando algunas ocurrencias pueden no tener ningún valor.

Por ejemplo, `FechaNacimiento` podría ser obligatorio en una entidad `PERSONA`, mientras que `Aficiones` podría ser opcional.

##### Atributos derivados y no derivados

Un atributo es **derivado** cuando su valor puede obtenerse a partir de otros datos.

Por ejemplo, `ImporteVenta` puede calcularse a partir de:

- `UnidadesVendidas`;
- `PrecioUnidad`.

Un atributo es **no derivado** cuando su valor se almacena directamente y no se obtiene a partir de otros atributos.

No conviene abusar de los atributos derivados almacenados, porque su valor puede quedar desactualizado si cambian los datos de los que depende.

##### Atributos clave

Una **clave** es un atributo o conjunto de atributos que permite identificar de forma única cada ocurrencia de una entidad.

Una clave debe:

- identificar de forma unívoca cada ocurrencia;
- no admitir valores duplicados;
- no admitir valores nulos;
- ser lo más sencilla y estable posible.

Una clave puede estar formada por un solo atributo o por varios atributos.

Entre las claves candidatas se distinguen:

- **Clave primaria:** clave candidata elegida como identificador principal de la entidad.
- **Clave alternativa:** cualquier otra clave candidata que también permite identificar de forma única una ocurrencia.

Para elegir una clave primaria deben tenerse en cuenta la simplicidad, la longitud, la estabilidad y la capacidad de identificar de forma única cada ocurrencia.

<div style="text-align: center;">
  <img src="img/atributo5.png" alt="Representación de los tipos de atributos" width="500">
</div>

#### Actividad 2

Observa la imagen y clasifica cada atributo según los siguientes criterios:

- obligatorio u opcional;
- compuesto o simple;
- derivado o no derivado;
- monovaluado o multivaluado.

<div style="text-align: center;">
  <img src="img/atributo6.png" alt="Ejemplo de atributos" width="500">
</div>

### 2.3. Relaciones

Una **relación** es una asociación o correspondencia entre dos o más entidades.

En los enunciados de los ejercicios, las relaciones suelen expresarse mediante verbos o formas verbales.

Por ejemplo:

- un alumno **se matricula en** un módulo;
- un profesor **imparte** un módulo;
- un cliente **realiza** un pedido.

Cada relación se representa mediante un rombo, que se une mediante líneas a las entidades participantes.

#### 2.3.1. Relación binaria

Una relación es **binaria** o de grado 2 cuando participan dos entidades.

<div style="text-align: center;">
  <img src="img/relacion1.png" alt="Relación binaria" width="500">
</div>

Las relaciones también pueden tener atributos. Por ejemplo, la relación `MATRÍCULA` podría tener los atributos `FechaMatricula` y `NotaFinal`.

#### 2.3.2. Relación unaria o reflexiva

Una relación es **unaria**, reflexiva o de grado 1 cuando relaciona ocurrencias de una misma entidad.

Por ejemplo, una persona puede supervisar a otras personas, o un empleado puede depender jerárquicamente de otro empleado.

<div style="text-align: center;">
  <img src="img/relacion2.png" alt="Relación unaria o reflexiva" width="500">
</div>

#### 2.3.3. Relación ternaria

Una relación es **ternaria** o de grado 3 cuando participan tres entidades.

Por ejemplo, un profesor puede impartir una asignatura a un grupo concreto:

- `PROFESOR`;
- `ASIGNATURA`;
- `GRUPO`.

Una relación ternaria puede transformarse en varias relaciones binarias en algunos casos, pero no siempre. Una transformación incorrecta puede perder información sobre la asociación simultánea de las tres entidades.

<div style="text-align: center;">
  <img src="img/relacion3.png" alt="Relación ternaria" width="500">
</div>

Antes de continuar con los siguientes conceptos, se realizarán algunos ejercicios básicos para practicar lo aprendido.

#### Problemas

- Cuaderno de problemas de Diagramas E-R: Problema 1, actividades 1, 2 y 3.

### 2.4. Cardinalidad

La **cardinalidad** indica cuántas ocurrencias de una entidad pueden estar relacionadas con una ocurrencia de otra entidad.

Se expresa mediante un valor mínimo y un valor máximo:

- el primer número indica la participación mínima;
- el segundo número indica la participación máxima.

Los valores habituales son:

- mínimo: `0` o `1`;
- máximo: `1` o `N`.

La notación se expresa mediante una pareja de números:

```text
(mínimo, máximo)
```

Por ejemplo:

- `(0,1)`: participación opcional y como máximo una ocurrencia;
- `(1,1)`: participación obligatoria y exactamente una ocurrencia;
- `(0,N)`: participación opcional y varias ocurrencias como máximo;
- `(1,N)`: participación obligatoria y varias ocurrencias como máximo.

<div style="text-align: center;">
  <img src="img/cardinalidad1.png" alt="Ejemplo de cardinalidad" width="500">
</div>

Para interpretar correctamente una cardinalidad hay que indicar desde qué entidad se está leyendo.

En una relación entre `ALUMNO` y `MÓDULO`:

- la cardinalidad situada junto a `ALUMNO` indica con cuántos módulos puede relacionarse un alumno;
- la cardinalidad situada junto a `MÓDULO` indica con cuántos alumnos puede relacionarse un módulo.

#### Preguntas para obtener mínimos y máximos

Pensando en la imagen anterior:

- ¿Cada alumno, como mínimo, cuántas materias puede cursar?

  **1**, ya que si no cursa ninguna materia no estaría matriculado.

- ¿Cada alumno, como máximo, cuántas materias puede cursar?

  **N**, ya que puede cursar más de una.

- ¿Cada materia puede ser cursada, como mínimo, por cuántos alumnos?

  **0**, ya que podría existir una materia sin alumnos matriculados.

- ¿Cada materia puede ser cursada, como máximo, por cuántos alumnos?

  **N**, ya que puede haber varios alumnos matriculados.

### 2.5. Tipo de correspondencia

El tipo de correspondencia resume el número máximo de ocurrencias que pueden relacionarse entre dos entidades.

#### Relación uno a uno `1:1`

Cada ocurrencia de una entidad se relaciona como máximo con una ocurrencia de la otra entidad, y viceversa.

Ejemplo:

- una persona puede estar casada con otra persona;
- una persona puede tener como máximo una pareja en el modelo simplificado.

#### Relación uno a muchos `1:N`

Una ocurrencia de la primera entidad puede relacionarse con muchas ocurrencias de la segunda entidad, mientras que cada ocurrencia de la segunda se relaciona como máximo con una de la primera.

Ejemplo:

- un municipio pertenece a una provincia;
- una provincia puede tener muchos municipios.

#### Relación muchos a muchos `N:M`

Una ocurrencia de cada entidad puede relacionarse con muchas ocurrencias de la otra entidad.

Ejemplo:

- un cliente puede comprar varios productos;
- un producto puede ser comprado por varios clientes.

**Nota:** el tipo de correspondencia resume la cardinalidad máxima, mientras que la pareja `(mínimo, máximo)` proporciona además información sobre si la participación es obligatoria u opcional.

#### Representación de la cardinalidad y del tipo de correspondencia

Relación unaria:

<div style="text-align: center;">
  <img src="img/correspondencia1.png" alt="Correspondencia en una relación unaria" width="500">
</div>

Relación binaria:

<div style="text-align: center;">
  <img src="img/correspondencia2.png" alt="Correspondencia en una relación binaria" width="500">
</div>

#### Problemas

- Cuaderno de problemas de Diagramas E-R: Problema 1, actividades 4 y 5.

### 2.6. Entidades débiles

Una **entidad débil** es una entidad cuya existencia o identificación depende de otra entidad, denominada **entidad fuerte**.

Los atributos propios de una entidad débil no son suficientes para identificar completamente sus ocurrencias. Por ello, su identificación suele construirse combinando:

- la clave de la entidad fuerte;
- una clave parcial o discriminante de la entidad débil.

Ejemplo:

- **Entidad fuerte:** `FACTURA`, identificada mediante `IDFactura`.
- **Entidad débil:** `DETALLE_FACTURA`, identificada mediante `IDFactura` y `NumLinea`.

Una factura puede tener varias líneas, pero cada línea pertenece a una única factura. Por ello, la relación entre `FACTURA` y `DETALLE_FACTURA` suele ser de tipo `1:N`.

Las entidades débiles se representan mediante un rectángulo doble:

<div style="text-align: center;">
  <img src="img/debil1.png" alt="Entidad débil" width="500">
</div>

#### Tipos de dependencia

##### Dependencia en existencia

Existe dependencia en existencia cuando las ocurrencias de una entidad débil no tienen sentido sin una ocurrencia de la entidad fuerte.

Por ejemplo, una línea de factura no puede existir si no existe la factura a la que pertenece.

<div style="text-align: center;">
  <img src="img/debil2.png" alt="Dependencia en existencia" width="500">
</div>

##### Dependencia en identificación

Existe dependencia en identificación cuando, además de depender de la entidad fuerte para existir, la entidad débil necesita la clave de la entidad fuerte para poder identificarse.

Por ejemplo, una línea de pedido puede identificarse mediante:

```text
(numPedido, numLinea)
```

En este caso:

- `numPedido` procede de la entidad fuerte `PEDIDO`;
- `numLinea` es la clave parcial de la entidad débil `LINEA_PEDIDO`.

<div style="text-align: center;">
  <img src="img/debil3.png" alt="Dependencia en identificación" width="500">
</div>

#### 📝 Problemas

> - Cuaderno de problemas de Diagramas E-R: Problema 2
> - Cuaderno de problemas de Diagramas E-R: Problema 3


## 3. EL MODELO ER AMPLIADO

El **Modelo E-R Ampliado** recoge todos los conceptos y especificaciones del modelo E/R y añade otros para mejorar el diseño de las BD. Se definen los siguientes conceptos dentro de este modelo:

- **Superclase**: Es una entidad genérica de la que derivan otras entidades. La superclase tiene unos atributos que van a tener también las entidades que derivan de ella.  

- **Subclase**: Es una entidad que deriva de una entidad genérica o superclase. La subclase va a tener los atributos de la superclase más unos atributos específicos. Los elementos que hay en la subclase también estarán en la superclase, aunque esta contendrá normalmente muchos más elementos.  

  Por ejemplo, 'EMPLEADO' sería una superclase y 'OPERARIO' y 'ENCARGADO' serían subclases de ésta. Otro ejemplo, en un centro de estudios, 'PERSONA' podría ser una superclase mientras 'ALUMNO' y 'PROFESOR' serían subclases.

- **Generalización**: es el proceso de construir una superclase a partir de las características comunes o que comparten varias subclases del sistema de información.  

  Una generalización se representa mediante un *triángulo invertido* que une la superclase y las subclases.  

    <div style="text-align: center;">
      <img src="img/ampliado1.png" alt="Generalización" width="300" style="max-width: 100%; height: auto;">
    </div>

- **Especialización**: es el proceso inverso a la generalización. En la especialización se trata de buscar los **atributos específicos de las subclases** y las **restricciones de existencia** de elementos de las entidades.  

Conforme a las restricciones de existencia de elementos de las entidades, nos podemos encontrar con los siguientes **tipos de especialización o generalización**:

a) **Especialización exclusiva total**: Por ser exclusiva, un elemento de la superclase sólo puede estar en una subclase. Por ser total, todos los elementos de la superclase están en alguna de las subclases.  

<div style="text-align: center;">
    <img src="img/ampliado2.png" alt="Especialización exclusiva total" width="600" style="max-width: 100%; height: auto;">
</div>

b) **Especialización exclusiva parcial**: Por ser exclusiva, un elemento de la superclase sólo puede estar en una subclase. Por ser parcial, no tienen por qué estar todos los elementos de la superclase en alguna de las subclases.  

<div style="text-align: center;">
    <img src="img/ampliado3.png" alt="Especialización exclusiva parcial" width="600" style="max-width: 100%; height: auto;">
</div>

c) **Especialización solapada total**: Por ser solapada, un elemento de la superclase podría pertenecer a varias subclases. Por ser total, todos los elementos de la superclase están en alguna de las subclases.  

<div style="text-align: center;">
    <img src="img/ampliado4.png" alt="Especialización solapada total" width="600" style="max-width: 100%; height: auto;">
</div>

d) **Especialización solapada parcial**: Por ser solapada, un elemento de la superclase podría pertenecer a varias subclases. Por ser parcial, no tienen por qué estar todos los elementos de la superclase en alguna de las subclases.  

<div style="text-align: center;">
    <img src="img/ampliado5.png" alt="Especialización solapada parcial" width="600" style="max-width: 100%; height: auto;">
</div>  

#### 📝 Problemas

> - Cuaderno de problemas de Diagramas E-R: Problema 4
> - Cuaderno de problemas de Diagramas E-R: Problema 5
> - Cuaderno de problemas de Diagramas E-R: Problema 6


## 4. MODELO RELACIONAL

El **modelo relacional** organiza la información en tablas con filas y columnas, lo que facilita su comprensión y manejo. Permite relacionar datos de diferentes tablas, evitar duplicidades y mantener la integridad y consistencia de la información. Además, el uso de SQL hace que las consultas, actualizaciones y análisis sean rápidos y eficientes, adaptándose a entornos desde pequeños sistemas hasta grandes empresas.

### 4.1. ELEMENTOS DE UNA RELACIÓN

El elemento principal del modelo relacional es la **RELACIÓN**. Una relación es una **tabla**. Cada elemento de la relación es una **fila**, denominada **tupla o registro**. Cada propiedad, atributo o característica de los elementos es una **columna**.  

> ⚠️ **NOTA IMPORTANTE**  
> No debes confundir el concepto de **relación en el modelo relacional** con el concepto de **relación en el modelo E/R**.

---

#### Relación en el modelo Entidad-Relación (ER)
- **Concepto lógico** que representa una **asociación entre entidades**.  
- Ejemplo: “Un cliente realiza un pedido” → relación entre *Cliente* y *Pedido*.

#### Relación en el modelo relacional
- **Estructura física o lógica** implementada como **tabla** en la BD.  
- Contiene **tuplas (filas)** y **atributos (columnas)** que representan los datos de la asociación.

---

Al conjunto de valores que puede tomar una columna se le denomina **dominio**, y estos pueden ser de dos tipos:  

- **General**: si los valores pueden ser todos los existentes dentro del tipo de dato correspondiente a la columna.  
- **Restringido**: si sólo puede tomar valores dentro de un rango de un dominio general, por ejemplo, números reales comprendidos entre 0 y 10.  

### 4.2. RESTRICCIONES DEL MODELO RELACIONAL

Los datos que almacenan las BD tienen como objetivo fundamental representar situaciones del mundo real. En ocasiones esto no es así.  

Supongamos, por ejemplo, el caso de una relación **empleados** en la que su sueldo es negativo (-1000 euros). Esto hace necesaria la creación de **restricciones** que nos permitan representar de manera coherente dicha información.  

Existen **dos tipos de restricciones**:  

- **Propias o inherentes al modelo relacional**: son condiciones más generales, propias de un modelo de datos, y se deben cumplir en toda BD que siga dicho modelo.  
    - No puede haber dos tuplas o filas que tengan el mismo contenido en todas sus columnas.  
    - Ninguna columna que sea clave primaria (restricción de usuario) admite nulos.  
    - Ninguna columna que sea clave primaria admite valores repetidos en las tuplas.  
    - Ninguna columna que sea clave alternativa admite valores repetidos en las tuplas.  

- **Propias del usuario**: son condiciones específicas de una BD concreta, es decir, son las que se deben cumplir en una BD particular con unos usuarios concretos, pero que no son necesariamente relevantes en otra BD. Por ejemplo, tener empleados con sueldo negativo. En otra BD, puede que no haya sueldo, o que sea siempre positivo.  
  El modelo permite que el usuario establezca:  
    - **Clave primaria** (Primary Key)  
    - **Unicidad o clave alternativa** (UNIQUE)  
    - **Obligatoriedad** (NOT NULL)  
    - **Clave ajena** (FOREIGN KEY)  
    - **Verificación o chequeo** (CHECK)  
    - **Aserciones o asertos** (ASSERTION)  
    - **Disparadores** (TRIGGER)  

### 4.4. INTEGRIDAD REFERENCIAL

Las **restricciones de integridad referencial** permiten que el SGBD controle incoherencias entre los datos cargados en la clave ajena y los datos existentes en la clave primaria de la tabla principal. 

Vamos a ver como actua la restricción de integridad referencial con un ejemplo entre dos tablas. El esquema está formado por dos tablas, una de paises y otra de ciudades. Una ciudad pertenece a un país, y cada país puede tener varias ciudades.

Las restricciones actúan cuando:  

- Se **inserta una nueva fila** en la tabla secundaria 

Al insertar una nueva **CITY**, se comprobaría que el **CountryCode** de la nueva ciudad esté cargado en **Code** de algún **COUNTRY**. Si no lo está, se rechaza la inserción.  

- Se **modifica el valor de la clave ajena** en la tabla secundaria  

Al modificar el contenido de una **CITY**, se comprueba que el nuevo valor cargado en la clave ajena **CountryCode** exista en la clave primaria **Code** de la tabla principal **COUNTRY**. Si no existe, se rechaza la modificación y queda la fila con el valor anterior.  

- Se **borra una fila en la tabla principal**. En este caso, podemos definir diferentes restricciones de integridad referencial.  

  - **Borrado en cascada (BC)**: Si se elimina un país, se eliminan todas las ciudades del país.  
  - **Borrado restringido (BR)**: Si se trata de eliminar un país y hay ciudades de ese país en la tabla CITY, no se permite la eliminación.  
  - **Borrado con puesta a nulos (BN)**: Si se trata de eliminar un país y hay ciudades de ese país en la tabla CITY, se elimina el país y en la columna clave ajena (**countrycode**) de CITY de todas las ciudades de ese país, se carga NULL.  
  - **Borrado con puesta a valor por defecto (BD)**: Si se trata de eliminar un país y hay ciudades de ese país en la tabla CITY, se elimina el país y en la columna clave ajena (**countrycode**) de CITY de todas las ciudades de ese país, se carga un valor por defecto.  

- Se **modifica la clave primaria en la tabla principal**. Al igual que en el caso anterior, también se pueden definir diferentes restricciones de integridad referencial.  

  - **Modificación en cascada (MC)**: Si se modifica el código de un país, se modifica **countrycode** de todas las ciudades del país.  
  - **Modificación restringida (MR)**: Si se trata de modificar el código de un país y hay ciudades de ese país en la tabla CITY, no se permite la modificación.  
  - **Modificación con puesta a nulos (MN)**: Si se trata de modificar el código de un país y hay ciudades de ese país en la tabla CITY, se carga NULL en la columna clave ajena (**countrycode**) de CITY de todas las ciudades de ese país.  
 

### 4.5. REPRESENTACIÓN DEL MODELO RELACIONAL

Existen diversas formas de representar el modelo relacional. Veamos ejemplos de algunas de ellas:

- **Esquema relacional conectado a columnas**: 
<div style="text-align: center;">
    <img src="img/esquema1.png" alt="Esquema relacional columnas" width="500" style="max-width: 100%; height: auto;">
</div> 

- **Esquema relacional crow's foot o pata de cuervo**: La parte de la pata va en la tabla donde está la clave ajena.  
<div style="text-align: center;">
    <img src="img/esquema2.png" alt="Esquema crow's foot" width="500" style="max-width: 100%; height: auto;">
</div>

- **Grafo relacional**  
<div style="text-align: center;">
    <img src="img/esquema3.png" alt="Grafo relacional" width="500" style="max-width: 100%; height: auto;">
</div>

#### 📝 Problemas

> - Cuaderno de problemas de Diagramas E-R: Problema 7
> - Cuaderno de problemas de Diagramas E-R: Problema 8
> - Cuaderno de problemas de Diagramas E-R: Problema 9
> - Cuaderno de problemas de Diagramas E-R: Problema 10

## 6. NORMALIZACIÓN

Al diseñar una BD se ha de evaluar la calidad del diseño. Para ello, uno de los parámetros que se utiliza son las **formas normales** en las que se encuentra dicho diseño.  
Se llama **normalización** al proceso de obligar a los atributos incluidos en el diseño a cumplir varias formas normales.

Las formas normales son reglas que aseguran que el esquema tenga buen comportamiento respecto a:

- Redundancia de información  
- Pérdida de información  
- Presentación de la información  

**Ejemplo:** tabla Suministros

| CodProv | CodArticulo | Cantidad | CiudadProv |
|---------|------------|---------|------------|
| P1      | C1         | 12      | Cantabria  |
| P1      | C2         | 25      | Cantabria  |
| P1      | C3         | 11      | Cantabria  |
| P2      | C1         | 52      | Valencia   |
| P2      | C2         | 35      | Valencia   |
| P3      | C5         | 22      | Valladolid |

Esta tabla presenta redundancia y posibles anomalías:

1. **Anomalías de modificación:** si un proveedor cambia de ciudad, hay que modificar todas las tuplas que lo contengan.  

2. **Anomalías de borrado:** si un proveedor deja de suministrar artículos, se pierden sus datos.  

3. **Anomalías de inserción:** si queremos añadir un proveedor sin artículos, tendríamos que poner NULL en columnas de clave primaria, rompiendo la integridad referencial.

El origen de estas anomalías: la tabla Suministros describe dos hechos diferentes: los artículos que suministra cada proveedor y el proveedor en sí, que son independientes, aunque se relacionen indirectamente.

Si la BD se diseña usando un modelo semántico (E/R), la normalización suele ser menos necesaria.  

En BD relacionales, las **formas normales (FN)** indican el grado de vulnerabilidad de una tabla a inconsistencias y anomalías. Cada FN incluye a las anteriores.

<img src="img/formas1.png" alt="Formas normales" width="400px"/>  

**Definiciones previas:**

- Dependencia funcional: A → B. Para cada valor de A hay un único valor de B.  
- Dependencia funcional completa: B depende de toda la clave A.  
- Dependencia transitiva: A → B → C. C depende transitivamente de A.  
- Determinante funcional: atributo del que depende otro.  
- Dependencia multivaluada: A →→ B. Un valor de A implica varios valores de B.

### 6.1. 1FN (PRIMERA FORMA NORMAL)

Una relación está en 1FN si cada atributo es atómico, es decir, cada celda contiene un solo valor.  

**Ejemplo:** tabla de pedidos de clientes

<img src="img/formas2.png" alt="Ejemplo pedidos 1FN" width="400px"/>  

Se observa que la tabla no está en 1FN, ya que hay campos repetidos: Num_art, Nom_art, Cant y Precio.  

Solución: crear una nueva tabla con estos campos y su clave primaria, dejando la tabla original con la clave primaria de la orden:

<img src="img/formas3.png" alt="Tabla normalizada 1FN" width="400px"/>  

### 6.2. 2FN (SEGUNDA FORMA NORMAL)

Una relación está en 2FN si está en 1FN y todos los atributos no clave dependen funcionalmente de la **clave completa**.  

Ejemplo: seguimos con la tabla en 1FN:

- Identificar columnas que dependen solo de parte de la clave primaria.  
- Crear una nueva tabla con estas columnas, usando como clave primaria la de la que dependen.  

Si la clave primaria solo tiene un campo, la tabla ya está en 2FN.  

En nuestro ejemplo:  

- Tabla **Ordenes** → clave principal Id_orden (ya está en 2FN).  
- Tabla **Articulos_Ordenes** → Nom_art y Precio dependen solo de Num_art → se crean tabla **Articulos** con estas columnas + Num_art como clave primaria.

Resultado final:

<img src="img/formas4.png" alt="Tablas 2FN 1" width="400px"/>  
<img src="img/formas5.png" alt="Tablas 2FN 2" width="400px"/>  

Tablas en 2FN:

- Ordenes (clave principal Id_orden)  
- Articulos_Ordenes (clave principal Id_orden, Num_art)  
- Articulos (clave principal Num_art)  


### 6.3. 3FN (TERCERA FORMA NORMAL)

Una relación está en 3FN si y solo si está en 2FN y no existen **dependencias transitivas**.  
Todas las dependencias funcionales deben ser respecto a la clave principal.  

Es decir, debemos identificar atributos que dependen de otros atributos que **no** son clave principal.  

**Ejemplo:** seguimos con las tres tablas obtenidas en 2FN. Los pasos son:

- Determinar columnas dependientes de atributos que no son clave.  
- Eliminar esas columnas de la tabla base.  
- Crear una nueva tabla con esas columnas y la columna no clave de la cual dependen.

En nuestro ejemplo:  

- Tabla **Articulos** → ya está en 3FN.  
- Tabla **Articulos_Ordenes** → ya está en 3FN.  
- Tabla **Ordenes** → **no está** en 3FN, porque `nom_cliente` y `estado` dependen de `Id_cliente`, que no es clave primaria.

<img src="img/formas6.png" alt="Normalización a 3FN" width="400px"/>  

Para normalizar: mover columnas no clave y la columna dependiente a otra tabla llamada **Clientes**. Resultado:

<img src="img/formas7.png" alt="Tablas Clientes y Ordenes" width="400px"/>  

El resultado final es:

<img src="img/formas8.png" alt="Resultado final 3FN" width="400px"/>  
<img src="img/formas11.png" alt="Tablas finales normalizadas" width="400px"/>  

> Nota: en clase trabajaremos hasta la 3FN.  
Si quieres profundizar en 4FN y 5FN, puedes consultar el siguiente enlace:  

#### HOJAS DE EJERCICIOS

💻 Hoja de ejercicios 15.  
💻 Hoja de ejercicios 16.  
💻 Hoja de ejercicios 17.  
💻 Hoja de ejercicios 18.  
💻 Hoja de ejercicios 19. REPASO DE TODO EL TEMA.
