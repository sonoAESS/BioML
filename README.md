# Investigación Multi-Ómicas en Cáncer — LinkedOmics

Este repositorio contiene investigaciones multi-ómicas en cáncer, con un enfoque principal en el Glioma de Bajo Grado (LGG) utilizando datos del The Cancer Genome Atlas (TCGA). Se desarrollan modelos predictivos de supervivencia a 3 años integrando datos de expresión génica, alteraciones en el número de copias (SCNA), mutaciones y datos clínicos.

## Estado del Arte

| Estudio / Año | Cohorte LGG | Datos | Modelo(s) | Métrica(s) | Limitaciones / Huecos |
|---|---|---|---|---|---|
| [IRGPs immune gene pairs, 2021](https://pmc.ncbi.nlm.nih.gov/articles/PMC8598129/) | TCGA‑LGG (train), CGGA (val) | Pares de genes inmunes (IRGPs) + clínica básica | Cox univariante + LASSO Cox | Buena separación alto/bajo riesgo en varias cohortes LGG | Sólo Cox lineal; sin RSF/DeepSurv; sin radiomics ni integración multi‑ómica completa |
| [5‑miRNA signature LGG, ~2019](https://www.sciencedirect.com/science/article/pii/S1936523319303223) | LGG TCGA/otros | Expresión de miRNA + clínica | Cox y firma de 5 miRNAs | Estratificación pronóstica aceptable | Enfoque estadístico clásico; no compara con ML no lineal ni integra otros ómics |
| [Microambiente TME 25 genes, Ann Transl Med 2020](https://atm.amegroups.org/article/view/37257/html) | 514 LGG TCGA | Genes asociados a TME (scores ESTIMATE inmune/estromal) | Cox, construcción de risk score con 25 genes TME | AUC ROC ≈0.77 para OS; scores inmune/estromal asociados a peor supervivencia | Modelo Cox centrado en TME; sin comparación con ML avanzados ni integración con otras ómicas |
| [Cuproptosis model in LGG, 2024 (Aging)](https://www.aging-us.com/article/205834/text) | TCGA‑LGG (train), CGGA (val) | Genes de cuproptosis + clínica | Cox univariante, LASSO Cox, nomograma | AUC aceptables a 1/3/5 años; firma de 5 genes estable | Sólo Cox penalizado; sin RSF/DL; centrado en una vía biológica, sin radiomics ni otras ómics |
| [pNGB 22‑gene signature, 2024 (OAEpublish)](https://www.oaepublish.com/articles/2394-4722.2024.32) | TCGA‑LGG + 2 cohortes CGGA | 22 genes N‑glycan + clínica | 22 modelos (incl. Enet, Cox penal., ML) | C‑index alto; Elastic Net mejor modelo en TCGA y CGGA | Firma fija; búsqueda limitada de features; interpretabilidad biológica parcial, sin radiomics |
| [Gene attention DL / Multi‑PEN, 2022](https://pmc.ncbi.nlm.nih.gov/articles/PMC9598836/) | TCGA‑LGG (train), CGGA (val) | mRNA + miRNA + clínica | Red profunda Multi‑PEN con atención génica vs modelos convencionales | C‑index y Brier competitivos o mejores que modelos clásicos | Complejidad alta; poca comparación con RSF/DeepSurv estándar; interpretabilidad aún limitada |
| [Deep learning survival in adult DLGG, 2025](https://pubmed.ncbi.nlm.nih.gov/41037075/) | 1 079 DLGG (3 cohortes) | 7 variables clínico‑patológicas | Modelo tipo DeepSurv (clínica‑only) | C‑index ≈0.81 (train), 0.76 (int), 0.87 (ext); IBS bajo | Sin ómics ni radiomics; cohorte externa pequeña; sin benchmark contra RSF/Cox penalizado |
| [APOLLO LGG model, 2022 (EBioMedicine)](https://pubmed.ncbi.nlm.nih.gov/35436725/) | 6 cohortes LGG (Europa/Asia) | Clínica + expresión génica (biomarcadores e interacciones) | Estrategia 3‑D para modelo pronóstico (APOLLO) | C‑index ≈0.82; AUC 36m ≈0.90 y 60m ≈0.84 con validación independiente | Modelo centrado en firma clínica‑transcriptómica; sin radiomics; no usa arquitecturas DL modernas |
| [Pan‑cáncer multimodal DL (incl. LGG), 2025](https://academic.oup.com/bib/article/26/2/bbaf121/8089949) | TCGA‑LGG dentro de 33 tumores | Multi‑omics (expresión, metilación, CNA…) + clínica | Deep learning multimodal | En LGG: C‑index ≈0.85, mejora clara frente a modelos unimodales | Estudio pan‑cáncer, no optimizado específicamente a LGG; sin radiomics ni análisis fino por subtipo |
| [TME‑related genes in LGG, Transl Cancer Res 2020](https://pubmed.ncbi.nlm.nih.gov/35117823/) | LGG TCGA subtipos | Genes TME + immune/stromal scores | Análisis de supervivencia y enriquecimiento funcional | Identifica genes TME pronósticos, sobre todo en astrocytoma IDH‑WT | No construye un modelo ML de predicción (sin C‑index/AUC claros); foco descriptivo TME |
| [HVFS + ensemble para grading glioma, 2022](https://pmc.ncbi.nlm.nih.gov/articles/PMC9697273/) | TCGA (LGG+GBM), CGGA | Clínica + marcadores moleculares (IDH, 1p/19q, etc.) | Esquema Hierarchical Voting‑Based Feature Selection + 16 clasificadores | Accuracy ≈87.6% (TCGA) y 79.7% (CGGA) para *grading* | Tarea de clasificación de grado, no supervivencia; pipeline reutilizable para supervivencia LGG |

## Características Principales

- **Análisis Exploratorio de Datos (EDA)**: Exploración de genes hub y patrones en datos crudos y procesados.
- **Modelos de Machine Learning**: Implementación de algoritmos como Random Forest, XGBoost, Gradient Boosting y LightGBM para predicción de supervivencia.
- **Integración de Datos Ómicos**: Combinación de múltiples tipos de datos (expresión, SCNA, mutaciones) para mejorar la precisión de los modelos.
- **Análisis de Supervivencia**: Uso de curvas de Kaplan-Meier y pruebas estadísticas para validar predicciones.
- **Evaluación Robusta**: Validación cruzada estratificada y métricas como AUC-ROC para asegurar la generalización de los modelos.

---

## Estructura del Proyecto

```
├── data/                          # Datos crudos y procesados (no incluidos en el repo por tamaño)
├── docs/                          # Documentos y enlaces de interés
├── BRCA/                          # Recursos y notebooks sobre cáncer de mama
│   ├── EDA_BRCA.ipynb             # Análisis exploratorio de datos crudos y genes hub
│   ├── EDA_datos_limpios_BRCA.ipynb # EDA de datos filtrados por genes hub
│   ├── modelos_BRCA.ipynb         # Modelos ML y DL desarrollados en BRCA
│   ├── data/                      # Datos específicos de BRCA
│   └── model_results/             # Resultados de modelos para BRCA
├── LGG/                           # Recursos y notebooks sobre Glioma de Bajo Grado
│   ├── analisis_via_cox.ipynb     # Análisis de supervivencia usando modelo de Cox
│   ├── data.csv                   # Datos integrados para LGG
│   ├── model_auc.ipynb            # Evaluación de modelos por AUC
│   ├── model_recall.ipynb         # Evaluación de modelos por Recall
│   ├── modelo_integracion_scna_clin_expr.ipynb # Integración de SCNA, clínicos y expresión
│   ├── modelos_expression_data.ipynb # Modelos basados en datos de expresión
│   ├── modelos_integracion_datos_scna.ipynb # Modelos con integración de SCNA
│   └── results/                   # Resultados y visualizaciones
├── modelos/                        # Modelos entrenados guardados
├── runs/                           # Resultados de experimentos y logs
├── requirements.txt                # Dependencias del proyecto
├── LICENSE
└── README.md
```

---

## Instalación y Requisitos

### Prerrequisitos

- Python 3.8+
- pip

### Instalación

1. Clona el repositorio:
   ```bash
   git clone https://github.com/tu-usuario/investigacionIA.git
   cd investigacionIA
   ```

2. Instala las dependencias:
   ```bash
   pip install -r requirements.txt
   ```

### Dependencias Principales

- numpy, pandas: Manipulación de datos
- scikit-learn: Algoritmos de machine learning
- xgboost, lightgbm: Modelos de boosting
- lifelines: Análisis de supervivencia
- matplotlib, seaborn: Visualización
- tensorflow: Redes neuronales (si se usan modelos DL)
- imbalanced-learn: Balanceo de datos
- ctgan: Generación de datos sintéticos

---

## Uso

### Datos

Los datos utilizados provienen de TCGA y LinkedOmics. Incluyen:

- **Datos Clínicos**: Edad, supervivencia, estadio, subtipos, tratamientos.
- **Expresión Génica (RNAseq)**: Expresión normalizada por gen.
- **Alteraciones en Número de Copias (SCNA)**: Cambios logarítmicos en copias génicas.
- **Mutaciones**: Variantes detectadas por muestra.
- **Proteómica (RPPA)**: Expresión proteica normalizada.
- **Otros**: Metilación, miRNA, etc.

**Nota**: Los archivos de datos crudos no están incluidos en el repositorio debido a su tamaño. Descárgalos desde [LinkedOmics](http://linkedomics.org/) o TCGA.

### Ejecución de Notebooks

1. Navega a la carpeta correspondiente (e.g., `LGG/`).
2. Abre los notebooks en Jupyter:
   ```bash
   jupyter notebook modelos_integracion_datos_scna.ipynb
   ```
3. Ejecuta las celdas paso a paso. Los notebooks incluyen:
   - Carga y preprocesamiento de datos.
   - Selección de genes relevantes (e.g., top 25 o 86 genes).
   - Entrenamiento y evaluación de modelos.
   - Generación de curvas ROC y matrices de confusión.

### Resultados

Los resultados se guardan en `LGG/results/`, incluyendo:
- Curvas ROC y Precision-Recall.
- Matrices de confusión.
- Métricas de rendimiento (AUC, F1, Recall).
- Redes de interacción proteína-proteína (PPI).

---

## Contribuciones

Este proyecto se centra en el Glioma de Bajo Grado (LGG), pero incluye análisis preliminares en BRCA. Futuras extensiones pueden incluir otros tipos de cáncer.

---

## Referencias

- [LinkedOmics](http://linkedomics.org/): Plataforma para análisis de datos ómicos.
- [The Cancer Genome Atlas (TCGA)](https://www.cancer.gov/tcga): Base de datos de genómica del cáncer.
- Artículos relacionados: Investigación basada en genes inmunológicos y vías de señalización en LGG.

---

## Licencia

Este proyecto está bajo la Licencia MIT. Ver `LICENSE` para más detalles.

## Contacto

Consultas o colaboraciones: [eliasyosoto@gmail.com](mailto:eliasyosoto@gmail.com)
