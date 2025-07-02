# Análisis de Supervivencia en Cáncer de Próstata Resistente a la Castración

Este repositorio contiene los scripts organizados por etapas del análisis descrito en el documento principal. Cada carpeta corresponde a una fase específica del flujo de trabajo, desde el preprocesamiento de los datos hasta la generación de resultados finales.

Los datos utilizados para realizar el estudio no son públicos actualmente. Se publicarán en un futuro. 

## 1. Preprocesamiento

Esta carpeta incluye dos scripts responsables de cargar, limpiar y preparar los conjuntos de datos utilizados en el estudio.

- **1.Preprocesamiento.R**  
  - Carga los datos clínicos y de expresión génica de las cohortes PREMIERE e IRST.  
  - Realiza el preprocesamiento descrito en la sección 3.2 del documento.  
  - Genera los conjuntos de datos de los cinco escenarios definidos, antes de aplicar selección de variables.

- **2.SeleccionVariables.R**  
  - Carga los escenarios generados en el script anterior.  
  - Aplica la selección de variables en dos etapas según la sección 3.4.1 del documento.  
  - Produce los conjuntos definitivos para cada escenario y cada método de selección (GSEA o RF-imp).

---

## 2. Modelos (selección GSEA)

Contiene los scripts de entrenamiento de modelos usando selección génica mediante GSEA, diferenciando entre dos estrategias de integración multi-ómica.

- **3.Modelos_gsea_integracion_basica.R**  
  - Entrena y valida modelos con integración básica (two-step).  
  - Experimentos: 1, 2, 4, 5, 9.

- **4.Modelos_gsea_integracion_apilada.R**  
  - Entrena y valida modelos con integración apilada (stacked).  
  - Experimentos: 2, 6, 10.

---

## 3. Modelos (selección RF-imp)

Contiene los scripts de entrenamiento de modelos usando selección génica basada en importancia de variables con RSF, también diferenciados por tipo de integración.

- **5.Modelos_rsf_integracion_basica.R**  
  - Entrena y valida modelos con integración básica.  
  - Experimentos: 3, 7, 11.

- **6.Modelos_rsf_integracion_apilada.R**  
  - Entrena y valida modelos con integración apilada.  
  - Experimentos: 3, 8, 12.

> Cada uno de los scripts de esta sección (3 a 6) guarda:
> - Modelos en formato `.rds`.  
> - Matrices de resultados con C-Index y AUC (a 1 y 2 años), para los conjuntos de entrenamiento y validación.

---

## 4. Resultados

- **7.Resultados.R**  
  - Analiza los resultados obtenidos de todos los experimentos.  
  - Carga las matrices generadas previamente y produce:  
    - Tablas y gráficos (ver Anexo II y Capítulo 4 del documento).  
    - Contrastes de hipótesis para evaluar el cumplimiento de los objetivos planteados.

---
