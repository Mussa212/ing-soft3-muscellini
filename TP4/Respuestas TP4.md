# 4.3
Es necesario contar con una tarea de Publish en un pipeline que corre en un agente de Microsoft en la nube por las siguientes razones:

1. **Distribución del artefacto**: La tarea de *Publish* permite empaquetar y almacenar los artefactos generados (como archivos binarios, imágenes de contenedores, archivos compilados, etc.) en un repositorio accesible. Esto facilita la distribución del software compilado para su posterior uso en otras etapas del pipeline, como el despliegue en un entorno de prueba o producción.

2. **Persistencia de resultados**: Los agentes en la nube son temporales y, una vez que finaliza la ejecución de un pipeline, todos los archivos y el estado del agente se eliminan. La tarea de *Publish* garantiza que los artefactos se almacenen en un lugar persistente, como **Azure Artifacts**, **Azure Storage** o algún otro repositorio, asegurando que los resultados no se pierdan.

3. **Separación de etapas**: En los pipelines de CI/CD, es común separar la etapa de **build** (compilación) de la de **deploy** (despliegue). La tarea de *Publish* permite que los artefactos generados durante la compilación estén disponibles para ser consumidos por otras etapas del pipeline (como la prueba o el despliegue), incluso si estas etapas ocurren en diferentes agentes o en diferentes momentos.

4. **Facilita el diagnóstico y seguimiento**: Publicar artefactos permite a los equipos de desarrollo y operaciones descargar y examinar los resultados de la compilación para fines de diagnóstico, auditoría o pruebas adicionales. Es una práctica recomendada para tener trazabilidad de los artefactos que se han generado y que son candidatos a ser desplegados.

# 4.5

Las diferencias clave entre el **Editor Clásico** de pipelines y el **Editor YAML** en Azure DevOps son las siguientes:

### 1. **Interfaz de Usuario vs. Código Declarativo**

- **Editor Clásico**:
  - Basado en una **interfaz gráfica de usuario (GUI)**. Permite crear pipelines utilizando un asistente visual que guía al usuario a través de diferentes pasos para agregar tareas y configuraciones.
  - Cada paso del pipeline se agrega a través de formularios y menús desplegables, lo que lo hace más accesible para usuarios que prefieren evitar escribir código.

- **Editor YAML**:
  - Basado en **archivos YAML**. Los pipelines se definen en un archivo de texto que contiene la configuración en formato YAML. Esto implica escribir el pipeline manualmente mediante código declarativo.
  - Al usar YAML, los usuarios pueden versionar su pipeline en el repositorio junto con el código fuente, permitiendo cambios controlados por el equipo de desarrollo.

### 2. **Versionamiento**

- **Editor Clásico**:
  - Los pipelines creados en el editor clásico no se almacenan en el control de versiones por defecto, ya que se configuran directamente en la plataforma Azure DevOps.
  - Cualquier cambio realizado en la configuración del pipeline clásico no queda registrado en el código fuente, lo que puede dificultar la colaboración y revisión de cambios en proyectos grandes.

- **Editor YAML**:
  - Los pipelines en YAML se almacenan como parte del código fuente del proyecto (generalmente en el repositorio Git). Esto permite rastrear los cambios y colaboraciones mediante commits, pull requests, y revisiones de código.
  - Este enfoque es más adecuado para equipos que desean un control total sobre el flujo del pipeline y que manejan cambios a través de procesos de versionado estándar.

### 3. **Flexibilidad y Personalización**

- **Editor Clásico**:
  - Proporciona una interfaz fácil de usar para construir pipelines, pero su flexibilidad es limitada en comparación con YAML. Está diseñado para usuarios que prefieren configuraciones rápidas sin necesidad de personalizar en profundidad.
  - Las opciones más avanzadas o personalizadas pueden requerir agregar scripts adicionales o tareas predefinidas, lo que puede ser menos intuitivo en comparación con YAML.

- **Editor YAML**:
  - Permite una mayor flexibilidad y personalización, ya que el archivo YAML puede incluir condiciones complejas, bucles, parámetros reutilizables, y la posibilidad de organizar diferentes tareas en una estructura más avanzada.
  - Es ideal para proyectos complejos con requisitos específicos y donde se desea controlar todos los aspectos del pipeline.

### 4. **Reutilización y Plantillas**

- **Editor Clásico**:
  - Aunque puedes clonar pipelines o copiar algunas configuraciones, el soporte para reutilización y modularización es limitado. Si necesitas compartir configuraciones comunes entre varios pipelines, deberás hacerlo manualmente.
  
- **Editor YAML**:
  - Soporta plantillas y reutilización de fragmentos de código. Esto permite definir una estructura común y luego reutilizarla en varios pipelines, facilitando la gestión de configuraciones comunes en diferentes proyectos.
  - También permite la creación de archivos YAML modulares que pueden ser referenciados desde diferentes pipelines, lo que es útil para la gestión de proyectos grandes o múltiples.

### 5. **Mantenimiento y Escalabilidad**

- **Editor Clásico**:
  - Es más fácil de mantener para usuarios que no están familiarizados con código, ya que la interfaz es clara y proporciona opciones predefinidas. Sin embargo, a medida que el pipeline se hace más complejo, la gestión mediante el editor clásico puede volverse difícil debido a la falta de control y personalización avanzada.
  
- **Editor YAML**:
  - Aunque requiere más conocimientos técnicos, la configuración en YAML es más escalable. En proyectos grandes y complejos, YAML ofrece un mejor control, menor repetición de código, y más capacidades para gestionar la evolución de los pipelines.

### 6. **Colaboración y Automatización**

- **Editor Clásico**:
  - Colaboración limitada, ya que los cambios en el pipeline no están directamente ligados al control de versiones. Es más adecuado para flujos de trabajo simples y equipos pequeños que no requieren control detallado de cambios.

- **Editor YAML**:
  - Favorece la colaboración entre equipos, ya que el archivo YAML puede ser compartido, revisado y versionado en Git. Esto facilita la automatización y mejora la trazabilidad de los cambios en el pipeline.

### ¿Cuándo usar cada uno?

- **Editor Clásico**:
  - Ideal para usuarios que buscan simplicidad y rapidez en la configuración sin necesidad de control avanzado o versionado de pipelines.
  - Adecuado para proyectos pequeños o para aquellos que prefieren una interfaz gráfica y no están familiarizados con la escritura de código en YAML.

- **Editor YAML**:
  - Recomendado para equipos de desarrollo que buscan flexibilidad, escalabilidad y control detallado sobre el pipeline.
  - Es adecuado para proyectos más grandes o complejos donde la personalización, la colaboración y el versionamiento son importantes.


# 4.8

### Diferencia entre un **Agente Microsoft-hosted** y un **Agente Self-Hosted** en Azure DevOps:

1. **Agente Microsoft-hosted**:
   - Este tipo de agente es administrado y provisto por Microsoft.
   - Cada vez que se ejecuta un pipeline, Azure DevOps aprovisiona un agente virtual de una máquina nueva (basada en un sistema operativo que elijas: Windows, Linux, o macOS), la cual se limpia después de cada ejecución.
   - Incluye una configuración predefinida con varias herramientas y entornos como Node.js, .NET, Java, Docker, etc.

2. **Agente Self-Hosted**:
   - Este tipo de agente es administrado por ti o por tu equipo.
   - Puedes instalarlo en tus propios servidores o máquinas virtuales (en las instalaciones o en la nube).
   - Ofrece control total sobre la configuración del agente, las herramientas instaladas, los tiempos de ejecución y otros parámetros.

### Ventajas y desventajas de un **Agente Microsoft-hosted**:

#### Ventajas:
- **Fácil de configurar**: No se necesita mantenimiento ni configuración manual del agente, ya que Azure DevOps lo maneja por completo.
- **Actualizado automáticamente**: Microsoft se encarga de mantener las herramientas y dependencias al día.
- **Disponibilidad inmediata**: No es necesario aprovisionar ni mantener hardware o software, ya que los agentes están siempre listos.
- **Escalabilidad**: Se pueden aprovisionar múltiples agentes rápidamente según sea necesario, lo que es ideal para proyectos con cargas de trabajo variables.

#### Desventajas:
- **Límites de tiempo de ejecución**: Los pipelines en agentes Microsoft-hosted tienen límites de tiempo de ejecución, lo que puede ser un problema para tareas que requieren tiempos más largos.
- **Menor personalización**: No puedes controlar qué versiones exactas de software están instaladas ni personalizar el entorno más allá de lo que Microsoft proporciona.
- **Costo en grandes volúmenes**: Si bien tienes una cantidad gratuita de minutos en agentes Microsoft-hosted, si tu proyecto es grande, es posible que el costo por minuto adicional se incremente rápidamente.

### Ventajas y desventajas de un **Agente Self-Hosted**:

#### Ventajas:
- **Control total**: Puedes instalar cualquier herramienta, software, o versiones específicas necesarias para tu proyecto.
- **Sin límites de tiempo de ejecución**: No hay restricciones de tiempo de ejecución en tus agentes Self-Hosted, lo que permite manejar trabajos más largos sin preocupaciones.
- **Ahorro en proyectos a largo plazo**: Si tienes una infraestructura ya existente, usar agentes Self-Hosted puede ser más rentable a largo plazo, especialmente si necesitas ejecutar muchas tareas continuamente.

#### Desventajas:
- **Mantenimiento**: Debes encargarte del mantenimiento, actualización, y escalabilidad de los agentes. Si necesitas nuevas versiones de software o parches de seguridad, debes gestionarlos manualmente.
- **Disponibilidad limitada**: Si el agente Self-Hosted tiene algún problema (como una caída del servidor o recursos insuficientes), los pipelines pueden fallar.
- **Costo inicial**: Necesitas aprovisionar tu infraestructura (máquinas, servidores, etc.), lo que puede tener un costo inicial más alto.

### Cuándo es conveniente usar un **Self-Hosted Agent**:

1. **Necesitas un entorno personalizado**: Si tus pipelines requieren herramientas o versiones específicas que no están disponibles en los agentes Microsoft-hosted.
2. **Trabajo intensivo**: Si tus tareas requieren largos tiempos de ejecución o consumen muchos recursos (CPU, memoria), como la compilación de grandes proyectos o pruebas extensivas, los Self-Hosted Agents permiten que controles mejor el rendimiento sin restricciones.
3. **Costos continuos**: Si estás ejecutando muchas compilaciones de forma constante, un Self-Hosted Agent puede ser más económico a largo plazo en comparación con pagar por el uso de agentes Microsoft-hosted.
4. **Acceso a recursos internos**: Si tus pipelines necesitan acceder a sistemas internos de tu red privada que no están accesibles desde los agentes Microsoft-hosted, los agentes Self-Hosted pueden estar configurados para trabajar en esa red.



> Written with [StackEdit](https://stackedit.io/).
