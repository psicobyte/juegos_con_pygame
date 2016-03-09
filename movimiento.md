##Movimiento

Dado lo que hemos visto en el tema anterior, mover una imagen no es nada complicado: Sólo hay que cambiar sus coordenadas y redibujarla.

Un detalle importante es que no estamos moviendo nada, simplemente estamos volviendo a dibujar el objeto en otra posición ¡Pero no desaparece del lugar donde estaba dibujado antes!

Esto quiere decir que, a cada ciclo de nuestro bucle, debemos redibujar el fondo y todos y cada uno de los objetos.

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-

# Importamos la librería
import pygame

import sys

# Importamos constantes locales de pygame
from pygame.locals import *

# Iniciamos Pygame
pygame.init()

# Creamos una surface (la ventana de juego), asignándole un alto y un ancho
ventana = pygame.display.set_mode((600, 400))

# Le ponemos un título a la ventana
pygame.display.set_caption("Moviendo Imágenes")

# Cargamos las imágenes
fondo = pygame.image.load("fondo.jpg")
imagen = pygame.image.load("imagen.png")

coordX = 300
coordY = 200
coordenadas = (coordX, coordY)

# Bucle infinito para mantener el programa en ejecución
while True:

    ventana.blit(fondo, (0, 0))
    ventana.blit(imagen, coordenadas)
    pygame.display.flip()

    # Manejador de eventos
    for evento in pygame.event.get():
        # Pulsación de la tecla escape
        if evento.type == pygame.KEYDOWN:
            if evento.key == pygame.K_ESCAPE:
                sys.exit()

            elif evento.key == pygame.K_RIGHT:
                coordX = coordX + 5
            elif evento.key == pygame.K_DOWN:
                coordY = coordY + 5
            elif evento.key == pygame.K_LEFT:
                coordX = coordX - 5
            elif evento.key == pygame.K_UP:
                coordY = coordY - 5
    coordenadas = (coordX, coordY)
```

Vale. Nuestro programa (que es casi el mismo del tema anterior) está creciendo y empieza a ser lo suficientemente complejo para ir necesitando que estructuremos el código, con sus funciones y sus clases, pero para estos ejemplos nos hace el apaño.

Las únicas diferencias sobre los ejemplos del tema anterior son:

* Hemos definido las coordenadas de "imagen" en un par de variables ("coordX" y "coordY"), para poder modificarlas cómodamente al recibir la pulsación de la tecla correspondiente.
* Hemos añadido el control para las interrupciones de teclado de las teclas de flecha.
* Ahora redibujamos "fondo" e "imagen" en cada ciclo de nuestro bucle (prueba a sacar ese `ventana.blit(Fondo, (0, 0))` y ponerlo *antes* de iniciar el bucle).

Un detalle importante es que, como el evento `KEYDOWN` ocurre al *pulsar* una tecla, "imagen" se mueve dando un "paso" cada vez que se pulsa. Si queremos que el movimiento sea contínuo, se puede hacer con un sistema de flags parecido al siguiente:

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-

# Importamos la librería
import pygame

import sys

# Importamos constantes locales de pygame
from pygame.locals import *

# Iniciamos Pygame
pygame.init()

# Creamos una surface (la ventana de juego), asignándole un alto y un ancho
ventana = pygame.display.set_mode((600, 400))

# Le ponemos un título a la ventana
pygame.display.set_caption("Moviendo Imágenes")

# Cargamos las imágenes
fondo = pygame.image.load("fondo.jpg")
imagen = pygame.image.load("imagen.png")

coordX = 300
coordY = 200
coordenadas = (coordX, coordY)

incrementoX = 0
incrementoY = 0

# Bucle infinito para mantener el programa en ejecución
while True:

    ventana.blit(fondo, (0, 0))
    ventana.blit(imagen, coordenadas)
    pygame.display.flip()

   # Manejador de eventos
    for evento in pygame.event.get():
        # Pulsación de la tecla escape
        if evento.type == pygame.KEYDOWN:
            if evento.key == pygame.K_ESCAPE:
                sys.exit()
            elif evento.key == pygame.K_RIGHT:
                incrementoX = 5
            elif evento.key == pygame.K_DOWN:
                incrementoY = 5
            elif evento.key == pygame.K_LEFT:
                incrementoX = -5
            elif evento.key == pygame.K_UP:
                incrementoY = -5
        if evento.type == pygame.KEYUP:
            incrementoX = 0
            incrementoY = 0

    coordX = coordX + incrementoX
    coordY = coordY + incrementoY

    coordenadas = (coordX, coordY)
```
Bueno, quizás no es mu elegante, pero es sencillo y deberías pararte un momento y verlo detenidamente para asegurarte de que lo entiendes.

Aunque posiblemente aún no nos hayamos dado cuenta, tenemos otro problema.

Dado que incrementamos las coordenadas en una cantidad fija a cada ciclo del bucle, la velocidad resultante depende de la velocidad a la que se complete el ciclo, y esta puede variar dependiendo del procesador, la carga del sistema, lo que esté haciendo nuestro programa en cada ciclo, etc.

¿Hay una forma de asegurarnos que la velocidad es constante independientemente de las circunstancias?

Bueno, si el procesador donde se ejecuta es muy lento o la máquina está muy sobrecargada, va a ser difícil hacer que vaya más rápido, pero sí podemos limitar la velocidad para que no exceda de cierto nivel.

Para esto (y para más cosas) tenemos la clase de **Pygame** `Clock`, que se llama del siguiente modo:

```
reloj= pygame.time.Clock()
```

y nos retorna un reloj que podemos usar para muchas cosas, entre las que está establecer un *tic*, un tiempo en milisegundos que limita la velocidad a la que se procesa nuestro bucle principal. Por ejemplo:

```
#!/usr/bin/env python
# -*- coding: utf-8 -*-

# Importamos la librería
import pygame

import sys

# Creamos un reloj
reloj= pygame.time.Clock()


# Importamos constantes locales de pygame
from pygame.locals import *

# Iniciamos Pygame
pygame.init()

# Creamos una surface (la ventana de juego), asignándole un alto y un ancho
ventana = pygame.display.set_mode((600, 400))

# Le ponemos un título a la ventana
pygame.display.set_caption("Moviendo Imágenes")

# Cargamos las imágenes
fondo = pygame.image.load("fondo.jpg")
imagen = pygame.image.load("imagen.png")

coordX = 300
coordY = 200
coordenadas = (coordX, coordY)

incrementoX = 0
incrementoY = 0

# Bucle infinito para mantener el programa en ejecución
while True:

    ventana.blit(fondo, (0, 0))
    ventana.blit(imagen, coordenadas)
    pygame.display.flip()

   # Manejador de eventos
    for evento in pygame.event.get():
        # Pulsación de la tecla escape
        if evento.type == pygame.KEYDOWN:
            if evento.key == pygame.K_ESCAPE:
                sys.exit()
            elif evento.key == pygame.K_RIGHT:
                incrementoX = 5
            elif evento.key == pygame.K_DOWN:
                incrementoY = 5
            elif evento.key == pygame.K_LEFT:
                incrementoX = -5
            elif evento.key == pygame.K_UP:
                incrementoY = -5
        if evento.type == pygame.KEYUP:
            incrementoX = 0
            incrementoY = 0

    coordX = coordX + incrementoX
    coordY = coordY + incrementoY

    coordenadas = (coordX, coordY)

    # Asignamos un "tic" de 30 milisegundos
    reloj.tick(30)
```

Fíjate que, en este ejemplo, creamos un reloj al principio del programa y le ponemos el tic de 30 milisegundos dentro del bucle (al final).

> Puedes cambiar el tiempo del tic y experimentar con los resultados.

Podemos usar este reloj para muchas otras cosas, como contar el tiempo (lógicamente), sincronizar eventos, hacer animaciones...

> Puedes ver más detalles en la [documentación oficial del módulo "time" de pygame](http://www.pygame.org/docs/ref/time.html)
