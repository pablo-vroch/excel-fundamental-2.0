# Tutorial de instalación

La instalación consta de tres partes:

Parte 1. Instalar Python  
Parte 2. Instalar las librerías necesarias  
Parte 3. Descargar y preparar el archivo de Excel  

## Parte 1. Instalar Python

Descarga Python desde el sitio oficial:
https://www.python.org/

Durante la instalación aparecerá la siguiente casilla:
![img1](imagenes/img1.png)

Es importante que la actives.  
Esto permite usar Python desde la terminal de Windows.

## Parte 2. Instalar librerías de Python

Excel Fundamental utiliza NumPy para cálculos numericos y Xlwings para conectarse a un libro de excel
Estas librerías deben instalarse manualmente.

### Paso 1. Abrir la terminal

- Haz clic en la pestaña **Buscar** de Windows.

![img2](imagenes/img2.png)

- Escribe `Terminal`.

![img3](imagenes/img3.png)

- Haz clic en la aplicación.

### Paso 2. Instalar NumPy

En la terminal escribe:

```bash
pip install numpy
```

Presiona Enter y espera a que termine la instalación.

### Paso 3. Instalar xlwings

Después, escribe:

```bash
pip install xlwings
```

Presiona Enter y espera a que termine.

## Parte 3 (ultima). Instalar Excel Fundamental

### Paso 1. Descargar el repositorio

Ingresa al siguiente enlace:

https://github.com/pablo-vroch/excel-fundamental

Haz clic en el botón verde **Code**.

![img4](imagenes/img4.png)

Luego selecciona **Download ZIP**.

![img5](imagenes/img5.png)

### Paso 2. Extraer los archivos

Haz clic derecho en el archivo:

`excel-fundamental-main.zip`

Selecciona **Extraer todo**.

![img6](imagenes/img6.png)

### Paso 3. Abrir la aplicación

Ingresa a la carpeta:

`excel_fundamental_app`

![img7](imagenes/img7.png)

Haz clic derecho en el archivo:

`excel_fundamental.xlsm`

Selecciona **Propiedades**.

![img8](imagenes/img8.png)

Marca la casilla **Desbloquear** y haz clic en **Aplicar**.

Ahora puedes uar excel_fundamental normalmente.
