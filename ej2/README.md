Objetivo:
Crear un juego en el que una bola (canica) se mueve por la pantalla en función de la inclinación del dispositivo (pitch y roll), con el objetivo de alcanzar un destino fijo.


Funcionamiento:

Al pulsar el botón "Iniciar Sensores y Jugar", se solicita permiso para acceder a los sensores de orientación (necesario en iOS). En navegadores que no lo requieren, se inicia directamente.

Se añade un listener para el evento deviceorientation, que proporciona los ángulos beta (inclinación adelante/atrás, almacenado en pitch) y gamma (inclinación izquierda/derecha, almacenado en roll). Los valores se limitan a ±45 grados para una jugabilidad más estable.

En un bucle continuo con requestAnimationFrame, se actualiza la posición de la bola sumando un factor de velocidad multiplicado por los valores de inclinación. Esto permite un movimiento suave y proporcional.

Se aplican límites (usando Math.max y Math.min) para que la bola no se salga del tablero de juego.

Se comprueba la colisión con el destino (círculo verde) calculando la distancia euclídea entre los centros. Si la distancia es menor que la suma de los radios (bola: 15px, destino: 20px, total 35px), se considera que el objetivo ha sido alcanzado.

Al alcanzar el destino:

La bola cambia a color verde.

Se activa una vibración de 200 ms si el dispositivo lo soporta (navigator.vibrate).

Se muestra un mensaje de éxito (alert) y se reinicia la posición de la bola al punto de partida.

El juego se pausa automáticamente cuando la pestaña del navegador pierde visibilidad (evento visibilitychange) y se reanuda al volver.