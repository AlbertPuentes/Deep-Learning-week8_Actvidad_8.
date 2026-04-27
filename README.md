# Deep-Learning-week8_Actvidad_8.

##  Conclusiones

Tras ejecutar ambos modelos bajo condiciones controladas cada uno para 10 épocas, mismo optimizador, mismo tamaño de lote, se observo lo siguiente:

### 1. ¿Qué mejoró y qué se mantuvo?
* **Velocidad de convergencia:** El modelo de Transfer Learning suele arrancar con una precisión inicial mucho más alta en la primera época porque ya tiene datos, por otro lado el modelo CNN base tiene que aprender a detectar bordes desde cero.
* **Precisión general (Accuracy):** Dependiendo de las épocas, el modelo base puede llegar entre un 65-70%. El modelo preentrenado suele ser más robusto a la validación temprana, aunque MobileNetV2 le cueste un poco ya que los pesos fueron optimizados para imágenes de 224x224, y se paso imágenes mas pequeñas de (32x32).

### 2. Trade-offs (Costo-Beneficio)
* **CNN:** 
 *  *ventajas:* Es un modelo ligero, tiene pocos parámetros y hace inferencias deforma rapida.
 * *Desventajas:* Tarda más en aprender y es muy propenso al *sobreajuste* (overfitting) si no se le aplican técnicas de regularización.
* **Transfer Learning:**
 * *Ventajas:* Generaliza mucho mejor gracias al conocimiento previo de ImageNet. Ahorra tiempo de cómputo masivo y es ideal cuando hay pocas imágenes locales.
 * *DAesventajas:* El modelo es mucho más pesado (incluso MobileNet que es eficiente, tiene millones de parámetros). Requiere más RAM y tiempo de carga.

### 3. Recomendaciones
Se evidencio que proyectos con datos limitados, **Transfer Learning** es el mas adecuado. Para mejorar el rendimiento de este modelo , el siguiente una opcion a aplicar seria el *Fine-Tuning*: descongelar las últimas capas convolucionales de MobileNetV2 y entrenarlas con una tasa de aprendizaje muy baja para adaptar los pesos preentrenados específicamente a las texturas.
