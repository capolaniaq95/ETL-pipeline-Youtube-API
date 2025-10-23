# ETL Pipeline YouTube API

## Descripción

Este proyecto implementa un pipeline ETL (Extract, Transform, Load) diseñado para consultar la API de YouTube y obtener información sobre canales relacionados con el tema "Data". El pipeline extrae datos básicos de los canales, transforma la información y evalúa métricas clave como estadísticas de suscriptores, vistas y actividad del canal. Los datos se procesan a través de capas de calidad de datos: Bronze (datos crudos), Silver (datos transformados) y Gold (datos analíticos listos para consumo).

El proyecto utiliza la YouTube Data API v3 para realizar búsquedas de canales y obtener métricas detalladas, permitiendo análisis de tendencias y rendimiento de canales de datos en YouTube.

## Características

- **Extracción (Bronze Layer)**: Consulta la API de YouTube para buscar canales relacionados con "Data" en una región específica (por defecto, US).
- **Transformación (Silver Layer)**: Limpieza y estructuración de los datos extraídos, incluyendo conversión de fechas y normalización de campos.
- **Carga y Evaluación (Gold Layer)**: Cálculo de métricas clave como tasa de crecimiento, engagement y comparación entre canales.
- **Almacenamiento por capas**: Los datos se guardan en formato JSON en directorios separados para cada capa de calidad.
- **Configuración flexible**: Parámetros ajustables para búsqueda (query, región, tipo, resultados máximos).

## Instalación

1. Clona este repositorio:
   ```bash
   git clone https://github.com/tu-usuario/ETL-pipeline-Youtube-API.git
   cd ETL-pipeline-Youtube-API
   ```

2. Crea un entorno virtual (opcional pero recomendado):
   ```bash
   python -m venv .venv
   source .venv/bin/activate  # En Windows: .venv\Scripts\activate
   ```

3. Instala las dependencias:
   ```bash
   pip install -r requeriments.txt
   ```

## Uso

### Requisitos previos

- Obtén una API Key de Google Cloud Console para la YouTube Data API v3.
- Actualiza la variable `API_KEY` en el código con tu clave.

### Ejecutar el Pipeline

1. Abre el notebook Jupyter:
   ```bash
   jupyter notebook content/notebooks/etl_pipeline.ipynb
   ```

2. Ejecuta las celdas del notebook para:
   - Inicializar la clase `bronze` con parámetros de búsqueda.
   - Extraer datos de la API.
   - Guardar datos en la capa Bronze.

### Parámetros de Búsqueda

- `q`: Query de búsqueda (por defecto: "Data")
- `regionCode`: Código de región (por defecto: "US")
- `type`: Tipo de búsqueda (por defecto: "channel")
- `maxresults`: Número máximo de resultados (por defecto: 50)

### Extensiones Futuras

El pipeline actual implementa solo la capa Bronze. Para completar el ETL:

- **Silver Layer**: Implementar transformación de datos (e.g., obtener estadísticas detalladas de canales usando la API de Channels).
- **Gold Layer**: Evaluar métricas y generar insights analíticos.

## Estructura del Proyecto

```
ETL-pipeline-Youtube-API/
├── README.md                          # Este archivo
├── requeriments.txt                   # Dependencias de Python
├── .gitignore                         # Archivos ignorados por Git
├── content/
│   ├── notebooks/
│   │   └── etl_pipeline.ipynb         # Notebook principal del pipeline
│   └── data/
│       ├── bronze/                    # Datos crudos extraídos
│       ├── silver/                    # Datos transformados
│       └── gold/                      # Datos analíticos finales
└── .venv/                             # Entorno virtual (opcional)
```

## Dependencias

- `requests`: Para realizar peticiones HTTP a la API de YouTube.
- `json`: Módulo estándar de Python para manejo de JSON.
- `datetime`: Módulo estándar para manejo de fechas.

## API de YouTube

Este proyecto utiliza la YouTube Data API v3. Asegúrate de:

- Habilitar la API en Google Cloud Console.
- Configurar cuotas adecuadas para evitar límites de uso.
- Mantener la API Key segura (no la subas a repositorios públicos).

## Contribución

1. Haz un fork del proyecto.
2. Crea una rama para tu feature (`git checkout -b feature/nueva-funcionalidad`).
3. Commit tus cambios (`git commit -am 'Agrega nueva funcionalidad'`).
4. Push a la rama (`git push origin feature/nueva-funcionalidad`).
5. Abre un Pull Request.

## Licencia

Este proyecto está bajo la Licencia MIT. Ver el archivo LICENSE para más detalles.

## Notas

- El código actual es un prototipo y solo implementa la extracción básica. Se recomienda extenderlo para incluir transformación y evaluación completa de métricas.
- Asegúrate de cumplir con los términos de servicio de la YouTube Data API.