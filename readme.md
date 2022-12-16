
Segundo Proyecto Individual de Henry, Data Science, cohorte 05. Autor: Ramon Blanc.

La propuesta:

Generar un modelo de machine learning para predecir si al ingresar un paciente a cierto centro de salud, éste tendrá o no una internacion de mas de 8 dias de duracion. La variable target, se debe definir como binaria, por lo que concluyo es un problema de clasificacion: dado un paciente, ó es '0', ó es '1'.


El EDA  y pre-procesamiento de datos se desarrolla en el archivo EDA.ipynb

La realizacion:

En primer lugar, cargué los archivos csv provistos de train y test, y realice un EDA de ambos. Sobre el archivo test, hice un analisis menos riguroso (fue esto un error?), pero sí checkié que correspondan los tipos de dato, nombres y cantidad de columnas (salvo por la columna target, la cual no esta en el dataset Test). No tuve que hacer grandes cambios en ese sentido, pude observar los datasets bastante 'limpios', sin datos faltantes.

Luego, evalue si tenia datos atipicos o 'mal escritos', pude ver esto con el metodo .unique(), para mi alegria, no observe rarezas ni datos atipicos. Ademas, observando los valores (discretos) de cada columna, consideré que no debia hacer ningun reescalado, igualmente, de ser necesario mas adelante en el proceso, tendria que realizarlo luego de convertir a datos numericos.

A la vez, fui observando algunos comportamientos o distribuciones de variables, sin sacar conclusiones certeras pero pudiendo de a poco sumergirme en los datos.

Pasé entonces a la codificacion de variables, muy pocas eran de tipo numerico originalmente. Para elegir qué tipo de codificacion utilizar, recurrí un poco al sentido comun, si existe algo como eso, intentando respaldar mis decisiones con la exploracion de los datos, algo que no me fue del todo posible en algunos casos. Lo que pude observar es que probablemente sean los distintos modelos, las distintas codificaciones, y las metricas de cada uno, lo que me terminen diciendo realmente qué era lo conventiente. Mi criterio en general fue el siguiente: si observaba cierta ordinalidad, hacer OrdinalEncoder o similar 'manualmente', dado que la clase existente OrdinalEncoder no me asignaba los valores en la forma en que yo esperaba. Si observaba features puramente nominales, opté por usar OneHotEncoder o similar, teniendo en cuenta que los valores que toma cada feature son reducidos en cantidad, por lo que no se aniaden demasiadas columnas.

Una vez habiendo codificado todas los features, trabaje con un dataframe sin las columnas originales, y asi puede plottear la matriz de correlacion. La cual, no me aportó grandes revelaciones, ya que las variables que esperaría tengan buena correlacion, no la tenian.

Sabiendo esto, pase a elegir un modelo inicial para comenzar a 'probar'. Como ya lo asenté en el notebook, no encontré criterios contundentes que me inclinen por uno u otro, por lo que decidi empezar por un DTree, por considerarlo sencillo. Ademas pensé, 'sera bueno un DT para un caso con variables tan discretas?'. Pude obtener buen recall pero mal accuracy, y plotteando la curva para distintas profundidades de arbol, observe que iba a ser imposible mejorar el accuracy, por mas de que no era la metrica de eleccion, un buen modelo deberia estar mas equilibrado en los valores accuracy-recall.
Habiendo probado algunos arboles de decision diferentes, pase a vecinos cercanos. 

Al momento de este commit, pude probar varios modelos de Knn, quedandome con el mejor de ellos, para k=22. 

Realmente siento que para sacar insights considerables necesitaria bastante mas juego y experiencia con variedad de modelos y casos de datos diferentes. 

En general, fue un proceso bastante entretenido. Quedo con ganas de seguir aprendiendo y practicando, pero contento con este primer approach al mundo de los modelos de ML. 

