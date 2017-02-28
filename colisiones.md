 ## Colisiones

Si ya sabemos cómo mover, animar y controlar nuestros sprites, sólo nos falta cómo hacer que interactúen entre ellos.

En particular, suele ser muy útil el concepto de colisión (cuando dos sprites coinciden total o parcialmente en el espacio).

Las colisiones pueden servir para saber cuándo se encuentran dos personajes, cúando un disparo impacta en un objetivo, cuando pasa un coche por la línea de meta...

Para ello tenemos varios métodos en la libería sprite, el principal de los cuales es `collide_rect` y se usa pánsandole como parámetros los dos sprites que queremos comprobar si colisionan del siguiente modo:

```
pygame.sprite.collide_rect(un_sprite, otro_sprite)
```

Esto nos retornará un valor True si los rectángulos del sprite están en contacto y un valor False si no lo están.

A menudo, sobre todo por el uso de transparencias, la imagen de un sprite no coincide visualmente con su redtángulo.

Por ejemplo, en el siguiente dibujo, al ser el sprite circular, las esquinas son transparentes (aquí las vemos en azul):

![imagen.gif](../master/recursos/imagen.gif)

Si dos sprites así colisionaran diagonalmente, sus rectángulos chocarían aunque nosotros viésemos dos círculos que no se tocan. En estos casos, a veces es más conveniente usar métodos de calcular la colisión alternativos.

Por ejemplo, collide_circle es una opción que usa un círculo en lugar del atributo rect del sprite:

```
pygame.sprite.collide_circle(un_sprite, otro_sprite)
```

Para ello, los sprites deben tener un atributo `radius` que se usará como radio de este círculo. Si no existe ese atributo, **Pygame** calculará automáticamente un radio que **contenga** el rect de nuestro sprite (y, por tanto, mayor que este).

La forma de obtener resultados más exactos es usando collide_mask.

collide_mask usa máscaras para calcular las colisiones. Se puede asignar un atributo mask que contenga la máscara o, si este no existe, **Pygame** usará el propio atributo image para ello.

```
pygame.sprite.collide_mask(un_sprite, otro_sprite)
```

En cualquier caso, siempre que sea posible debe usarse preferentemente `collide_rect`, porque es el que menos recursos consume.

Tienes más detalles sobre los métodos de colisión en [la página oficial de la libería sprite](http://www.pygame.org/docs/ref/sprite.html#pygame.sprite.collide_rect).
