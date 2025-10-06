# Investigación Multi-Ómicas en Cáncer — LinkedOmics

Este repositorio investiga datasets asociados al Cáncer para la construcción de modelos predictivos útiles en entornos clínicos o de investigación.

---

## Estructura del Proyecto

```
├── docs/ # Documentos y enlaces de interés
├── BRCA/ # Recursos y notebooks sobre cáncer de mama
│ ├── EDA_BRCA.ipynb # Análisis exploratorio de datos crudos y genes hub
│ ├── EDA_datos_limpios_BRCA.ipynb # EDA de datos filtrados por genes hub
│ ├── modelos_BRCA.ipynb # Modelos ML y DL desarrollados en BRCA
├── notebooks/ # Notebooks de investigación TCGA-LGG
│ ├── modelos_fintegracion_ht.ipynb
│ ├── modelos_expression_data.ipynb
| |── modelos_integracion_datos.ipynb
│ ├── via_cox.ipynb
├── [otros archivos CSV] # Datasets multi-ómicos en formato CSV
├── README.md
├── LICENSE
```


---

## Contenido de los Datos

Los archivos CSV incluyen:

- Datos Clínicos: Edad, supervivencia, estadio, subtipos, tratamientos, etc.
- Número de Copias: Alteraciones focales/genómicas.
- miRNA: Expresiones normalizadas por gen e isoforma.
- Mutaciones: Variantes detectadas en cada participante.
- Metilación: Valores beta por muestra.
- RNAseq: Expresión génica normalizada.
- RPPA: Expresión proteica normalizada.
- Proteómica: Razones logarítmicas de iones peptídicos.
- Fosfo-proteómica y Glico-proteómica: Modificaciones proteicas específicas.

---

## Carpetas especializadas

- **BRCA/**  
  Incluye notebooks para el análisis exploratorio (EDA) tanto de datos crudos como filtrados por genes hub y los modelos machine learning y deep learning desarrollados específicamente para cáncer de mama.

- **notebooks/**  
  Aquí están los scripts asociados a la investigación sobre TCGA-LGG (glioma cerebral), con métodos de modelado, análisis de supervivencia y procesamiento avanzado de datos ómicos.

---

## Referencias

- [LinkedOmics](http://linkedomics.org/)
- The Cancer Genome Atlas (TCGA)

---

## Contacto

Consultas o colaboraciones: [eliasyosoto@gmail.com](mailto:eliasyosoto@gmail.com)
