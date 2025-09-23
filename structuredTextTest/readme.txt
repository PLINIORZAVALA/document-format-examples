AWS TEXTRACT DOCUMENT EXTRACTION API
====================================

DESCRIPCIÓN
-----------
API profesional para extracción de texto de documentos utilizando AWS Textract
y librerías locales de Python. Soporta múltiples formatos de archivo y fuentes
de datos (archivos locales, S3 URIs, URLs HTTPS).

AUTOR
-----
Plinior Zavala
Versión: 1.0.0
Fecha: 2024

CARACTERÍSTICAS PRINCIPALES
---------------------------
- Doble motor de extracción: AWS Textract + Librerías locales Python
- Múltiples fuentes: Archivos locales, S3 URIs, URLs HTTPS
- Procesamiento inteligente: Síncrono/asíncrono según el formato
- API REST moderna: FastAPI con documentación automática
- Manejo robusto de errores: Validaciones y logs detallados
- Escalable: Diseñado para entornos de producción

FORMATOS SOPORTADOS
------------------

AWS Textract (OCR avanzado):
- PDF - Procesamiento asíncrono vía S3
- TIFF - Procesamiento asíncrono para archivos grandes
- PNG/JPG/JPEG - Procesamiento síncrono

Extracción local (Python):
- DOCX - Microsoft Word
- XLSX/XLS - Microsoft Excel
- PPTX - Microsoft PowerPoint
- RTF - Rich Text Format
- ODT - OpenDocument Text

Texto estructurado:
- TXT - Archivos de texto plano
- MD - Markdown
- LOG - Archivos de log
- JSON - JavaScript Object Notation
- CSV - Comma Separated Values
- XML - eXtensible Markup Language
- HTML - HyperText Markup Language
- YAML - YAML Ain't Markup Language
- INI - Archivos de configuración

INSTALACIÓN
-----------
1. Clonar repositorio
2. Crear entorno virtual: python -m venv venv
3. Activar entorno: source venv/bin/activate
4. Instalar dependencias: pip install -r requirements.txt
5. Configurar AWS: aws configure
6. Ejecutar: python fastapi_app.py

ENDPOINTS PRINCIPALES
--------------------
- POST /api/extract - Procesa archivos subidos
- POST /api/extract-url - Procesa desde URLs/S3
- GET /health - Health check
- GET /docs - Documentación Swagger

CONFIGURACIÓN
------------
Variables de entorno:
- AWS_REGION=us-east-1
- AWS_S3_BUCKET=textract-plinior-bucket

LÍMITES
-------
- Procesamiento síncrono: Máximo 10 MB
- Procesamiento asíncrono: Máximo 500 MB
- Descarga HTTPS: Máximo 16 MB

SOPORTE
-------
Para soporte técnico y consultas, contactar al autor.
Documentación completa disponible en /docs
