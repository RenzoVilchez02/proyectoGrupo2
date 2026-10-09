# Datos del proyecto

## Archivo utilizado

**`raw/online_shoppers_intention.csv`** es el único CSV de entrada del
[notebook del proyecto](../F1/Definicion.ipynb). Contiene **12.330 filas y 18 columnas**:
17 características y el resultado binario `Revenue`.

Cada fila corresponde a una sesión de navegación. `Revenue=True` indica que terminó
en compra; `False`, que no lo hizo. No se dispone de un importe de compra en esa columna.
El diccionario de las 18 variables y sus unidades está en la sección 3 del notebook.

## Fuente y atribución

- **Autores:** C. Sakar y Y. Kastro.
- **Dataset:** *Online Shoppers Purchasing Intention Dataset* (2018).
- **Repositorio:** UCI Machine Learning Repository.
- **Documentación:** https://archive.ics.uci.edu/dataset/468/online+shoppers+purchasing+intention+dataset
- **DOI:** https://doi.org/10.24432/C5F88Q
- **Descarga oficial (ZIP):** https://archive.ics.uci.edu/static/public/468/online+shoppers+purchasing+intention+dataset.zip
- **Licencia del dataset:** Creative Commons Attribution 4.0 International (CC BY 4.0),
  según UCI. Esta atribución corresponde a los datos; no asigna una licencia al código del grupo.

## Recuperación del original

La definición inicial del equipo registraba una descarga el **07/10/2026**.
El **09/10/2026** se comparó la copia local con el CSV de la descarga oficial.
Ambos tenían las mismas dimensiones, pero se detectaron diferencias en seis columnas:

- `Administrative_Duration`
- `Informational_Duration`
- `ProductRelated_Duration`
- `BounceRates`
- `ExitRates`
- `PageValues`

Por ejemplo, el valor `2.666.666.667` de la copia local correspondía a `2.666666667`
en la misma fila del original. La causa de la alteración no quedó determinada; no se
atribuye a una edición manual de ningún integrante.

Se reemplazó **el archivo completo por el original de UCI**, sin reconstruir los decimales
mediante eliminación de puntos. Se verificó igualdad exacta de bytes con el CSV extraído
del ZIP oficial. Se conserva un respaldo local en `data/backup`, excluido mediante
`.gitignore`; ese respaldo no debe usarse en el análisis.

**SHA-256 del CSV oficial incorporado:**

```text
b3055ee355f59134d851d32641183cb4a8b45def7124d2f50442a042f358e0d9
```

El notebook calcula y muestra el hash del archivo que efectivamente carga.

## Interpretación y preparación

- Los decimales del CSV original usan punto; cargarlo con `pd.read_csv` sin tratar ese punto
  como separador de miles. No abrir y guardar sobre el original desde una hoja de cálculo.
- Las tres columnas `*_Duration` representan tiempo acumulado en **segundos** por categoría
  de páginas; no son tiempo medio por página. El notebook convierte a minutos solo para comunicar resultados.
- `BounceRates` y `ExitRates` son métricas expresadas como proporciones; multiplicar por 100
  únicamente para mostrarlas como porcentajes.
- Los códigos de navegador, región, sistema operativo y tráfico son categorías, no magnitudes numéricas.
- `PageValues` no se presenta con una moneda específica porque la fuente no la identifica.
- No hay identificadores que permitan confirmar si las filas idénticas corresponden a sesiones duplicadas.

La carga del original detectó **cero faltantes y 125 filas idénticas posteriores a la primera**.
El análisis principal conserva las sesiones y evalúa por separado la sensibilidad a eliminar
esas filas. No se altera el archivo de `raw`, no se imputa información y no se eliminan
automáticamente ceros o extremos.

## Restaurar el dato si fuera necesario

1. Descargar el ZIP oficial desde el enlace anterior.
2. Extraer `online_shoppers_intention.csv`.
3. Guardarlo con ese nombre dentro de `data/raw`, conservando sus valores originales.
4. Comparar el SHA-256 y ejecutar la revisión de calidad del notebook.

Si el archivo está abierto o bloqueado por otra aplicación, cerrarlo antes de reemplazarlo.
No crear otra copia con un nombre distinto como entrada del análisis.
