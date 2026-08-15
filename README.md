# clinical-trial-analysis
Clinical Trial Analysis: Detectando la Paradoja de Simpson
🎯 Objetivo del proyecto

Este notebook analiza los resultados de un ensayo clínico para responder una pregunta aparentemente simple:

¿Qué tratamiento es más efectivo para la recuperación de los pacientes, el tratamiento A o el B?

El objetivo real del ejercicio va más allá de responder esa pregunta: es demostrar cómo una conclusión basada únicamente en el promedio global puede ser engañosa, y cómo segmentar los datos por una variable relevante (en este caso, sexo del paciente) puede revelar un resultado completamente distinto — y más correcto — al patrón inicial. Este fenómeno se conoce como paradoja de Simpson.

📂 Dataset utilizado
clinical_trial.csv → Datos de pacientes de un ensayo clínico, con las columnas:
tratamiento — Grupo de tratamiento asignado (A o B).
sexo — Sexo del paciente.
recuperado — Indica si el paciente se recuperó (variable binaria).
🔄 Etapas del análisis realizadas
Cálculo de la tasa de recuperación global por tratamiento: se agrupan los datos únicamente por tratamiento y se calcula el promedio de recuperado, obteniendo una primera conclusión (aparente): el tratamiento A tiene una tasa de recuperación ligeramente superior al B (~83% vs ~81%).
Segmentación por sexo: se repite el mismo cálculo, pero agrupando ahora por sexo y tratamiento en conjunto. Al segmentar, el resultado se invierte: el tratamiento B resulta más efectivo tanto en mujeres como en hombres, contradiciendo la conclusión inicial.
Revisión de la distribución de sexo por tratamiento: se calcula primero la proporción general de hombres y mujeres en todo el dataset (balanceada), y luego cómo se distribuyen dentro de cada grupo de tratamiento, revelando un desbalance marcado: la mayoría de los pacientes del tratamiento A son mujeres, mientras que en el tratamiento B predominan los hombres.
Explicación del hallazgo: se documenta cómo ese desbalance en la composición de cada grupo de tratamiento es la causa raíz de la paradoja — el promedio global "mezcla" subgrupos con tasas de recuperación distintas en proporciones distintas, produciendo una conclusión que no se sostiene al segmentar.
🔍 Principal hallazgo
La conclusión inicial ("el tratamiento A es más efectivo") es engañosa. Al segmentar por sexo, el tratamiento B es consistentemente más efectivo tanto en mujeres (98% vs 93%) como en hombres (73% vs 61%).
La causa es un desbalance en la composición de los grupos: el 70% de los pacientes del tratamiento A son mujeres (que tienen, en general, mayor tasa de recuperación en ambos tratamientos), mientras que el tratamiento B tiene una mayoría de hombres. Esto hace que el promedio global favorezca a A aunque, subgrupo por subgrupo, B sea mejor.
Recomendación: nunca tomar decisiones clínicas o de negocio basándose únicamente en promedios globales sin antes verificar si existen variables de segmentación relevantes (como sexo, edad, región, etc.) que puedan estar ocultando o distorsionando el patrón real.
▶️ Cómo ejecutar el notebook

Puedes abrir y correr este análisis directamente en Google Colab, sin instalar nada en tu computador:

Entra a Google Colab.
Ve a Archivo > Abrir notebook > GitHub.
Pega la URL de este repositorio.
Selecciona el archivo clinical_trial_analysis.ipynb de la lista que aparece.
El notebook se abrirá listo para ejecutar.

💡 Alternativa rápida: si el repositorio es público, puedes pegar directamente esta estructura de URL en tu navegador: https://colab.research.google.com/github/<usuario>/<repositorio>/blob/main/clinical_trial_analysis.ipynb

🔁 Guía de reproducción
Ejecuta todas las celdas en orden, usando Entorno de ejecución > Reiniciar y ejecutar todo. El notebook sigue una secuencia lógica: cálculo global → segmentación → revisión de proporciones → explicación del hallazgo.
La carga del dataset está incluida en la primera celda de código (/content/clinical_trial.csv) — no necesitas subir el archivo manualmente antes de empezar, siempre que lo hayas cargado en la carpeta /content de tu entorno de Colab (o ajustes la ruta si usas otro entorno).
No se requieren pasos manuales adicionales — el notebook es corto y cada celda depende únicamente del DataFrame df cargado al inicio.

⚠️ Si al ejecutar alguna celda aparece un error de tipo FileNotFoundError, verifica que el archivo clinical_trial.csv esté efectivamente subido a la carpeta /content de tu sesión de Colab (los archivos subidos a Colab se eliminan al cerrar la sesión, por lo que hay que volver a subirlos cada vez que se reinicia el entorno).

🔗 Repositorio

Link al repositorio público del proyecto:
