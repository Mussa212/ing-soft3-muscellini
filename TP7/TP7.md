
#### 4.1 Agregar Code Coverage a nuestras pruebas unitarias de backend y front-end e integrarlas junto con sus resultados en nuestro pipeline de build.

- ##### 4.1.1 En el directorio raiz de nuestro proyecto Angular instalar el siguiente paquete:
![[Pasted image 20241002165154.png]]


- ##### 4.1.2 Editar nuestro archivo karma.conf.js para que incluya reporte de cobertura

![[Pasted image 20241002165239.png]]

##### 4.1.3 En el dir raiz del proyecto EmployeeCrudApi.Tests ejecutar:

![[Pasted image 20241002165326.png]]

- ##### 4.1.4 Agregar a nuestro pipeline ANTES del Build de Back la tarea de test con los argumentos especificados y la de publicación de resultados de cobertura:
- ##### 4.1.5 Agregar a nuestro pipeline ANTES del Build de front la tarea de test y la de publicación de los resultados.

![[Pasted image 20241002171956.png]]
![[Pasted image 20241002172024.png]]
![[Pasted image 20241002172041.png]]


- ##### 4.1.6 Ejecutar el pipeline y analizar el resultado de las pruebas unitarias y la cobertura de código.

![[Pasted image 20241002172404.png]]


#### 4.2 Agregar Análisis Estático de Código con SonarCloud:

##### 4.2.1 Integraremos SonarCloud para analizar el código fuente. Configurar SonarCloud en nuestro pipeline siguiendo instructivo 5.1
![[Pasted image 20241002174744.png]]
![[Pasted image 20241002174807.png]]


- ##### 4.2.2 Vemos el resultado de nuestro pipeline, en extensions tenemos un link al análisis realizado por SonarCloud

![[Pasted image 20241002175706.png]]


- ##### 4.2.3 Ir al link y analizar toda la información obtenida. Detallar en la entrega del TP los puntos más relevantes del informe, qué significan y para qué sirven.
![[Pasted image 20241002175802.png]]


![[Pasted image 20241002175835.png]]

Esto indica que utilizar este atributo tiene un impacto medio a la hora de compilar y que el mismo podría intercambiarse para verificar si el nombre contiene un número.

![[Pasted image 20241002175959.png]]

Indica que si la función para formatear el nombre no accede a instancias de datos, debería implementarse como una función estática.

![[Pasted image 20241002180033.png]]

Indica lo mismo que el caso anterior.

![[Pasted image 20241002180131.png]]

Indica que debería usarse otro método(Si count es i, deberíamos usar i-1) en vez del metodo "Last"

![[Pasted image 20241002180452.png]]

Este mensaje significa que cuando propiedades de tipo de valor se usan como parámetros de entrada en un controlador de ASP.NET, puede haber un riesgo de "under-posting", que ocurre cuando no se envían todos los datos necesarios al servidor.

![[Pasted image 20241002180536.png]]

Nos indica que no deberiamos escribir los datos de ingreso a nuestra BD en nuestro código.

#### 4.3 Pruebas de Integración con Cypress:


- ##### 4.3.1 En el directorio raiz de nuestro proyecto Angular instalar el siguiente paquete:
![[Pasted image 20241002180813.png]]

- ##### 4.3.2 Abrir Cypress:

![[Pasted image 20241002180903.png]]


- ##### 4.3.4 Crear nuestra primera prueba navegando a nuestro front.

![[Pasted image 20241002182102.png]]

- ##### 4.3.5 Correr nuestra primera prueba

![[Pasted image 20241002182140.png]]

![[Pasted image 20241002182225.png]]

##### 4.3.6 Modificar nuestra prueba para que falle.

![[Pasted image 20241002182334.png]]

![[Pasted image 20241002182418.png]]

![[Pasted image 20241002182426.png]]

##### 4.3.6 Grabar nuestras pruebas para que Cypress genere código automático y genere reportes:


![[Pasted image 20241002182527.png]]

![[Pasted image 20241002182858.png]]

##### 4.3.7 Hacemos prueba de editar un empleado

![[Pasted image 20241002183313.png]]

![[Pasted image 20241002183329.png]]

![[Pasted image 20241002183404.png]]

![[Pasted image 20241002183536.png]]

