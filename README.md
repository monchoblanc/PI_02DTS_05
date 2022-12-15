# PI_02DTS_05

Segundo Proyecto Individual de Henry, Data Science, cohorte 05. Autor: Ramon Blanc.

La propuesta:

Generar un modelo de machine learning para predecir si al ingresar un paciente a cierto centro de salud, éste tendrá o no una internacion de mas
de 8 dias de duracion. La variable target, se debe definir como binaria, por lo que concluyo es un problema de clasificacion: dado un paciente, o es '0', 
ó es '1'.  

El formato es del tipo hatathon, donde realizamos nuestro modelo, pero entregamos la prediccion sobre una porcion de los datos donde desconocemos las 
respuestas esperadas. Se prioriza la metrica Recall sobre otras. 

La realizacion:

En primer lugar, cargué los archivos csv provistos de train y test, y realice un EDA de ambos. Sobre el archivo test, hice un analisis menos riguroso
(fue esto un error?), pero sí checkié que correspondan los tipos de dato, nombres y cantidad de columnas (salvo por la columna target, la cual no esta en 
el dataset Test). No tuve que hacer grandes cambios en ese sentido, pude observar los datasets bastante 'limpios', sin datos faltantes. 

Luego, evalue si tenia datos atipicos o 'mal escritos', pude ver esto con el metodo .unique(), para mi alegria, no observe rarezas ni datos atipicos. 
Ademas, por como son los valores (discretos) de cada columna, considere  que no debia hacer ningun reescalado, sabiendo que de ser necesario, tendria que 
realizarlo luego de convertir a datos numericos. 

Entre medio de estos procesos, fui observando algunos comportamientos o distribuciones de variables, sin sacar conclusiones certeras pero pudiendo
de a poco sumergirme en los datos. 

Pasé entonces a la codificacion de variables, muy pocas eran de tipo numerico originalmente. Para elegir qué tipo de codificacion utilizar, recurrí un poco
al sentido comun, si existe algo como eso, intentando respaldar mis decisiones con la exploracion de los datos, algo que no me fue del todo posible. Lo que
pude observar es que probablemente sean los distintos modelos, las distintas codificaciones, y las metricas de cada uno, lo que me terminen diciendo 
realmente qué era lo conventiente. Mi criterio en general fue el siguiente: si observaba cierta ordinalidad, hacer OrdinalEncoder o similar 'manualmente', 
dado que la clase existente no me asignaba los valores en la forma en que yo esperaba. Si observaba features puramente nominales, opté por usar 
OneHotEncoder o similar, teniendo en cuenta que los valores de cada feature eran reducidos en cantidad, por lo que no estaria aniadiendo una cantidad 
demasiado grande de columnas. 

Una vez habiendo codificado todas los features, trabaje con un dataframe sin las columnas originales, y asi puede plottear la matriz de correlacion. La 
cual, no me aportó grandes revelaciones, ya que las variables que esperaría tengan buena correlacion, no la tenian. 

Sabiendo esto, pase a elegir un modelo inicial para comenzar a 'probar'. Como ya lo asenté en el notebook, no encontré criterios contundentes que me 
inclinen por uno u otro, por lo que decidi empezar por un DTree, por considerarlo sencillo. Ademas pense, 'sera bueno un DT para un caso con variables
tan discretas?'. Pude obtener buen recall pero mal accuracy, y plotteando la curva para distintas profundidades de arbol, observe que iba a ser imposible 
mejorar el accuracy, por mas de que no era la metrica de eleccion, un buen modelo deberia estar mas equilibrado en los valores accuracy-recall. 

Al momento, me queda probar con otros modelos, K-nn o mas complejos de tipo ensamble, y ver que resultados obtengo. 

