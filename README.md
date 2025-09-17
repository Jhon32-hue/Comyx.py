# Comyx

<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/a14ccc94-6aad-429c-907c-ac1d388b0892" />


**Comyx** es una librería en Python para la simulación avanzada de sistemas de comunicación inalámbrica, pensada como una de las bases tecnológicas de **Argo**, un framework orientado a la creación de aplicaciones distribuidas basadas en grafos.

**Comyx** combina modelos de comunicación tradicionales con optimización inteligente y procesamiento distribuido, creando un puente entre la investigación teórica y las aplicaciones prácticas en telecomunicaciones de próxima generación.

**Características principales**:

Comyx se centra en tres grandes bloques funcionales que corresponden a la arquitectura presentada en el diagrama.

## 1. Simulación de redes inalámbricas (Comyx Core)

Esto es el núcleo del sistema. Aquí definimos cómo se comporta la red, desde la señal física hasta las métricas de rendimiento.

Funciones principales:

Modelos de canal
Representa cómo se comporta el medio inalámbrico:

AWGN → ruido básico (como estática en la radio).

Rayleigh Fading → zonas con múltiples rebotes de señal.

Rician Fading → mezcla de línea directa y rebotes.

Procesamiento de señal
Aplica modulación y demodulación como BPSK, QPSK, QAM, etc.

Cálculo de métricas
Mide el rendimiento de la simulación:

Throughput (velocidad efectiva).

Outage Probability (probabilidad de caída de señal).

Sum Rate (capacidad total de la red).


## 2. Optimización (Optimization Layer)

Una vez simulada la red, entra la capa de optimización para mejorar su rendimiento automáticamente.

### **Reinforcement Learning (RL)**:
El sistema aprende por sí mismo a tomar mejores decisiones:

Ajusta parámetros como potencia de transmisión o asignación de canales.

Similar a cómo un coche autónomo mejora su conducción practicando.

### **Metaheurísticas**:
Algoritmos clásicos como:

Genéticos (evolución).
Enjambre de partículas.
Búsqueda tabú.


## **3. Visualización (Visualization Tools)**

Esta parte es donde los resultados se convierten en gráficos y dashboards, para que los investigadores o ingenieros puedan interpretar los datos.

Ejemplo:

Gráficas de throughput vs. ruido.

Mapas de cobertura.

Reportes exportables para documentación.


Comyx está construido sobre una arquitectura modular que separa simulación, optimización y visualización. Esto facilita la integración con Argo y otros sistemas.

flowchart TD
    A[User Scripts] --> B[Comyx Core]
    B --> C[Channel Models]
    B --> D[Signal Processing]
    B --> E[Performance Metrics]
    B --> F[Optimization Layer]
    F --> G[Reinforcement Learning]
    F --> H[Metaheuristics]
    B --> I[Visualization Tools]
    
    J[External Systems/Argo] <--> B


Instala la última versión estable con pip:

pip install comyx


Recomendación: Usar un entorno virtual para evitar conflictos de dependencias con otros proyectos.

Instalación editable para desarrollo y contribuciones:

git clone https://github.com/muhd-umer/comyx.git
cd comyx
pip install -e .

Primeros pasos

Un ejemplo rápido de simulación con un canal Rayleigh y modulación QPSK:

import comyx as cx
import numpy as np

# Parámetros básicos
snr_db = np.arange(0, 20, 2)
modulation = "QPSK"
channel_model = "rayleigh"

# Simulación
results = cx.simulate(
    snr_db=snr_db,
    modulation=modulation,
    channel=channel_model,
    num_symbols=1e5
)

# Resultados
print("Throughput:", results['throughput'])
print("Outage Probability:", results['outage_prob'])

Soporte para Reinforcement Learning (RL)

Comyx permite optimizar redes y algoritmos usando RL.

Instalación de dependencias:

PyTorch (estable)

pip install torch torchvision torchaudio


Ray RLlib (optimización distribuida)

pip install -U ray[default]   # núcleo y herramientas base
pip install -U ray[rllib]     # librerías específicas de RL


## **Visión a Futuro**

La evolución de Comyx dentro de Argo permitirá:

Simulaciones en tiempo real para aplicaciones críticas como IoT, Smart Cities y redes vehiculares.
Optimización autónoma de redes mediante RL y técnicas de metaheurística.
Integración cloud-native para escalabilidad en entornos de producción.
Entorno extensible para investigadores y desarrolladores.

Diagrama de la evolución hacia Argo
flowchart LR
    A[Comyx: Simulación independiente] --> B[Optimización y ML]
    B --> C[Procesamiento distribuido]
    C --> D[Integración con Argo]
    D --> E[Simulación en tiempo real y orquestación de grafos]


## **Analogía práctica con algo común**

Comyx es como Google Maps, pero en versión laboratorio:


Nuestros Channel Models son como Calles y carreteras
Los Signal Processing son Señales de tráfico y direcciones
Los Performance Metrics son la Información de tráfico y tiempos
Los Optimization Layer (RL)	son las Ruta más rápida en tiempo real
La Visualization Tools	es El mapa que ves en pantalla
Y los External Systems que usemos en el futuro con Argo gracias a Comyx son como los datos que usan Uber o Waze de Google Maps


## **Resumen final**

Comyx es:

Hoy: un simulador avanzado de redes 5G/B5G que permite probar y validar algoritmos.

Mañana: la pieza clave dentro de Argo para ejecutar simulaciones en tiempo real y optimizar redes distribuidas vivas.

Esto lo hace esencial para cualquier aplicación futura de IoT, Smart Cities, vehículos autónomos o comunicaciones críticas.


Este proyecto está bajo la licencia MIT.
Consulta el archivo LICENSE

 
