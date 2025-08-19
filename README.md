# Investigación Multi-Ómicas en Cáncer - LinkedOmics

Este repositorio contiene datasets multi-ómicas de LinkedOmics, que integra datos clínicos y multi-ómicos de 32 tipos de cáncer (TCGA) y datos proteómicos de CPTAC. El objetivo es facilitar análisis integrados para avanzar en bioinformática, biología molecular y medicina personalizada.

---

## Estructura del Proyecto

```
├── docs/ # Documentos y enlaces de interés
├── modelos.ipynb # Cuaderno de modelos
├── via_cox.ipynb # Cuaderno via_cox
├── README.md
├── LICENSE
└── [otros archivos CSV]
```


---

## Contenido de los Datos

Los datos están organizados en archivos CSV e incluyen:

- **Datos Clínicos:** Edad, supervivencia, estadio, subtipos, terapias, etc.
- **Número de Copias:** Alteraciones a nivel focal y genómico.
- **miRNA:** Expresiones normalizadas a nivel gen e isoforma.
- **Mutaciones:** Llamadas de mutación por participante.
- **Metilación:** Valores beta por muestra mapeados al genoma.
- **RNAseq:** Expresión génica normalizada.
- **RPPA:** Expresión proteica normalizada.
- **Proteómica:** Razones logarítmicas de iones peptídicos.
- **Fosfo-proteómica y Glico-proteómica:** Datos específicos de modificaciones proteicas.

---

## Cómo usar estos datos

1. Clona el repositorio.
2. Carga los archivos CSV con Python (pandas) o R.
3. Realiza análisis estadísticos, exploratorios o modelos con machine learning.
4. Personaliza filtros según subtipos clínicos o moleculares.

---

## Referencias

- LinkedOmics: [http://linkedomics.org/](http://linkedomics.org/)
- The Cancer Genome Atlas (TCGA)
- Clinical Proteomic Tumor Analysis Consortium (CPTAC)

---

## Contacto

Para preguntas o colaboraciones: [eliasyosoto@gmail.com](mailto:eliasyosoto@gmail.com)
