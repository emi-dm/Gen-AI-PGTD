# 🚀 Gen-AI-PGTD

<div align="center">
  <img src="src/aigogh.jpg" alt="Portada: IA Gogh pintando La Noche Estrellada" style="max-width: 700px; border-radius: 12px; box-shadow: 0 4px 16px rgba(0,0,0,0.15); margin-bottom: 1em;" />
</div>

¡Bienvenido al repositorio de **Inteligencia Artificial Generativa** para el **Programa de Gestión y Transformación Digital (PGTD)**! 🤖✨

---

## 📚 ¿Qué encontrarás aquí?

Este repositorio reúne **materiales, ejemplos prácticos, recursos y documentación** para aprender y experimentar con IA generativa en el contexto de la generación de imágenes.

---

## 🗂️ Contenido

- 📝 **Ejercicios prácticos**: Scripts y notebooks para experimentar con modelos de IA generativa.
- 📖 **Material teórico**: Documentos, presentaciones y explicaciones sobre conceptos clave.
- 🔗 **Recursos adicionales**: Enlaces, referencias y lecturas recomendadas para profundizar en el tema.
- 💡 **Casos de uso**: Ejemplos reales de aplicación de IA generativa en empresas y organizaciones.

---

## 🎯 Objetivo

Facilitar el aprendizaje y la experimentación con herramientas de IA generativa, proporcionando ejemplos claros, recursos útiles y retos para los alumnos del PGTD. Queremos que explores, pruebes y te inspires para aplicar la IA en tus propios proyectos.

---

## 🚦 ¿Cómo empezar?

1. **Clona este repositorio** en tu equipo:
   ```bash
   git clone https://github.com/tu-usuario/Gen-AI-PGTD.git
   ```
2. **Crea un entorno virtual con Python 3.11** usando [uv](https://github.com/astral-sh/uv):
   ```bash
   uv venv .venv --python 3.11
   source .venv/bin/activate
   ```
3. **Instala las dependencias** desde el fichero `requirements.txt`:
   ```bash
   uv pip install -r requirements.txt
   ```
4. **Explora las carpetas** y revisa los materiales disponibles.
5. **Lee las instrucciones** específicas en cada carpeta o archivo para ejecutar los ejemplos.
6. Si tienes dudas o sugerencias, ¡abre un issue o contribuye con tus propias mejoras!

---

## 🤝 Contribuciones

¡Las contribuciones son bienvenidas! Si tienes ideas, mejoras o encuentras algún error, no dudes en hacer un pull request o abrir un issue.

---

## 📬 Contacto

Para cualquier consulta, puedes contactar con el equipo docente o dejar tus preguntas en el repositorio.

---

## ⚠️ Nota importante sobre PyTorch

- **Instalación de PyTorch (Windows y Linux):**
  PyTorch **NO está incluido en el archivo `requirements.txt`** porque su instalación depende de tu sistema operativo y de si tienes o no GPU compatible. 
  
  Debes instalar PyTorch manualmente siguiendo las instrucciones de la web oficial ([https://pytorch.org/get-started/locally/](https://pytorch.org/get-started/locally/)). Selecciona tu sistema (Windows, Linux, Mac) y elige la opción adecuada para CPU o GPU. Por ejemplo, para Linux con CPU:
  ```bash
  pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cpu
  ```
  Para Windows con CPU:
  ```cmd
  pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cpu
  ```
  Si tienes GPU NVIDIA, selecciona la opción correspondiente en la web para aprovechar la aceleración.

- **Después de instalar PyTorch**, puedes continuar instalando el resto de dependencias con:
  ```bash
  uv pip install -r requirements.txt
  ```

- **Activación del entorno virtual en Windows:**
  Si estás en Windows, después de crear el entorno virtual, actívalo con:
  ```cmd
  .venv\Scripts\activate
  ```
  (Recuerda usar doble barra invertida o una sola si lo escribes directamente en la terminal de Windows.)

---

¡Esperamos que este repositorio te ayude a aprender, experimentar y divertirte con la IA generativa! 🚀🤩

---

