# Curso: IA Generativa

**Lugar de impartición:** Universidad de Extremadura (Campus de Cáceres, Campus de Badajoz)

**Fecha:** A determinar

**Duración:** 50 horas

**Profesores:**

Emilio Delgado Muñoz (edm@unex.es)

**Conocimientos Previos Recomendados:**

* Programación en Python
* Conocimientos básicos de Deep Learning (opcional pero recomendable)

**Descripción del Curso:**

Este curso está diseñado para proporcionar a los estudiantes conocimientos fundamentales y habilidades prácticas en el campo de la Inteligencia Artificial Generativa. El curso explorará diferentes tipos de modelos generativos, con un enfoque especial en modelos de difusión para la generación de imágenes, incluyendo Stable Diffusion y Gemini 2.0 Exp, modelos para la generación de vídeo con Wan2.1 y modelos para la generación de audio con DiffRythim. Los estudiantes aprenderán a utilizar herramientas y frameworks populares en cada área, a evaluar la calidad de los resultados generados y a desarrollar un proyecto práctico aplicando estas tecnologías. Se hará énfasis en la experimentación práctica y en la comprensión de los principios subyacentes de cada técnica.

**Metodología:**

Se seguirá un enfoque PBL (aprendizaje basado en proyectos, Project Based Learning). Se plantearán desafíos y tareas prácticas que los estudiantes deberán resolver utilizando las herramientas y técnicas aprendidas en cada módulo. A medida que sea necesario, se introducirá la teoría fundamental detrás de los modelos generativos.

**Programa del Curso:**

## Módulo 1: Introducción a la IA Generativa (6 horas)

* Definición y panorama de la IA Generativa
* Tipos de modelos generativos: GANs, VAEs, Modelos de Flujo, Modelos de Difusión
* Aplicaciones actuales de la IA Generativa: arte, diseño, entretenimiento, ciencia
* Consideraciones éticas y desafíos de la IA Generativa

## Módulo 2: Modelos de Difusión y Generación de Imágenes (23 horas)

* Fundamentos de los Modelos de Difusión (2 horas)
    * Proceso de difusión (forward process)
    * Proceso de eliminación de ruido (reverse process)
    * Entrenamiento de modelos de difusión
* **Generación de Imágenes con Stable Diffusion (17 horas)**
    * Introducción a Stable Diffusion
        * Arquitectura y componentes clave
        * Instalación y configuración del entorno
        * Uso de la interfaz de línea de comandos y librerías de Python
    * Experimentación práctica con Stable Diffusion
        * Generación de imágenes a partir de texto (text-to-image)
        * Edición y manipulación de imágenes (image-to-image, inpainting, outpainting)
        * Control de la generación con prompts y parámetros avanzados
        * Entrenamiento de modelos personalizados (fine-tuning [DreamBooth](https://colab.research.google.com/drive/1IcBoNKTgx-2xDYU6aQYE6Fr-AnDiFTAa?usp=sharing)) - Introducción
    * Evaluación de la calidad de las imágenes generadas: métricas comunes y evaluación subjetiva
* **Generación de Imágenes con Gemini 2.0 Exp (4 horas)**
    * Introducción al modelo Gemini 2.0 Exp para generación de imágenes
        * Arquitectura y características principales
        * Acceso y uso de la API o herramientas disponibles
    * Experimentación práctica con Gemini 2.0 Exp
        * Generación de imágenes a partir de texto (text-to-image)
        * Exploración de las capacidades y limitaciones del modelo
        * Comparación con Stable Diffusion (si es pertinente)
    * Evaluación de la calidad de las imágenes generadas con Gemini 2.0 Exp

## Módulo 3: Generación de Vídeo con Wan2.1 (4 horas)

* Desafíos de la generación de vídeo con IA
* Introducción a Wan2.1: modelo de generación de vídeo desarrollado por la empresa Qwen
    * Arquitectura y principios de funcionamiento
    * Instalación y configuración
* Experimentación práctica con Wan2.1
    * Generación de vídeo a partir de texto (text-to-video)
    * Manipulación y edición de vídeo generado
    * Control de los parámetros de generación
* Alternativas y modelos relacionados para la generación de vídeo
* Evaluación de la calidad de los vídeos generados: métricas y consideraciones específicas

## Módulo 4: Generación de Audio con DiffRythim (4 horas)

* Introducción a la generación de audio con IA
* Modelos generativos para audio: WaveNet, SampleRNN, DiffRythim
    * Principios básicos de DiffRythim
    * Instalación y configuración
* Experimentación práctica con DiffRythim
    * Generación de audio a partir de texto (text-to-audio)
    * Generación de música
    * Manipulación y edición de audio generado
* Evaluación de la calidad del audio generado: métricas y evaluación perceptiva

## Módulo 5: Evaluación de Modelos Generativos y Proyecto Final (13 horas)

* **Técnicas y Métricas de Evaluación (1 hora):**
    * Métricas objetivas para imágenes (FID, IS, PSNR, SSIM)
    * Evaluación subjetiva y estudios de percepción
    * Desafíos en la evaluación de la creatividad y la coherencia
* **Presentación del Proyecto Final (12 horas):**
    * Cada estudiante o grupo presentará su proyecto, explicando la idea, la metodología utilizada, los resultados obtenidos y la evaluación realizada.

## Calendario del Curso: (aprox.)

Teoría (Horas) | Laboratorio (Horas) | Actividad Asíncrona | Total Horas | Contenido                                                                 |
:-------------: | :-----------------: | :------------------: | :----------: | :------------------------------------------------------------------------ |
|        3        |          3          |          0           |      6       | Introducción a la IA Generativa                                         |
|        3        |          12          |          8           |      23      | Stable Diffusion: Experimentación y Generación de Imágenes      |
|        1        |          3          |          0           |      4       | Generación de Vídeo con Wan2.1                                          |
|        1        |          3          |          0           |      4       | Generación de Audio con DiffRythim                                       |
|        1        |          11          |          1           |      13      | Generación de Imágenes con Gemini 2.0 Exp, Evaluación y Proyecto Final (Asíncrono) [POR DEFINIR] |
| **9** |       **32** |         **9** |          **50** |     |                                                                           |

## Proyecto Final:

El proyecto final consistirá en que los estudiantes, en grupos pequeños, deberán **seleccionar un tema o desafío específico que pueda ser abordado utilizando las técnicas de IA generativa aprendidas en el curso**.

**Posibles ideas para el proyecto:**

* Generación de contenido multimedia coherente: Crear una secuencia de imágenes (utilizando Stable Diffusion o Gemini 2.0 Exp), un vídeo corto con su banda sonora (generada con DiffRythim o modelos similares) que cuenten una historia o transmitan un mensaje específico.
* Estilización y transformación de contenido existente: Utilizar modelos generativos para aplicar estilos artísticos a vídeos (con Wan2.1), transformar imágenes en diferentes formatos (con Stable Diffusion o Gemini 2.0 Exp) o generar variaciones de una pieza musical (con DiffRythim).
* Creación de personajes o mundos virtuales: Generar imágenes (con Stable Diffusion o Gemini 2.0 Exp) y/o vídeos (con Wan2.1) de personajes o entornos virtuales basados en descripciones textuales.
* Exploración creativa con prompts avanzados: Investigar y experimentar con prompts complejos para Stable Diffusion, Gemini 2.0 Exp, Wan2.1 y DiffRythim para generar resultados novedosos e interesantes.
* Análisis comparativo de modelos: Comparar la calidad y las características de diferentes modelos generativos para una tarea específica (por ejemplo, comparar Stable Diffusion y Gemini 2.0 Exp para la generación de imágenes).
* Desarrollo de una pequeña creación artística: Crear una pieza artística original utilizando modelos generativos como herramienta creativa (por ejemplo, una composición musical generada con DiffRythim y una imagen / video generada con Stable Diffusion).
* Ejemplo básico: [StoryLine Gemini 2.0 Exp](https://aistudio.google.com/app/prompts?state=%7B%22ids%22:%5B%221RKmtghrU5JuEcQr4eO64SAXTN9ITB3u5%22%5D,%22action%22:%22open%22,%22userId%22:%22103782615399509209696%22,%22resourceKeys%22:%7B%7D%7D&usp=sharing)

**Requisitos del proyecto:**

* **Utilización de al menos dos de las modalidades de generación aprendidas** (imágenes, vídeo, audio), siendo obligatorio el uso de al menos uno de los modelos de difusión para imágenes (Stable Diffusion o Gemini 2.0 Exp).
* **Documentación del proceso:** Descripción del tema elegido, la metodología utilizada, los modelos y herramientas empleadas, los parámetros ajustados y los desafíos encontrados.
* **Evaluación de los resultados:** Aplicación de las métricas de evaluación aprendidas en el Módulo 5 (opcional) y una reflexión sobre la calidad y la coherencia del contenido generado.
* **Presentación final:** Presentación oral del proyecto al resto de la clase. Se valorará la claridad, la creatividad y la originalidad de la presentación.