Materiales de ingenieria / Engineering materials
====

# Español

I. Objetivo del Código:

Nuestro objetivo al desarrollar este código es dotar al vehículo con la capacidad de navegar de manera autónoma en una pista, utilizando sensores ultrasónicos y un servo para tomar decisiones y ajustar su movimiento.

II. Estructura del Código:

Presentamos el código en varias secciones clave:

Importación de Librerías: Aquí, importamos las librerías necesarias para controlar el servo, la comunicación I2C y la pantalla LCD.
Declaración de Variables: Definimos variables que almacenan valores relevantes como distancias, velocidades y ángulos.
Funciones Personalizadas: Creamos funciones personalizadas, como la que mide la distancia ultrasónica y aquellas que gestionan la presentación de datos en la pantalla LCD.
Configuración Inicial: En la función setup(), configuramos los pines y establecemos valores iniciales.
Bucle Principal: La lógica principal del vehículo reside aquí:
Medimos distancias usando sensores ultrasónicos.
Controlamos el movimiento del vehículo mediante motores y un servo.
Actualizamos la información en la pantalla LCD.

III. Funciones Clave:

Destacamos algunas funciones importantes:

fnc_ultrasonic_distance: Mide distancias utilizando un sensor ultrasónico y devuelve valores en centímetros.
adelante, giro_derecho, giro_izquierda, retroceder: Funciones que controlan el movimiento del vehículo y el servo.
datos_en_pista, datos_en_calculo: Funciones que presentan información relevante en la pantalla LCD.

IV. Proceso de Desarrollo:

Para construir y utilizar este código:

Configuramos el entorno de desarrollo, como Arduino IDE.
Conectamos componentes como sensores ultrasónicos, motores y la pantalla LCD según las especificaciones del código.
Escribimos y editamos el código en Arduino IDE.
Compilamos el código y lo cargamos en el microcontrolador del vehículo usando un cable de programación.
Al encender el vehículo, seguirá las instrucciones del código y se moverá de manera autónoma en la pista.

V. Conclusiones:

El código presentado es el núcleo de nuestro vehículo autónomo.
Permite que el vehículo tome decisiones informadas basadas en datos recopilados por sus sensores.
La integración precisa de funciones, variables y decisiones lo convierte en un sistema autónomo eficiente y capaz.

# English

I. Code Objective:

Our objective in developing this code is to equip the vehicle with the ability to navigate autonomously on a track, utilizing ultrasonic sensors and a servo to make decisions and adjust its movement.

II. Code Structure:

We present the code in several key sections:

Library Imports: Here, we import the necessary libraries to control the servo, I2C communication, and the LCD screen.
Variable Declarations: We define variables that store relevant values such as distances, speeds, and angles.
Custom Functions: We create custom functions, such as the one measuring ultrasonic distance and those managing data presentation on the LCD screen.
Initial Configuration: In the setup() function, we configure pins and establish initial values.
Main Loop: The main logic of the vehicle resides here:
We read distances using ultrasonic sensors.
We control vehicle movement using motors and a servo.
We update information on the LCD screen.

III. Key Functions:

We highlight some important functions:

fnc_ultrasonic_distance: Measures distances using an ultrasonic sensor and returns values in centimeters.
forward, turn_right, turn_left, reverse: Functions controlling vehicle movement and the servo.
data_on_track, data_in_calculation: Functions presenting relevant information on the LCD screen.

IV. Development Process:

To build and use this code:

Set up the development environment, such as the Arduino IDE.
Connect components like ultrasonic sensors, motors, and the LCD screen as per the code's specifications.
Write and edit the code in the Arduino IDE.
Compile the code and load it onto the vehicle's microcontroller using a programming cable.
Upon powering the vehicle, it will follow the code's instructions and autonomously move along the track.

V. Conclusions:

The presented code is the backbone of our autonomous vehicle.
It enables the vehicle to make informed decisions based on data collected by its sensors.
The precise integration of functions, variables, and decisions transforms it into an efficient and capable autonomous system.
