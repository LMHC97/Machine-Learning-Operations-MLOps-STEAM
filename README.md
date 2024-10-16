# Proyecto individual de Machine Learning.
### Liz Mariana Henao Cardona
En este proyecto se construyó un producto mínimo viable (MVP) a partir de una base de datos de una compañía de videojuegos. Se llevó a cabo un proceso inicial de limpieza y preparación de datos (ETL), seguido de un análisis exploratorio (EDA) para identificar patrones y características relevantes. Los datos resultantes fueron optimizados para su uso en la plataforma en la nube Render, lo que permitió desplegar una aplicación de manera rápida y eficiente. Además, se desarrolló un sistema de recomendación que utiliza el algoritmo de similitud de coseno para sugerir productos o contenidos a los usuarios en función de sus preferencias y el comportamiento de otros usuarios similares.
## Objetivo
Desarrollar una API básica (MVP) que exponga puntos de acceso específicos para realizar consultas a una base de datos y ofrecer recomendaciones personalizadas utilizando un algoritmo de similitud de coseno.
## Fuentes de datos
#### Australian_users_reviews.json
Este archivo contiene las opiniones de los usuarios australianos sobre nuestros juegos, incluyendo si lo recomendarían o no.
![image](https://github.com/user-attachments/assets/77de9efa-5d1c-4e50-a44c-68a8d26388d3)
### australian_users_items.json
Este archivo contiene la información de todos los jugadores australianos, incluyendo los juegos que han comprado y el tiempo que han jugado.
![image](https://github.com/user-attachments/assets/ec2301a2-2b5c-409a-843c-8f68bb45ece6)
### output_steam_games.json
Este archivo contiene la información detallada de los juegos de Steam, como género y etiquetas.
![image](https://github.com/user-attachments/assets/808b9221-5084-495a-9372-ca28fbd25316)
## Proceso de extracción, transformación y carga de archivos (ETL)
La limpieza y transformación de los datos (ETL) se llevó a cabo en tres cuadernos de Jupyter independientes, donde se eliminaron duplicados, filas vacías y se trataron los valores nulos.
Se pueden encontrar en el repositorio, comienzan por las siglas ETL. Cada archivo se encuentra debidamente comentado. Se exportaron los datos a parquet.
## Análisis exploratorio de datos
Luego de limpiar los datos, se realizó un análisis exploratorio detallado para comprender mejor las características de los juegos y los patrones de consumo de los jugadores. A través de visualizaciones, se identificaron los géneros más populares, los juegos con precios más elevados y las palabras clave más frecuentes en los títulos. Estos hallazgos proporcionarán una base sólida para el desarrollo de un modelo de predicción más preciso y robusto.
![image](https://github.com/user-attachments/assets/556cad84-a868-4c71-a223-2d9751d5e465)
![image](https://github.com/user-attachments/assets/532918e2-f0c8-4e30-9f06-39cfe54b2404)
![image](https://github.com/user-attachments/assets/a71ed777-0a39-4b9e-a2f5-e7eb017f4f2e)
![image](https://github.com/user-attachments/assets/12827701-f47c-44cf-904e-a2cb1f68d1f2)
## Análisis de sentimiento
Se llevó a cabo un análisis de sentimiento en las reseñas de los usuarios, clasificándolas como positivas (2), neutrales (1) o negativas (0). Cada juego cuenta con múltiples reseñas que pueden pertenecer a cualquiera de estas categorías. La nube de palabras muestra los términos más comunes en las reseñas positivas.
![image](https://github.com/user-attachments/assets/66d49de3-453f-4e78-8f41-8ee946d60da6)
## Sistema de recomendación
Se seleccionó un sistema de recomendación basado en ítems, utilizando la distancia del coseno como métrica de similitud. Cada ítem fue representado por un conjunto de características específicas. El modelo de similitud del coseno es una técnica que permite encontrar usuarios con preferencias similares. Cada usuario se representa como un punto en un espacio multidimensional, donde cada dimensión corresponde a una característica del usuario. La similitud entre dos usuarios se calcula midiendo la cercanía entre estos puntos en el espacio
## Despliegue de la API
La API fue construida con FastAPI y desplegada en Render para su acceso online.
Los endpoints de la API son los siguientes:
### Endpoint 1: /developer/{desarrollador}
Retorna la cantidad de ítems y el porcentaje de contenido gratuito para cada año del desarrollador ingresado.
### Endpoint 2: /userdata/{user_id}
Para el usuario ingresado, retorna el dinero gastado, el porcentaje de recomendación y la cantidad de ítems comprados.
### Endpoint 3: /UserForGenre/{genero}
Para el género ingresado, retorna el usuario con más horas jugadas y el detalle de cuántas horas por año.
### Endpoint 4: /best_developer_year/{anio}
Para el año ingresado, retorna los 3 desarrolladores con más comentarios positivos.
### Endpoint 5: /developer_reviews_analysis/{desarrolladora}
Para el desarrollador ingresado, retorna la cantidad de comentarios positivos y negativos totales.
### Endpoint 6: /recomendacion_juego/{id_producto}
Para el ID de producto ingresado, recomienda 5 juegos relacionados.

Se detectaron problemas con los endpoints 3 y 6. El endpoint 3 no pudo ser desplegado en Render debido al gran tamaño del archivo asociado, lo cual impidió subirlo a GitHub. El endpoint 6, por su parte, presentó errores durante su desarrollo y no funciona como se esperaba.

En el siguiente video se puede observar el funcionamiento de la API.



