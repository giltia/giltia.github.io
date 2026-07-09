---
title: "Whisper-LM con léxico maya: corrección de transcripciones ASR de maya yucateco usando Gemini y un diccionario como referencia"
authors:
- admin
date: "2026-07-09T00:00:00Z"
doi: ""

# Schedule page publish date (NOT publication's date).
publishDate: "2026-07-09T00:00:00Z"

# Publication type.
# Accepts a single type but formatted as a YAML list (for Hugo requirements).
# Enter a publication type from the CSL standard.
publication_types: ["report"]

# Publication name and optional abbreviated publication name.
publication: "Cuaderno técnico (Google Colab)"
publication_short: ""

abstract: Presentamos un cuaderno de Google Colab que implementa un pipeline de posprocesamiento para transcripciones automáticas de maya yucateco generadas con Whisper. Dado que Whisper no tiene soporte para el maya yucateco, sus salidas son ruidosas y con frecuencia se identifican erróneamente como español, inglés o incluso japonés. El pipeline combina tres componentes; un normalizador ortográfico basado en reglas morfológicas del maya yucateco, un léxico maya–español de 2,988 entradas usado como referencia ortográfica al estilo RAG, y un modelo de lenguaje (Gemini 2.0 Flash) que corrige la transcripción sin traducirla. Evaluado sobre 1,010 segmentos de audio con transcripción de referencia, el sistema reduce marginalmente el CER (1.074 → 1.073) y el WER (1.180 → 1.169) respecto a la salida cruda de Whisper turbo, lo que evidencia tanto el potencial como los límites de la corrección post-ASR cuando el modelo acústico base desconoce la lengua.

# Summary. An optional shortened abstract.
summary: Un pipeline en Google Colab que corrige transcripciones ruidosas de Whisper en maya yucateco combinando reglas morfológicas, un léxico de 2,988 entradas y Gemini 2.0 Flash como modelo corrector.

tags:
- Yucatec Maya
- ASR
- Whisper
- Large Language Models
- Low-Resource Languages
featured: true

links: []
url_pdf: ''
url_code: ''
url_dataset: ''
url_poster: ''
url_project: ''
url_slides: ''
url_source: ''
url_video: ''

# Associated Projects (optional).
projects: []

# Slides (optional).
slides: ''
---

## ¿Qué problema resuelve este cuaderno?

Whisper, el sistema de reconocimiento automático de voz (ASR) de OpenAI, no incluye el maya yucateco entre sus lenguas soportadas. Al transcribir audio en maya, el modelo produce salidas muy ruidosas y con frecuencia "detecta" la lengua equivocada: en nuestros datos, segmentos en maya fueron etiquetados como español, inglés e incluso japonés. Este cuaderno explora una pregunta práctica: **¿cuánto puede mejorar un modelo de lenguaje grande (LLM) la salida de Whisper si le damos un léxico maya como referencia?**

## Arquitectura del pipeline

El flujo completo es:

```
Audio → Whisper (turbo) → Normalizador de reglas → Gemini + léxico → Normalizador → Evaluación (CER/WER)
```

### 1. Datos de entrada

Se parte de un CSV (`transcription_results41Turbo.csv`) con 1,010 segmentos de audio ya transcritos por Whisper turbo. Cada fila incluye la transcripción de referencia hecha por humanos (`original_transcription`), la predicción de Whisper (`whisper_prediction`), la lengua detectada y métricas iniciales (chrF, WER, CER).

### 2. Léxico maya como referencia (componente RAG)

Se carga un diccionario maya–español en formato TSV (`yua_dictionary.tsv`) con **2,988 entradas**. Una clase `YuaLexicon` ofrece búsqueda exacta y búsqueda difusa (*fuzzy matching* con `difflib.get_close_matches`), lo que permite encontrar la palabra maya válida más cercana a un token mal transcrito.

### 3. Normalizador ortográfico basado en reglas

Antes y después de pasar por el LLM, el texto se normaliza con reglas lingüísticas del maya yucateco tomadas de una gramática de referencia:

- **Reglas morfológicas de raíz**: por ejemplo, *bin* (ir) con raíz irregular *xi'* en futuro indefinido intransitivo, o posicionales como *chil*, *kul* y *wa'al* que pierden la *l* antes de *-tal*.
- **Patrones regulares "seguros"**: *bins* → *bis*, *taals* → *taas*, y verbos que cambian la *b* final por estructura con saltillo (*jáalk'ab* → *jáalk'a'a*).
- **Verificación contra el léxico**: si la forma normalizada existe en el diccionario, se conserva; si la original era válida, se respeta.

### 4. Corrección con Gemini (Whisper-LM)

Cada transcripción normalizada se envía a **Gemini 2.0 Flash** con un prompt que incluye hasta 500 palabras del léxico maya como referencia ortográfica. Las instrucciones clave del prompt son: corregir respetando la gramática y ortografía estándar del maya yucateco, **no traducir al español**, elegir la opción más probable según el léxico y devolver únicamente el texto corregido.

### 5. Evaluación

Se calcula la tasa de error por carácter (CER) y por palabra (WER) con `editdistance`, comparando contra la transcripción humana de referencia:

| Métrica | Whisper turbo | Whisper-LM (este pipeline) |
|---------|--------------|---------------------------|
| CER medio | 1.0743 | 1.0725 |
| WER medio | 1.1796 | 1.1692 |

## ¿Qué aprendimos?

La mejora es **marginal**: el posprocesamiento con LLM y léxico recupera algo de forma ortográfica, pero no puede reconstruir información que el modelo acústico nunca capturó. Con valores de CER/WER superiores a 1.0, la salida de Whisper está tan alejada de la referencia que la corrección textual tiene poco material con el que trabajar. La conclusión práctica es que, para el maya yucateco, **el cuello de botella está en el modelo acústico**: se necesita ajuste fino (*fine-tuning*) de Whisper con datos de habla maya, y no solo corrección posterior.

## Próximos pasos

- Ajuste fino de Whisper con audio transcrito en maya yucateco.
- Ampliar las reglas ortográficas (`ORTHO_RULES`) con los errores recurrentes observados en las transcripciones.
- Ampliar el léxico y experimentar con recuperación selectiva (enviar al prompt solo las entradas relevantes para cada segmento, en lugar de una lista fija).

## Acceso al cuaderno

Si te interesa el cuaderno de Colab, puedes ponerte en contacto con el autor en [jaziel.carballo@gmail.com](mailto:jaziel.carballo@gmail.com).
