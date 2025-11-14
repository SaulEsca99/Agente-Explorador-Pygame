# 🤖 Agente Explorador de Laberintos con Pygame

[![Python](https://img.shields.io/badge/Python-3.x-blue.svg)](https://www.python.org/)
[![Libraries](https://img.shields.io/badge/Librerías-Pygame%20%7C%20NumPy-green.svg)](https://pypi.org/)

Este proyecto es un simulador interactivo de exploración de laberintos, construido con Pygame y NumPy. Permite a un usuario controlar un **agente** con diferentes habilidades para explorar un entorno cargado desde un archivo (`mapa.txt`).

La característica principal es el concepto de **entorno parcialmente observable** ("Fog of War"): el agente solo puede "ver" las celdas que explora, y el mapa se revela progresivamente.

## 🖼️ Demostración

![Demo del Juego](demo.png)

## ✨ Características Principales

* **Visualización Interactiva:** Creado con Pygame, muestra el laberinto, el agente, su dirección y el mapa explorado.
* **Entorno Parcialmente Observable:** El laberinto está oculto por una "niebla de guerra" (`mapa_visible`) que se revela a medida que el agente avanza o usa su sensor.
* **Sistema de Agentes Modulares:** La clase `Agente` permite definir diferentes tipos de exploradores con habilidades únicas.
* **Múltiples Tipos de Terreno:** El mapa (cargado desde `map.txt`) no solo tiene paredes y caminos, sino que también puede incluir agua, arena, bosque y montañas, cada uno con un color distintivo.
* **Registro de Acciones:** El agente lleva un `historial` de todas las decisiones tomadas, que se puede revisar en cualquier momento.
* **Configuración Dinámica:** El usuario define las posiciones de inicio y objetivo en la consola antes de que comience el juego.

### 🤖 Habilidades del Agente

El comportamiento del agente está determinado por un diccionario de `habilidades`:
* `puede_girar_izquierda` / `puede_girar_derecha`: Restringe la capacidad de giro.
* `vision_lejana`: Permite al sensor (tecla Espacio) revelar celdas a 3 pasos de distancia en lugar de 1.
* `rango_movimiento`: El agente puede avanzar múltiples celdas en una sola acción.
* `vision_omni`: Una habilidad especial (tecla 'O') que revela un área de 3x3 alrededor del agente, pero tiene un tiempo de *cooldown*.

## ⚙️ Dependencias

Para ejecutar este proyecto, necesitas las siguientes bibliotecas de Python:

* `pygame`: Para el motor de juego y la visualización.
* `numpy`: Para cargar y manejar la matriz del laberinto.

Puedes instalarlas usando `pip`:

```bash
pip install pygame numpy
```

## 🚀 Cómo Jugar

1.  Asegúrate de tener `pygame` y `numpy` instalados.
2.  Coloca el archivo `map.txt` en la misma carpeta que el script de Python.
3.  Ejecuta el script:
    ```bash
    python tu_script.py
    ```
    *(Reemplaza `tu_script.py` con el nombre de tu archivo)*

4.  **En la consola:**
    * Selecciona el tipo de agente (1-4).
    * Introduce la fila y columna de **INICIO**.
    * Introduce la fila y columna de **OBJETIVO**.

5.  **En la ventana de Pygame:**
    * La ventana del juego se abrirá.
    * ¡Usa las teclas para explorar y encontrar el objetivo!

## ⌨️ Controles

* **Flechas (Arriba, Izquierda, Derecha):** `Avanzar`, `Girar Izquierda`, `Girar Derecha`.
* **Espacio:** `Sensar` (revela la niebla de guerra en la dirección del agente, según su habilidad de visión).
* **O:** `Activar Visión Omni` (si el agente tiene la habilidad y no está en cooldown).
* **T:** `Ver Historial` (muestra un resumen de todas las acciones en pantalla).
* **R:** `Reiniciar` (vuelve al estado inicial).
* **ESC:** `Salir` del juego.
