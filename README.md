# TP4 - Redes convolucionales para clasificar lesiones de piel (ISIC)

Trabajo Práctico 4 de Redes Neuronales en Bioingeniería (ITBA). Se clasifican imágenes dermatoscópicas del dataset ISIC (9 clases, unas 880 imágenes) con una red convolucional y se la compara con un MLP.

El notebook parte del notebook base de la cátedra ([cselmo/CNN-en-Skin-Dataset](https://github.com/cselmo/CNN-en-Skin-Dataset)). El código del pipeline, los modelos y los experimentos es el de la cátedra; el trabajo propio son el análisis exploratorio, la explicación del código convolucional y los cuatro análisis de resultados (celdas ✏️).

## Contenido

| Archivo | Descripción |
|---|---|
| `TP4_CNN_Skin_DELIA.ipynb` | Notebook ejecutado, con todos los outputs y los análisis. |
| `requirements.txt` | Dependencias de Python. |
| `.gitignore` | Excluye el dataset y los modelos entrenados. |

El dataset **no** está en este repositorio.

## Cómo reproducirlo

Se instalan las dependencias con `pip install -r requirements.txt` y se ejecuta el notebook completo. Si no existe la carpeta `data/Split_smol`, el notebook clona el repositorio de la cátedra y usa su carpeta `data/`, para lo cual hace falta tener `git` instalado. En CPU la corrida tarda entre 15 y 25 minutos, y con GPU bastante menos.

## Metodología

- Se eliminan las imágenes duplicadas (mismo hash MD5) y se vuelve a dividir en train/val/test (60/20/20) de forma estratificada, con la semilla fija de la cátedra (`SEED_SPLIT = 42`).
- La normalización usa media y desvío por canal calculados solo con train.
- La data augmentation se aplica solo a train y después del split.
- Las comparaciones se hacen con 3 semillas (media ± desvío) y todas las decisiones se toman con validación. El test se usa una sola vez, en la sección 8, con 5 semillas.

## Uso de herramientas de IA

Declarado en la última celda del notebook.
