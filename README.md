# Game-Coraje — El Archivo

Juego de bombas por niveles, en 8 bits, protagonizado por Coraje. Es la parte
jugable de *El Coleccionista*, un episodio perdido en forma de historieta
interactiva: se leen unas hojas, se juega un nivel, sigue la historia.

Un solo archivo HTML sobre canvas. Sin dependencias, sin build, sin red.

---

## Arrancar

No hay `npm install`. Basta con servirlo por HTTP:

```bash
python3 -m http.server 8080
```

y abrir `http://localhost:8080/index.html`.

Abrirlo con doble clic (`file://`) también funciona, pero es mejor servirlo:
así se comporta igual que dentro de la aplicación, que lo carga por HTTP.

---

## Qué hay

```
index.html                 el juego entero: HTML, CSS, JS y canvas
coraje-atlas.png           Coraje, 6 columnas x 5 filas de 96 px
espantapajaros-atlas.png   enemigo, 4 direcciones x 2 fotogramas de 96 px
bloque-paja.png            bloque destructible
soft-block-crate.png       bloque destructible alterno
```

### Los atlas

`coraje-atlas.png` — 6 x 5 celdas de 96 px:

| fila | contenido |
|---|---|
| 0 | Coraje de frente |
| 1 | de espaldas |
| 2 | de perfil, **mirando a la izquierda** |
| 3 | poses con bomba |
| 4 | bombas y explosión |

Solo existe el perfil izquierdo: para la derecha se dibuja en espejo
(`ctx.scale(-1, 1)`).

`espantapajaros-atlas.png` — 4 x 2 celdas de 96 px. Columnas en el orden
`abajo, arriba, izquierda, derecha`; las dos filas son el ciclo de caminado.

Los dos salieron de recortar hojas de sprites más grandes. Si hay que rehacer
un recorte, pídele al director creativo la hoja original.

---

## Los cinco sellos

El Coleccionista parte en cinco el sistema que retiene a Coraje. Cada nivel es
un tramo de su colección y tiene un objetivo propio; no es "mata todo y sal".

| # | Nivel | Objetivo |
|---|---|---|
| 1 | La Granja Corrupta | Recupera el primer fragmento y encuentra la salida |
| 2 | El Archivo de Criaturas | Libera a quien mantiene capturado |
| 3 | El Pantano Espectral | Recupera el tercer fragmento |
| 4 | *por definir* | |
| 5 | *por definir* | |

Los nombres salen de las páginas de la historieta. Si cambian ahí, cambian aquí.

### Nivel 1 — La Granja Corrupta

**Enemigos**, cada uno con su comportamiento en `ENEMIGOS`:

| | Ritmo | Cómo se mueve | Puntos |
|---|---|---|---|
| Espantapájaros | normal | patrulla recto, gira al chocar | 300 |
| Gallina | rápido | errática, estorba más que mata | 150 |
| Topo | lento | se arrastra pero te busca | 180 |

**Bloques:** piedra indestructible, caja de madera y bala de paja. Cuál toca en
cada casilla se decide con la propia posición, así el tablero se ve variado
pero sale igual cada vez.

**Power-ups:** fuego (explosión más grande), bomba (más bombas a la vez), bota
(más velocidad) y escudo (aguanta un golpe).

---

## Pendiente

**La mecánica de Berenice.** Coraje está dentro del juego y solo ve lo que
tiene alrededor; Berenice está fuera, en una terminal, y ve el mapa completo.
El jugador representa a los dos. Se implementa con niebla de guerra sobre el
tablero más un minimapa que sí lo muestra todo. Es la pieza que le da sentido
narrativo al juego y todavía no existe.

**El escenario pintado.** Hay una maqueta con la granja de fondo —cerca,
granero, molino, luna— y un marco de madera. Ahora mismo el suelo se dibuja por
código. Para montarla hace falta el escenario **sin los bloques del interior**:
los bloques los coloca el juego encima, que es lo que permite destruirlos.

**Sprites propios** para la gallina y el topo. Hoy se dibujan como mapas de
píxeles dentro de `index.html` (ver `BICHOS`), porque no había hoja para ellos.

---

## Reglas

**Nada de red.** El juego es offline. Sin `fetch`, sin CDNs, sin analítica.
Traía un sistema de marcadores contra un servidor externo y se quitó.

**Rutas relativas siempre.** Esto acaba dentro de una APK servida desde otra
raíz. Ni `localhost` ni URLs absolutas.

**Los sprites del director creativo no se redibujan.** No se sustituyen por
formas de canvas ni se recolorean. Si uno no encaja, se mide y se ajusta el
contenedor.

**Nombres en minúsculas, sin espacios.** Android distingue mayúsculas.

**Probar en móvil, no solo en escritorio.** Los controles táctiles ya dieron un
fallo que no se veía con ratón.
