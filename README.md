# Laura_Mtnez_HLF
Juego de "Hundir La Flota" en Python realizado durante Bootcamp DS 26/27


## Hundir la Flota (Battleship)

¡Bienvenido a **Hundir la Flota**, el clásico juego de estrategia naval ambientado con embarcaciones tradicionales! Enfréntate a la Inteligencia Artificial en una batalla de ingenio y probabilidad en alta mar.


## Instrucciones del juego
El juego funciona por **turnos competitivos**:
* **Tablero**: Cada jugador cuenta con un mapa de **10x10 posiciones**.
* **El Objetivo**: Localizar y hundir los **10 barcos** del adversario antes de que él destruya los tuyos.
* **Mecánica de Tiro**:
  * Si tu disparo impacta en un barco enemigo (**Tocado** o **Hundido**), **conservas el turno** y puedes volver a disparar.
  * Si tu disparo cae al mar (**Agua**), pasas el turno al rival.
* **Fin de la Partida**: El primer jugador que se quede sin barcos en el mar, pierde inmediatamente.


## La Flota Corsaria

La flota está inspirada en navíos históricos y tradicionales. Cada jugador cuenta con un total de **10 embarcaciones** distribuidas de la siguiente forma:

* **1x Ballenero** (4 celdas de eslora)
* **2x Trainera** (3 celdas de eslora cada una)
* **3x Txalupa** (2 celdas de eslora cada una)
* **4x Batel** (1 celda de eslora cada una)

---

## Arquitectura del Código

El proyecto está diseñado bajo el paradigma de **Programación Orientada a Objetos (POO)** en Python y se estructura de la siguiente manera:

### Constantes del Sistema
Al inicio del script se definen los parámetros de configuración global:
* `DIMENSION`: Longitud del tablero (10x10).
* `SIMBOLO_AGUA` (`" "`): Representación visual del mar.
* `SIMBOLO_BARCO` (`"B"`): Ubicación de tus naves.
* `SIMBOLO_TOCADO` (`"x"`): Impacto certero sobre un barco.
* `SIMBOLO_FALLO` (`"o"`): Disparo fallido al agua.


### Clase `Tablero`
Encapsula el estado del mapa y las interacciones de cada jugador de manera aislada.
* **`tablero_barcos`**: Matriz donde se sitúan en secreto los barcos.
* **`tablero_disparos`**: Matriz de registro histórico de los ataques ejecutados contra el rival.
* **`coordenadas_barco`**: Diccionario dinámico que asocia cada navío con sus coordenadas restantes para validar cuándo se hunde.

#### Métodos Principales
* **`colocar_barcos_random()`**: Ubica automáticamente la flotilla de forma horizontal (`E-O`) o vertical (`N-S`).
* **`validar_posicion()`**: Comprueba mediante álgebra matricial que los barcos no se salgan del mapa ni se solapen entre sí.
* **`disparo_coordenada(x, y)`**: Recibe el impacto, actualiza las matrices y retorna estados (`AGUA`, `TOCADO`, `HUNDIDO`, `REPETIR`, `FIN`).
* **`solicitar_coordenada()`**: Gestiona el control de excepciones por teclado, garantizando que el usuario introduzca únicamente números enteros válidos dentro del rango de la matriz.


## Flujo de Ejecución (`main`)

El ciclo del programa se controla mediante funciones procedimentales y estructuras modernas de Python:

1. **`iniciar_juego()`**: Despliega un menú interactivo robusto que implementa `try-except` para evitar caídas por datos inválidos y un control `match-case` para las opciones de menú (Jugar, Instrucciones, Salir).
2. **`jugar()` (Bucle Principal)**:
   * Inicializa las dos instancias de `Tablero` (Humano y Máquina).
   * Automatiza el despliegue de las flotas.
   * Ejecuta un **bucle anidado** (`while True`) que alterna los turnos del usuario y la máquina.
   * Procesa las respuestas de combate en tiempo real mediante `match-case` hasta detectar la condición de victoria (`quedan_barcos() == False`).

---

## Requisitos e Instalación

Este proyecto se ejecuta nativamente en tu terminal y utiliza librerías de la biblioteca estándar de Python, por lo que **no requiere instalar dependencias externas**.

### Requisitos mínimos:
* **Python 3.10** o superior (necesario para la sintaxis estructurada `match-case`).

### Instrucciones para ejecutar:
1. Clona o descarga el archivo del código.
2. Abre tu terminal en el directorio del archivo.
3. Lanza el juego con el comando:
   ```bash
   python main.py
   ```
