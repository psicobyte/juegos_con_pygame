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



