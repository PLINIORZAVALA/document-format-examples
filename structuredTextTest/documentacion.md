# AWS Textract Document Extraction API

[![Python](https://img.shields.io/badge/Python-3.9+-blue.svg)](https://python.org)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.115+-green.svg)](https://fastapi.tiangolo.com)
[![AWS](https://img.shields.io/badge/AWS-Textract-orange.svg)](https://aws.amazon.com/textract/)

## 🚀 Descripción

API profesional para extracción de texto de documentos utilizando **AWS Textract** y **librerías locales de Python**. Soporta múltiples formatos de archivo y fuentes de datos.

## ✨ Características Principales

- **Triple motor de extracción**: AWS Textract + Librerías locales + Texto estructurado
- **Múltiples fuentes**: Archivos locales, S3 URIs, URLs HTTPS
- **Procesamiento inteligente**: Selección automática del motor óptimo
- **API REST moderna**: FastAPI con documentación automática
- **Manejo robusto de errores**: Validaciones y logs detallados

## 📋 Formatos Soportados

### AWS Textract (OCR avanzado)
- `PDF` - Procesamiento asíncrono vía S3
- `TIFF` - Procesamiento asíncrono para archivos grandes
- `PNG/JPG/JPEG` - Procesamiento síncrono

### Extracción local (Python)
- `DOCX` - Microsoft Word
- `XLSX/XLS` - Microsoft Excel
- `PPTX` - Microsoft PowerPoint
- `RTF` - Rich Text Format
- `ODT` - OpenDocument Text

### Texto estructurado (Nuevo)
- `TXT` - Archivos de texto plano
- `MD` - Markdown
- `LOG` - Archivos de log
- `JSON` - JavaScript Object Notation
- `CSV` - Comma Separated Values
- `XML` - eXtensible Markup Language
- `HTML` - HyperText Markup Language
- `YAML` - YAML Ain't Markup Language
- `INI` - Archivos de configuración

## 🛠️ Instalación

```bash
# Clonar repositorio
git clone <repository-url>
cd awstextract

# Crear entorno virtual
python -m venv venv
source venv/bin/activate

# Instalar dependencias
pip install -r requirements.txt

# Configurar AWS
aws configure
```

## ⚙️ Configuración

### Variables de entorno
```bash
export AWS_REGION=us-east-1
export AWS_S3_BUCKET=textract-plinior-bucket
```

## 🚀 Ejecución

```bash
# Desarrollo
python fastapi_app.py

# Producción
uvicorn fastapi_app:app --host 0.0.0.0 --port 8000 --workers 4
```

## 📚 Endpoints de la API

### 1. `/api/extract` - Archivos locales
```bash
# Texto estructurado (nuevo)
curl -X POST http://localhost:8000/api/extract \
  -F "file=@config.json" \
  -F "engine=auto"

# Imágenes con Textract
curl -X POST http://localhost:8000/api/extract \
  -F "file=@imagen.jpg" \
  -F "analysis_type=simple"

# Documentos Office con librerías locales
curl -X POST http://localhost:8000/api/extract \
  -F "file=@documento.docx" \
  -F "engine=local"
```

### 2. `/api/extract-url` - URLs y S3 URIs
```bash
# PDF desde S3
curl -X POST http://localhost:8000/api/extract-url \
  -F "source_url=s3://mi-bucket/documento.pdf" \
  -F "analysis_type=simple"

# HTML desde URL HTTPS
curl -X POST http://localhost:8000/api/extract-url \
  -F "source_url=https://ejemplo.com/pagina.html" \
  -F "analysis_type=simple"
```

## 📊 Parámetros de la API

### `engine`
- `auto` - Selección automática inteligente (recomendado)
- `textract` - Forzar AWS Textract
- `local` - Forzar librerías locales
- `structured` - Forzar texto estructurado (nuevo)

### `analysis_type`
- `simple` - Extracción básica de texto
- `forms` - Análisis de formularios y tablas (solo Textract)

## 🎯 Lógica de Selección Automática

1. **🥇 Texto estructurado** - Máxima prioridad (más rápido, sin costos)
2. **🥈 AWS Textract** - Para imágenes y PDFs (OCR de alta calidad)
3. **🥉 Librerías locales** - Para documentos Office

## 📈 Límites y Consideraciones

- **Procesamiento síncrono**: Máximo 10 MB
- **Procesamiento asíncrono**: Máximo 500 MB
- **Descarga HTTPS**: Máximo 16 MB
- **Texto estructurado**: Sin límites especiales

## 🔒 Permisos IAM Requeridos

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "textract:DetectDocumentText",
        "textract:AnalyzeDocument",
        "textract:StartDocumentTextDetection",
        "textract:StartDocumentAnalysis",
        "textract:GetDocumentTextDetection",
        "textract:GetDocumentAnalysis"
      ],
      "Resource": "*"
    },
    {
      "Effect": "Allow",
      "Action": [
        "s3:GetObject",
        "s3:PutObject"
      ],
      "Resource": "arn:aws:s3:::mi-bucket-textract/*"
    }
  ]
}
```

## 📝 Ejemplos de Respuesta

### Respuesta exitosa
```json
{
  "success": true,
  "filename": "config.json",
  "engine_used": "json",
  "text": "{\n  \"aplicacion\": {\n    \"nombre\": \"AWS Textract API\"\n  }\n}",
  "lines_count": 15,
  "average_confidence": 0.0,
  "analysis_type": "structured"
}
```

## 🐛 Solución de Problemas

### Error: "Formato no soportado"
- **Causa**: Extensión de archivo no incluida en ALLOWED_EXTENSIONS
- **Solución**: Verificar que el formato esté soportado

### Error: "BeautifulSoup no disponible"
- **Causa**: Librería no instalada para procesar HTML
- **Solución**: `pip install beautifulsoup4`

## 🤝 Contribución

1. Fork el proyecto
2. Crear rama de feature (`git checkout -b feature/AmazingFeature`)
3. Commit cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abrir Pull Request

## 📄 Licencia

Distribuido bajo la Licencia MIT. Ver `LICENSE` para más información.

## 📞 Contacto

**Plinior Zavala** - Autor del proyecto

Enlace del proyecto: [https://github.com/usuario/aws-textract-api](https://github.com/usuario/aws-textract-api)
