# Tutorial de uso - Excel Fundamental 2.0
## Consideraciones
### Acerca de la base de datos
Las funciones de Excel fundamental requieren de propiedades termodinámicas. Estas se obtienen del Apéndice A del libro Properties of Gases and Liquids (5ta edición) (Poling, Prausnitz y O’Connell, 2001). Este apéndice recibe el nombre de *Data Bank*.

### Unidades
Excel Fundamental trabaja con unidades (Kelvin, bar, mol, Joule) para temperatura, presión absoluta, materia y energía respectivamente.

### ¿Cómo referenciar un compuesto químico?
Al momento de llamar una función de Excel Fundamental resulta necesario especificar que compuestos químicos están involucrados. Esto se puede hacer de 4 formas diferentes; ID, CAS, nombre IUPAC, nombre común.

|**Tipo de referencia**|**Explicación**|**Ejemplo**|
|:----------------:|:---------:|:-----:|
|**ID**|Número identificador que tiene asignado en el Data Bank|60
|**CAS**|Número único universal asignado por el Chemical Abstracts Service|64-19-7|
|**Nombre IUPAC**|Nombre del compuesto que sigue las reglas de IUPAC. (Ingles)|Ethanoic Acid|
|**Nombre común**|Nombre coloquial del compuesto. (Ingles)|Acetic Acid|

### ¿Cómo referenciar una propiedad termodinámica?
Referenciar una propiedad termodinámica solo resulta útil cuando se quiere buscar o modificar datos de la base de datos.
Se puede referenciar una propiedad termodinámica de dos formas: ID o nombre.

|**Tipo de referencia**|**Explicación**|**Ejemplo**|
|:--------------------:|:-------------:|:---------:|
|**Nombre**|Nombre de la propiedad termodinámica (existen muchos nombres para una sola propiedad)|Temperatura critica, Tc, Critical Temperature|
|**ID**|Posición de la propiedad en la base de datos|6|

## Documentación de funciones
En esta sección se muestra como usar todas las funciones disponibles en Excel Fundamental.

**Contenido**

**Funciones que acceden a la base de datos**
- [obtener](#obtener)
- [modificar_datos](#modificar_datos)

**Ecuaciónes cúbicas de estado**
- [van_der_waals](#van_der_waals)
- [redlich_kwong](#redlich_kwong)
- [soave](#soave)
- [peng_robinson](#peng_robinson)

**Propiedades termodinámicas**
- [antoine](#antoine)
- [cp](#cp)
- [integral_cp](#integral_cp)
- [integral_cp_entre_t](#integral_cp_entre_t)

**Fugacidad**
- [coef_fugacidad_mezcla_peng_robinson](#coef_fugacidad_mezcla_peng_robinson)
- [coef_fugacidad_mezcla_soave](#coef_fugacidad_mezcla_soave)
- [coef_fugacidad_puro_peng_robinson](#coef_fugacidad_puro_peng_robinson)
- [coef_fugacidad_puro_soave](#coef_fugacidad_puro_soave)

**Modelos de actividad**
- [unifac](#unifac)

**Correcciones y propiedades energéticas**
- [poynting](#poynting)
- [entropia_ideal](#entropia_ideal)
- [entalpia_ideal](#entalpia_ideal)
- [entalpia_ideal_vapor](#entalpia_ideal_vapor)

## obtener

> **obtener(compuestos, propiedades)**

Busca propiedades termodinámicas en la base de datos y las imprime como tabla de Excel.

### Parámetros:

* **compuestos:** Lista de celdas que contienen una referencia a un compuesto químico.
* **propiedades:** Lista de celdas que contienen una referencia a una propiedad termodinámica.

### Devuelve:

* **tabla de propiedades:** Tabla que contiene las propiedades seleccionadas de los compuestos seleccionados.


### Ejemplo:

| Entrada | Salida |
| :--- | :--- |
| ![Imagen Entrada](imagenes/obtener_in.png) | ![Imagen Salida](imagenes/obtener_out.png) |


## modificar_datos

>**modificar_datos(compuestos, propiedades, valores)**

Modifica temporalmente los valores de la base de datos.

### Parámetros

* **compuestos:** Lista de celdas que contienen una referencia a un compuesto químico.
* **propiedades:** Lista de celdas que contienen una referencia a una propiedad termodinámica.
* **valores:** Matriz de celdas que contienen los nuevos valores que se asignaran a cada compuesto para cada propiedad termodinámica.

### Devuelve

* **Texto:** La cadena "Datos Añadidos". Solo se muetra cuando se modifica la base exitosamente.

### Ejemplo

| Entrada | Salida |
| :--- | :--- |
| ![Imagen Entrada](imagenes/modificar_datos_in.png) | ![Imagen Salida](imagenes/modificar_datos_out.png) |


## van_der_waals

>**van_der_waals(compuestos, composiciones, presion, temperatura, volumen, raw)**

Calcula la variable termodinámica faltante (P, T o V) utilizando la ecuación de estado de Van der Waals para una mezcla. Si se proporcionan las tres variables, la función actúa como un validador que evalúa si la relación se cumple o calcula el error relativo entre ellas.

### Parámetros

* **compuestos:** Lista de celdas que contienen una referencia a los compuestos químicos de la mezcla.

* **composiciones:** Lista de celdas que contienen las fracciones molares de cada compuesto en la mezcla

* **presion:** (Opcional) Celda o rango de celdas con la presión absoluta en **bar**

* **temperatura:** (Opcional) Celda o rango de celdas con la temperatura en **Kelvin**

* **volumen:** (Opcional) Celda o rango de celdas con el volumen molar en **mL/mol**

### Devuelve

* **Variable calculada:** Si se omitió una variable (P, V, T), devuelve su valor calculandolo con la ecuación de Van der Waals.

* **Validación / Error relativo:** Si se especificaron todas las variables, devuelve `True / False` dependiendo si esas varaibles satisfacen la ecuacion de estado de Van der Waals.

### Ejemplo 1 - Calculo de volumen molar

| Entrada | Salida |
| :--- | :--- |
| ![Imagen Entrada](imagenes/van_der_waals_in_v.png) | ![Imagen Salida](imagenes/van_der_waals_out_v.png) |

**Nota:** Es importante notar que cuando no se especifica el volumen al llamar la funcion, aun asi se coloca su respectiva coma.
> van_der_waals(compuestos, composiciones, presion, temperatura,   )

### Ejemplo 2 - Calculo de presión

| Entrada | Salida |
| :--- | :--- |
| ![Imagen Entrada](imagenes/van_der_waals_in_p.png) | ![Imagen Salida](imagenes/van_der_waals_out_p.png) |

### Ejemplo 3 - Calculo de temperatura

| Entrada | Salida |
| :--- | :--- |
| ![Imagen Entrada](imagenes/van_der_waals_in_t.png) | ![Imagen Salida](imagenes/van_der_waals_out_t.png) |

### Ejemplo 4 - Se especifican las tres variabes P, V, T.

| Entrada | Salida |
| :--- | :--- |
| ![Imagen Entrada](imagenes/van_der_waals_in_n.png) | ![Imagen Salida](imagenes/van_der_waals_out_n.png) |

## redlich_kwong

> **redlich_kwong(compuestos, composiciones, presion, temperatura, volumen)**

Calcula la variable termodinámica faltante (P, T o V) utilizando la ecuación de estado de **Redlich-Kwong** para una mezcla. Si se proporcionan las tres variables, la función actúa como un validador que evalúa si la relación se cumple o calcula el error relativo entre ellas.

### Parámetros

* **compuestos:** Lista de celdas que contienen una referencia a los compuestos químicos de la mezcla.

* **composiciones:** Lista de celdas que contienen las fracciones molares de cada compuesto en la mezcla.

* **presion:** (Opcional) Celda o rango de celdas con la presión absoluta en **bar**.

* **temperatura:** (Opcional) Celda o rango de celdas con la temperatura en **Kelvin**.

* **volumen:** (Opcional) Celda o rango de celdas con el volumen molar en **mL/mol**.

### Devuelve

* **Variable calculada:** Si se omitió una variable (P, V, T), devuelve su valor calculándolo con la ecuación de Redlich-Kwong.

* **Validación / Error relativo:** Si se especificaron todas las variables, devuelve `True / False` dependiendo de si esas variables satisfacen la ecuación de estado.

### Ejemplo 1 - Cálculo de volumen molar

| Entrada | Salida |
| :--- | :--- |
| ![Imagen Entrada](imagenes/redlich_kwong_in_v.png) | ![Imagen Salida](imagenes/redlich_kwong_out_v.png) |

**Nota:** Es importante notar que cuando no se especifica el volumen al llamar la función, aun así se coloca su respectiva coma.
> redlich_kwong(compuestos, composiciones, presion, temperatura,   )

### Ejemplo 2 - Cálculo de presión

| Entrada | Salida |
| :--- | :--- |
| ![Imagen Entrada](imagenes/redlich_kwong_in_p.png) | ![Imagen Salida](imagenes/redlich_kwong_out_p.png) |

### Ejemplo 3 - Cálculo de temperatura

| Entrada | Salida |
| :--- | :--- |
| ![Imagen Entrada](imagenes/redlich_kwong_in_t.png) | ![Imagen Salida](imagenes/redlich_kwong_out_t.png) |

### Ejemplo 4 - Se especifican las tres variables P, V, T.

| Entrada | Salida |
| :--- | :--- |
| ![Imagen Entrada](imagenes/redlich_kwong_in_n.png) | ![Imagen Salida](imagenes/redlich_kwong_out_n.png) |

## soave

> **soave(compuestos, composiciones, presion, temperatura, volumen)**

Calcula la variable termodinámica faltante (P, T o V) utilizando la ecuación de estado de **Soave-Redlich-Kwong (SRK)** para una mezcla. Si se proporcionan las tres variables, la función actúa como un validador que evalúa si la relación se cumple o calcula el error relativo entre ellas.

### Parámetros

* **compuestos:** Lista de celdas que contienen una referencia a los compuestos químicos de la mezcla.

* **composiciones:** Lista de celdas que contienen las fracciones molares de cada compuesto en la mezcla.

* **presion:** (Opcional) Celda o rango de celdas con la presión absoluta en **bar**.

* **temperatura:** (Opcional) Celda o rango de celdas con la temperatura en **Kelvin**.

* **volumen:** (Opcional) Celda o rango de celdas con el volumen molar en **mL/mol**.

### Devuelve

* **Variable calculada:** Si se omitió una variable (P, V, T), devuelve su valor calculándolo con la ecuación de Soave.

* **Validación / Error relativo:** Si se especificaron todas las variables, devuelve el error relativo (como valor numérico) al verificar la consistencia de los datos ingresados.

### Ejemplo 1 - Cálculo de volumen molar

| Entrada | Salida |
| :--- | :--- |
| ![Imagen Entrada](imagenes/soave_in_v.png) | ![Imagen Salida](imagenes/soave_out_v.png) |

**Nota:** Es importante notar que cuando no se especifica el volumen al llamar la función, aun así se coloca su respectiva coma.
> soave(compuestos, composiciones, presion, temperatura,   )

### Ejemplo 2 - Cálculo de presión

| Entrada | Salida |
| :--- | :--- |
| ![Imagen Entrada](imagenes/soave_in_p.png) | ![Imagen Salida](imagenes/soave_out_p.png) |

### Ejemplo 3 - Cálculo de temperatura

| Entrada | Salida |
| :--- | :--- |
| ![Imagen Entrada](imagenes/soave_in_t.png) | ![Imagen Salida](imagenes/soave_out_t.png) |

### Ejemplo 4 - Se especifican las tres variables P, V, T.

| Entrada | Salida |
| :--- | :--- |
| ![Imagen Entrada](imagenes/soave_in_n.png) | ![Imagen Salida](imagenes/soave_out_n.png) |

## peng_robinson

> **peng_robinson(compuestos, composiciones, presion, temperatura, volumen)**

Calcula la variable termodinámica faltante (P, T o V) utilizando la ecuación de estado de **Peng-Robinson** para una mezcla. Si se proporcionan las tres variables, la función actúa como un validador que evalúa si la relación se cumple o calcula el error relativo entre ellas.

### Parámetros

* **compuestos:** Lista de celdas que contienen una referencia a los compuestos químicos de la mezcla.

* **composiciones:** Lista de celdas que contienen las fracciones molares de cada compuesto en la mezcla.

* **presion:** (Opcional) Celda o rango de celdas con la presión absoluta en **bar**.

* **temperatura:** (Opcional) Celda o rango de celdas con la temperatura en **Kelvin**.

* **volumen:** (Opcional) Celda o rango de celdas con el volumen molar en **mL/mol**.

### Devuelve

* **Variable calculada:** Si se omitió una variable (P, V, T), devuelve su valor calculándolo con la ecuación de Peng-Robinson.

* **Validación / Error relativo:** Si se especificaron todas las variables, devuelve el error relativo (como valor numérico) al verificar la consistencia de los datos ingresados.

### Ejemplo 1 - Cálculo de volumen molar

| Entrada | Salida |
| :--- | :--- |
| ![Imagen Entrada](imagenes/peng_robinson_in_v.png) | ![Imagen Salida](imagenes/peng_robinson_out_v.png) |

**Nota:** Es importante notar que cuando no se especifica el volumen al llamar la función, aun así se coloca su respectiva coma.
> peng_robinson(compuestos, composiciones, presion, temperatura,   )

### Ejemplo 2 - Cálculo de presión

| Entrada | Salida |
| :--- | :--- |
| ![Imagen Entrada](imagenes/peng_robinson_in_p.png) | ![Imagen Salida](imagenes/peng_robinson_out_p.png) |

### Ejemplo 3 - Cálculo de temperatura

| Entrada | Salida |
| :--- | :--- |
| ![Imagen Entrada](imagenes/peng_robinson_in_t.png) | ![Imagen Salida](imagenes/peng_robinson_out_t.png) |

### Ejemplo 4 - Se especifican las tres variables P, V, T.

| Entrada | Salida |
| :--- | :--- |
| ![Imagen Entrada](imagenes/peng_robinson_in_n.png) | ![Imagen Salida](imagenes/peng_robinson_out_n.png) |

## antoine
## cp
## integral_cp
## coef_fugacidad_mezcla_peng_robinson
## coef_fugacidad_mezcla_soave
## coef_fugacidad_puro_peng_robinson
## coef_fugacidad_puro_soave
## unifac
## poynting
## entropia_ideal
## entalpia_ideal
## entalpia_ideal_vapor
## integral_cp_entre_t


