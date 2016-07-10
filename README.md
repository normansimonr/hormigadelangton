# La hormiga de Langton en NetLogo.

Este es un modelo en NetLogo para ilustrar el comportamiento de un autómate celular (la hormiga de Langton). Preparado para la clase de evaluación de políticas públicas (Universidad Nacional de Colombia, sede Medellín).

## Códigos preliminares.

Primero queremos resetear el tablero (por si queremos a correr el modelo varias veces).

```
  to setup
  clear-all
```
  
Ahora vamos a definir la forma del autómata celular (en este caso una hormiga o “bug”). En la pestaña “código” escribimos:

```
to setup
  clear-all
  set-default-shape ants "bug"
```

Creamos la hormiguita (color rojo, tamaño 15, mirando hacia arriba). En la pestaña “código” escribimos:

```
  to setup
  clear-all
  set-default-shape ants "bug"
  create-ants 1
  [
  set color red
  set size 15
  set heading 0
  ]
  reset-ticks
  end
```

Ahora creamos el tipo de agente. Antes de todo el código escribimos:

```
  breed [ants]
```

El universo es negro. Queremos ponerlo blanco, entonces escribimos esto dentro del procedimiento setup (antes de la creación de la hormiga).

```
ask patches
    [ set pcolor white ]
```

## Reglas del autómata.

### La primera regla:

1. Si está en un cuadro blanco, gira 90° a la derecha.
2. Si está en un cuadro negro, gira 90° a la izquierda.

```
to go
  ifelse (pcolor = black)
  [ right 90 ]
  [ left 90  ]
 end
 ```

Al procedimiento de correr el modelo lo llamamos “go”.

### Segunda regla: El cuadro donde la hormiga está cambia de color (los únicos colores existentes son blanco y negro).

```
to go
  ifelse (pcolor = black)
  [ right 90
    set pcolor white ]
  [ left 90
    set pcolor black ]
 end
```

### Tercera regla: la hormiga da un paso al frente.

```
to go
  ifelse (pcolor = black)
  [ right 90
    set pcolor white ]
  [ left 90
    set pcolor black ]
forward 1
end
```

## Código final

```
breed [ants]
to setup
  clear-all
  ask patches
    [ set pcolor white ]
  set-default-shape ants "bug"
  create-ants 1
  [
    set color red
    set size 15
    set heading 0
    ]
  reset-ticks
  end

to go
  ifelse (pcolor = black)
  [ right 90
    set pcolor white ]
  [ left 90
    set pcolor black ]
  forward 1
 end
 ```
 
 ¡Gracias!
