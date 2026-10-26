Informe Técnico: Análisis de la Brecha Digital y la EPH

1. Introducción y Marco Teórico
El presente análisis se centra en estudiar la brecha digital con el propósito principal de dimensionar la inversión en infraestructura y evaluar la desigualdad regional. A través del procesamiento de datos socioeconómicos, la organización busca identificar las disparidades en el acceso a las tecnologías de la información y la comunicación (TIC) según la región geográfica y el nivel socioeconómico. De este modo, se pretende proveer evidencia empírica que permita optimizar la asignación de recursos públicos y privados, orientando la inversión hacia las zonas más vulnerables y reduciendo así la inequidad digital.

2. Análisis Estadístico de la EPH (Python)
A continuación, se presenta el script desarrollado en Python (para ejecutar en Google Colab) utilizando la librería `pandas` para procesar los microdatos de la Encuesta Permanente de Hogares (`eph_tecnologia_microdatos.csv`) y obtener las estadísticas descriptivas univariantes de la variable clave **ITF** (Ingreso Total Familiar).

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

1. CARGA DEL DATASET
df = pd.read_csv("eph_tecnologia_microdatos.csv")

2. ESTADÍSTICAS DESCRIPTIVAS UNIVARIANTES
print("--- ESTADÍSTICAS DESCRIPTIVAS: Ingreso Total Familiar (ITF) ---")

promedio = df["ITF"].mean()
mediana = df["ITF"].median()
minimo = df["ITF"].min()
maximo = df["ITF"].max()
desviacion = df["ITF"].std()

print(f"• Media (Promedio): {promedio:.2f}")
print(f"• Mediana:          {mediana:.2f}")
print(f"• Mínimo:           {minimo}")
print(f"• Máximo:           {maximo}")
print(f"• Desviación Est.:  {desviacion:.2f}\n")


3. GENERACIÓN DE HISTOGRAMA
sns.set_theme(style="whitegrid")

plt.figure(figsize=(10, 6))
sns.histplot(data=df, x="ITF", bins=30, kde=True, color='teal')

plt.title("Distribución del Ingreso Total Familiar (ITF)", fontsize=14, fontweight='bold')
plt.xlabel("Ingreso Total Familiar (ITF)", fontsize=12)
plt.ylabel("Frecuencia", fontsize=12)

plt.show()
