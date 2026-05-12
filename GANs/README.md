# Recursos del Laboratorio 5a (GANs)

Esta carpeta contiene los recursos que descarga el Laboratorio 5a para entrenar
una GAN generadora de niveles de Super Mario Bros. Está pensada para ser
referenciada por el notebook del lab vía `git clone` o vía URLs raw del repo
público.

## Contenido

```
GANs/
├── levels/          # 31 niveles del Video Game Level Corpus en formato texto
├── sprites/         # 13 tiles 16x16 px en PNG con transparencia
├── vocab.json       # Vocabulario y mapeo char -> archivo de sprite
└── README.md        # Este archivo
```

## Niveles

Cada archivo `levels/SuperMarioBros2(J)-WorldX-Y.txt` (y `mario-X-Y.txt`) es
un nivel completo codificado como una grilla de caracteres ASCII. **Todos los
archivos tienen exactamente 14 filas** y la **última fila** es el suelo; el
ancho varía según el nivel.

Origen: [Video Game Level Corpus (VGLC)](https://github.com/TheVGLC/TheVGLC).
Los niveles fueron extraídos del repo público
[MatiasTelo/Global-Redes-Neuronales-Telo-Blangetti](https://github.com/MatiasTelo/Global-Redes-Neuronales-Telo-Blangetti),
trabajo final de la materia (edición previa).

### Normalización aplicada al corpus

Los archivos del VGLC original tenían heterogeneidades que se eliminaron para
simplificar el código del laboratorio:

- **Alturas distintas.** El VGLC contenía algunos archivos con menos de 14 filas
  (`World1-1.txt` con 12, `World6-3.txt` con 13). Esos archivos se completaron
  con filas de cielo (`-`) arriba para llegar a 14 filas, manteniendo el suelo
  alineado en la fila inferior.
- **Subsuelo eliminado.** Tres archivos (`World1-3.txt`, `World2-1.txt`,
  `World6-3.txt`) tenían el patrón "suelo + subsuelo" del juego original
  (dos filas casi idénticas al fondo). Se quitó la fila de subsuelo y se
  agregó cielo arriba para mantener las 14 filas. La motivación es que el
  subsuelo aparecía en menos del 10% del corpus y aportaba inconsistencia
  estructural sin agregar diversidad significativa.

## Sprites

Los 13 sprites de 16x16 px representan cada uno de los caracteres del
vocabulario. Los nombres de archivo son semánticos (no usan caracteres
especiales) — el mapeo char -> archivo está en `vocab.json`.

## Vocabulario

13 caracteres en total:

| char | sprite              | descripción                |
|------|---------------------|----------------------------|
| `X`  | block.png           | Bloque sólido (terreno)    |
| `S`  | ground.png          | Suelo destructible         |
| `-`  | empty.png           | Vacío (cielo / aire)       |
| `?`  | question.png        | Bloque pregunta (item)     |
| `Q`  | block_q.png         | Bloque pregunta usado      |
| `E`  | enemy.png           | Enemigo (Goomba/Koopa)     |
| `<`  | pipe_l.png          | Tubo - lado izquierdo      |
| `>`  | pipe_r.png          | Tubo - lado derecho        |
| `[`  | pipe_top_l.png      | Tubo - tope izquierdo      |
| `]`  | pipe_top_r.png      | Tubo - tope derecho        |
| `o`  | coin.png            | Moneda                     |
| `B`  | brick.png           | Ladrillo                   |
| `b`  | brick_broken.png    | Ladrillo roto              |

## Atribución

- **Niveles**: VGLC ([TheVGLC](https://github.com/TheVGLC/TheVGLC)) — corpus
  abierto de niveles de juegos clásicos.
- **Sprites**: extraídos de Super Mario Bros. (Nintendo, 1985), uso educativo.
- **Curado y formato**: trabajo previo de Matías Telo y Tomás Blangetti, edición
  2024 de la materia.
