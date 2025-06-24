# Guía Profesional de Prompting para Flux y Stable Diffusion

## Introducción

El prompting es el arte y la ciencia de diseñar instrucciones textuales precisas que guían la generación de imágenes mediante modelos avanzados como Flux y Stable Diffusion.  A diferencia de interfaces más simplificadas como Midjourney o DALL-E, estos modelos ofrecen un control granular a través de prompts positivos, negativos, la asignación de pesos semánticos y múltiples mecanismos de condicionalidad.  Esta guía está dirigida a profesionales, artistas digitales y técnicos que buscan dominar la generación visual a nivel de arquitectura de prompt, semántica profunda e integración eficiente en pipelines de producción.

## 1. Fundamentos del Prompting en Flux y Stable Diffusion

### 1.1. Qué es un Prompt Positivo y uno Negativo

Ambos tipos de prompts son cruciales y se procesan como condicionales que influyen en el espacio latente durante el proceso de difusión.

  * **Prompt Positivo**: Describe los elementos, estilos y la composición deseada en la imagen.
      * **Ejemplo Básico**:
        ```
        a futuristic cityscape at sunset, neon lights, cinematic lighting
        ```
      * **Ejemplo Mejorado y Detallado**:
        ```
        Epic matte painting of a sprawling cyberpunk city skyline during a vibrant sunset, towering holographic advertisements, flying vehicles leaving light trails, dramatic cinematic lighting, highly detailed, 8K resolution, artstation masterpiece.
        ```
  * **Prompt Negativo**: Especifica los elementos, artefactos o características estéticas que se deben evitar.
      * **Ejemplo Básico**:
        ```
        ugly, deformed, low resolution, text, watermark
        ```
      * **Ejemplo Mejorado y Específico**:
        ```
        photorealistic, blurry, jpeg artifacts, noise, poorly drawn faces, mutated hands, missing limbs, extra fingers, signature, username, text, watermark, oversaturated, dull colors, flat lighting, cartoonish, 3d render, video game.
        ```

### 1.2. Principios Clave para Ambos Tipos de Prompt

  * **Especificidad y Concisión**: Evitar la vaguedad.  Ser directo pero descriptivo.
      * **Menos Efectivo**: `A dog.`
      * **Más Efectivo**: `A photorealistic portrait of a golden retriever puppy sitting in a field of wildflowers, soft morning light.`
  * **Modularidad Semántica**: Las frases separadas por comas actúan como bloques de significado que el modelo intenta combinar.
      * **Ejemplo**: `masterpiece, best quality, ultra-detailed, illustration, a majestic lion with a flowing mane, standing on a rocky cliff, overlooking a vast savanna at sunset, volumetric lighting, dramatic sky.`
  * **Priorización por Orden (Implícita)**: Los términos al inicio del prompt suelen tener una influencia ligeramente mayor.
  * **Control Explícito del Énfasis**: El uso de paréntesis y pesos numéricos permite un control preciso sobre la prominencia de cada elemento.
  * **Separación Clara entre Positivo y Negativo**: Es fundamental, especialmente en interfaces como AUTOMATIC1111 o ComfyUI, donde suelen tener campos de texto dedicados.

### 1.3. Parámetros Relevantes: CFG Scale (Classifier-Free Guidance)

CFG Scale (Guidance Scale): Controla la adherencia del modelo al prompt.  Es un equilibrio entre fidelidad y creatividad.

  * **Valores Bajos (ej. 3-6)**: Mayor libertad creativa para el modelo, resultando en más variación y a veces sorpresas, pero puede desviarse del prompt.  Útil para exploración inicial.
  * **Valores Medios (ej. 7-11)**: Generalmente un buen punto de partida, ofreciendo un equilibrio entre fidelidad al prompt y calidad estética.  Se recomienda iniciar en 7.5 - 9.
  * **Valores Altos (ej. 12-20)**: Mayor adherencia al prompt, pero puede llevar a imágenes "sobrecocinadas", con artefactos o falta de diversidad.  Se debe usar con cautela y para estilos muy específicos.

## 2. Anatomía Detallada del Prompt

Un prompt bien estructurado se compone de varios elementos clave que, combinados, definen la imagen final.

  * **Tema Principal/Sujeto**: El foco central de la imagen.
      * **Ejemplo**: `portrait of an ancient warrior queen, intricate armor, determined expression`
  * **Atributos y Estilo Artístico**: Modificadores que definen la estética.
      * **Ejemplo**: `realistic, hyperdetailed, concept art, fantasy, style of Frank Frazetta, oil painting texture`
  * **Iluminación**: Describe cómo se ilumina la escena.
      * **Ejemplo**: `dramatic volumetric lighting, rim lighting from a setting sun, god rays, subtle bioluminescence`
  * **Técnica Visual/Medio**: El tipo de arte o técnica que se emula.
      * **Ejemplo**: `digital painting, 3D render (Unreal Engine 5), film photography (Kodachrome), watercolor sketch`
  * **Composición y Encuadre**: Cómo se organizan los elementos y la perspectiva.
      * **Ejemplo**: `dynamic low-angle shot, close-up portrait, centered, rule of thirds, dutch angle, panoramic view`
  * **Paleta Cromática**: Los colores predominantes o el esquema de color.
      * **Ejemplo**: `vibrant contrasting colors, monochrome (sepia), dark moody blues and purples, pastel color palette`
  * **Referencias Visuales (Artistas, Obras)**: Para guiar el estilo hacia influencias específicas.
      * **Ejemplo**: `inspired by H.R. Giger and Zdzisław Beksiński, in the style of Studio Ghibli, reminiscent of Blade Runner 2049`

**Ejemplo Combinado (Prompt Positivo)**:

```
Epic portrait of a stoic elven sorceress (long silver hair, glowing blue eyes), wearing ornate dark leather armor with silver filigree, (casting a complex arcane spell:1.3) that illuminates her face, ((ancient mystical forest background at twilight:1.2)), volumetric god rays filtering through the canopy, hyperdetailed, digital painting, style of Brom and Greg Rutkowski, cinematic composition, atmospheric, 8K.
```

### 2.2. Prompt Negativo: Corrección Implícita y Explícita

Actúa como un filtro para refinar la salida, eliminando características no deseadas o corrigiendo tendencias problemáticas del modelo.

  * **Ejemplo de Prompt Negativo Estándar Mejorado**:
    ```
    ugly, tiling, poorly drawn hands, (malformed fingers:1.3), (deformed face:1.4), extra limbs, missing limbs, disfigured, blurry, out of focus, low contrast, flat colors, bad anatomy, ((text, watermark, signature, username:1.5)), jpeg artifacts, noise, grain, cartoon, 3d render (if aiming for 2D), childish, amateur, oversaturated, undersaturated.
    ```
  * **Modulación Negativa de Estilo**:
    ```
    photorealistic, realistic, photographic (if aiming for a painterly style), anime, manga, sketch, grayscale (if color is desired).
    ```

### 2.3. Uso de Pesos: Énfasis Controlado en la Latente Semántica

Permite ajustar la influencia de términos específicos dentro del prompt.

  * **Paréntesis Simples ()**: Aumentan ligeramente el énfasis (aproximadamente $\times 1.1$).
      * `(cinematic lighting)` es más fuerte que `cinematic lighting`.
  * **Múltiples Paréntesis (())**: Aumentan el énfasis progresivamente.
      * `((ethereal atmosphere))` tiene un énfasis mayor que `(ethereal atmosphere)`. (Cada par puede ser $ \times 1.1 $, así `(())` sería \~$ \times 1.21 $).
  * **Notación Explícita con Peso Decimal `(term:weight)`**:
      * `(term:1.4)`: Intensifica el término (1.0 es el valor neutro).
      * `(term:0.8)`: Atenúa el término sin eliminarlo.
  * **Notación de Atenuación `[term]`**: En algunas UIs, puede usarse para disminuir el peso. Otra forma es usando un peso decimal menor a 1.0, como `(term:0.9)`.

**Ejemplos de Uso con Pesos Explícitos**:

  * **Prompt Positivo con Énfasis**:
    ```
    A stunning matte painting of a (bioluminescent jellyfish:1.4) gracefully floating in a ((deep dark ocean trench:1.3)), surrounded by (tiny sparkling plankton:1.1), mysterious atmosphere, ultra realistic, artstation.
    ```
    Aquí, `bioluminescent jellyfish` tiene la mayor preponderancia, seguido por `deep dark ocean trench`.
  * **Prompt Negativo con Penalización Fuerte**:
    ```
    ugly, (deformed tentacles:1.6), (blurry background:1.4), ((watermark:1.8)), pixelated, low quality, unrealistic physics.
    ```
    Se penaliza con más fuerza la deformidad de los tentáculos y especialmente cualquier marca de agua.

### 2.4. Ejemplos de Prompts por Nivel de Detalle

  * **Nivel Básico (Rápido, pero genérico y poco controlado)**:

      * **Prompt Positivo**: `a dragon`
      * **Prompt Negativo**: `(none)`
      * **Resultado Esperado**: Una imagen probablemente genérica de un dragón, con estilo y calidad variables.

  * **Nivel Intermedio (Mejor composición y atmósfera)**:

      * **Prompt Positivo**: `a majestic red dragon flying over a mountain range, sunset, fantasy art`
      * **Prompt Negativo**: `blurry, cartoon, poorly drawn wings`
      * **Resultado Esperado**: Un dragón rojo más definido, en un entorno específico, con un intento de estilo artístico y algunas correcciones básicas.

  * **Nivel Avanzado (Control de estilo, técnica e iluminación)**:

      * **Prompt Positivo**: `cinematic film still, a colossal ancient black dragon with glowing molten eyes, perched atop a jagged volcanic peak, ((stormy sky with lightning:1.3)), scales shimmering with obsidian texture, volumetric lighting, hyperdetailed, style of Todd Lockwood, fantasy illustration, 8k.`
      * **Prompt Negativo**: `blurry, lowres, bad composition, text, watermark, oversaturated, cartoony, friendly dragon, smooth skin, jpeg artifacts, poorly rendered smoke, extra limbs.`
      * **Resultado Esperado**: Una imagen mucho más específica, con alta calidad, estilo artístico definido, iluminación dramática y mayor control sobre los detalles y la atmósfera.

  * **Nivel Profesional (Prompt completo con pesos estratégicos)**:

      * **Prompt Positivo**: `masterpiece, best quality, (photorealistic:1.2) concept art of a (female cyborg assassin:1.3), ((intricate glowing neon cybernetic implants:1.4)), sleek black tactical suit, rain-slicked futuristic city street at night, (reflections on wet pavement:1.1), anamorphic lens flare, cinematic lighting, style of Maciej Kuciara and Blade Runner 2049, extremely detailed, sharp focus.`
      * **Prompt Negativo**: `(worst quality, low quality:1.4), normal quality, (ugly:1.3), deformed, (bad anatomy:1.3), poorly drawn face, mutated hands, extra fingers, (missing limbs:1.2), (blurry:1.1), out of focus, text, watermark, signature, username, (cartoonish: 1.2), 3d render, simplistic, dull, plastic look, oversaturated colors, duplicate, artifacts.`
      * **Resultado Esperado**: Una imagen de alta fidelidad, con un sujeto, entorno y estilo muy específicos, donde los pesos guían la atención del modelo hacia los aspectos más cruciales y los negativos pulen intensamente los defectos comunes.

## 3. Estrategias Avanzadas para Flux y SD

### 3.1. Iteración Sistemática con Seeds Fijos

Al fijar el `seed` (semilla de aleatoriedad), se obtiene la misma imagen base para un prompt, lo que permite realizar cambios incrementales en el prompt y observar directamente su impacto.

  * **Proceso**:

    1.  Genera una imagen con un prompt inicial y un seed aleatorio.
    2.  Fija ese seed.
    3.  Modifica ligeramente el prompt (ej. cambia `(blue eyes:1.1)` a `(green eyes:1.1)`).
    4.  Genera de nuevo y compara.

  * **Ejemplo Práctico**:

      * **Prompt A (Seed 12345)**: `photo of a cat, park` -> Imagen de un gato genérico en un parque.
      * **Prompt B (Seed 12345)**: `photo of a (Siamese cat:1.3), sunlit park, (bokeh background:1.2)` -> La misma composición base, pero ahora el gato es Siamés y el fondo tiene bokeh.

### 3.2. Uso de LoRA y Embeddings (Textual Inversion)

  * **LoRA (Low-Rank Adaptation)**: Pequeños archivos que modifican un modelo base para aplicar un estilo, personaje o concepto específico.
      * **Uso en Prompt**: Se invocan con una sintaxis especial, como `<lora:nombreLoRA:peso>`.
      * **Ejemplo**: `masterpiece, <lora:animeFlatColor_v1:0.7> portrait of a girl, vibrant hair, detailed eyes, clean lineart, (simple background:1.2).`
  * **Embeddings (Textual Inversion)**: Entrenan una nueva "palabra" que representa un concepto visual a partir de imágenes de ejemplo.
      * **Uso en Prompt**: Se utiliza la palabra clave entrenada directamente.
      * **Ejemplo**: `A landscape painting, myUniqueArtstyle, rolling hills, dramatic clouds.`

### 3.4. Encadenamiento de Prompts (Prompt Chaining)

Técnica para crear secuencias, donde la salida de un prompt sirve como base para el siguiente, a menudo usando `img2img`.

  * **Ejemplo de Storytelling Visual**:
    1.  **Prompt 1 (Definición de personaje, Seed 5678)**: `Full body portrait of Zara, a young space explorer, orange and white spacesuit, short spiky blue hair, determined expression, concept art.`
    2.  **Prompt 2 (Escena 1, usando la salida 1 en img2img con Denoising bajo)**: `Zara, space explorer, standing on a desolate red planet, two moons in the purple sky, alien flora.`
    3.  **Prompt 3 (Escena 2, similar al paso 2)**: `Zara, space explorer, inside a derelict alien spaceship, eerie green emergency lights, holographic displays flickering.`

## 4. Buenas Prácticas Profesionales

  * **Separación Visual y Lógica Clara**: Utiliza campos de texto distintos para prompts positivos y negativos y organiza las ideas de forma lógica (sujeto, estilo, etc.).
  * **Curación por Lotes (Batch Generation)**: Genera múltiples imágenes (ej. batch size de 4 u 8) con el mismo prompt pero diferentes seeds para obtener variaciones.
  * **Documentación Exhaustiva (Metadata)**: Guarda siempre el prompt positivo y negativo, Seed, Sampler, CFG Scale, Resolución, y nombres de LoRAs o Embeddings utilizados.
  * **Auditoría de Errores Visuales**: Clasifica los fallos comunes (ej. mala anatomía) y refina el prompt negativo de forma específica para contrarrestarlos. Por ejemplo, si aparecen manos con 6 dedos, añade `(six fingers:1.5)` al prompt negativo.
  * **Normalización y Plantillas de Prompts**: Para proyectos, crea plantillas base que definan el estilo general y modifica solo las partes variables.
      * **Ejemplo Plantilla Positiva (Cyberpunk Noir)**: `cinematic shot, film noir aesthetic, (cyberpunk city:1.2), rain-slicked streets, neon signs casting long shadows, mysterious atmosphere, high contrast, gritty textures, [SUJETO_Y_ACCION], style of Syd Mead and Katsuhiro Otomo.`
      * **Ejemplo Plantilla Negativa (General)**: `worst quality, low quality, ugly, deformed, blurry, oversaturated, bright, cheerful, daytime, clean, modern, minimalistic.`

## 5. Automatización y Pipelines

  * **Prompt Templates Parametrizados**: Usa marcadores de posición (`placeholders`) en tus prompts que se rellenan dinámicamente.
      * **Ejemplo de Plantilla**: `A {adjective} {creature_type} in a {environment_type} during a {time_of_day}, {art_style}.`
      * **Ejemplo de Relleno**: `A colossal bioluminescent jellyfish in a deep-sea trench during the midnight hour, digital painting.`
  * **Generadores de Prompts Asistidos por LLM**: Utiliza modelos de lenguaje grandes (como GPT) para generar prompts detallados a partir de un concepto general.
      * **Input al LLM**: "Necesito un prompt para Stable Diffusion que muestre un guerrero espacial melancólico en un planeta alienígena en ruinas, con un estilo de arte similar a Simon Stålenhag."
      * **Output del LLM (potencial)**: `melancholy space warrior, weathered armor, standing amidst colossal alien ruins on a desolate planet, twin suns setting, atmospheric dust, muted color palette, digital painting, style of Simon Stålenhag, cinematic, introspective.`
  * **Pipelines Multi-Etapa**:
      * **Sketch-to-Image**: Un boceto se usa con ControlNet y un prompt para generar una base.
      * **Img2Img Refinement**: La imagen base se pasa a `img2img` con un prompt más detallado para refinarla.
      * **Inpainting Selectivo**: Se utiliza para corregir o añadir detalles en áreas específicas.
      * **Upscaling Inteligente**: Se aumenta la resolución con upscalers específicos para IA (como ESRGAN).
      * **Post-Procesamiento**: Ajustes finales de color y contraste.

## 6. Recursos Especializados y Lecturas Recomendadas

  * **Comunidades y Repositorios**:
      * **Civitai.com**: Repositorio principal para modelos, LoRAs, e inversiones textuales.
      * **Hugging Face Hub**: Gran colección de modelos y herramientas de IA.
  * **Bases de Datos de Prompts**:
      * PromptHero.com
      * Lexica.art
      * Mage.space
  * **Software y Herramientas Populares**:
      * **AUTOMATIC1111's Stable Diffusion WebUI**: Interfaz de usuario popular y potente.
      * **ComfyUI**: Interfaz basada en nodos para pipelines complejos.
      * **InvokeAI**: Interfaz robusta con buen soporte para ControlNet.
      * **Fooocus**: Interfaz simplificada inspirada en Midjourney.
  * **Bibliotecas para programación**:
      * **Diffusers (de Hugging Face)**: Biblioteca de Python para interactuar con modelos de difusión.
  * **Papers Fundamentales (Lectura Avanzada)**:
      * "High-Resolution Image Synthesis with Latent Diffusion Models" (El paper original de Stable Diffusion).
      * "ControlNet: Adding Conditional Control to Text-to-Image Diffusion Models".
      * "LORA: Low-Rank Adaptation of Large Language Models".