# Investigación Multi-Ómicas en Cáncer - LinkedOmics

Este repositorio contiene datasets multi-ómicas obtenidos de LinkedOmics, una plataforma pública que integra datos clínicos y multi-ómicos de 32 tipos de cáncer del proyecto TCGA, junto con datos proteómicos generados por CPTAC. El objetivo es facilitar análisis integrados de datos de cáncer para fomentar investigaciones en bioinformática, biología molecular y medicina personalizada.

---

## Contenido del Repositorio

Los datos están organizados en archivos CSV correspondientes a diferentes modalidades ómicas y datos clínicos, que incluyen pero no se limitan a:

- **Clinical Data (Datos Clínicos)**: Atributos como edad, supervivencia global, etapa filológica (I, II, III, IV), estadificación TNM, subtipo clínico, subtipo molecular, número de ganglios linfáticos, y terapia de radiación.
- **Copy Number (Número de Copias) (Nivel: Focal, Gen)**: Número de copias normalizado y alteraciones en el número de copias para regiones agregadas/segmentadas por muestra.
- **miRNA (miARN) (Nivel: Gen, Isoforma)**: Señales normalizadas por sonda o conjunto de sondas para muestras tumorales.
- **Mutation (Mutación) (Nivel: Sitio, Gen)**: Llamadas de mutación para cada participante.
- **Methylation (Metilación) (Nivel: Gen)**: Valores beta calculados y mapeados al genoma por muestra.
- **RNAseq (Secuenciación de ARN) (Nivel: Gen)**: Señal de expresión normalizada de genes individuales por muestra.
- **RPPA (Análisis de Proteínas por Transferencia en Membrana) (Nivel: Analito, Gen)**: Expresión proteica normalizada para cada gen, por muestra.
- **Proteomics (Proteómica) (Nivel: Gen)**: Promedio del logaritmo de la razón entre el ion reportero de la muestra y la referencia común de iones peptídicos asociados con el gen.
- **Phospho-Proteomics (Fosfo-Proteómica) (Nivel: Sitio)**: Promedio del logaritmo de la razón entre el ion reportero de la muestra y referencia común de iones peptídicos asociados con sitios fosforilados.
- **Glyco-Proteomics (Glico-Proteómica) (Nivel: Sitio)**: Promedio del logaritmo de la razón entre el ion reportero de la muestra y referencia común de iones peptídicos en sitios de N-glicosilación desglucosilados.

---

## Estructura recomendada

```
/README.md
/LICENSE
```
---

## Cómo usar estos datos

1. Clonar el repositorio.
2. Cargar los archivos CSV usando Python (pandas) o R.
3. Realizar análisis estadísticos, exploratorios, modelos predictivos o integrativos con machine learning.
4. Personalizar filtros para subtipos clínicos o moleculares según el estudio.

---

## Referencias

- LinkedOmics: http://linkedomics.org/
- The Cancer Genome Atlas (TCGA)
- Clinical Proteomic Tumor Analysis Consortium (CPTAC)

---

## Contacto

Para preguntas o colaboraciones, contacta a eliasyosoto@gmail.com.
