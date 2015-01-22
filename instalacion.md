##Instalación

**Pygame** está desarrollado sobre **Python 2.7.X**, que es el que se usara en los ejemplos de este libro, aunque también hay una versión (ligeramente más limitada en algunos aspectos) para **Python 3.X**.

Además de **Python**, naturalmente, hace falta instalar el propio **Pygame**.

En general, **Pygame** se instala como cualquier otro módulo de **Python**. En ordenadores con sistema operativo GNU/Linux, por ejemplo, puede instalarse desde los propios repositorios de la distribución.

Para distribuciones basadas en Debian (Ubuntu, Linux Mint), necesitaremos instalar el paquete *python-pygame*. `apt-get` se encargara de instalar las dependencias necesarias.

```
# apt-get install python-pygame
```

En Archlinux se puede instalar con el gestor de paquetes `pacman` del siguente modo:

```bash
# pacman -S python2-pygame
```
para la versón de **Python 2.7.X**

O con:

```
# pacman -S python-pygame-hg
```
para la versión de **Python 3.X**


En Fedora (y Red Hat), usando `yum`:

```
# yum install python-pygame
```

> Naturalmente, es necesario tener permisos de *superusuario* para instalar paquetes. Por lo que, dependiendo del sistema, será necesario entrar como root o ejecutar `sudo`.


Para instalar **Pygame** en Windows sólo hay que acceder a la [página de descargas oficial de Pygame](http://www.pygame.org/download.shtml) y descargar el archivo de instalación (*\*.msi*) correspondiente. Una vez descargado, sólo hay que ejecutarlo como cualquier otra instalación de software para Windows.

> Existe una versión de 64 bits que actualmente está en fase de *pre release*. Al estar aún en pruebas y no ser completamente funcional, es preferible utilizar la versión de 32 bits, para lo que es necesario que la versión instalada de **Python** también sea de 32 bits.


En Macintosh se puede instalar **Pygame** ejecutando el archivo de instalación (*\*.dmg*) disponible en la [página de descargas oficial de Pygame](http://www.pygame.org/download.shtml).

Como cualquier otro módulo de **Python**, también es posible instalarlo en cualquier sistema operativo usando `pip` de este modo:

```
# pip install pygame
```


