# Proyecto_final_Robotica
Integrantes

Juan Barrera, Theylor Amaya, Andres Serna, Nicolas Guio, Daniel Segura, Juan Pablo Ortiz

# Entregables

1. Descripción
2. Diagrama de flujo acciones
3. Gripper
4. Modelo robotstudio
5. Codigo Rapid
6. Comparacion tiempo manual vs automatizado
7. Presentación y video


## Descripción

**Descripción de la Solución: Automatización de Procesos de Pick & Place**

Para abordar el problema de optimizar los procesos de alistamiento de pedidos mediante la implementación de un sistema robotizado, se ha desarrollado una solución integral que combina la automatización de tareas, el diseño de herramientas especializadas y la creación de una interfaz humano-máquina (HMI) para facilitar la interacción y supervisión del sistema.

### Proceso de Alistamiento:

1. **Alistamiento Manual:**
   Se llevó a cabo una fase inicial de alistamiento manual para comprender el tiempo promedio necesario para preparar combinaciones específicas de productos en la estantería de 6 posiciones (A1, A2, B1, B2, C1, C2). Este tiempo se midió con el objetivo de establecer una referencia para evaluar la eficiencia del proceso automatizado.

2. **Diseño y Construcción del Gripper:**
   Se diseñó un gripper personalizado capaz de adaptarse fácilmente a los cilindros de doble efecto disponibles en el LabSIR. El gripper se controla mediante una señal digital conectada a una electroválvula. 
   ![Gripper Design](url_del_diseño_del_gripper)

   *Imagen: Diseño del Gripper.*

3. **Elementos Neumáticos:**
   Se seleccionaron y utilizaron una electroválvula 5/2 y acoples disponibles en el LabSIR para construir el gripper. Se aseguró que el diseño permitiera un fácil ajuste y posicionamiento de los dedos del gripper sobre los cilindros, minimizando la necesidad de desmontar otros componentes.

   ![Elementos Neumáticos](url_de_elementos_neumaticos)

   *Imagen: Elementos Neumáticos Disponibles.*

### Alistamiento de la Estantería:

- **Posicionamiento de Elementos:**
  Las piezas fueron ubicadas en posiciones aleatorias en la estantería, considerando la disposición de 3 elementos diferentes en las 6 posiciones disponibles.

- **Ajustes con Brazo Inmóvil:**
  Todos los ajustes en la estantería y las piezas se realizaron con el brazo manipulador inmóvil al inicio del proceso.

- **Análisis de Tiempo Manual:**
  Se realizaron pruebas de alistamiento manual con una sola mano para determinar el tiempo promedio necesario para diferentes combinaciones de objetos. Este análisis proporciona una referencia para evaluar la eficiencia del proceso automatizado.

### Proceso Automatizado:

- **Interfaz Gráfica:**
  Se diseñó una interfaz humano-máquina (HMI) utilizando la herramienta ScreenMaker de RobotStudio. La interfaz permite la selección de objetos desde la estantería y su posicionamiento en la zona de alistamiento mediante la banda transportadora.

   ![Interfaz Gráfica](url_de_interfaz_grafica)

   *Imagen: Interfaz Gráfica de la Herramienta.*

- **Ejemplo de Proceso:**
  Se presentaron ejemplos de secuencias de posicionamiento de objetos sobre la banda transportadora, asegurando que siempre se respeten las posiciones finales de los objetos, independientemente del orden de llegada.

### Consideraciones Finales:

- **Dimensiones Reales:**
  El diseño de la herramienta se ajusta a las dimensiones reales de la construcción, garantizando una integración adecuada con los equipos disponibles en el LabSIR.

- **Velocidades y Parámetros de Movimiento:**
  Las velocidades, zonas de aproximación y otros parámetros de movimiento se determinan de acuerdo con las condiciones de trabajo seguro y las indicaciones del docente en el laboratorio.

- **Documentación Completa:**
  Se documentó todo el proceso del proyecto, incluyendo dificultades encontradas y lecciones aprendidas. Esta documentación se presenta de manera detallada para facilitar la comprensión y evaluación del trabajo realizado por otros equipos.

La solución propuesta no solo aborda la automatización del proceso de Pick & Place, sino que también demuestra una cuidadosa consideración de los detalles técnicos, la eficiencia del diseño y la usabilidad a través de la interfaz gráfica.

## Diagrama de flujo acciones
Para la explicación del proceso por medio de diagramas de flujo primero se hizo un diagrama del código principal, para luego realizar el respectivo diagrama de cada una de las subrutinas.

![image](https://github.com/JuanPabloOrt/Proyecto_final_Robotica/assets/144573976/3e48a617-3f0f-4374-b8e4-5315ce587827)

Para la rutina principal, lo primeor que se hace es enviar el robot a posición de "HOME" donde todas sus posicones articulares se ponen en 0. Luego se abre el gripper para preparar la erramienta para tomar algún objeto, luego con ayuda de un contador se delimita cuántas veces se va a realizar el ciclo principal y co un nuevocondicional se indica la espera a que se acrive un botón, que sería de la interfaz.

![image](https://github.com/JuanPabloOrt/Proyecto_final_Robotica/assets/144573976/aaa26204-bd25-439d-a15c-21701afc1b1f)

Para la rutina de toma de producto se toma el dato del botón que fue presionado y se revisa uno a uno cuál fue para realizar la rutina respectiva.

![image](https://github.com/JuanPabloOrt/Proyecto_final_Robotica/assets/144573976/8400e2d5-16f7-4d70-99b1-d30866adb00b)

Para la rutina encargada de dejar los productos en la banda se revisa en órden ascendente cuál de las posicones está libre y se ejecuta la rutina de la primera que encuentre.

![image](https://github.com/JuanPabloOrt/Proyecto_final_Robotica/assets/144573976/a74977b7-564e-4d9b-b6a9-fb179ea57de9)
![image](https://github.com/JuanPabloOrt/Proyecto_final_Robotica/assets/144573976/300c934d-d081-4de4-b721-dc855754854e)

Para las rutinas de las trayectorias de los conjuntos A Y B se sigue la misma lógica, se dirige primero a un posición de "retorno" que tiene una funci´n similar al "HOME" pero este es respecto a la posicón de la pieza en función de la psición del estante, no de valores articulares. Luego se dirige a la posición respectiva por medio de las trayectorias definidas en el RobotStudio, para después cerrar el gripper y agarrar el proucto. Seguido a esto vuelve a la posicion de "retorno" siguiendo la misa trayectoria anterior en sentido contrario.

![image](https://github.com/JuanPabloOrt/Proyecto_final_Robotica/assets/144573976/07478ca1-7aa6-4cc3-b852-a6f433061374)

Para las rutinas de las trayectorias deL conjunto P se sigue una lógica muy similar a la de los dos conjuntos anteriores, con la única diferencia es que en este caso el gripper se abre para soltar el producto. 

## Gripper

## Modelo robotstudio
### Interfaz HMI:
Para la elaboracion de esta interfaz se uso el sdk 'ScreenMaker' el cual se puede complementa complementa 'RobotStudio' y permite la creacion de este tipo de interfaces. A continuacion se muestra el modelo de la interfaz creada:
![image](https://github.com/JuanPabloOrt/Proyecto_final_Robotica/assets/70239708/8da08764-7069-448e-bf93-232f323218f9)

Esta interfaz esta divida en dos zonas principales, la primera es la zona 'Ubicacion de los objetos' esta zona muestra las 6 diferentes areas de la estanteria en la cual se encuentran los objetos a recoger. Por cada una de estas areas hay dos elementos, el primero es un boton el cual permite seleccionar la el area a la que se quiere llegar dirigiendo el robot hacia ese punto. El segundo elemento es un led el cual indica si la respectiva posicion fue escogida previamente en el ciclo de trabajo. En la segunda zona de la interfaz, se observan las tres posiciones de la banda transportadora mediante el uso de leds que indican si la respectiva posicion ya fue ocupada en el ciclo de trabajo.
La conexion de los diferentes elementos con el programa de rapid se realizo mediante la escritura o lectura de variables en el programa segun sea el caso, la logica bajo la cual esto funcionan cada una de las variables seran explicadas en la seccion 'Codigo RAPID'.
En el repositorio se encuentra el video explicativo, este video mostrara el resultado de las simulaciones realizadas previas a la implementacion en los robots del LabSIR.




## Codigo Rapid
Esta seccion explicara la logica usada en el codigo de RAPID para la solucion del problema propuesto (se dejara de lado la descripcion detallada de la creacion de las rutinas de movimiento, ya que para eso solo se definen los puntos en el espacio de trabajo del robot y se recorren uno a uno) asi como la conexion con los distintos elementos de la interfaz HMI.
![Robotstudio](https://github.com/JuanPabloOrt/Proyecto_final_Robotica/assets/144573976/b5ef4aab-e12d-40c4-818e-4c2aa47a3279)

### Definicion de variables:

![image](https://github.com/JuanPabloOrt/Proyecto_final_Robotica/assets/70239708/b72d4d27-3fe5-47ab-be20-534a53806014)

Todas las variables tipos 'PERS' son aquellas que se usan para comunicarse con la interfaz HM, entes caso se usaron unicamente variables booleanas ya que unicamente era necesario indicar estados binarios. En primer lugar, las variables cuyo nombre inicia con la palabra 'trayectoria' indican a cual de las distintas ubicaciones de la estanteria debe ir el robot. Todas estas variables inician con un valor 'False' y al presionar el boton respectivo en la interfaz HM su valor cambia a 'True' haciendo que el robot se mueva. Luego se encuentran las variables que inician con la palabra 'Disp' que se usa como abreviacion de 'Disponible', estas variables estan asociadas a los led de cada una de las posiciones de los objetos de la estanteria  e indican su disponibilidad. Por lo tanto estas variables tienen un valor inicial 'True' y cuando son recogidos por el robot este cambia a 'False' indicando que en esta ubicacion de la estanteria ya no hay ningun objeto a recoger. Finalmente, las variables que inician con la palabra 'Banda' representan las tres posiciones posibles que se usan para ubicar los objetos a lo largo de la banda transportadora y estan asociadas a los led de su respectiva posicion. Ya que la banda transportadora inicia sin ningun objeto sobre ella, estas variables incian con un valor 'False' y a medida de que se ubican objetos sobre la banda se van cambiando a 'True'.

### Lógica del Programa
Luego de definir as variables se hace uso de los procesos presentados anteriormente en los diagramas de flujo:

Primero, con la ayuda de un contador, se limita a que el ciclo principal solo se ejecute la cantidad de veces nesearia, en este caso son 3, debido a la cantidad de productos que se van a utilizar.

Luego se espera a que alguno de los botones de la interfaz sea presionado y se evalúan, en orden, las variables relacionadas a las posciones del conjunto A y el conjunto B para que el robot realice la rutina correspondiente al botón seleccionado, finalmente se retorna a "FALSE" la variable de la rutina para que esta no se siga ejecutando la siguente vez que se realice el ciclo principal. 

Después de realizar la rutina selecconada se procede a revisar en orden las posiciones en la banda. Cuando se encuentra que una está disponible el robot realiza la rutina respectiva del conjunto de trayectorias P, y se cabia el valor de la variable de la posición para indicar que esta se encuentra ocupada.





## Comparacion tiempo manual vs automatizado

## Presentación y video

