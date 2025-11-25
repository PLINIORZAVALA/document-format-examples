# DataTest - Test Data Repository

## 📋 Descripción

Este repositorio contiene una colección organizada de archivos de prueba para sistemas de procesamiento de documentos, extracción de texto y análisis de contenido. Los datos están estructurados para facilitar pruebas de APIs de extracción de texto (como AWS Textract), procesamiento de imágenes, y análisis de documentos en múltiples formatos.

## 🗂️ Estructura del Proyecto

```
dataTest/
├── 📸 Imágenes de Prueba
│   ├── 0.1.maxresdefault.jpg
│   ├── 0.2.yura.jpg
│   ├── 0.3.yurapro.jpg
│   ├── 1.6.img.jpeg - 1.9.img.jpeg
│   ├── 1.8.img.png
│   ├── 2.0.img.jpeg - 2.1.img.jpeg
│   ├── test_yuraPro.tiff
│   └── yuraPro.tiff
│
├── 📄 Documentos PDF
│   ├── 1.5.ficha-tecnica-rumi.pdf
│   └── fake.pdf
│
├── 📁 dataApple/
│   └── Archivos de formato Apple (Numbers, Pages, WebLoc)
│
├── 📚 dataLibrary/
│   └── Documentos de oficina (Word, Excel, PowerPoint, ODT, RTF)
│
├── 🌐 structuredTextTest/
│   └── Archivos de texto estructurado (JSON, CSV, XML, HTML, YAML, INI, MD)
│
└── ☁️ dowloadAWS/
    └── Archivos descargados desde AWS S3
```

## 📊 Tipos de Archivos Incluidos

### Imágenes
- **Formatos**: JPG, JPEG, PNG, TIFF
- **Uso**: Pruebas de OCR y reconocimiento de imágenes
- **Casos de prueba**: Imágenes de diferentes resoluciones y calidades

### Documentos PDF
- **Uso**: Pruebas de extracción de texto de documentos escaneados y nativos
- **Casos de prueba**: PDFs técnicos, formularios, documentos con múltiples páginas

### Documentos de Oficina
- **Formatos**: DOCX, XLSX, PPTX, ODT, RTF
- **Ubicación**: `dataLibrary/`
- **Uso**: Pruebas de extracción de contenido de documentos estructurados

### Archivos Apple
- **Formatos**: Numbers (.numbers), Pages (.pages), WebLoc (.webloc)
- **Ubicación**: `dataApple/`
- **Uso**: Pruebas de compatibilidad con formatos propietarios de Apple

### Texto Estructurado
- **Formatos**: JSON, CSV, XML, HTML, YAML, INI, MD, TXT
- **Ubicación**: `structuredTextTest/`
- **Uso**: Pruebas de parsing y procesamiento de datos estructurados

## 🎯 Casos de Uso

### 1. Pruebas de Extracción de Texto (OCR)
- Validar precisión de OCR en imágenes con diferentes calidades
- Probar procesamiento de documentos escaneados
- Evaluar rendimiento con diferentes formatos de imagen

### 2. Procesamiento de Documentos
- Extracción de texto de documentos PDF
- Análisis de documentos de oficina (Word, Excel, PowerPoint)
- Procesamiento de formatos propietarios

### 3. Análisis de Contenido
- Parsing de archivos estructurados (JSON, XML, CSV)
- Extracción de datos de documentos técnicos
- Procesamiento de configuraciones y documentación

### 4. Integración con AWS Services
- Pruebas con AWS Textract
- Validación de procesamiento asíncrono vía S3
- Testing de límites y casos edge

## 🔧 Uso Recomendado

### Para Desarrolladores
```bash
# Navegar al directorio
cd dataTest

# Usar archivos específicos para pruebas
python test_extraction.py --input 1.5.ficha-tecnica-rumi.pdf

# Probar con imágenes
python test_ocr.py --image 0.2.yura.jpg
```

### Para Testing Automatizado
```bash
# Ejecutar suite completa de pruebas
pytest tests/ --test-data-dir ./dataTest

# Probar formato específico
pytest tests/test_pdf_extraction.py --test-data 1.5.ficha-tecnica-rumi.pdf
```

## 📝 Convenciones de Nomenclatura

Los archivos siguen una convención de numeración para facilitar la organización:
- `0.x.*` - Archivos de referencia o ejemplos base
- `1.x.*` - Archivos de prueba primarios
- `2.x.*` - Archivos de prueba secundarios

## ⚠️ Consideraciones

- **Tamaño de archivos**: Algunos archivos pueden ser grandes; verificar espacio en disco antes de clonar
- **Datos sensibles**: Revisar archivos antes de compartir; pueden contener información de prueba
- **Formato**: Los archivos están organizados por tipo y propósito de prueba

## 🔗 Integración con Proyectos Relacionados

Este repositorio está diseñado para trabajar con:
- Sistemas de extracción de texto (AWS Textract, Tesseract)
- APIs de procesamiento de documentos
- Sistemas de análisis de contenido
- Pipelines de ETL para documentos

## 📦 Mantenimiento

### Agregar Nuevos Archivos de Prueba
1. Colocar archivos en el directorio apropiado según su tipo
2. Seguir la convención de nomenclatura existente
3. Documentar casos de uso específicos si es necesario

### Organización
- Mantener estructura de directorios por tipo de archivo
- Actualizar este README al agregar nuevas categorías
- Documentar casos de prueba especiales

## 📄 Licencia

Este repositorio contiene datos de prueba para uso en desarrollo y testing. Verificar licencias de los archivos individuales antes de uso comercial.

## 👤 Autor

**Plinior Zavala**

---

## 📚 Referencias

Para más información sobre procesamiento de documentos y extracción de texto, consultar:
- [AWS Textract Documentation](https://docs.aws.amazon.com/textract/)
- Documentación del proyecto principal en `structuredTextTest/readme.txt`

---

**Última actualización**: 2024

