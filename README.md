# Sistema RAG con NVIDIA AI Endpoints :rocket:

Sistema de Recuperación Aumentada por Generación (RAG) para documentos PDF, utilizando modelos avanzados de NVIDIA y técnicas de procesamiento de lenguaje natural.

## Visión General

Este proyecto implementa un pipeline completo para:
- Procesar documentos PDF (extracción, división de texto)
- Generar embeddings con modelos de NVIDIA
- Realizar búsquedas semánticas usando FAISS
- Responder preguntas mediante el modelo Llama 3.3 de NVIDIA

**Casos de uso**: Investigación académica, análisis de documentos legales, asistentes inteligentes para PDFs.

## Requisitos Previos

- Python 3.9+
- NVIDIA API Key (registrada en [NVIDIA NGC](https://catalog.ngc.nvidia.com/))
- Librerías listadas en `requirements.txt`

## Instalación

1. Clonar el repositorio:
```bash
git clone [repo-url]
cd [repo-name]
```

2. Instalar dependencias:
```bash
pip install -r requirements.txt
```

3. Configurar API key (opción preferida: usar variables de entorno):
```bash
export NVIDIA_API_KEY="tu_api_key_aquí"
```

## Uso Básico

1. Colocar tu PDF en la carpeta `/data`
2. Ejecutar el sistema:
```python
python rag_pipeline.py --pdf_path /data/tu_documento.pdf
```

3. Interactuar con el asistente:
```
🌟 Asistente RAG - Basado en tu PDF 📄

🤔 Tu pregunta: ¿Cuál es el objetivo principal del documento?
```

## Estructura del Código

```
/project
├── rag_pipeline.py          # Pipeline principal
├── config.py                # Configuraciones
├── utils/                   # Utilidades
│   ├── text_processing.py   # Procesamiento de texto
│   └── error_handling.py    # Manejo de errores
├── data/                    # Documentos PDF
└── README.md                # Este archivo
```

## Configuración Avanzada

Parámetros personalizables en `config.py`:
```python
CHUNK_SIZE = 200              # Tamaño de fragmentos de texto
MODEL_NAME = "llama-3.3-nemotron-super-49b-v1"
SEARCH_KWARGS = {"k": 2}      # Resultados por consulta
MAX_TOKENS = 400              # Límite para embeddings
```

## Ejemplo Completo

Procesamiento de un trabajo académico:
```python
from pipeline import create_rag_system

rag = create_rag_system(
    pdf_path="Trabajo_de_Titulo_FINAL.pdf",
    chunk_size=150,           # Más pequeño para español
    model="nvidia/llama-3.3"
)

response = rag.query("¿Qué metodología usó el autor?")
print(response["result"])
```

## Licencia

MIT License - Ver archivo [LICENSE](LICENSE) para detalles.

## Notas Técnicas

:warning: **Requisitos de Hardware**:  
Se recomienda GPU NVIDIA para embeddings grandes. Para CPU:
- Reducir `chunk_size` a 100-150
- Usar `NVIDIAEmbeddings(..., model="small")`

:tools: **Soporte**:  
Problemas conocidos y soluciones en [ISSUES.md](ISSUES.md)
```

### Características clave de este README:
1. **Estructura modular**: Separación clara de componentes
2. **Instrucciones detalladas**: Desde instalación hasta uso avanzado
3. **Ejemplos prácticos**: Código listo para copiar-pegar
4. **Notas técnicas**: Optimizaciones para diferentes hardware
5. **Enfoque en español**: Parámetros ajustados para texto en español

¿Te gustaría que agregue alguna sección adicional? Por ejemplo:
- 📊 Benchmarks de rendimiento
- 🧩 Ejemplo de archivo requirements.txt
- 🎥 Demo con GIF animado
