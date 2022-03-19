# Lemoncode: Master Front End (Edición XI)
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

## Paso 2: Despliegue manual en GithubPages.

Por defecto GitHub Pages despliega el contenido estático de la rama 'gh-pages'. Para hacer la pubicación manual seguimos los siguientes pasos:
a) Creamos una rama local "gh-pages".
b) Limpiamos el contenido, dejando únicamente el contenido de la carpeta `dist`creada en el paso anterior.
c) Publicamos esta rama
  * Al publicar la rama se lanza un proceso de publicación que realiza el despliegue de esta rama en GithubPages.

Resultado: [GithubPages - Modulo VII.Ejercicio 1] (https://aghlearning.github.io/LCXI_MVII_LAB_CLOUD_Front/)

___

## Paso 3: Despliegue en GithubPages mediante Github Actions.

a) Para automatizar la publicación de la página utilizaremos la libreria `gh-pages`que en tiempo de desarrollo realizará la publicación a la rama `gh-pages`

```
npm install gh-pages --save-dev
```

b) Creamos en `package.json`el script para realizar el deploy:
```
"deploy": "gh-pages -d dist"
```

Al ejecutar el deploy, se realiza la publicación de la rama gh-pages en Github.

c) Automatizamos el proceso con Github Actions:

* Creamos fichero yml en la carpeta `.github\workflows`:
* Creamos clave ssh para conexión entre github y el servidor de despliegue:
  - Creamos nuevo par de claves:
  ```
  ssh-keygen -m PEM -t rsa -C "gh-pages@agh.local"
  ```
  - Añadimos la clave publica
* Publicamos la rama `main`




