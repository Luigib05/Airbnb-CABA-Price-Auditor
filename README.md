PROYECTO DE CIENCIA DE DATOS: Airbnb

1- Objetivo: Detectar anomalías en el precio de hospedajes disponibles en la plataforma Airbnb basado en la información 
declarada por el anfitrión y las revisiones de los usuarios.

2- Dataset: El dataset utilizado fue extraido de Inside Airbnb (https://insideairbnb.com/get-the-data/). 
Consta de 2 archivos en formato .csv, asociados a un id del hospedaje.

Archivo 1 - listings.csv.gz (80 MB): contiene información del anuncio como, descripción de la propiedad, precio, y datos del anfitrión, entre otros.
Archivo 2 - reviews.csv.gz (260 MB): contiene revisiones y comentarios de la experiencia de los usuarios.

3- Flujo de trabajo:

3.1. Se utilizó google colab como entorno de desarrollo.

3.2. Se subieron los datos a google Drive y desde google colab se generó un shortcut a los archivos.

3.3. Data wrangling (visualización, limpieza, estructuración y enriquecimiento de los datos). 
Solo se aceptó un % máximo de pérdida de datos de 5%. Esto se logró mediante imputación y filtrado estratégico de nulos.

3.4. Se Visualizaron los archivos, se analizaron las caraceterísticas y se seleccionaron un grupo de ellas, 
como 'id', 'name' 'description', bedrooms, accommodates, bathrooms, entre otras de listings.csv y id, listing_id, 
commnets, de reviews.csv (ver apartado 3.3. y 3.4 en .ipynb).

3.5. Se identificaron precios anómalos o muy alejados de la realidad (datos mal cargados, especulación, etc.) 
los cuales fueron filtrados para precios de 15,000 a 400,000 (ver apartado 3.5.).

3.5. Se transformó la variable 'price' (target) de string a .float.

3.6. Extrayendo información de las variables de texto como 'name' y 'descriptions' y 'comments' 
se cruzó información para crear nuevas variables categóricas, como: el depto tiene o no espacio abierto privado,
score de cocina, score de quejas, etc. Se realizaron algunos gráficos representativos barchart 
(images/Top 10 Barrios con más Quejas por Depto.png) y burbujas (images/Relación Precio vs. Quejas por Barrio en BA.png). 
El análisis fue bilingue usando NLP: keyword extraction.

3.7 Se generó un dataframe maestro 'df_master()' con las caracetísticas mas importante y 
generamos una matriz de correlación para ver las características que mas afectan al precio (apartado 3.7.).

3.8. Se entrenó un modelo de Random Forest para auditar y predecir el precio correcto en base a sus caracerísticas.

Métricas:

R^2=0.49,

MAE \approx = 16,000

3.9. Se auditó el modelo para determintar la diferencia entre el valor predicho y el valor real publicado en 10 hospedajes con valores muy elevados. 
Las diferencias fueron muy grandes entre 150,000 y 300,000. Limitación del modelo o 'especulación inmobiliaria'?

3.10. Se creó una función de tasación de hospedajes para determinar el precio predicho por el modelo en base a las features importance. 
Se creó una gráfico de barra para el top 15 features importance (images/Top 15 Características que determinan el Precio en CABA.png).

3.11. Se creó un gráfico de residuos (images/Gráfico de Residuos - Error de Predicción vs Precio Predicho.png).

3.12. Conclusiones finales

3.13. Este proyecto se realizó con fines de aprendizaje.
