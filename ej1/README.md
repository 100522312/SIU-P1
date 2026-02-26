Objetivo:
Desarrollar un prototipo de aplicación móvil que permita al usuario fijar un destino en un mapa y recibir una notificación cuando se encuentre cerca de ese punto.


Funcionamiento:

Se inicializa un mapa centrado en Madrid (coordenadas por defecto) con capas de OpenStreetMap usando la librería Leaflet.

El usuario hace clic en el mapa para establecer un destino. Se coloca un marcador con un emoji 📍 en esa posición.

El dispositivo comienza a rastrear la posición del usuario mediante watchPosition con alta precisión (enableHighAccuracy: true).

Cada vez que se obtiene una nueva ubicación, se actualiza un marcador circular azul que representa al usuario y un círculo semitransparente que indica la precisión de la medición.

Se calcula la distancia entre la posición actual y el destino usando el método distanceTo de Leaflet.

La interfaz muestra continuamente la distancia, una barra de progreso que se llena a medida que el usuario se acerca y el estado actual.

Si la distancia es inferior a 50 metros y no se ha notificado previamente, se muestra un toast emergente y se envía una notificación del sistema (solicitando permiso si es necesario). Además, el marcador de destino cambia a una bandera 🏁.

Para evitar notificaciones repetidas, se usa una bandera hasBeenNotified que se reinicia al cambiar el destino.

El panel inferior incluye botones para centrar el mapa en la ubicación del usuario y para limpiar el destino actual.