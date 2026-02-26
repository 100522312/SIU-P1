Objetivo:
Implementar un gesto táctil con dos dedos que permita ampliar, reducir y rotar una imagen en dispositivos móviles.


Funcionamiento:

Se configura la vista para que el navegador no aplique zoom nativo (user-scalable=no en el viewport) y se previene el zoom con doble tap mediante un manejador de eventos.

En el evento touchstart con exactamente dos dedos:

Se calcula la distancia inicial entre los dos puntos táctiles (getDistance, usando el teorema de Pitágoras).

Se calcula el ángulo inicial de la línea que forman (getAngle, usando Math.atan2).

Se guardan estos valores junto con la escala y rotación actuales (variables baseScale y baseRotation).

Durante el evento touchmove (también con dos dedos):

Se calculan la nueva distancia y el nuevo ángulo.

El factor de escala se obtiene como nuevaDistancia / distanciaInicial. La escala actual se calcula como baseScale * factor.

La rotación se obtiene como la diferencia entre el ángulo actual y el inicial, sumada a la rotación base.

Se limitan los valores de escala entre 0.3 y 5 para evitar que la imagen desaparezca o se agrande excesivamente.

Se aplica la transformación CSS combinada scale() y rotate() a la imagen mediante style.transform.

Al finalizar el gesto (touchend o touchcancel):

Se actualizan las variables baseScale y baseRotation con los valores actuales, de modo que el siguiente gesto continúe desde el estado actual.

La interfaz incluye un panel de depuración que muestra en tiempo real la escala y rotación aplicadas, y un botón para resetear la imagen a su estado original (escala 1, rotación 0).