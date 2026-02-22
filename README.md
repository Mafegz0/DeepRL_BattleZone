# Deep Reinforcement Learning – BattleZone (DDQN Tuned)

## Descripción del Proyecto

Este proyecto implementa un agente de **Aprendizaje por Refuerzo Profundo (Deep RL)** para el entorno **ALE/BattleZone-v5** utilizando **Double Deep Q-Network (DDQN)** con Stable-Baselines3.

---

## ¿Qué es BattleZone?

**BattleZone** es un videojuego clásico de Atari (1980) en el que el jugador controla un tanque en un entorno tridimensional en primera persona. El objetivo es sobrevivir y destruir vehículos enemigos mientras se navega en un terreno abierto con obstáculos.

Desde la perspectiva de aprendizaje por refuerzo, BattleZone presenta varios desafíos técnicos:

- Observaciones visuales de alta dimensionalidad (frames RGB del juego).
- Espacio de acción discreto amplio (18 acciones posibles).
- Recompensas esporádicas y dependientes de eventos.
- Dinámica parcialmente estocástica.
- Necesidad de coordinación entre movimiento y disparo.

Estas características lo convierten en un entorno adecuado para evaluar la estabilidad y capacidad de generalización de algoritmos basados en estimación de valores Q.

---

## Objetivo del Proyecto

Entrenar un agente capaz de aprender una política superior al comportamiento aleatorio a partir de observaciones visuales crudas (frames del juego), empleando:

- Redes neuronales convolucionales (CnnPolicy)
- Experience Replay
- Target Network
- Double Q-Learning
- Frame Stacking (4 frames)

---

## Algoritmo Implementado

### Double Deep Q-Network (DDQN)

DDQN reduce el sesgo de sobreestimación presente en DQN estándar al desacoplar:

- **Selección de la acción óptima** (red online)
- **Evaluación del valor Q** (red target)

Esta separación permite estimaciones más estables y reduce la acumulación de errores en la función de valor, lo cual es especialmente relevante en entornos con espacios de acción amplios y observaciones visuales complejas.

---

## Configuración del Entrenamiento

- Total timesteps: **200,000**
- Replay buffer: **80,000**
- Learning starts: **10,000**
- Batch size: **32**
- Gamma (discount factor): **0.99**
- Exploración prolongada (ε decay ≈ 60%)
- Frame stacking: **4 frames**
- Dispositivo: **GPU (CUDA)**

---

##  Resultados

El agente DDQN logró:

- Superar ampliamente el comportamiento aleatorio.
- Desarrollar mayor supervivencia en el entorno.
- Mejorar el direccionamiento de disparos.
- Acumular puntos de manera más consistente.

La evolución de recompensas puede visualizarse mediante los logs de TensorBoard incluidos en este repositorio.

---

##  Contenido de la Carpeta
```
BattleZone/
│
├── ddqn_battlezone_tuned.zip
├── 1771728423....mp4
├── 1771728437....mp4    (Renderización del comportamiento del agente en entrenamiento y final)
├── logs/  (Checkpoints intermedios)
└── Problema_dificultad_alta_BattleZone.ipynb
```


### Comparación Experimental

El modelo DDQN tuned mostró un desempeño más estable y consistente frente a DQN estándar, evidenciando:

- Menor volatilidad en la estimación de valores Q.
- Mayor estabilidad en recompensas promedio.
- Mejor consolidación de la política aprendida.

### Hardware Utilizado

- Google Colab
- GPU NVIDIA (CUDA)
- Stable-Baselines3 v2.x
