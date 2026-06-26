# reiteración

Instalación basada en pieza construida en p5.js

Ejecutar en <https://misaaaaaa.github.io/reiteracion/>

Una versión fue montada en agosto de 2025 en la exposición [Cuando todas las palabras sean borradas](https://misaa.cc/projects/cuandotodaslaspalabras.html)

![imagen de instalación](./imagenes/reiteracion.png)

---

## Descripción

*Reiteración* es una instalación audiovisual de raíz generativa, basada en una figura bidimensional ahogada en un monitor antiguo, sostenido gracias a fuerzas elásticas y de gravedad. Construida con **p5.js** y **p5.sound**. La pieza dibuja un cuadrilátero cuyos cuatro vértices se desplazan de forma autónoma por el canvas, rebotando en los márgenes de la pantalla a distintas velocidades. A partir de esas posiciones se trazan líneas principales y secundarias —incluyendo puntos medios y una cara rellena con transparencia— que generan una figura en constante mutación con apariencia tridimensional. La figura está basada en geometría euclideana, con una cambiante relación entre sus nodos. Sin embargo, aquí Euclides es sometido a sentir a la realidad, "y que aprenda cuatro cosas de la vida". El color del fondo y de los trazos cicla continuamente por el espectro HSB. Cada vértice controla en tiempo real la frecuencia, amplitud y paneo de uno de los cuatro osciladores sinusoidales, creando un juego de batimentos que evoluciona junto a la imagen.

## Estructura del proyecto

| Archivo | Descripción |
|---|---|
| `index.html` | Punto de entrada; carga jQuery, p5.js, p5.sound y el sketch principal |
| `lavalamp.js` | Sketch principal — lógica visual y síntesis de audio |
| `lavalamp.css` | Estilos (canvas a pantalla completa, sin márgenes) |
| `p5.js` / `p5.sound.js` | Librerías p5.js incluidas localmente |
| `instrucciones.md` | Guía de instalación en Raspberry Pi (modo kiosk con audio USB) |

## Instalación en Raspberry Pi

La pieza está pensada para correr de forma autónoma en una Raspberry Pi con Chromium en modo kiosk. Ver [instrucciones.md](instrucciones.md) para el setup completo: servidor local con `python3 -m http.server`, salida de audio USB y archivo `.desktop` para arranque automático.

