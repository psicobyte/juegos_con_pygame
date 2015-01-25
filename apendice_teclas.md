|Constante | Tecla |
|----------|-------|
| K_BACKSPACE | retroceso (backspace) |
| K_TAB | tabulador |
| K_CLEAR | clear [APPLE] |
| K_RETURN | enter (return) |
| K_PAUSE | pausa |
| K_ESCAPE | escape |
| K_SPACE | barra espaciadora |
| K_EXCLAIM | ! exclaim [USA] |
| K_QUOTEDBL | " quotedbl [USA] |
| K_HASH | # hash [USA] |
| K_DOLLAR | $ dollar [USA] |
| K_AMPERSAND | & ampersand [USA] |
| K_QUOTE | quote [USA] |
| K_LEFTPAREN | ( left parenthesis [USA] |
| K_RIGHTPAREN | ) right parenthesis [USA] |
| K_ASTERISK | * asterisk [USA] |
| K_PLUS | + |
| K_COMMA | , |
| K_MINUS | - |
| K_PERIOD | . |
| K_SLASH | / forward slash |
| K_0 | 0 |
| K_1 | 1 |
| K_2 | 2 |
| K_3 | 3 |
| K_4 | 4 |
| K_5 | 5 |
| K_6 | 6 |
| K_7 | 7 |
| K_8 | 8 |
| K_9 | 9 |
| K_COLON | : colon [USA] |
| K_SEMICOLON | ; semicolon [USA] |
| K_LESS | < [USA] |
| K_EQUALS | = equals sign [USA] |
| K_GREATER | > greater-than sign [USA] |
| K_QUESTION | ? question mark [USA] |
| K_AT | @ at [USA] |
| K_LEFTBRACKET | \[ left bracket [USA] |
| K_BACKSLASH | \ backslash [USA] |
| K_RIGHTBRACKET | ] right bracket [USA] |
| K_CARET | ^ caret [USA] |
| K_UNDERSCORE | _ underscore [USA] |
| K_BACKQUOTE | ` grave [USA] |
| K_a | a |
| K_b | b |
| K_c | c |
| K_d | d |
| K_e | e |
| K_f | f |
| K_g | g |
| K_h | h |
| K_i | i |
| K_j | j |
| K_k | k |
| K_l | l |
| K_m | m |
| K_n | n |
| K_o | o |
| K_p | p |
| K_q | q |
| K_r | r |
| K_s | s |
| K_t | t |
| K_u | u |
| K_v | v |
| K_w | w |
| K_x | x |
| K_y | y |
| K_z | z |
| K_DELETE | supr (delete) |
| K_KP0 | 0 (teclado numérico) |
| K_KP1 | 1 (teclado numérico) |
| K_KP2 | 2 (teclado numérico) |
| K_KP3 | 3 (teclado numérico) |
| K_KP4 | 4 (teclado numérico) |
| K_KP5 | 5 (teclado numérico) |
| K_KP6 | 6 (teclado numérico) |
| K_KP7 | 7 (teclado numérico) |
| K_KP8 | 8 (teclado numérico) |
| K_KP9 | 9 (teclado numérico) |
| K_KP_PERIOD | . (teclado numérico) |
| K_KP_DIVIDE | / (teclado numérico) |
| K_KP_MULTIPLY | * (teclado numérico) |
| K_KP_MINUS | - (teclado numérico) |
| K_KP_PLUS | + (teclado numérico) |
| K_KP_ENTER | enter (teclado numérico) |
| K_KP_EQUALS | = (teclado numérico) |
| K_UP | flecha arriba (up) |
| K_DOWN | flecha abajo (down) |
| K_RIGHT | flecha derecha (right) |
| K_LEFT | flecha izquierda (left) |
| K_INSERT | insertar |
| K_HOME | inicio |
| K_END | fin |
| K_PAGEUP | avance página |
| K_PAGEDOWN | retroceso página |
| K_F1 | F1 |
| K_F2 | F2 |
| K_F3 | F3 |
| K_F4 | F4 |
| K_F5 | F5 |
| K_F6 | F6 |
| K_F7 | F7 |
| K_F8 | F8 |
| K_F9 | F9 |
| K_F10 | F10 |
| K_F11 | F11 |
| K_F12 | F12 |
| K_F13 | F13 |
| K_F14 | F14 |
| K_F15 | F15 |
| K_NUMLOCK | bloqueo números |
| K_CAPSLOCK | bloqueo mayúsculas |
| K_SCROLLOCK | scrollock |
| K_RSHIFT | mayúsculas (derecha) |
| K_LSHIFT | mayúsculas (izquierda) |
| K_RCTRL | control (derecha) |
| K_LCTRL | control (izquierda) |
| K_RALT | alt (derecha) |
| K_LALT | alt (izquierda) |
| K_RMETA | meta (derecha) [APPLE] |
| K_LMETA | meta (izquierda) [APPLE] |
| K_LSUPER | tecla windows (izquierda) |
| K_RSUPER | tecla windows (derecha) |
| K_MODE | mode shift |
| K_HELP | help [APPLE] |
| K_PRINT | imprimir pantalla |
| K_SYSREQ | petición del sistema |
| K_BREAK | pausa interna |
| K_MENU | tecla menu |
| K_POWER | power [APPLE] |
| K_EURO | euro ¿? |

Las teclas marcadas con [USA] pertenecen a la distribución de teclas estadounidense, y no aparecen en el teclado en español. Las teclas marcadas como [APPLE] son propias de los teclados de Apple. Dado que estas constantes están concebidas para la distribución de teclado de Estados Unidos no hay constantes definidas para referise a teclas carácterísticas del teclado español.

Para acceder a otras teclas se puede usar directamente el valor numérico de la tecla, como por ejemplo:

| Código | Tecla |
|----------|-------|
| 39 | ' |
| 161 | ¡ |
| 186 | º |
| 231 | ç |
| 241 | ñ |

Otra opción para identificar la tecla pulsada es usar los valores unicode, aunque esto distinguirá entre mayúculas y minúsculas.

Es importante recordar que algunas teclas no aparecerán o se mostrarán de modo distinto en algunos teclados (por ejemplo, en teclados de ordenadores portátiles). Además, ciertas teclas como "imprimir pantalla", normalmente, son capturadas por el sistema operativo. Es mejor evitar el uso de estas en nuestros juegos.
