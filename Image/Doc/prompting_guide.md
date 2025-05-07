**Guía Profesional de Prompting para Flux y Stable Diffusion**

---

### Introducción

El *prompting* es el arte de diseñar instrucciones textuales que guíen la generación de imágenes mediante modelos como **Flux** y **Stable Diffusion**. A diferencia de interfaces como Midjourney o DALL·E, estos modelos permiten un control fino mediante prompts positivos, negativos, pesos semánticos y múltiples mecanismos de condicionalidad. Esta guía está dirigida a profesionales y técnicos que deseen dominar la generación visual a nivel de arquitectura, semántica e integración en pipelines.

---

### 1. Fundamentos del Prompting en Flux y Stable Diffusion

#### 1.1. Qué es un Prompt Positivo y uno Negativo

* Prompt positivo: texto que describe lo que debe aparecer en la imagen. Ejemplo: a steampunk cityscape at night, cinematic lighting

* Prompt negativo: texto que especifica lo que no debe aparecer. Ejemplo: ugly, deformed, low resolution, text, watermark

Ambos se procesan como condicionales independientes que afectan la latente de atención durante la generación.

#### 1.2. Principios Clave para Ambos Tipos de Prompt

* Especificidad y concisión: Evitar prompts vagos o sobrecargados.

* Modularidad semántica: Frases separadas por comas funcionan como bloques independientes.

* Priorización por orden: Los primeros bloques tienen mayor peso implícito.

* Control explícito: El uso de paréntesis o notación de pesos da control sobre énfasis.

* Separación clara entre positivo y negativo: fundamental en interfaces como AUTOMATIC1111.

#### 1.3. Parámetros Relevantes: CFG Scale (Classifier-Free Guidance)

* **CFG Scale (guidance scale)**: controla cuánto el modelo debe seguir el prompt.

* **Valores bajos (~3–6)**: más creatividad y variación, pero menos fidelidad.

* **Valores altos (~12–20)**: mayor adherencia al prompt, pero menos diversidad.

* **Recomendación**: iniciar en 7.5–9 y ajustar según nivel de control deseado.

---

### 2. Anatomía Detallada del Prompt

* **Tema principal**: `portrait of a woman`, `abandoned futuristic ruins`
* **Atributos y estilo**: `realistic`, `dreamlike`, `cyberpunk`, `analog horror`
* **Iluminación**: `volumetric lighting`, `neon lights`, `soft morning sun`
* **Técnica visual**: `3D render`, `film photography`, `watercolor painting`
* **Composición**: `isometric view`, `close-up`, `Dutch angle`
* **Paleta cromática**: `pastel colors`, `monochrome`, `black and red only`
* **Referencias visuales**: `inspired by H.R. Giger`, `in the style of Blade Runner`

Ejemplo:

```text
portrait of a young woman, ethereal atmosphere, 85mm lens, shallow depth of field, soft lighting, pastel colors, film grain, in the style of Sofia Coppola
```

#### 2.2. Prompt Negativo: Corrección Implícita

Este prompt actúa como filtro. Comúnmente se incluyen términos asociados a deformaciones, errores comunes o artefactos.

Ejemplo de prompt negativo estándar:

```text
ugly, tiling, poorly drawn hands, deformed face, extra limbs, blur, text, watermark, grainy, low-res, bad anatomy
```

Puedes modular negativamente el estilo también:

```text
cartoon, cel shading, low contrast, flat colors
```

#### 2.3. Uso de Pesos: Énfasis Controlado en la Latente Semántica

Los modelos como Flux y Stable Diffusion permiten ajustar el grado de influencia de cada término dentro del prompt mediante una sintaxis de **ponderación explícita**, útil para refinar la prioridad semántica durante la atención.

##### Sintaxis y Notación Común

* Paréntesis simples `()` aumentan el énfasis:

  * `(cinematic lighting)` es más fuerte que `cinematic lighting`
* Doble paréntesis `((...))` aplican un énfasis aún mayor (algunos entornos los interpretan como multiplicadores implícitos, típicamente x1.1 o x1.2 por cada capa).
* Notación explícita con peso decimal: `(term:1.4)`

  * Valores >1 intensifican el término
  * Valores <1 lo atenúan sin eliminarlo

##### Ejemplos de uso:

```text
a portrait of a woman, (cinematic lighting:1.5), (soft focus:1.2), ((ethereal atmosphere))
```

En este prompt, *cinematic lighting* y *ethereal atmosphere* tendrán mayor peso en la generación que el resto de elementos.

En prompts negativos, puedes aplicar la misma lógica para penalizar con más fuerza atributos indeseados:

```text
ugly, (deformed face:1.6), (text:1.4), ((bad anatomy))
```

##### Recomendaciones Estratégicas

* Evita sobredimensionar múltiples términos (>1.6) simultáneamente: puede provocar saturación semántica y confundir la atención del modelo.
* Usa pesos explícitos para dirigir diferencias sutiles (ej. cambiar solo la iluminación sin alterar la composición).
* Puedes combinar pesos con templates programáticos para adaptar el énfasis según metas visuales o métricas de calidad.

##### Consideraciones por Plataforma

* AUTOMATIC1111, ComfyUI y otras UIs de difusión permiten estas notaciones, pero algunos entornos como Diffusers de HuggingFace requieren transformar el prompt en tokens ponderados mediante código.
* Algunos modelos personalizados responden de forma no lineal a pesos extremos (>2.0), y pueden generar resultados impredecibles.


#### 2.4. Ejemplos de Prompts por Nivel de Detalle

* **Nivel básico** (rápido pero genérico):

```text
a forest
```

* **Nivel intermedio** (mejor composición y atmósfera):
```text
a misty forest at dawn, soft lighting, trees with moss, volumetric light
```

* **Nivel avanzado** (control de estilo, técnica y detalle):
```text
a cinematic photo of a misty enchanted forest at dawn, volumetric lighting, detailed moss on tree trunks, ambient fog, f1.8 aperture, high contrast, shot on 35mm film, ultra realistic, masterpiece
```


* **Nivel profesional** (prompt completo con negativos y pesos):
```text
a cinematic photo of a misty enchanted forest at dawn, volumetric lighting, detailed moss on tree trunks, ambient fog, f1.8 aperture, high contrast, shot on 35mm film, ultra realistic, masterpiece, ((depth of field:1.4)), (film grain:1.2)
```

**Negative prompt**: blurry, lowres, bad composition, text, watermark, oversaturated



---

### 3. Estrategias Avanzadas para Flux y SD

#### 3.1. Iteración con Logs y Seeds

Establecer el mismo `seed` permite comparar prompts controlando la aleatoriedad. Compara cambios finos (una palabra o peso) para afinar.

#### 3.2. LoRA y Embeddings Personalizados

* Usa LoRA para aplicar estética entrenada (ej. "cybermecha\_v2")
* Usa textual inversion para insertar conceptos propios como `style-museum45`

#### 3.3. ControlNet y Condicionales Visuales

* **Pose**: skeleton o pose keypoints para controlar figuras humanas
* **Depth**: mapa de profundidad para preservar estructura espacial
* **Canny / Lineart**: para preservar contorno
* **Segmentation**: para preservar categorías semánticas (ropa, fondo, etc.)

Combina ControlNet con prompts para mantener la semántica en una composición específica.

#### 3.4. Encadenamiento de Prompts

Ideal en flujos programáticos o de storytelling:

* Prompt inicial define el personaje
* Variaciones lo muestran en diferentes escenas
* Estilo mantenido por embudos o templates

---

### 4. Buenas Prácticas Profesionales

* **Separación visual clara**: positivo y negativo deben estar claramente separados.
* **Curación por lotes**: genera variantes con ligeros cambios y selecciona manualmente.
* **Documentación**: guarda prompt completo, seed, pasos, sampler, LoRA y embeddings usados.
* **Auditoría de errores visuales**: clasifica tipos de fallo (anatomía, artefactos, estética) y refina el prompt negativo acorde.
* **Normaliza tus prompts base por proyecto**: crea plantillas estilísticas coherentes.

---

### 5. Automatización y Pipelines

Para integrar Flux o SD en flujos:

* **Prompt templates parametrizados**: usar llaves como `{subject}`, `{style}` y rellenar desde base de datos o inferencia semántica.
* **Generadores de prompt via LLM**: usa GPT para construir prompts desde un objetivo visual o metadatos.
* **Ponderación adaptativa**: ajustar pesos según calificación de output.
* **Multistep pipelines**: sketch → inpainting → upscaling → color grading

---

### 6. Recursos Especializados

* **CivitAI.com**: explora modelos LoRA, embeddings, estilos y ejemplos de prompt.
* **Diffusers de HuggingFace**: biblioteca para uso programático de SD.
* **PromptHero, Lexica, Mage.space**: bases de datos de prompts reales.
* Papers recomendados:

  * "High-Resolution Image Synthesis with Latent Diffusion Models"
  * "ControlNet: Adding Conditional Control to Text-to-Image Diffusion Models"

---

### Conclusión

El dominio de prompting en modelos como Flux y Stable Diffusion no es trivial: requiere entender las interacciones entre semántica textual, arquitectura de atención, y mecanismos de control condicional. Esta guía detalla tanto la práctica estructurada como los principios profesionales que permiten generar imágenes precisas, estilizadas y reproducibles. Prompting es un lenguaje de control visual; dominarlo es programar la estética con intención.
