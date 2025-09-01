# DL_Proyecto_RiveroHayner_GANs
## Comparación de Funciones de Pérdida en Pix2Pix: Colorización de sketchs

Una comparación de tres configuraciones diferentes de funciones de pérdida para GANs Pix2Pix aplicadas a la colorización de sketchs, evaluando su impacto en la calidad de imagen, estabilidad de entrenamiento y costo computacional.

## Ruta Elegida y Dataset

- **Ruta elegida**: GANs (Image to Image).
- **Dataset**: [Anime Sketch Colorization Pair Dataset](https://www.kaggle.com/datasets/ktaebum/anime-sketch-colorization-pair).
  - **Fuente/Licencia**: Kaggle, bajo licencia CC0 (Dominio Público).
  - **Tamaño**: 14.200 pares de entrenamiento y 3.545 pares de validación.
  - **Formato**: Imágenes lado a lado (sketch a la izquierda, color a la derecha) en resolución 1024x512 píxeles.
  - **Uso**: Limitado a un total de 10.000 imágenes por fines prácticos, además se usó una version optimizada con un script debido al peso excesivo del dataset. [Drive del dataset optimizado](https://drive.google.com/drive/folders/160bTiC_yAv5teC7MZu1bHrQbSG83Uh0U?usp=sharing)

## Cómo Ejecutar
- Preferiblemente abre el proyecto preconfigurado y listo para ejecutar desde el siguiente enlace: **[DL_Project](https://lightning.ai/cliche-1/slack-bot/studios/dl-project/code?source=copylink)**
- **Plataforma utilizada:** Se utilizó Lightning AI Studio porque mantiene los archivos del proyecto indefinidamente y tiene accesi gratuito a GPUs más potentes durante horas limitadas para tener una mayor flexibilidad durante el desarrollo.
- **Selección de GPU**: Recomendada A100 (40 GB) para un entrenamiento total de ~3-4 horas.

## Cómo Entrenar y Evaluar

- Pasos para entrenar: Ejecuta todas las celdas ("Run All") en el notebook `Proyecto_GANs.ipynb` o selecciona celdas específicas. Los procesos están preconfigurados y divididos en secciones (Setup, Preprocesamiento, ...,  Entrenamiento A/B/C, Evaluación, etc).
- Pasos breves para evaluar: Ejecuta las secciones de Evaluación en el notebook. Ajusta parámetros en la clase `Config` si es necesario (por ejemplo, reduce **`NUM_EPOCHS`** a 25 y **`BATCH_SIZE`** a 8 para un entrenamiento más rápido pero con menor calidad).

## Cómo Generar la Tabla y el Gráfico de Métricas

- Ejecuta el notebook completo o las secciones de Evaluación y Resultados.
- Las tablas y gráficos se generan automáticamente y se guardan en:
  - **`results/summary/csv/`**
  - **`results/summary/img_reports/`**
  
## Estructura del Proyecto

```
├── notebooks/
│   ├── Proyecto_GANs.ipynb          # Notebook principal dividido en secciones
│   ├── results/
│   │   ├── generated_samples/       # Imágenes generadas durante el entrenamiento
│   │   │   ├── standard/            # Configuración A
│   │   │   ├── perceptual/          # Configuración B
│   │   │   └── regularized/         # Configuración C
│   │   └── summary/
│   │       ├── img_reports/         # Gráficos y visualizaciones
│   │       └── csv/                 # Tablas y métricas en formato CSV
│   └── checkpoints/                 # Modelos guardados (cada 10 epochs)
├── README.md
└── requirements.txt              
```

## Requisitos

La celda inicial del notebook está configurada para instalar las dependencias. El archivo `requirements.txt` incluye las dependecias.

## Recursos de referencia principales utilizados durante la elaboración del Proyecto
### Artículos y Papers
- [Image-to-Image Translation with Conditional Adversarial Networks](https://arxiv.org/abs/1611.07004)
- [U-Net Architecture Explained](https://www.geeksforgeeks.org/machine-learning/u-net-architecture-explained/)
### Repositorios
- [Pix2pix: Image-to-Image Translation with Conditional Adversarial Networks](https://github.com/phillipi/pix2pix)
- [pix2pix: Painting with conditional GAN](https://github.com/romacka/pix2pix)
### Multimedia
- [Pix2Pix Image to Image Translation - Everything you need to know!](https://www.youtube.com/watch?v=VGNM5ou2vUE)
