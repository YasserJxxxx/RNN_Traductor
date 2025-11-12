# 🇪🇸➡️🇬🇧 Traductor RNN (Seq2Seq) Español → Inglés

Este proyecto presenta un **traductor automático de oraciones del español al inglés**, desarrollado utilizando una **Red Neuronal Recurrente (RNN)** bajo una arquitectura **Seq2Seq (Sequence-to-Sequence)** con celdas **LSTM (Long Short-Term Memory)**.  
El sistema ha sido diseñado y optimizado para ejecutarse en **Google Colab**, aprovechando la integración con **Google Drive** para el almacenamiento y recuperación automática de los pesos del modelo.

El propósito de este proyecto es proporcionar un ejemplo educativo y práctico de cómo funcionan los traductores neuronales a nivel básico, sin depender de modelos preentrenados masivos como los de Google Translate o DeepL, permitiendo así comprender cada etapa del pipeline de traducción.

---

## 🚀 Características Principales

✅ Implementa un **modelo Seq2Seq completo** (encoder + decoder) con LSTM.  
✅ Soluciona el **colapso del modelo** mediante normalización de texto y preprocesamiento robusto.  
✅ **Carga y guardado automático de pesos** en Google Drive, evitando repetir entrenamientos.  
✅ Modo de **traducción interactiva** desde la terminal o consola de Colab.  
✅ Entrenamiento configurable con parámetros como número de muestras, épocas y dimensión latente.  
✅ Código totalmente documentado, modular y adaptable a otros pares de idiomas.  
✅ Compatible con GPU de Colab para acelerar el entrenamiento.  

---

## 🧠 Arquitectura del Modelo

El traductor utiliza una arquitectura **Encoder–Decoder**, que es un paradigma estándar en tareas de traducción automática neuronal (NMT - Neural Machine Translation).

### 🔹 1. Encoder (Codificador)
Procesa la secuencia de entrada en español carácter por carácter (vectorizada en formato one-hot).  
Resume toda la información semántica de la frase en dos vectores de estado:  
  - state_h: estado oculto del LSTM  
  - state_c: estado de la celda del LSTM  
Estos estados son la representación abstracta de la oración en el espacio latente.

### 🔹 2. Decoder (Decodificador)
Recibe los estados finales del encoder como entrada inicial.  
Genera la secuencia de salida (en inglés) carácter por carácter, prediciendo cada símbolo de forma autoregresiva.  
Durante el entrenamiento utiliza la técnica de **Teacher Forcing**, donde cada paso recibe como entrada el carácter correcto previo en lugar de su propia predicción.

### 🔹 3. Inferencia (Traducción en tiempo real)
Se crean modelos separados para **inferencia**, permitiendo traducir frases nuevas sin volver a entrenar.  
Se genera la traducción carácter a carácter hasta que se predice el token de fin (\n).  

---

## 📂 Estructura del Proyecto
plaintext


📁 Traductor_RNN_Español_Inglés/
│
├── traductor_rnn_es_en.py           # Código principal del proyecto
├── README.md                        # Documentación del repositorio
├── spa-eng.zip                      # Dataset descargado automáticamente
├── /spa-eng/spa.txt                 # Dataset descomprimido (pares español-inglés)
└── /drive/MyDrive/Colab_Modelos/    # Carpeta de Google Drive para pesos del modelo
