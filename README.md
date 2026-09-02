# Market CAPo

**Un roguelite satírico de carrera corpo.** Elegí tus orígenes y estilo. Conseguite un laburo honesto, hacete de abajo, aguantá los puestos que te toquen, año a año, hasta llegar al directorio. O hasta el corchazo.

🎮 **Jugar: [untaladro.github.io/mc](https://untaladro.github.io/mc/)**

---

## Qué es

Empezás a los 22 con un origen sorteado entre ocho (el que hizo un MBA, el que volvió de Miami, el hijo del proveedor del Estado, el que fundió su startup) y jugás una carrera entera hasta la jubilación — o hasta que algo la corte antes. Cada año elegís entre las ofertas que el mercado te da, aguantás eventos que no controlás, y decidís qué hacer con la plata que juntaste.

No hay forma de ganar. Hay catorce formas de terminar, y el juego te escribe un epitafio con lo que efectivamente hiciste.

## Cómo correrlo

No hay build, no hay dependencias, no hay servidor.

```
git clone https://github.com/untaladro/mc.git
cd mc
```

Y abrí `index.html` en el navegador. Eso es todo.

El juego es **un solo archivo HTML** con el CSS y el JavaScript adentro. Se puede servir desde cualquier lado o abrir con `file://`; guarda la partida en `localStorage` y no necesita conexión para jugar.

## Estructura

```
index.html                    el juego entero
og-image.png                  imagen de las tarjetas al compartir (1200×630)
market-capo-icon.svg          la marca
favicon.ico                   íconos
favicon-16x16.png
favicon-32x32.png
apple-touch-icon.png
android-chrome-192x192.png
android-chrome-512x512.png
```

## Configuración

Todo lo configurable son constantes al principio del `<script>`, y **cada una se apaga sola si la dejás vacía**:

| Constante | Qué hace | Si la vaciás |
|---|---|---|
| `UMAMI_ID` | Analítica sin cookies | No se hace ni un pedido de red |
| `DONACION_URL` | Link de donación | El bloque no se renderiza |
| `DONACION_TEXTO` | Texto del botón | — |
| `URL_JUEGO` / `URL_JUEGO_FULL` | La URL que se dibuja en la tarjeta compartible | — |

Si clonás esto para tu propia versión, **vaciá `UMAMI_ID` y `DONACION_URL`**: son de este proyecto y si no vas a estar mandando tus datos y tus donaciones al lugar equivocado.

**Ojo con la URL:** si cambiás `URL_JUEGO`, `og-image.png` **no** se actualiza sola — la dirección está pintada en píxeles adentro de la imagen y hay que regenerarla. La tarjeta del epitafio sí se dibuja en runtime y se arregla sola.

## Notas técnicas

- **Sin librerías.** La tarjeta compartible se dibuja a mano con Canvas 2D. Todo su armado es sincrónico a propósito: un solo `await` antes de `clipboard.write()` hace que Safari dé por perdido el gesto del usuario y el botón deja de funcionar.
- **Compartir tiene cuatro caminos** con su propio cartel honesto cada uno: celular → menú nativo; escritorio → portapapeles; si falla → descarga del PNG; último recurso → texto plano, y lo dice.
- **El OVR es una fórmula, no un número guardado.** Sale de la especialidad más alta, los cuatro atributos, los años de experiencia y el prestigio, con un techo blando en 65 donde cada punto pasa a costar el doble. Nada le suma por fuera.
- **La analítica no manda el nombre del jugador**, que es texto libre y podría ser real.

## Créditos

Una idea de **[@un_taladro](https://x.com/un_taladro)** tercerizando a Claude y Gemini. Los errores son míos.

## Licencia

[MIT](LICENSE). Hacé lo que quieras con esto — usalo, cambialo, publicá tu versión, vendelo si te sirve — con solo mantener el aviso de copyright.

Si hacés algo con esto, me encantaría verlo.
