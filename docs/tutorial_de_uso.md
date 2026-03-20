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
- [Función obtener](#obtener)
- [Funcion modificar_datos](#modificar_datos)

**Ecuaciónes cúbicas de estado**

## obtener
## modificar_datos
## van_der_waals
## redlich_kwong
## soave
## peng_robinson
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


