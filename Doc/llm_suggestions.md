### Guía para Pedir Prompts a ChatGPT para Stable Diffusion y Flux

---

#### Objetivo de esta Guía

Esta guía está diseñada para usuarios técnicos o creativos que deseen usar **ChatGPT como generador de prompts** de alta calidad para modelos como **Stable Diffusion** y **Flux**. El objetivo es convertir descripciones abstractas, requisitos visuales o ideas estilísticas en prompts estructurados y compatibles con estos modelos de generación de imagen.

---

### 1. Fundamentos: Qué necesita saber ChatGPT

ChatGPT no es un generador de imagen, pero puede estructurar prompts efectivos si le das:

1. **Tema central o sujeto**: ej. "una ciudad futurista", "un retrato barroco".
2. **Estilo visual deseado**: ej. "oil painting", "cyberpunk", "Studio Ghibli".
3. **Atributos técnicos o artísticos**: tipo de lente, iluminación, paleta.
4. **Nivel de detalle o fidelidad**: básico, intermedio, avanzado, profesional.
5. **Restricciones negativas**: qué evitar (blur, deformed, text, etc).
6. (Opcional) **Formato de output**: prompt positivo, prompt negativo, CFG scale, etc.

---

### 2. Plantilla de Solicitud Efectiva

```text
Quiero que generes un prompt para Stable Diffusion (o Flux).

Tema: una ciudad flotante sobre el océano
Estilo: retrofuturista, Studio Ghibli
Iluminación: atardecer dorado, volumetric light
Técnica: digital painting con detalles cinematográficos
Nivel de detalle: profesional

Formato requerido:
1. Prompt positivo
2. Prompt negativo sugerido
3. CFG recomendado
```

ChatGPT responderá con una estructura como:

```
Prompt positivo:
a floating city above a golden ocean at sunset, retrofuturistic architecture, volumetric lighting, soft clouds, highly detailed, cinematic style, in the style of Studio Ghibli, masterpiece

Prompt negativo:
blurry, lowres, bad anatomy, deformed, watermark, text, poorly drawn

CFG recomendado: 8.5
```

---

### 3. Variantes de Instrucciones

* **Prompt desde narrativa**:
  "Describe en prompt visual una escena en la que un monje ciego recorre una biblioteca infinita iluminada por luciérnagas."

* **Optimizar prompt existente**:
  "Este prompt es muy genérico: 'a fantasy forest'. Hazlo profesional y detallado."

* **Adaptar prompt a estilo específico**:
  "Transforma este prompt a un estilo inspirado en Moebius."

* **Generar prompts iterativos**:
  "Dame 3 variantes estilísticas del mismo tema para exploración visual."

---

### 4. Buenas Prácticas

* Especifica claramente el **modelo objetivo** (SD 1.5, SDXL, Flux, etc.) si sabes cuál usarás.
* Indica si quieres usar **ControlNet, LoRA (incluir TriggerWords) o embeddings**: ChatGPT puede incluir menciones si se lo pides.
* Puedes pedir **pesos semánticos** en notación: `(term:1.4)` o `((term))`.
* Si trabajas con scripts, solicita formato JSON o Python-ready para integración.

---

### 5. Ejemplo Avanzado

```text
Dame un prompt profesional para Flux que represente una ruina alienígena en un desierto con luz cenital. Que use referencias de Moebius y tenga un estilo de acuarela digital. Incluye un prompt negativo con artefactos típicos y sugerencia de CFG.
```

**Output esperado:**

Prompt positivo:
an ancient alien ruin in the middle of a desert, zenithal lighting, surreal forms, soft watercolor texture, detailed stonework, minimal color palette, in the style of Moebius, digital watercolor, ethereal mood, masterpiece

Prompt negativo:
lowres, bad anatomy, deformed, overexposed, jpeg artifacts, watermark, text

CFG recomendado: 9.0

---

### 6. Recomendaciones Finales

* Usa el mismo formato al iterar con variantes.
* Guarda los mejores prompts junto con la imagen, seed, sampler y modelo.
* Aprovecha la capacidad de ChatGPT para refinar, expandir o sintetizar familias de prompts.

ChatGPT no reemplaza la curación humana, pero sí acelera la exploración sistemática con control semántico. La clave está en pedir con precisión y evaluar iterativamente.
