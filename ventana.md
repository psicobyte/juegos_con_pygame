#Ventana



Lo primero que haremos para mejorar nuestro ejemplo será hacer que nuestra ventana se cierre al pulsar el botón X de la propia ventana. Para ello tenemos que responder al evento QUIT de modo parecido a como hicimos con la pulsación de teclas:

``` {.python .numberLines}
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
pygame.display.set_caption("Hola. Pulsa Escape para salir")

# Bucle infinito para mantener el programa en ejecución
while True:
    # Manejador de eventos
    for evento in pygame.event.get():
        # Pulsación de la tecla escape
        if evento.type == pygame.KEYDOWN and evento.key == pygame.K_ESCAPE:
            sys.exit()
        # Botón de cerrar ventana
        if evento.type == QUIT:
            sys.exit()
```



Hemos usado `pygame.display.set_mode((600, 400))`, pasándole como parámetro una *tupla* (se puede usar también una *lista*) con las dimensiones del ancho y el alto, para crear la ventana. Cambiando esos valores obtendremos ventanas de distintas proporciones.

Pero nuestra ventana tiene un tamaño fijo y no es posible cambiarlo. Para ello tenemos otro parámetro (la constante de **Pygame** `pygame.RESIZABLE`) que podemos añadir a continuación del tamaño de este modo:

``` {.python .numberLines}
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
ventana = pygame.display.set_mode((600, 400), pygame.RESIZABLE)

# Le ponemos un título a la ventana
pygame.display.set_caption("Ventana elástica")

# Bucle infinito para mantener el programa en ejecución
while True:
    # Manejador de eventos
    for evento in pygame.event.get():
        # Pulsación de la tecla escape
        if evento.type == pygame.KEYDOWN and evento.key == pygame.K_ESCAPE:
            sys.exit()
        # Botón de cerrar ventana
        if evento.type == QUIT:
            sys.exit()
```

Esta no es la única constante que podemos usar para definir la ventana de juego, podemos activar cosas como al aceleración gráfica o el soporte de OpenGl:

Constante | uso
---|---
pygame.FULLSCREEN | en lugar de en una ventana, el juego se ejecutará a pantalla completa.
pygame.DOUBLEBUF | activa el doble buffer, recomendable para HWSURFACE u OPENGL.
pygame.HWSURFACE | usa aceleración por hardaware, sólo tienen sentido en FULLSCREEN.
pygame.OPENGL | activa el uso de OpenGL.
pygame.RESIZABLE | como ya jemos visto, permite cambiar el tamaño de ventana.
pygame.NOFRAME | elimina todos los elementos decorativos de la ventana (bordes, cabecera...).

Para usar más de una de estas constantes se debe usar el signo "|" como separador, por ejemplo:

pygame.display.set_mode((600, 400), pygame.FULLSCREEN | pygame.DOUBLEBUF | pygame.HWSURFACE)
