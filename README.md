# prueba-tecnica-sc

[![uv](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/astral-sh/uv/main/assets/badge/v0.json)](https://github.com/astral-sh/uv)
[![Ruff](https://img.shields.io/endpoint?url=https://raw.githubusercontent.com/charliermarsh/ruff/main/assets/badge/v2.json)](https://github.com/charliermarsh/ruff)
[![pre-commit](https://img.shields.io/badge/pre--commit-enabled-brightgreen?logo=pre-commit\&logoColor=white)](https://github.com/pre-commit/pre-commit)
[![security: bandit](https://img.shields.io/badge/security-bandit-yellow.svg)](https://github.com/PyCQA/bandit)
[![Checked with mypy](https://www.mypy-lang.org/static/mypy_badge.svg)](https://mypy-lang.org/)

---

## 📊 Descripción general

Este proyecto implementa un pipeline completo de machine learning para la **detección de transacciones atípicas** (potencialmente fraudulentas) en operaciones financieras. El objetivo principal es construir, evaluar e interpretar modelos predictivos capaces de identificar operaciones sospechosas a partir de millones de registros transaccionales reales.

Incluye desde la limpieza y enriquecimiento de datos (EDA y Feature Engineering) hasta la experimentación y comparación de modelos como **CatBoost, Random Forest y Regresión Logística**, con análisis de interpretabilidad, recomendaciones de negocio y despliegue productivo.

---

## ✨ Principales características

* **EDA avanzado**: Análisis exploratorio exhaustivo, detección de inconsistencias, visualizaciones interactivas y generación de insights de negocio.
* **Ingeniería de variables**: Creación de más de 10 variables derivadas enfocadas en riesgo crediticio, temporalidad, geolocalización y comportamiento del cliente.
* **Limpieza y preprocesamiento robusto**: Corrección de outliers, manejo de valores nulos, discretización y encoding eficiente de variables categóricas.
* **Modelado y evaluación**: Implementación de modelos con validación cruzada estratificada, ajuste para desbalance extremo y análisis de desempeño en conjunto de prueba y dataset completo.
* **Interpretabilidad**: Importancia de variables mediante CatBoost, SHAP values y permutation importance.
* **Pipeline reproducible**: Basado en notebooks, scripts, tests automáticos y configuración estándar para ambientes de ciencia de datos.
* **Buenas prácticas**: Linter, type checking, pre-commit, pruebas unitarias y documentación integrada.

---

## 🚀 Tecnologías y dependencias clave

* **Python 3.11+**
* [CatBoost](https://catboost.ai/) - modelo principal para datos tabulares y categóricos
* [scikit-learn](https://scikit-learn.org/) - preprocesamiento, modelado y métricas
* [pandas](https://pandas.pydata.org/) & [numpy](https://numpy.org/) - manipulación y análisis de datos
* [matplotlib](https://matplotlib.org/) & [seaborn](https://seaborn.pydata.org/) - visualización
* [SHAP](https://shap.readthedocs.io/) - interpretabilidad de modelos
* [uv], [ruff], [mypy], [bandit], [pre-commit], [pytest], [coverage.py], \[cookiecutter/cruft] (ver tabla abajo)

---

## 🗃️ Estructura del proyecto

```bash
.
├── data/                       # Capas de datos (raw, feature, model_input, etc)
├── docs/                       # Documentación técnica y de negocio
├── notebooks/                  # Notebooks por etapa del pipeline
├── src/                        # Código fuente modular (data, model, inference, pipelines)
├── models/                     # Modelos entrenados y artefactos finales
├── tests/                      # Pruebas unitarias y de integración
├── .github/                    # Acciones, plantillas y workflows de CI
├── Makefile                    # Comandos útiles para setup y automatización
├── pyproject.toml              # Configuración y dependencias del proyecto
├── .pre-commit-config.yaml     # Hooks de pre-commit
└── README.md                   # Este archivo
```

---

## ⚡ Setup rápido del entorno

1. Inicializa el repositorio:

   ```bash
   make init_git
   ```

2. Configura el entorno virtual:

   ```bash
   make init_env
   ```

3. Instala las librerías de ciencia de datos:

   ```bash
   make install_data_libs
   ```

4. Para instalar nuevos paquetes usa:

   ```bash
   uv add <package-name>
   ```

---

## 📚 Documentación técnica

* **Estructura y flujos de datos**: Ver `docs/` y los README.md en cada subcarpeta.
* **Pipelines principales**: Extracción, limpieza, feature engineering, entrenamiento, interpretación y reporte.
* **Convenciones de código**: Linting con ruff, type checking con mypy, pre-commit para asegurar calidad.
* **Ejecución de pruebas**:

  ```bash
  make test
  ```

* **Cobertura**:

  ```bash
  make coverage
  ```

---

## 📝 Resumen del flujo de trabajo

1. **Análisis exploratorio (EDA):** Estadística descriptiva, exploración de desbalance y visualizaciones clave.
2. **Feature engineering:** Diseño de variables enfocadas en comportamiento crediticio, geográfico y temporal.
3. **Preprocesamiento:** Limpieza de datos, imputación, discretización, encoding eficiente.
4. **Modelado:** Comparación de modelos; CatBoost seleccionado por su balance y desempeño en recall/f1-score.
5. **Interpretabilidad:** SHAP y permutation importance para explicar predicciones y relevancia de variables.
6. **Recomendaciones y conclusiones:** Insights para negocio, consideraciones para producción, monitoreo y mejoras futuras.

---

## 📈 Resultados principales

* **Dataset procesado:** 1.53M de registros; \~0.03% transacciones atípicas (altísimo desbalance)
* **Modelo seleccionado:** CatBoost
* **F1-Score (test):** 0.8045
* **Recall (fraudes):** 0.8889 en test, 0.9777 en dataset completo
* **Tasa de falsos positivos:** \~0.26%
* **Variables más relevantes:** cupo\_alto\_utilizado, cantidad\_creditos\_ultima\_semana, día y hora del crédito, coincidencia geográfica

---

## 📢 Créditos

Este proyecto se construyó sobre el template de [@JoseRZapata]: [data science project template], adaptado y extendido para los requerimientos de una prueba técnica real de análisis de fraude.

---

[@JoseRZapata]: https://github.com/JoseRZapata
[data science project template]: https://github.com/JoseRZapata/data-science-project-template
[bandit]: https://github.com/PyCQA/bandit
[coverage.py]: https://coverage.readthedocs.io/
[Mypy]: http://mypy-lang.org/
[pre-commit]: https://pre-commit.com/
[Pytest]: https://docs.pytest.org/en/latest/
[Ruff]: https://docs.astral.sh/ruff/
[UV]: https://docs.astral.sh/uv/

---
