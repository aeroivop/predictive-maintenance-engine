# predictive-maintenance-engine
Este proyecto implementa un sistema de Mantenimiento Predictivo Universal utilizando Machine Learning (XGBoost) para estimar la Vida Útil Restante (RUL - Remaining Useful Life) de motores aeronáuticos turbofán, basándose en la telemetría desclasificada del dataset CMAPSS de la NASA.
-El Problema de Ingeniería
Predecir cuándo va a fallar un motor en vuelo no es solo un problema matemático, sino físico. Los modelos tradicionales fallan al enfrentarse a la telemetría real debido a dos grandes retos:

Ruido Atmosférico: Los sensores (temperatura, presión, rpm) varían drásticamente según la altitud y la velocidad del avión, enmascarando la degradación real del metal.

Múltiples Modos de Fallo: Un motor no falla siempre por la misma pieza (puede ser el Compresor de Alta Presión o el Ventilador Frontal).

-La Solución (Arquitectura del Modelo)
	Este proyecto unifica los 4 niveles de dificultad del dataset de la NASA (FD001 al FD004) en un único Súper-Predictor Universal aplicando técnicas avanzadas de Ingeniería de Datos:

Inyección de Física (Clipping): Se limita el RUL de entrenamiento a 60 ciclos, enseñando matemáticamente a la IA que un motor sano no muestra síntomas termodinámicos de fatiga en sus primeros vuelos.

Normalización por Régimen de Vuelo (Z-Score): Se agrupan los vuelos mediante Clustering de condiciones operativas (Mach, Altitud, Acelerador) para aislar la degradación puramente mecánica del ruido provocado por los cambios de 	régimen.

Ética de Seguridad Aeronáutica (Pesos Asimétricos): El algoritmo XGBoost está modificado para penalizar hasta 10 veces más los errores cometidos al final de la vida útil del motor, priorizando la detección temprana y garantizando un 	margen de seguridad operativo de 5 vuelos.

-Panel de Control (Dashboard)
El código incluye un módulo de visualización que genera un panel de diagnóstico 2x2. Permite auditar motores aleatorios comparando la degradación real (Verdad Absoluta) frente a la curva de predicción suavizada de la IA, resaltando 	automáticamente las zonas rojas de peligro (sobreestimación).

-Instalación y Uso
Clona este repositorio: git clone https://github.com/tu-usuario/predictive-maintenance-engine.git

Instala las dependencias necesarias: pip install pandas numpy matplotlib xgboost scikit-learn

Ejecuta el cuaderno interactivo o el script principal para descargar automáticamente los datos de la NASA, entrenar el modelo generalista y visualizar el panel de control. El script también exporta el cerebro entrenado (cerebro_turbofan_universal.json) para despliegues en producción.
