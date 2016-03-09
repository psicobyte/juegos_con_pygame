# Ventana

En el capítulo anterior hemos creado nuestra primera ventana usando la librería `display`.

En principio, el primer método de esta libreŕia que se debería usar es `display.init()`, que sirve para iniciarla. Sin embargo, `display` ya se inicia automáticamente al hacer `pygame.init()`, por lo que no suele ser necesario utilizarlo.

El siguiente paso es crear nuestra ventana que, como hemos visto, se hace con `display.set_mode()`, pasándole como parámetro una *tupla* (se puede usar también una *lista*) con las dimensiones en *pixels* del ancho y el alto (en ese orden), para crear la ventana. Cambiando esos valores obtendremos ventanas de distintas proporciones.

> Un *pixel* es un punto en la pantalla. Más adelante veremos esto con más detalle.

Lo primero que haremos para mejorar nuestro ejemplo será hacer que la ventana se cierre al pulsar el botón "X" de la propia ventana. Para ello tenemos que responder al evento `QUIT` de modo parecido a como hicimos con la pulsación de teclas:

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

En un juego de verdad, lo más probable es que, para finalizar, llamásemos a una función que pida confirmación al jugador, guarde lo que haya que guardar, etc. Pero, para nuestro pequeño ejemplo, llamar a `sys.exit()` es suficiente.

> **Pygame** no puede tener más de un objeto `display` al mismo tiempo. Si intentas crear una ventana en tu programa con `display.set_mode()` cuando ya existe otra, la nueva reemplazará a la anterior.

Pero nuestra ventana tiene un tamaño fijo y no es posible cambiarlo. Para poder hacerlo tenemos un *flag*, otro parámetro (la constante de **Pygame** `pygame.RESIZABLE`) que podemos añadir a continuación del tamaño de este modo:

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
`pygame.FULLSCREEN` | en lugar de en una ventana, el juego se ejecutará a pantalla completa.
`pygame.DOUBLEBUF` | activa el doble buffer, recomendable para HWSURFACE u OPENGL.
`pygame.HWSURFACE` | usa aceleración por hardaware, sólo tienen sentido en FULLSCREEN.
`pygame.OPENGL` | activa el soporte de OpenGL.
`pygame.RESIZABLE` | como ya jemos visto, permite cambiar el tamaño de ventana.
`pygame.NOFRAME` | elimina todos los elementos decorativos de la ventana (bordes, cabecera...).

Para usar más de una de estas constantes se debe usar el signo "|" como separador, por ejemplo:

``` {.python .numberLines}
# Pantalla completa, con aceleración por hardware y doble buffer
pygame.display.set_mode((600, 400), pygame.FULLSCREEN | pygame.DOUBLEBUF | pygame.HWSURFACE)
```

Para saber si un modo de display está disponible en el hardware en el que se está ejecutando nuestro juego, tenemos la función `pygame.display.mode_ok()`. Esta función admite los mismos parámetros que `display.set_mode()`, y retorna un número entero indicando la mejor profundidad de color para esos parámetros. En caso de que ese modo de display no sea soportado por el hardware, la función retorna un valor cero. El principal uso de esta función es para asegurarnos la validez de flags como `pygame.HWSURFACE` o `pygame.DOUBLEBUF`.
