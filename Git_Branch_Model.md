# **Git Branching Model**
El Git Branching Model *"Modelo de ramificacion de git"*, como su nombre lo indica, es un modelo de trabajo que busca implementar la funcionalidad de creacion y gestion de ramas en git para el desarrollo de proyectos grandes. 

Cuando nos enfrentamos a proyectos de software grandes, el tener que resolver un error, añadir una nueva caracteristica,etc. si es que no tenemos una correcta organizacion, puede volverse una pesadilla. Es debido a esto que Vincent Driessen propuso este modelo de trabajo, que divide el desarrollo del proyecto en varias ramas, donde cada rama tiene un objetivo especifico.

Este modelo consta de dos ramas principales y tres ramas de soporte, las cuales son:
 * Ramas principales   
    * Master
    * Develop
 * Ramas de soporte
    * Feature
    * Release 
    * Hot fix

Aqui podemos ver un ejemplo visual de este sistema de ramas, y como estas se manejan a traves del tiempo. A continuacion explicare el funcionamiento de cada rama, a demás del posible origen de una rama y su union con otra.
![Imagen ejemplo](https://nvie.com/img/git-model@2x.png)

 ## **Rama Master**
Al iniciar un repositorio git en cualquier proyecto, la rama **Master** es la primera en crearse. El objetivo de la rama master en este flujo de trabajo es la de almacenar unicamente commits que tengan versiones lanzables de un proyecto, versiones que pueden ser distribuidas, comercializadas, entregadas a los usuarios, etc.

Aqui no deberiamos guardar commits que tengan versiones incompletas del proyecto, ni siquiera aquellas que le falten arreglar pequeños detalles del proyecto (para esto existen otras ramas).

Esta rama nunca debe ser usada para desarrollar el proyecto, solo para almacenar versiones utilizables y que se consideran finales del mismo.

## **Rama Develop**
La rama  **Develop** *"Rama de Desarrollo"* , como su nombre lo indica, es la rama donde desarrollaremos el proyecto, aqui es donde trabajamos en nuevas versiones del proyecto.
Esta es la rama donde pasaremos mas tiempo y de echo es la rama que guarda mas relacion con todas las demas.

Esta rama trabaja de la mano con **Release**, ya que en realidad esta no se une directamente con **Master**, si no que primero lo hace con **Release**, para posteriormente pasar de esta a la rama **Master**. El echo de dicidir cuando pasar a **Release** sera explicado en el subtitulo de dicha rama.

Cabe aclarar que la rama **Master** y **Develop** se consideran infinitas, ya que estas permaceran durante toda la vida del software, desde su creacion hasta su ultima version, estas no seran eliminadas.

De forma contraria las ramas de soporte son creadas para solucionar una necesidad y una vez cumplido su objetivo, eliminarse.

## **Rama Feature**
La primera de las ramas secundarias, **Feature** *"Caracteristica,rasgo"*, esta nace como una ramaficacion de la rama **Develop**, y una vez terminado su objetivo se une nuevamente con esta.

Su objetivo es llevar a cabo el desarrollo de nueva funcionalidades para el software, ya sea para implementarlos proximamente o en un futuro distante. 

Dicha rama existira mientras la funcionalidad este en desarrollo, una vez completada, esta rama se volvera a unir con **Develop** para posteriormente desaparecer, hasta que se quiera implementar otra funcionalidad nuevamente.

Como mencionamos anteriormente, esta rama tienen un tiempo de vida finito, una vez que la funcionalidad esta terminada e implementada, no hay necesidad de guardarla, ya que todo lo que esta contenga, tambien lo tendra **Develop**.
## **Rama Release**
La rama **Release** *"lanzamiento"*, como lo mencionamos anteriormente, nace como una ramificacion de **Develop**, y puede unirse con **Master** o **Develop** nuevamante.

Esta rama tiene el objetivo de afinar los ultimo detalles antes de unirse con la rama **Master**, o si es que presenta algun problema que impida dicho lanzamiento, regresar nuevamente a **Develop**

En esta rama surge la pregunta, ¿Cuando nace esta rama?. Si bien no existe una formula exacta que aplicar que nos diga el momento exacto de creacion de esta rama (ya que cada proyecto de software es unico), bien hay unos cuantos indicadores que podemos tomar en cuenta. Esta rama nace cuando, el objetivo a desarrollar a sido concluido y funciona correctamente. A esta rama nunca debe llegar un proyecto que este incompleto, unicamente deben llegar aquellos que presenten errores pequeños que no sean criticos en el funcionamiento del software. 

A demás aqui es donde se le asigna un numero de version al desarrollo actual del software, y si es que todos los pequeños detalles son solucionados, el proyecto pasara a **Master**, caso contrario volvera **Develop**.

## **Rama Hot Fix**
La rama **Hot fix** *"Que se podria traducir como arreglo urgente"*, nace cuando se presenta una falla critica en el software, que impide el correcto funcionamiento del mismo, o ya de plano, no deja que funcione totalmente.

Una vez que dicho error es solucionado, esta se une nuevamente con **Master** y **Develop**.

Esta rama permite que el error sea solucionado, sin la necesidad de parar todo el proyecto. El proyecto puede continuar su desarrollo, y cuando el error sea solucionado, simplemente unir este a las demas ramas.

### **Notas finales**
Si bien los nombres de estas ramas son los mas utilizados, cada equipo puede cambiar los nombres si es que lo vieran conveniente. Esto si bien es permitido, no es muy recomendable a no ser que el nombre sea bastante descriptivo, ya que podria confundir a nuevos integrantes en el proyecto sobre el correcto uso de estas. 

Igualmente si un equipo considera conveniente, podria crear otras ramas extras,con objetivos especificos.

Por ultimo, la forma de unir ramas en esta metodologia es evitando el **Fast Forward**, y utilizando la forma recursiva de git, creando un nuevo commit, donde apunte la cabezera de ambas ramas. Tampoco usa **Rebase** para unir ramas. Nuevamente, cada equipo es libre de unir las ramas como vean mas conveniente, pero cabe aclarar que esta metodologia esta pensada para unir ramas como se explico anteriormente.
