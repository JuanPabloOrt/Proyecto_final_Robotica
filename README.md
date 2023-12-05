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

## Diagrama de flujo acciones

## Gripper

## Modelo robotstudio
Interfaz HMI:
Para la elaboracion de esta interfaz se uso el sdk 'ScreenMaker' el cual se puede complementa complementa 'RobotStudio' y permite la creacion de este tipo de interfaces. A continuacion se muestra el modelo de la interfaz creada:
![image](https://github.com/JuanPabloOrt/Proyecto_final_Robotica/assets/70239708/8da08764-7069-448e-bf93-232f323218f9)

Esta interfaz esta divida en dos zonas principales, la primera es la zona 'Ubicacion de los objetos' esta zona muestra las 6 diferentes areas de la estanteria en la cual se encuentran los objetos a recoger. Por cada una de estas areas hay dos elementos, el primero es un boton el cual permite seleccionar la el area a la que se quiere llegar dirigiendo el robot hacia ese punto. El segundo elemento es un led el cual indica si la respectiva posicion fue escogida previamente en el ciclo de trabajo. En la segunda zona de la interfaz, se observan las tres posiciones de la banda transportadora mediante el uso de leds que indican si la respectiva posicion ya fue ocupada en el ciclo de trabajo.
La conexion de los diferentes elementos con el programa de rapid se realizo mediante la escritura o lectura de variables en el programa segun sea el caso, la logica bajo la cual esto funcionan cada una de las variables seran explicadas en la seccion 'Codigo RAPID'.
En el repositorio se encuentra un video con el nombre 'Simulaciones.mp4' como su nombre lo indica, este video mostrara el resultado de las simulaciones realizadas previas a la implementacion en los robots del LabSIR.




## Codigo Rapid
Esta seccion explicara la logica usada en el codigo de RAPID para la solucion del problema propuesto (se dejara de lado la descripcion detallada de la creacion de las rutinas de movimiento, ya que para eso solo se definen los puntos en el espacio de trabajo del robot y se recorren uno a uno) asi como la conexion con los distintos elementos de la interfaz HMI.

Definicion de variables:

![image](https://github.com/JuanPabloOrt/Proyecto_final_Robotica/assets/70239708/b72d4d27-3fe5-47ab-be20-534a53806014)

Todas las variables tipos 'PERS' son aquellas que se usan para comunicarse con la interfaz HM, entes caso se usaron unicamente variables booleanas ya que unicamente era necesario indicar estados binarios. En primer lugar, las variables cuyo nombre inicia con la palabra 'trayectoria' indican a cual de las distintas ubicaciones de la estanteria debe ir el robot. Todas estas variables inician con un valor 'False' y al presionar el boton respectivo en la interfaz HM su valor cambia a 'True' haciendo que el robot se mueva. Luego se encuentran las variables que inician con la palabra 'Disp' que se usa como abreviacion de 'Disponible', estas variables estan asociadas a los led de cada una de las posiciones de los objetos de la estanteria  e indican su disponibilidad. Por lo tanto estas variables tienen un valor inicial 'True' y cuando son recogidos por el robot este cambia a 'False' indicando que en esta ubicacion de la estanteria ya no hay ningun objeto a recoger. Finalmente, las variables que inician con la palabra 'Banda' representan las tres posiciones posibles que se usan para ubicar los objetos a lo largo de la banda transportadora y estan asociadas a los led de su respectiva posicion. Ya que la banda transportadora inicia sin ningun objeto sobre ella, estas variables incian con un valor 'False' y a medida de que se ubican objetos sobre la banda se van cambiando a 'True'.


## Comparacion tiempo manual vs automatizado

## Presentación y video

