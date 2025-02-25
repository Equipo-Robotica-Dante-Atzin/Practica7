# Práctica 7

## Integrantes

- Dante Mejía Silva
- Atzin Morales Alejandre

## Introducción 

En esta práctica de laboratorio de robótica, se estudió y aplicó el software de control Epson RC+ para programar un robot industrial en la realización de tareas de precisión. Inicialmente, se llevó a cabo una revisión teórica de funciones y comandos específicos del software, esenciales para la programación de trayectorias y la ejecución de movimientos complejos. Las funciones estudiadas incluyeron:

1. **Función Here**: utilizada para almacenar posiciones específicas del robot, permitiendo definir puntos de referencia clave para los movimientos.
2. **Operaciones + y :** que permiten manipular y ajustar coordenadas y vectores, cruciales para el diseño de trayectorias en el espacio de trabajo del robot.
3. **Funciones en Paralelo y Serie**: fundamentales para la organización de los movimientos y tareas del robot, permitiendo realizar acciones de manera secuencial o simultánea.
4. **Comandos en Paralelo**: empleados para ejecutar múltiples instrucciones al mismo tiempo, optimizando los tiempos de proceso.
5. **Función Pallet**: utilizada para programar patrones de disposición de puntos en el espacio, ideal para tareas que requieren una distribución uniforme.

Como parte final de la práctica, se desarrolló un código empleando la función de pallet para que el robot trazara una figura en una hoja de papel mediante una serie de puntos. Esta actividad permitió aplicar los conceptos teóricos adquiridos y evaluar la precisión del robot en la ejecución de trayectorias programadas.

## Instrucciones

En primer lugar, se seleccionó la figura que se deseaba trazar y se representó inicialmente en Excel, utilizando una matriz de 10x10 en la cual se ubicaron y numeraron los puntos clave. Esta disposición permitió visualizar la estructura de la figura y organizar los puntos de manera ordenada, facilitando su posterior programación en el robot.

![image](https://github.com/user-attachments/assets/098a3833-ddd4-4d45-be64-186617e104f3)

Con base en los conocimientos adquiridos durante la clase de laboratorio, se desarrolló el siguiente código para que el brazo robótico Epson pudiera trazar la figura seleccionada. Este código permite que el robot ejecute con precisión la secuencia de movimientos necesarios para recrear el diseño elegido.
```
Function main
	
	Motor On
	Power Low
		
	Home
	Pallet 0, esq_inf_izq, esq_inf_der, esq_sup_izq, 10, 10
	Go Pallet(0, 52)
	Jump3 Here +Z(20), Pallet(0, 42) +Z(20), Pallet(0, 42)
	Jump3 Here +Z(20), Pallet(0, 32) +Z(20), Pallet(0, 32)
	Jump3 Here +Z(20), Pallet(0, 43) +Z(20), Pallet(0, 43)
	Jump3 Here +Z(20), Pallet(0, 44) +Z(20), Pallet(0, 44)
	Jump3 Here +Z(20), Pallet(0, 45) +Z(20), Pallet(0, 45)
	Jump3 Here +Z(20), Pallet(0, 76) +Z(20), Pallet(0, 76)
	Jump3 Here +Z(20), Pallet(0, 66) +Z(20), Pallet(0, 66)
	Jump3 Here +Z(20), Pallet(0, 56) +Z(20), Pallet(0, 56)
	Jump3 Here +Z(20), Pallet(0, 46) +Z(20), Pallet(0, 46)
	Jump3 Here +Z(20), Pallet(0, 36) +Z(20), Pallet(0, 36)
	Jump3 Here +Z(20), Pallet(0, 26) +Z(20), Pallet(0, 26)
	Jump3 Here +Z(20), Pallet(0, 16) +Z(20), Pallet(0, 16)
	Jump3 Here +Z(20), Pallet(0, 67) +Z(20), Pallet(0, 67)
	Jump3 Here +Z(20), Pallet(0, 27) +Z(20), Pallet(0, 27)
	Jump3 Here +Z(20), Pallet(0, 58) +Z(20), Pallet(0, 58)
	Jump3 Here +Z(20), Pallet(0, 38) +Z(20), Pallet(0, 38)
	Jump3 Here +Z(20), Pallet(0, 49) +Z(20), Pallet(0, 49)
	
	Home
	Motor Off
	
Fend
```

**Function main:** La función principal, denominada main, contiene la secuencia de comandos para que el robot ejecute el proceso de trazar la figura sobre el papel.

**Motor On:** Activa el motor del robot.

**Power Low:** Establece una potencia baja, adecuada para tareas de precisión.

**Home:** El robot se posiciona en su ubicación de referencia o punto de inicio, asegurando que todos los movimientos siguientes partan de una posición conocida.

**Pallet:** La cuadrícula o pallet está definida como una matriz de 10x10 puntos, identificada por el número 0. Sus parámetros se detallan a continuación:

- Esquinas: La cuadrícula se ubica entre tres puntos de referencia: la esquina inferior izquierda (esq_inf_izq), la esquina inferior derecha (esq_inf_der), y la esquina superior izquierda (esq_sup_izq).
- Dimensiones: La matriz tiene una disposición de 10 filas por 10 columnas.

**Go Pallet(0, 52):** El robot se dirige al punto número 52 dentro de la cuadrícula (pallet 0), representando el inicio de la figura.

**Jump3:** Cada paso de la secuencia Jump3 se compone de tres movimientos, y está diseñado para permitir que el robot baje y suba en el eje Z en cada posición de la cuadrícula, asegurando un trazo preciso en cada punto.

**Formato del Movimiento:** Cada línea de movimiento sigue la estructura Jump3 Here +Z(20), Pallet(0, XX) +Z(20), Pallet(0, XX).

**Here +Z(20):** Mueve al robot a una posición 20 unidades sobre su ubicación actual, permitiéndole "sobrevolar" el área de trabajo.

**Pallet(0, XX) +Z(20):** Lleva al robot a 20 unidades sobre el punto XX en la cuadrícula sin tocar la superficie.

**Pallet(0, XX):** Finaliza el movimiento en el punto XX, tocando la superficie del papel para simular el trazo.

**Puntos Visitados:** El robot se desplaza a varios puntos en la cuadrícula (por ejemplo, Pallet(0, 42), Pallet(0, 32), etc.), permitiendo la creación de la figura a través de trazos precisos.

**Motor Off:** Para completar la tarea, el motor del robot se apaga, finalizando todas las operaciones de movimiento.

**Fend:** Este comando marca el fin de la función principal main, concluyendo la ejecución del código.

La siguiente imagen muestra el resultado del trazo obtenido después de ejecutar el código en el brazo robótico:

![Imagen de WhatsApp 2024-10-25 a las 17 51 03_45ce59c7](https://github.com/user-attachments/assets/ff2c97cd-a523-4638-9961-4d952d25defc)

## Conclusiones

***Atzin Morales Alejandre:*** En esta práctica de laboratorio, se pudo aplicar los conceptos de programación y control del brazo robótico del laboratório. A través de funciones como "Here", "Pallet" y "Jump3", se logró que el robot trazara una figura en una cuadrícula de 10x10, siguiendo puntos específicos con precisión. La función "Here" fue clave para marcar posiciones de referencia sin necesidad de enseñarselas de manera manual al robot, haciendo la programación más eficiente.

La función "Pallet" permitió organizar una cuadrícula de puntos para que el robot siguiera un patrón uniforme, ideal para tareas repetitivas. El comando "Jump3" fue importante para mover la herramienta en el eje Z, logrando que el robot bajara y subiera con precisión en cada punto de la figura, simulando un trazo controlado en el papel.

Esta práctica facilitó una comprensión más profunda del funcionamiento de las funciones como “Pallet”, “Jump3” y “Here” y cómo estas permiten programar trayectorias complejas. Gracias a este ejercicio, se desarrollaron habilidades prácticas en el control de movimientos específicos, útiles para futuras aplicaciones en tareas de precisión en el ámbito industrial.



***Dante Mejía Silva:*** 

La práctica realizada en el laboratorio de robótica permitió aplicar de forma integral los conceptos teóricos estudiados sobre el control y programación de robots industriales. Durante la actividad, se implementaron funciones clave como "Here", "Pallet", "Jump3", etc, que resultaron fundamentales para el trazado preciso de una figura en una cuadrícula predefinida.

En primer lugar, la función Here fue indispensable para establecer puntos de referencia en la programación de movimientos, permitiendo que el robot registrara posiciones clave y ajustara su posición actual en el espacio de trabajo. Esto facilitó la programación de la secuencia sin necesidad de reubicar físicamente el robot, optimizando el proceso de codificación y la precisión de los movimientos.

La función Pallet jugó un papel crucial al permitir la creación de una cuadrícula de puntos distribuidos de manera uniforme en un área determinada, en este caso, una matriz de 10x10. Al definir las esquinas de la cuadrícula mediante puntos de referencia, se logró una disposición controlada y eficiente de los puntos en el espacio, lo cual es esencial para aplicaciones industriales que requieren patrones repetitivos o distribuciones sistemáticas, como en tareas de ensamblaje o empaque.

El comando Jump3 fue fundamental para coordinar movimientos en tres fases, ajustando la posición en el eje Z de manera que el robot pudiera levantar y bajar su herramienta en puntos específicos de la cuadrícula. Este comando permitió al robot "sobrevolar" áreas y luego descender suavemente para trazar en los puntos deseados, garantizando precisión y control en el proceso de dibujo. La incorporación de desplazamientos en el eje Z también contribuyó a evitar colisiones y a asegurar que el robot se moviera con la precisión necesaria al pasar entre puntos de la figura.

En conjunto, esta práctica no solo reforzó la comprensión de las funciones y comandos nuevos del software de Epson RC+, sino que también brindó experiencia en el diseño y ejecución de movimientos complejos en un robot industrial. 

## Referencias Bibliográficas 

[1] 	EpsonCompany, «Especialistas en automatización industrial». 2024, https://www.epson.es/es_ES/robots





















