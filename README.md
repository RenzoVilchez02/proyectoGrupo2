# Grupo 2 · Estadística Computacional

Proyecto del curso **MCDI501 · Estadística computacional para la toma de decisiones**.

**Integrantes:** Cristian Hurtado, Jorge Altamirano, Renzo Vilchez y Luis Paredes.

## Problema y alcance

Se estudian las características de navegación de una tienda online y su asociación
con que una sesión termine en compra. La pregunta central es:

> ¿Qué diferencias de navegación observamos entre las sesiones que terminan en compra y las que no?

Se utiliza **Online Shoppers Purchasing Intention**, publicado por UCI, con
12.330 sesiones y 18 columnas. `Revenue` indica compra/no compra; no es el importe gastado.
La fuente, licencia y recuperación del CSV se documentan en [data/README.md](data/README.md).

El avance de la **Sumativa 1** incluye calidad de datos, estadística descriptiva,
visualización, análisis bivariado, tres estimaciones de medias con intervalos del 95 %
y dos contrastes de Welch con ajuste de Holm. También se comparan intervalos t y
bootstrap y se evalúa la sensibilidad a filas idénticas. Las conclusiones son
observacionales: no demuestran causalidad ni desarrollan un modelo predictivo.

## Archivos principales

```text
proyectoGrupo2/
├── README.md
├── .gitignore
├── requirements.txt
├── F1/
│   └── Definicion.ipynb
└── data/
    ├── README.md
    └── raw/
        └── online_shoppers_intention.csv
```

[F1/Definicion.ipynb](F1/Definicion.ipynb) es el notebook de avance de la Sumativa 1.
La carpeta `F1` conserva el nombre inicial del equipo. El diccionario completo de
variables, los procedimientos, las tablas, las figuras y sus interpretaciones están
en el notebook; no se mantienen copias separadas de esos contenidos.

El entorno `.venv` y un eventual respaldo local en `data/backup` se excluyen de Git.
Puede haber carpetas de trabajo adicionales: no son necesarias para ejecutar este avance.

## Preparar el proyecto en VS Code

1. Tener Git, Python y VS Code, con las extensiones **Python** y **Jupyter** de Microsoft.
   La ejecución completa se verificó con **Python 3.13.5** y las versiones de `requirements.txt`.
2. Descargar el repositorio. Si GitHub solicita autenticación, usar una cuenta con acceso al grupo:

   ```powershell
   git clone https://github.com/RenzoVilchez02/proyectoGrupo2.git
   cd proyectoGrupo2
   code .
   ```

3. En VS Code, abrir **Terminal → New Terminal**. La terminal debe estar en la raíz
   `proyectoGrupo2`. Comprobar la versión de Python y crear el entorno solo si todavía no existe:

   ```powershell
   python --version
   python -m venv .venv
   ```

   `python` debe apuntar a la instalación que se desea usar para este proyecto.
   Si ya existe `.venv`, no es necesario recrearlo.

4. Instalar las dependencias en ese entorno y esperar a que termine sin errores:

   ```powershell
   .\.venv\Scripts\python.exe -m pip install -r requirements.txt
   ```

   Los comandos usan directamente el Python del entorno; no requieren ejecutar
   `Activate.ps1` ni cambiar la política de ejecución de PowerShell.

5. Abrir **F1 → Definicion.ipynb**. Pulsar **Select Kernel → Python Environments…**
   (primero **Select Another Kernel…** si aparece) y elegir la `.venv` de este repositorio.
   La ruta debe terminar en `proyectoGrupo2\.venv\Scripts\python.exe`.
   El entorno del curso anterior es distinto y no debe actualizarse para este trabajo.

6. Reiniciar el kernel si había celdas ejecutadas y pulsar **Run All**.
   La primera celda debe informar:

   ```text
   Entorno correcto: versiones fijadas en requirements.txt verificadas.
   ```

7. Guardar con **Ctrl + S** después de revisar que todas las celdas finalizaron sin errores.

### Si no aparece el entorno

Usar **Ctrl + Shift + P → Python: Select Interpreter → Enter interpreter path…** y
seleccionar el `python.exe` dentro de `.venv/Scripts` de este proyecto. Después volver
al selector de kernel del notebook: seleccionar intérprete y seleccionar kernel son
acciones diferentes. Si la lista no se actualiza, guardar y usar **Developer: Reload Window**.

El nombre visible puede ser `.venv (3.13.5)` o un nombre de kernel registrado.
Lo que identifica el entorno es su ruta y sus bibliotecas. No hace falta registrar
un kernel adicional ni iniciar un servidor Jupyter para la ejecución local normal.
Si la conexión se queda bloqueada, revisar el registro de Jupyter antes de reinstalar paquetes.

## Datos y reproducibilidad

- El CSV oficial está incluido en `data/raw` para ejecutar sin descargarlo en cada sesión.
- Se conserva sin transformaciones; las conversiones y decisiones de preparación se explican en el notebook.
- Las rutas se resuelven desde la raíz del repositorio, sin depender del usuario ni de una unidad específica.
- La semilla de remuestreo y submuestreo es `20261009`.
- Los gráficos y resultados quedan dentro del `.ipynb`; no se generan archivos de salida adicionales.
- Las afirmaciones sobre independencia, cobertura temporal y medición se tratan como supuestos o limitaciones.
- La ejecución se verificó desde un kernel nuevo, pero queda pendiente reproducirla y revisar las
  interpretaciones en otro equipo del grupo antes de la entrega.

## Entrega de la Sumativa 1

Según las instrucciones de Canvas, se entregan:

1. **Informe técnico PDF**, máximo ocho páginas, sin anexos, con el enlace al repositorio.
2. **Notebook `.ipynb`**, documentado y ejecutable.
3. **Enlace a GitHub**, accesible para el docente.

El informe editable está en [Informe_Sumativa1.docx](Informe_Sumativa1.docx), con ocho páginas
incluidas las referencias. Sus cifras se contrastaron con la ejecución del notebook.
Queda pendiente la revisión del equipo y exportarlo a PDF para Canvas. El notebook no sustituye el PDF.

Guardar archivos localmente no los publica en GitHub: el equipo debe revisar y subir los cambios.

## Referencias

- Sakar, C. y Kastro, Y. (2018). *Online Shoppers Purchasing Intention Dataset*.
  UCI Machine Learning Repository. https://doi.org/10.24432/C5F88Q
- Instrucciones y rúbrica de Sumativa 1, Fase 2, MCDI501, disponibles en Canvas.


## Sumativa 2: validación, simulación y remuestreo

La evaluación continúa los resultados de S1 con bootstrap no paramétrico, permutación,
estabilidad de Spearman, cohortes sintéticas Monte Carlo y análisis de robustez.

```text
S1/
├── Definicion.ipynb          # copia idéntica del original conservado en F1
└── resultados_s1.json       # referencia extraída al reproducir S1, con hashes y unidades
S2/
├── Validacion_Simulacion.ipynb
└── resultados_validados.json
```

- **Abrir y ejecutar:** [S2/Validacion_Simulacion.ipynb](S2/Validacion_Simulacion.ipynb).
  Usar la misma `.venv` del proyecto, reiniciar el kernel y ejecutar todas las celdas en orden.
  No se instalan nuevas dependencias ni se necesita internet. Ejecutar desde la carpeta S2
  o cualquier carpeta dentro del repositorio; las rutas se resuelven automáticamente.
- **Referencia:** la copia de S1 conserva exactamente el notebook de `F1/Definicion.ipynb`
  integrado en el commit `5fbcaf4`. El original no se mueve ni se modifica. Los resultados
  de referencia se extrajeron de una reproducción completa de S1; S2 comprueba los hashes
  de contenido y reproduce sus tres IC t, Welch y Spearman antes de validar. Los hashes LF
  permiten diferencias de fin de línea de Git, sin aceptar cambios de contenido.
- **Métodos:** 10.000 remuestras por media (percentil y BCa), 10.000 permutaciones por
  contraste y 10.000 remuestras emparejadas por correlación; 10.000 cohortes por escenario
  Monte Carlo. Se procesan lotes y multiplicidades para controlar memoria sin submuestrear
  el dataset. Semilla maestra: `20261015`; subsemillas por bloque documentadas en el notebook.
- **Retroalimentación S1:** las secciones 1.2 y 1.3 añaden 10.000 remuestras para diferencias
  de medias (percentil y BCa), medianas globales y diferencias de medianas (percentil).
  La sección 6.1 documenta desbalance, redundancia y la disponibilidad previa de PageValues
  aún no confirmada, con acciones pendientes para S3.
- **Salida:** todas las tablas y once figuras permanecen en el notebook. Al terminar se
  genera únicamente [S2/resultados_validados.json](S2/resultados_validados.json), con las
  cifras, configuración, observaciones influyentes, limitaciones y recomendaciones para S3.
  La fecha UTC y los tiempos medidos pueden cambiar entre ejecuciones; las cifras aleatorias
  se reproducen con el entorno y semillas indicados.
- **Interpretación:** los recortes cambian el estimando; mantener un signo no garantiza
  estabilidad de magnitud. Monte Carlo condiciona en las probabilidades estimadas de S1,
  sin propagar incertidumbre de parámetros ni validar causalidad o predicciones externas.
- **Informe:** su redacción queda a cargo de los compañeros. No se genera ni añade un PDF
  de S2 en este trabajo. La entrega de Canvas exige, además del notebook y enlace GitHub,
  el informe PDF de máximo siete páginas. Revisarlo después contra las cifras de S2.
- **Estado de revisión:** la ejecución completa y los algoritmos se verifican localmente;
  quedan la revisión del grupo y la reproducción en otro equipo. Guardar cambios no los
  publica: no se realiza commit, push ni entrega en Canvas automáticamente.

Referencia docente: [ejemplo oficial de Sumativa 2](https://github.com/jpmaidana/MCDI501-202682/tree/main/03-evaluaciones/Sumativa-2-validacion-simulacion-remuestreo).
