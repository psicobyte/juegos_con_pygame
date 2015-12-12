##¡Hola Pygame!

Vamos a dar nuestros primeros pasos en la programación de videojuegos con **Pygame** usando un clásico "Hola Mundo".

``` {.python .numberLines}
#!/usr/bin/env python
# -*- coding: utf-8 -*-

# Importamos la librería
import pygame

# Iniciamos Pygame
pygame.init()

# Creamos una surface (la ventana de juego), asignándole un alto y un ancho
ventana = pygame.display.set_mode((600, 400))

# Le ponemos un título a la ventana
pygame.display.set_caption("Hola Mundo")
```

Como se puede leer en los comentarios (y cómo deberías comprobar ejecutándolo), este código crea una ventana de 600X400 pixels y le asigna un título.

Tras importar el módulo, el primer método que ejecuta nuestro ejemplo es `pygame.init()`, que iniciará  **Pygame** y nos permitirá usar sus funciones y métodos.

> El módulo `pygame.display` es el encargado de crear y controlar la ventana y la pantalla de juego que contiene (que, a efectos prácticos, es un objeto `surface` (una imagen), como veremos más adelante.
> Nosotros hemos creado una ventana muy simple, pero puedes ver más posibilidades en el siguiente capítulo.

Al ejecutar este ejemplo comprobarás que, inmediatamente, la ejecución del programa finaliza y esta ventana se cierra.

Para poder manejar nuestro programa, necesitaremos un bucle de eventos. Un bucle de eventos es un bucle infinito donde, a cada ciclo, comprobamos si ocurre algún envento y actuamos en consecuencia. El programa permanecerá en ejecución mientras permanezca en el bucle.

Veamoslo con un ejemplo algo más complejo:

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
```

> [RECORDATORIO] `while True` creará un bucle que se ejecuta contínuamente hasta que se sale de él con una instrucción 
`break` o se finaliza el programa por otro medio (como, por ejemplo, con `sys.exit()`).

Para empezar, debes notar que estamos importando `pygame.locals` justo después de importar la librería `pygame` (Bueno, también hemos importado `sys`, pero esa librería no debería necesitar explicación).

Se trata de una serie de constantes que contienen los códigos para poder acceder a las teclas, eventos de ratón, etc, y que usaremos como *alias* para referirnos a ellos. En nuestro ejemplo usaremos la tecla Escape.

> Los nombres de las constantes de tecla están siempre formados por el prefijo "K\_" seguido de la tecla a la que se refiere. Por ejemplo `K\_a`, `K\_f`, `K\_ESCAPE` o `K\_UP`.

En este ejemplo usamos un bucle infinito (normalmente llamado bucle de eventos o *event loop*) que mantiene el programa en ejecución, por lo que nuestra ventana no se cierra.

En cada ciclo del bucle infinito estamos usando pygame.event.get(), que nos retorna los eventos de **Pygame** que estén ocurriendo.

Si el tipo de evento es una pulsación de tecla (al que accedemos con la constante de **Pygame** `KEYDOWN`) y esa tecla es Escape (`K_ESCAPE`), salimos del programa.

Por otro lado notarás que, si tratas de cerrarla pulsando el botón de cerrar de la propia ventana, esto no funciona.

Como práctica, puedes intentar hacer que funcione teniendo en cuenta que la constante de **Pygame** correspondiente a pulsar ese botón es `QUIT`.

Como ya te estarás imaginado, prácticamente toda la interacción que hagamos con nuestro juego en **Pygame** se hará por medio de eventos.

Puedes verlos todos en esta [lista completa de eventos de pygame](http://www.pygame.org/docs/ref/event.html)

> Como veremos más adelante, todos nuestros juegos con **Pygame** van a tener un bucle de eventos con la misma estructura básica. similar a esto:

> Comprobar eventos

> Hacer cosas en base a esos eventos

> Redibujar la pantalla

> Y vuelta a empezar...

