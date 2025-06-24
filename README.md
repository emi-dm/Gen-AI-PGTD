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
   # En Linux/Mac
   source .venv/bin/activate
   # En Windows
   .venv\Scripts\activate
   ```
3. **Instala PyTorch** siguiendo las instrucciones de la web oficial ([https://pytorch.org/get-started/locally/](https://pytorch.org/get-started/locally/)), eligiendo tu sistema operativo y si tienes GPU o no.
4. **Instala las dependencias** desde el fichero `requirements.txt`:
   ```bash
   uv pip install -r requirements.txt
   ```
5. **Explora las carpetas** y revisa los materiales disponibles.
6. **Lee las instrucciones** específicas en cada carpeta o archivo para ejecutar los ejemplos.
7. Si tienes dudas o sugerencias, ¡abre un issue o contribuye con tus propias mejoras!

---

## 🤝 Contribuciones

¡Las contribuciones son bienvenidas! Si tienes ideas, mejoras o encuentras algún error, no dudes en hacer un pull request o abrir un issue.

---

## 📬 Contacto

Para cualquier consulta, puedes contactar con el equipo docente o dejar tus preguntas en el repositorio.

---

## ⚠️ Nota importante sobre PyTorch

- PyTorch **NO está incluido en el archivo `requirements.txt`** porque su instalación depende de tu sistema operativo y de si tienes o no GPU compatible. 
  
  Debes instalar PyTorch manualmente siguiendo las instrucciones de la web oficial ([https://pytorch.org/get-started/locally/](https://pytorch.org/get-started/locally/)). Selecciona tu sistema (Windows, Linux, Mac) y elige la opción adecuada para CPU o GPU. Por ejemplo, para Linux con CPU:
  ```bash
  pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cpu
  ```
  Para Windows con CPU:
  ```cmd
  pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cpu
  ```
  Si tienes GPU NVIDIA, selecciona la opción correspondiente en la web para aprovechar la aceleración.

---

¡Esperamos que este repositorio te ayude a aprender, experimentar y divertirte con la IA generativa! 🚀🤩

---

