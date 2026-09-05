# 🎙️ Speech-to-Text API (MaaS) con OpenAI Whisper y FastAPI

![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![FastAPI](https://img.shields.io/badge/FastAPI-0.100+-green.svg)
![OpenAI Whisper](https://img.shields.io/badge/OpenAI_Whisper-Transformer-orange.svg)
![Colab](https://img.shields.io/badge/Deployed_on-Google_Colab-F9AB00.svg)

## 📌 Visión General del Proyecto
Este proyecto es una solución de **Model-as-a-Service (MaaS)** que automatiza la conversión de grabaciones de llamadas a texto estructurado. Diseñado para entornos de análisis de datos y operaciones, expone un modelo fundacional de Deep Learning a través de una API RESTful, permitiendo la ingesta de archivos multimedia y devolviendo JSON listos para análisis de Procesamiento de Lenguaje Natural (NLP).

## 🚀 Arquitectura y Tecnologías
La arquitectura está pensada para separar el motor de inferencia pesada de la capa de consumo web:

*   **Inteligencia Artificial (Backend):** `OpenAI Whisper` (arquitectura Transformer Encoder-Decoder) soportado sobre `PyTorch`. Capaz de manejar audios ruidosos y jerga técnica sin necesidad de fine-tuning previo (Zero-shot).
*   **Procesamiento de Audio:** `FFmpeg` para la decodificación de formatos complejos (wav, mp3, mpeg) a formas de onda tensoriales.
*   **Microservicio (API):** `FastAPI` y `Uvicorn`. Elegido por su rendimiento asíncrono y la auto-generación de documentación (Swagger UI).
*   **Infraestructura de Despliegue:** Nube con aceleración por hardware GPU NVIDIA T4.

## ⚙️ Uso y Consumo de la API
El sistema cuenta con una interfaz interactiva Swagger UI. Alternativamente, se puede consumir programáticamente.

**Ejemplo de Petición (cURL):**
```bash
curl -X 'POST' \
  'https://[TU_URL]/api/v1/transcribir/' \
  -H 'accept: application/json' \
  -H 'Content-Type: multipart/form-data' \
  -F 'archivo=@audio_llamada.mpeg'
