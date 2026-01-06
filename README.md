# Investigación Multi-Ómicas en Cáncer — LinkedOmics

Este repositorio contiene investigaciones multi-ómicas en cáncer, con un enfoque principal en el Glioma de Bajo Grado (LGG) utilizando datos del The Cancer Genome Atlas (TCGA). Se desarrollan modelos predictivos de supervivencia a 3 años integrando datos de expresión génica, alteraciones en el número de copias (SCNA), mutaciones y datos clínicos.

## Estado del Arte

| Estudio / Año                                                                  | Cohorte LGG                   | Datos                                                | Modelo(s)                                                                                      | Métrica(s)                                                                                       | Limitaciones / Huecos                                                                                                                                                |
| ------------------------------------------------------------------------------ | ----------------------------- | ---------------------------------------------------- | ---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| IRGPs immune gene pairs, 2021pmc.ncbi.nlm.nih​                                 | TCGA‑LGG train, CGGA val      | Pares de genes inmunes (IRGPs) + clínica básica      | Cox univariante + LASSO Cox                                                                    | Buena separación alto/bajo riesgo en TCGA y CGGApmc.ncbi.nlm.nih​                                | Sólo Cox lineal, sin RSF/DeepSurv; sin radiomics ni multi‑ómica integradapmc.ncbi.nlm.nih​                                                                           |
| 5‑miRNA signature LGG, ~2019sciencedirect​                                     | LGG TCGA/otros                | Expresión de miRNA + clínica                         | Cox y firma de 5 miRNAs                                                                        | Estratificación pronóstica aceptablesciencedirect​                                               | Enfoque estadístico clásico; no compara con ML no lineal ni integra otros ómicssciencedirect​                                                                        |
| Microambiente TME 25 genes, Ann Transl Med 2020pmc.ncbi.nlm.nih+1​             | 514 LGG TCGA                  | Genes asociados a TME (ESTIMATE immune/stromal)      | Cox, construcción de risk score con 25 genes TME                                               | AUC ROC ≈0.771 para OS; scores inmune/estromal asociados a peor supervivenciapmc.ncbi.nlm.nih+1​ | Modelo Cox con foco sólo en TME; sin comparación con ML avanzados ni integración con otros tipos de datospmc.ncbi.nlm.nih+1​                                         |
| Cuproptosis model in LGG, 2024 (Aging)aging-us​                                | TCGA‑LGG train, CGGA val      | Genes de cuproptosis + clínica                       | Cox univariante, LASSO Cox, nomograma                                                          | AUC razonables 1/3/5 años; firma de 5 genes estableaging-us​                                     | Sólo Cox penalizado; sin RSF/DL; centrado en una vía biológica, sin radiomicsaging-us​                                                                               |
| pNGB 22‑gene signature, 2024 (OAEpublish)oaepublish​                           | TCGA‑LGG + 2 cohortes CGGA    | 22 genes N‑glycan + clínica                          | 22 modelos (incl. Enet, Cox penal., ML)                                                        | C‑index alto; Enet mejor modelo en TCGA y CGGAoaepublish​                                        | Firma fija; búsqueda limitada de features; interpretabilidad biológica parcial, sin radiomicsoaepublish​                                                             |
| Gene attention DL for LGG, 2022pmc.ncbi.nlm.nih​                               | TCGA‑LGG train, CGGA val      | Transcriptoma completo                               | Red con atención génica vs Cox y RSF                                                           | C‑index y Brier mejores que Cox/RSFpmc.ncbi.nlm.nih​                                             | No integra clínica ni radiomics; estabilidad de atención poco exploradapmc.ncbi.nlm.nih​                                                                             |
| Deep learning survival in adult DLGG, 2025pubmed.ncbi.nlm.nih​                 | 1 079 DLGG (3 cohortes)       | 7 variables clínico‑patológicas                      | DeepSurv‑like clínica‑only                                                                     | C‑index ≈0.81 (train), 0.76 (int), 0.87 (ext); IBS bajopubmed.ncbi.nlm.nih​                      | Sin ómics ni radiomics; cohorte externa pequeña; sin comparación con RSF/Cox penalizadopubmed.ncbi.nlm.nih​                                                          |
| APOLLO LGG model, 2022 (EBioMedicine)thelancet​                                | Múltiples centros LGG         | Clínica + marcadores moleculares clave               | Nomograma Cox / modelos penalizados                                                            | Buen C‑index y calibración con validación externathelancet​                                      | Modelo clínico‑molecular clásico; sin ómics de alta dimensión ni DLthelancet​                                                                                        |
| Pan‑cáncer multimodal DL (incl. LGG), 2025academic.oup​                        | TCGA LGG dentro de 33 tumores | Multi‑omics + clínica                                | DL multimodal                                                                                  | C‑index LGG ≈0.849, mejora clara vs unimodalacademic.oup​                                        | Pan‑cáncer, no optimizado a LGG; sin radiomics ni análisis detallado por subtipo LGGacademic.oup​                                                                    |
| Screening TME‑related genes in LGG, Transl Cancer Res 2020pubmed.ncbi.nlm.nih​ | LGG TCGA subtipos             | Genes TME + immune/stromal scores                    | Análisis de supervivencia y enriquecimiento funcional                                          | Identifica genes TME pronósticos, sobre todo en astrocytoma IDH‑WTpubmed.ncbi.nlm.nih​           | No construye un modelo ML explícito (C‑index, AUC) para predicción clínica; foco descriptivo TMEpubmed.ncbi.nlm.nih​                                                 |
| HVFS + ensemble learning para grading glioma, 2022pubmed.ncbi.nlm.nih+1​       | TCGA LGG+GBM, CGGA            | Clínica + marcadores moleculares (IDH, 1p/19q, etc.) | Esquema Hierarchical Voting‑Based Feature Selection + 16 combinaciones de modelos supervisados | Accuracy ≈87.6% (TCGA) y 79.7% (CGGA) en grading gliomapubmed.ncbi.nlm.nih+1​                    | Tarea de clasificación de grado, no supervivencia; pero el pipeline de selección/ensemble es reutilizable para modelos de supervivencia en LGGpubmed.ncbi.nlm.nih+1​ |

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
