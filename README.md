# LCemoncode: Master Front End (Edición XI)
***Ejercicios del módulo VII: Cloud***

## Preparación del entorno:

Partimos de una solución previamente creada que consta un Frontend y un Backend.

Creamos dos repositorios diferentes, uno para cada solución:
* Front: [LCXI_MVII_LAB_CLOUD_Front](https://github.com/AghLearning/LCXI_MVII_LAB_CLOUD_Backend) ”(Repositorio Actual)”
* Back: [LCXI_MVII_LAB_CLOUD_Backend](https://github.com/AghLearning/LCXI_MVII_LAB_CLOUD_Front)

Y agregamos en ellos los proyectos previamente creados.

___

## Paso 1: Configuración de la aplicación para producción

a) Creamos una configuración de producción de Webpack: ./config/webpck/prod.js
  - Utilizamos Webpack Merge.
  - Definimos modo de producción
  - Modificamos las opciones del output.
  - Modificmos el entorno para que utilice las variables de producción.
  - Añadimos la configuración de optimizacíón. (*)


b) Creamos el fichero con variables de entorno para producción: prod.env
  - Replicamos el fichero de test y sustituimos las variables de entorno por sus valores en producción.

c) Creamos los comandos de build en el package.json:
```
    "build": "run-p -l type-check build:prod",
    "build:prod": "npm run clean && webpack --config ./config/webpack/prod.js",
```
d) Probamos la nueva configuración.

___

## Paso 2: Despliegue en GitPages.
