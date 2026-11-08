# Actividad 06 - Ítem C: Faster R-CNN en video

Aplicación de detección de objetos con Faster R-CNN MobileNetV3 FPN 320, pesos preentrenados en COCO, utilizando OpenCV y PyTorch.

## Instalación

Python 3.10 o superior recomendado. Crear entorno virtual:

```bash
python -m venv .venv
.venv\Scripts\activate
pip install torch torchvision --index-url https://download.pytorch.org/whl/cu118
pip install opencv-python numpy
```

Si tu instalación actual de PyTorch y Torchvision con CUDA ya funciona, puedes conservarla. Verifica la compatibilidad en https://pytorch.org/get-started/locally/ . Alternativa para CPU: `pip install torch torchvision opencv-python numpy`.

## Ejecución

Webcam:
```bash
python detector_faster_rcnn.py
```

Video local:
```bash
python detector_faster_rcnn.py --video prueba.mp4
```

Guardar video:
```bash
python detector_faster_rcnn.py --guardar
```

Otros parámetros: `--conf 0.5`, `--width 640`. Teclas: Q salir; S captura.

## Evidencias y métricas

- `resultados/metricas.csv`: latencia de inferencia por fotograma, FPS de procesamiento completo, número de detecciones.
- `resultados/captura_*.jpg`: capturas bajo demanda.
- `resultados/deteccion.mp4`: salida si se usa `--guardar`.

Nota: FPS de visualización/procesamiento y 1000/latencia de inferencia no son exactamente equivalentes. El CSV contiene FPS del ciclo de procesamiento, incluida la captura y presentación, y latencia exclusivamente del modelo, con sincronización CUDA.

## Modelo

Faster R-CNN MobileNetV3 Large FPN 320 de Torchvision (COCO). Es una variante liviana apropiada para una demostración en webcam; no es YOLO. El rendimiento real depende del hardware, escenario y resolución. Se descargan los pesos en la primera ejecución.

## Comparación con YOLO

Se recomienda usar el mismo video, resolución, umbral de confianza cuando sea comparable y dispositivo. Reportar FPS, latencia promedio y observaciones de detección. Para precisión real (mAP) usar videos/imágenes anotados con cajas verdaderas; la confianza del modelo no es una medida de accuracy.
