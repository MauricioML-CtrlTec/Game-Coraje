# EL ARCHIVO --- ARCHIVO MAESTRO DEL JUEGO

**Versión:** 1.0  
**Estado:** Documento maestro / fuente de verdad del proyecto  
**Formato visual:** Pixel art 16-bit  
**Uso:** Diseño, desarrollo, arte, integración y control de coherencia.

\---

## 1\. PROPÓSITO DE ESTE ARCHIVO

Este documento concentra las decisiones aprobadas del juego **EL
ARCHIVO**.

Debe utilizarse como referencia principal antes de crear o modificar
escenarios, personajes, enemigos, fragmentos, power-ups, UI o mecánicas.

### Regla principal

> \*\*Todo elemento aprobado se considera canon y no debe rediseñarse
> salvo que se solicite expresamente.\*\*

Cuando se necesite un estado alternativo de un elemento existente ---por
ejemplo, terminal activa, salida abierta o Coraje ladrando--- se
modifica el elemento aprobado; no se inventa otro diseño.

\---

## 2\. CONCEPTO GENERAL

**EL ARCHIVO** es un juego 2D en pixel art 16-bit integrado
narrativamente como un episodio perdido inspirado en el universo de
*Coraje, el perro cobarde*.

Coraje queda atrapado dentro de **El Archivo** y debe recuperar cinco
fragmentos para poder escapar.

Cada nivel posee un fragmento y una mecánica principal diferente.

### Progresión general

Nivel   Mecánica principal   Fragmento   Color

\---

1       BUSCAR               C-001       Morado
2       LIBERAR              C-002       Azul
3       ACTIVAR              C-003       Verde
4       PERSEGUIR            C-004       Amarillo
5       ESCAPAR              C-005       Rojo

Los niveles no deben sentirse como variaciones de la misma misión. Cada
uno tiene una identidad jugable propia.

\---

## 3\. ESTRUCTURA NARRATIVA

La historieta y el juego forman una sola experiencia.

``` text
HISTORIETA
    ↓
Coraje entra / queda atrapado en EL ARCHIVO
    ↓
NIVEL 1 — C-001
    ↓
HISTORIETA
    ↓
NIVEL 2 — C-002
    ↓
HISTORIETA
    ↓
NIVEL 3 — C-003
    ↓
NIVEL 4 — C-004
    ↓
NIVEL 5 — C-005
    ↓
HISTORIETA
    ↓
FINAL DEL EPISODIO
```

**Importante:** Los niveles 3, 4 y 5 se juegan de manera consecutiva
antes del desenlace final de la historieta.

El episodio debe tener un final cerrado; no debe terminar como una
historia que dependa de una continuación.

\---

## 4\. IDENTIDAD VISUAL

### Estilo obligatorio

* Pixel art 16-bit.
* Perspectiva coherente con los mapas aprobados.
* Escala consistente entre personajes, enemigos, bloques y objetos.
* Los assets deben poder integrarse directamente al mapa.
* Evitar renders 3D, concept art moderno o ilustraciones demasiado
detalladas.
* Mantener paletas y siluetas legibles.
* Los elementos interactivos deben reconocerse rápidamente.

### Regla de assets

Los elementos deben entregarse **por separado**.

Un escenario limpio no debe incluir:

* Coraje.
* Enemigos.
* Fragmentos.
* Power-ups.
* Salidas.
* HUD.
* Marcadores.
* Instrucciones.

El nivel se construye como un rompecabezas:

``` text
ESCENARIO
+ BLOQUES / OBJETOS
+ CORAJE
+ ENEMIGOS
+ FRAGMENTO
+ POWER-UPS
+ SALIDA
+ HUD
= NIVEL FINAL
```

Esto permite corregir una pieza sin rehacer el nivel completo.

\---

## 5\. CORAJE

Debe conservar el diseño/sprite aprobado del proyecto.

### Movimientos necesarios

No crear animaciones que no se utilicen.

El set necesario es:

* Idle / quieto.
* Caminar arriba.
* Caminar abajo.
* Caminar izquierda.
* Caminar derecha.
* Ladrar arriba.
* Ladrar abajo.
* Ladrar izquierda.
* Ladrar derecha.

**Coraje no tiene una mecánica independiente de correr.**

La Bota de Muriel aumenta su velocidad de desplazamiento usando las
mismas animaciones de movimiento.

\---

## 6\. CONTROLES

Los controles principales son táctiles en pantalla.

### Pad direccional

* Arriba
* Abajo
* Izquierda
* Derecha

### Botón A --- LADRIDO

Coraje ladra únicamente hacia la dirección que está mirando.

Reglas generales:

* El ladrido viaja hacia adelante.
* Se detiene con obstáculos sólidos.
* Normalmente no elimina enemigos.
* Aturde temporalmente.
* Puede mejorar mediante el Chile de Muriel.

### Botón B --- INTERACTUAR

Se utiliza para acciones contextuales como:

* Activar terminales.
* Recoger fragmentos.
* Interactuar con objetos del escenario.

### Pausa

Pausa el juego.

\---

## 7\. MECÁNICA DEL LADRIDO

El ladrido sustituye completamente la antigua mecánica de bombas.

### Comportamiento general

``` text
BOTÓN A
   ↓
CORAJE LADRA
   ↓
ATAQUE FRONTAL
   ↓
ENEMIGO ALCANZADO
   ↓
ATURDIMIENTO TEMPORAL
```

Los enemigos recuperan su comportamiento normal después del
aturdimiento.

### Excepción

En el Nivel 4, el **Portador C-004** es el único enemigo que recibe
impactos acumulativos y puede ser derrotado mediante cinco ladridos.

\---

## 8\. POWER-UPS OFICIALES

Solo existen tres power-ups oficiales.

### Chile de Muriel

**Función:** mejora el ladrido.

* Mayor alcance.
* Mayor duración del aturdimiento.

### Bota de Muriel

**Función:** aumenta la velocidad de desplazamiento de Coraje.

### Amuleto de Muriel

**Función:** protege a Coraje de un ataque.

### Elementos eliminados

* No existe power-up de bomba.
* No debe reincorporarse la antigua mecánica de bombas.

\---

## 9\. FRAGMENTOS

Todos los fragmentos utilizan **la misma forma/símbolo oficial
establecido en la historieta**.

No deben convertirse en cinco objetos con diseños diferentes.

La identificación se realiza principalmente mediante color.

Fragmento     Nivel Color

\---

C-001             1 Morado
C-002             2 Azul
C-003             3 Verde
C-004             4 Amarillo
C-005             5 Rojo

### Regla visual

La forma permanece constante.

``` text
C-001 = símbolo oficial morado
C-002 = símbolo oficial azul
C-003 = símbolo oficial verde
C-004 = símbolo oficial amarillo
C-005 = símbolo oficial rojo
```

Los efectos y contexto pueden variar según el escenario, pero no la
identidad del fragmento.

\---

# 10\. NIVEL 1 --- INTRODUCCIÓN / GRANJA

**Fragmento:** C-001 --- Morado  
**Función:** Tutorial / introducción  
**Mecánica principal:** BUSCAR

El primer nivel ocurre en la **granja**.

Debe ser sencillo y enseñar al jugador las reglas básicas sin saturarlo.

### Objetivo

Encontrar C-001 y llegar a la salida.

### Secuencia

``` text
INICIO
  ↓
EXPLORAR LA GRANJA
  ↓
ENCONTRAR C-001
  ↓
RECOGER C-001
  ↓
SALIDA ACTIVA
  ↓
SALIR
```

### C-001 dentro de la granja

El fragmento debe integrarse visualmente al entorno rural.

No utilizar:

* Pedestal futurista.
* Plataforma tecnológica.
* Holograma.
* Base sci-fi.

Debe aparecer asociado al suelo de la granja:

* Tierra removida.
* Piedras.
* Raíces.
* Pasto seco.
* Resplandor morado.

Al descubrirlo, C-001 puede elevarse ligeramente desde la tierra y
emitir un brillo tenue.

### Salida

La salida está oculta/debajo de un elemento del mapa.

Tiene dos estados:

* Apagada / encontrada pero bloqueada.
* Encendida / disponible después de obtener C-001.

Debe sentirse como un remolino/energía directamente sobre el suelo y
ocupar buena parte de una casilla.

\---

# 11\. NIVEL 2 --- LIBERACIÓN

**Fragmento:** C-002 --- Azul  
**Mecánica principal:** LIBERAR

C-002 se encuentra encerrado en el centro del escenario.

### Objetivo

Romper los sellos necesarios para liberar C-002.

### Secuencia

``` text
INICIO
  ↓
EXPLORAR
  ↓
LOCALIZAR SELLOS
  ↓
ROMPER SELLOS
  ↓
LIBERAR C-002
  ↓
RECOGER C-002
  ↓
SALIDA
```

### Elementos principales

* Escenario propio.
* Bloques fijos.
* Bloques rompibles cuando correspondan al diseño aprobado.
* Sellos diferenciados visualmente del entorno.
* Enemigos.
* Celda/prisión central de C-002.
* Estado encerrado.
* Estado liberado.
* Salida.

### Identidad

**Nivel 1 = encontrar.**  
**Nivel 2 = liberar.**

\---

# 12\. NIVEL 3 --- LA COLECCIÓN VIVA

**Fragmento:** C-003 --- Verde  
**Mecánica principal:** ACTIVAR  
**Bloques rompibles:** No

C-003 está encerrado en una prisión central.

### Terminales oficiales

Existen exactamente tres terminales:

* **Terminal A --- Verde --- Círculo**
* **Terminal B --- Naranja --- Triángulo**
* **Terminal C --- Azul --- Cuadrado**

Estas identidades son canon y no deben intercambiarse ni rediseñarse.

Cada terminal tiene:

* Estado desactivado.
* Estado activado.

Una terminal activada permanece activada.

### Objetivo

Activar las tres terminales para liberar C-003.

``` text
0/3 = C-003 BLOQUEADO
1/3 = C-003 BLOQUEADO
2/3 = C-003 BLOQUEADO
3/3 = C-003 LIBERADO
```

El orden de activación es libre.

### Enemigos

#### Espécimen Fugado

* Patrulla el escenario.
* Puede ser aturdido.
* No puede eliminarse.

#### Guardián de Contención

* Protege las zonas de terminales.
* Puede ser aturdido.
* No puede eliminarse.

### Secuencia

``` text
INICIO
  ↓
ACTIVAR A / B / C
  ↓
3/3
  ↓
PRISIÓN DESACTIVADA
  ↓
C-003 LIBERADO
  ↓
RECOGER C-003
  ↓
SALIDA ACTIVA
  ↓
NIVEL 4
```

\---

# 13\. NIVEL 4 --- LA CACERÍA

**Fragmento:** C-004 --- Amarillo  
**Mecánica principal:** PERSEGUIR  
**Bloques rompibles:** No

El fragmento está en posesión de un enemigo especial.

### Portador C-004

El Portador comienza el nivel llevando el fragmento amarillo.

Debe mantener estética 16-bit y ser aproximadamente 1.5 veces el tamaño
de Coraje, sin convertirse en un personaje gigante.

### Objetivo

Perseguir al Portador y acertarle cinco ladridos.

``` text
5 → 4 → 3 → 2 → 1 → 0
```

Cada impacto debe producir una reacción visual clara.

Al llegar a cero:

``` text
PORTADOR DERROTADO
       ↓
SUELTA C-004
       ↓
CORAJE RECOGE C-004
       ↓
SALIDA ACTIVA
```

### Rastreadores del Archivo

Son los secuaces del Portador.

Cantidad aproximada: **4--5**.

Comportamiento:

* Patrullan.
* Detectan a Coraje.
* Lo persiguen temporalmente.
* El ladrido los aturde.
* No pueden eliminarse.

Su función es dificultar la persecución, no convertirse en el objetivo
principal.

### Salida

Dos estados:

* Cerrada / bloqueada.
* Abierta / portal dorado activo.

Solo se activa después de recoger C-004.

### Secuencia completa

``` text
INICIO
  ↓
PERSEGUIR PORTADOR
  ↓
5 LADRIDO
  ↓
PORTADOR DERROTADO
  ↓
C-004 CAE
  ↓
RECOGER C-004
  ↓
SALIDA ACTIVA
  ↓
NIVEL 5
```

\---

# 14\. NIVEL 5 --- COLAPSO DEL ARCHIVO

**Fragmento:** C-005 --- Rojo  
**Mecánica principal:** ESCAPAR  
**Enemigos:** No

Es el último nivel jugable.

### Estado inicial

El escenario comienza:

* Limpio.
* Tranquilo.
* Estable.
* Sin enemigos.
* Sin persecución.
* Con C-005 visible y disponible.

El verdadero reto comienza cuando Coraje toma C-005.

### Activación

``` text
CORAJE RECOGE C-005
        ↓
ALARMA
        ↓
SALIDA ACTIVA
        ↓
COMIENZA EL COLAPSO
```

### Colapso

Aparecen progresivamente **bloques de corrupción**.

Estos bloques:

* No pueden destruirse.
* Ocupan casillas.
* Cierran caminos.
* Reducen progresivamente el espacio disponible.
* Siguen una secuencia predefinida.
* No aparecen aleatoriamente.

El diseño debe permitir una ruta de escape si el jugador avanza a
tiempo.

### Objetivo

Llegar a la salida antes de que el mapa quede cerrado.

### Victoria

``` text
C-005
  ↓
COLAPSO
  ↓
HUIDA
  ↓
SALIDA
  ↓
FINAL DEL JUEGO
  ↓
HISTORIETA FINAL
```

### Derrota

Si la corrupción bloquea todas las rutas:

``` text
CORAJE ATRAPADO
      ↓
REINICIAR NIVEL 5
```

### Power-ups

La Bota de Muriel es especialmente útil por el aumento de velocidad.

No es necesario introducir enemigos ni combate.

### Regla temática

**En este nivel, el escenario es el enemigo.**

\---

# 15\. RESUMEN DE RETOS

Nivel   Verbo       Reto                          Condición principal

\---

1       Buscar      Encontrar C-001               Recoger fragmento y salir
2       Liberar     Romper sellos                 Liberar C-002
3       Activar     Activar 3 terminales          Liberar C-003
4       Perseguir   Golpear 5 veces al Portador   Recuperar C-004
5       Escapar     Evitar cierre del escenario   Salir con C-005

\---

# 16\. ESTRUCTURA DE CARPETAS

``` text
EL\_ARCHIVO/
│
├── 00\_DOCUMENTACION/
│   ├── EL\_ARCHIVO\_MASTER.md
│   ├── CONTROLES.txt
│   ├── POWERUPS.txt
│   ├── FRAGMENTOS.txt
│   └── SECUENCIA\_HISTORIA.txt
│
├── 01\_GLOBAL/
│   ├── CORAJE/
│   │   ├── idle/
│   │   ├── movimiento/
│   │   └── ladrido/
│   │
│   ├── CONTROLES/
│   │   ├── pad\_direccional/
│   │   ├── boton\_A/
│   │   └── boton\_B/
│   │
│   ├── POWERUPS/
│   │   ├── chile\_muriel/
│   │   ├── bota\_muriel/
│   │   └── amuleto\_muriel/
│   │
│   ├── FRAGMENTOS/
│   │   ├── C001\_morado/
│   │   ├── C002\_azul/
│   │   ├── C003\_verde/
│   │   ├── C004\_amarillo/
│   │   └── C005\_rojo/
│   │
│   └── EFECTOS/
│       ├── ladrido/
│       ├── aturdimiento/
│       └── recoger\_fragmento/
│
├── 02\_NIVEL\_01/
│   ├── INSTRUCCIONES\_NIVEL\_01.txt
│   ├── escenario/
│   ├── bloques\_fijos/
│   ├── bloques\_rompibles/
│   ├── enemigos/
│   ├── fragmento\_C001/
│   └── salida/
│
├── 03\_NIVEL\_02/
│   ├── INSTRUCCIONES\_NIVEL\_02.txt
│   ├── escenario/
│   ├── bloques/
│   ├── sellos/
│   ├── enemigos/
│   ├── fragmento\_C002/
│   └── salida/
│
├── 04\_NIVEL\_03/
│   ├── INSTRUCCIONES\_NIVEL\_03.txt
│   ├── escenario/
│   ├── terminales/
│   │   ├── terminal\_A\_circulo\_verde/
│   │   ├── terminal\_B\_triangulo\_naranja/
│   │   └── terminal\_C\_cuadrado\_azul/
│   ├── enemigos/
│   │   ├── especimen\_fugado/
│   │   └── guardian\_contencion/
│   ├── fragmento\_C003/
│   │   ├── bloqueado/
│   │   └── liberado/
│   └── salida/
│
├── 05\_NIVEL\_04/
│   ├── INSTRUCCIONES\_NIVEL\_04.txt
│   ├── escenario/
│   ├── portador\_C004/
│   ├── rastreador\_archivo/
│   ├── fragmento\_C004/
│   └── salida/
│
├── 06\_NIVEL\_05/
│   ├── INSTRUCCIONES\_NIVEL\_05.txt
│   ├── escenario/
│   ├── fragmento\_C005/
│   ├── bloques\_corrupcion/
│   ├── secuencia\_colapso/
│   └── salida/
│
├── 07\_UI/
│   ├── marco\_juego/
│   ├── HUD/
│   ├── instrucciones/
│   ├── indicadores/
│   └── pausa/
│
└── 08\_HISTORIETA/
    ├── introduccion/
    ├── transicion\_nivel\_01/
    ├── transicion\_nivel\_02/
    ├── transicion\_nivel\_03/
    └── final/
```

\---

# 17\. CONVENCIÓN RECOMENDADA PARA ASSETS

Para facilitar integración y evitar archivos ambiguos:

``` text
NXX\_TIPO\_NOMBRE\_ESTADO\_DIRECCION\_FRAME.png
```

Ejemplos:

``` text
N03\_TERMINAL\_A\_DESACTIVADA.png
N03\_TERMINAL\_A\_ACTIVADA.png
N04\_PORTADOR\_CAMINAR\_DERECHA\_01.png
N04\_PORTADOR\_IMPACTO\_DERECHA\_01.png
N05\_BLOQUE\_CORRUPCION\_APARICION\_01.png
GLOBAL\_CORAJE\_LADRIDO\_DERECHA\_01.png
GLOBAL\_POWERUP\_CHILE\_MURIEL.png
```

\---

# 18\. ESTADOS IMPORTANTES PARA PROGRAMACIÓN

### Fragmento

``` text
OCULTO / BLOQUEADO
VISIBLE / LIBERADO
RECOGIDO
```

Según el nivel pueden no utilizarse todos.

### Salida

``` text
INACTIVA
ACTIVA
```

### Terminal

``` text
DESACTIVADA
ACTIVADA
```

### Enemigo normal

``` text
IDLE
PATRULLA
DETECCIÓN
PERSECUCIÓN
ATURDIDO
RECUPERACIÓN
```

### Portador

``` text
IDLE
DESPLAZAMIENTO
IMPACTO
5 HITS
4 HITS
3 HITS
2 HITS
1 HIT
DERROTADO
SUELTA C-004
```

### Bloque de corrupción

``` text
NO EXISTE
ADVERTENCIA / APARICIÓN
FORMACIÓN
BLOQUE COMPLETO
```

\---

# 19\. REGLAS DE COHERENCIA --- NO MODIFICAR SIN APROBACIÓN

1. El juego utiliza estética **pixel art 16-bit**.
2. Coraje mantiene el diseño aprobado.
3. No crear animación de correr como mecánica independiente para
Coraje.
4. El ataque principal es el **ladrido frontal**.
5. Las bombas fueron eliminadas.
6. El ladrido normalmente aturde; no elimina enemigos.
7. El Portador C-004 es la excepción y requiere cinco impactos.
8. Existen únicamente tres power-ups oficiales: Chile, Bota y Amuleto
de Muriel.
9. Los cinco fragmentos conservan la misma forma.
10. C-001 morado.
11. C-002 azul.
12. C-003 verde.
13. C-004 amarillo.
14. C-005 rojo.
15. Terminal A = verde / círculo.
16. Terminal B = naranja / triángulo.
17. Terminal C = azul / cuadrado.
18. Nivel 3 no utiliza bloques rompibles.
19. Nivel 4 no utiliza terminales ni sellos.
20. Nivel 5 no utiliza enemigos.
21. El colapso del Nivel 5 no es aleatorio.
22. Los niveles 3, 4 y 5 son consecutivos.
23. Después del Nivel 5 se reproduce el final de la historieta.
24. Los assets se crean separados y se ensamblan posteriormente.
25. No rediseñar un asset aprobado para crear un estado alternativo;
conservar su identidad.

\---

# 20\. CHECKLIST PARA CREAR UN ASSET NUEVO

Antes de aprobar un asset comprobar:

* \[ ] ¿Es realmente necesario para la mecánica?
* \[ ] ¿Respeta pixel art 16-bit?
* \[ ] ¿Respeta la perspectiva del mapa?
* \[ ] ¿Respeta la escala de los assets existentes?
* \[ ] ¿Conserva la identidad aprobada?
* \[ ] ¿Está separado del escenario?
* \[ ] ¿Tiene únicamente los estados/animaciones necesarios?
* \[ ] ¿No introduce una mecánica nueva accidentalmente?
* \[ ] ¿Encaja con el nivel donde será utilizado?
* \[ ] ¿Puede entregarse directamente al desarrollador?

\---

# 21\. FILOSOFÍA DE DISEÑO

La prioridad del proyecto es:

> \*\*Crear únicamente lo necesario para cumplir el objetivo de cada
> nivel.\*\*

No añadir movimientos, enemigos, power-ups, animaciones o sistemas que
no tengan una función concreta.

Cada asset debe responder a una necesidad jugable.

La variedad debe venir de las reglas de los niveles:

``` text
BUSCAR
→ LIBERAR
→ ACTIVAR
→ PERSEGUIR
→ ESCAPAR
```

y no de acumular mecánicas innecesarias.

\---

# 22\. ESTADO ACTUAL

### Nivel 1

Concepto, escenario/granja, fragmento C-001 y salida definidos.

### Nivel 2

Concepto de liberación, sellos, prisión/celda, enemigos y C-002
definidos.

### Nivel 3

Mecánica, escenario, terminales, prisión, enemigos, C-003, ladrido y
salida definidos.

### Nivel 4

Mecánica, escenario, Portador, Rastreadores, C-004 y salida definidos.

### Nivel 5

Mecánica, escenario limpio, C-005 y bloques de corrupción definidos.
Falta continuar detallando visualmente la secuencia final de
colapso/salida según sea necesario.

\---

## FIN DEL ARCHIVO MAESTRO

Este documento debe actualizarse cuando una decisión del proyecto cambie
de forma definitiva.

