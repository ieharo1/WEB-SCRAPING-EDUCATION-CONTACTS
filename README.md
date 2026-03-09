# 🎓 Web Scraping Education Contacts

Sistema de web scraping avanzado para recolección automatizada de correos electrónicos institucionales de centros educativos en Ecuador. Desarrollado por **Isaac Esteban Haro Torres**.

---

## 📝 Descripción

Suite profesional de herramientas para obtener contactos de instituciones educativas. Utiliza búsqueda programada y scraping inteligente para encontrar emails institucionales.

### ¿Qué hace este proyecto?

- **Búsqueda Google**: Encuentra instituciones educativas automáticamente
- **Scraping directo**: Extrae emails de sitios web institucionales
- **Validación**: Verifica si los emails existen
- **Categorización**: Organiza por tipo de institución
- **Exportación**: CSV, JSON, Excel con contactos
- **Detección de patrones**: Encuentra emails en cualquier formato

---

## ✨ Características Principales

| Característica | Descripción |
|----------------|-------------|
| 🔍 **Búsqueda Inteligente** | Google Custom Search API |
| 🌐 **Scraping Multi-página** | Navega sitios completos |
| ✅ **Validación SMTP** | Verifica emails reales |
| 📂 **Categorización** | Por provincia, tipo, nivel |
| 📊 **Múltiples formatos** | CSV, JSON, Excel |
| ⚡ **Parallel processing** | Múltiples scrapers simultáneos |

---

## 🛠️ Stack Tecnológico

- **Lenguaje**: Python 3.10+
- **Web Scraping**: BeautifulSoup, requests
- **Búsqueda**: googlesearch-python
- **Validación**: dnspython, smtplib
- **Datos**: Pandas, NumPy
- **Procesamiento**: concurrent.futures

---

## 🚀 Instalación y Uso

### Instalación

```bash
pip install beautifulsoup4 requests pandas googlesearch-python dnspython
```

### Uso básico - Búsqueda de instituciones

```python
from scraper_edu import BuscadorInstituciones

buscador = BuscadorInstituciones()

# Buscar instituciones por provincia
instituciones = buscador.buscar(
    provincia='Pichincha',
    tipo=['colegio', 'universidad'],
    cantidad=50
)

print(f"Encontradas: {len(instituciones)} instituciones")
```

### Extracción de emails

```python
from scraper_edu import ExtraerEmails

extractor = ExtraerEmails()

# Extraer emails de una institución
emails = extractor.extraer_de_url(
    url='https://www.colegioejemplo.edu.ec',
    timeout=30
)

print(f"Encontrados: {len(emails)} emails")
```

### Pipeline completo

```python
# Pipeline completo
pipeline = ScrapingPipeline(
    provincia='Guayas',
    nivel=['primaria', 'secundaria'],
    cantidad=100
)

resultado = pipeline.ejecutar()

# Guardar resultados
pipeline.guardar_csv('contactos_guayas.csv')
pipeline.guardar_json('contactos_guayas.json')
```

---

## 📊 Pipeline de Scraping

```
┌──────────────┐    ┌──────────────┐    ┌──────────────┐    ┌──────────────┐
│ 1. BÚSQUEDA  │ -> │ 2. EXTRACCIÓN│ -> │ 3. VALIDACIÓN│ -> │ 4. EXPORT   │
│              │    │              │    │              │    │              │
│ Google Search │    │ BeautifulSoup│    │ SMTP Check   │    │ CSV/JSON/    │
│ Instituciones │    │ Emails found │    │ Real emails  │    │ Excel        │
└──────────────┘    └──────────────┘    └──────────────┘    └──────────────┘
```

---

## 📁 Estructura de Datos

```csv
# contactos_educativos.csv
institucion,email,tipo,nivel,provincia,ciudad,web
Colegio Nacional Quito,info@cnq.edu.ec,Colegio,Secundaria,Pichincha,Quito,cnq.edu.ec
Universidad Catolica,admisiones@ucatolica.edu.ec,Universidad,Superior,Guayas,Guayaquil,ucatolica.edu.ec
```

---

## 📈 Dashboard de Resultados

```
╔═══════════════════════════════════════════════════════╗
║  🎓 EDUCATIONAL CONTACTS SCRAPER - ESTADÍSTICAS     ║
╠═══════════════════════════════════════════════════════╣
║                                                       ║
║  📊 RESUMEN DE EXTRACCIÓN                            ║
║  ┌─────────────────────────────────────────────┐     ║
║  │ Instituciones encontradas:    450           │     ║
║  │ Emails extraídos:           1,230           │     ║
║  │ Emails validados:           1,045 (85%)     │     ║
║  │ Emails únicos:                892            │     ║
║  └─────────────────────────────────────────────┘     ║
║                                                       ║
║  📍 POR PROVINCIA:                                  ║
║  Pichincha:  234 | Guayas:  189 | Azuay:  67        ║
║  Manabí:     45  | Loja:    34  | Other:   91      ║
║                                                       ║
║  🏫 POR TIPO:                                       ║
║  Colegios:   312 | Universidades:  89 | Institutos: 49
╚═══════════════════════════════════════════════════════╝
```

---

## 💡 Casos de Uso

1. **Marketing educativo**: Campañas a instituciones
2. **Investigación**: Base de datos de contactos académicos
3. **Networking**: Conectar con profesionales de educación
4. **Ventas B2B**: Contactar-decisores escolares
5. **Estudios**: Análisis del sector educativo

---

## 🔧 Configuración Avanzada

```python
# Configuración con validaciones
config = {
    'scraping': {
        'delay': 2,                # Segundos entre requests
        'timeout': 30,             # Timeout por página
        'user_agent': 'Mozilla/5.0...',
        'proxy': ['proxy1', 'proxy2'],  # Rotación de proxies
        'max_retries': 3,
    },
    'validacion': {
        'smtp_check': True,        # Validar con SMTP
        'timeout': 10,
        'parallel': 5,
    },
    'filters': {
        'exclude_patterns': ['gmail.com', 'hotmail.com'],
        'only_patterns': ['@edu.ec', '@educacion.gob.ec']
    }
}

scraper = ScraperEducativo(**config)
```

---

## ⚠️ Consideraciones Éticas

- Respeta robots.txt de los sitios web
- No satures los servidores con requests
- Usa delays apropiados entre peticiones
- Evita scraping de datos personales
- Cumple con términos de servicio

---

## 📂 Estructura del Proyecto

```
web-scraping-education-contacts/
├── web_scrappyng_v0_0_2.py
├── web_scrapping_v0_0_1.py
├── web_scrapping_v0_0_3.py
├── scraper/
│   ├── __init__.py
│   ├── busqueda.py
│   ├── extractor.py
│   ├── validador.py
│   └── exportador.py
├── datos/
│   └── contactos/
└── README.md
```

---

## 👨‍💻 Desarrollado por Isaac Esteban Haro Torres

**Ingeniero en Sistemas · Full Stack · Automatización · Data**

- 📧 Email: zackharo1@gmail.com
- 📱 WhatsApp: 098805517
- 💻 GitHub: https://github.com/ieharo1
- 🌐 Portafolio: https://ieharo1.github.io/portafolio-isaac.haro/

---

© 2026 Isaac Esteban Haro Torres - Todos los derechos reservados.
