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

El informe PDF está pendiente de elaboración y revisión del equipo. Cuando esté listo,
se incorporará al repositorio y se añadirá su enlace aquí. El notebook no sustituye el PDF.
Las cifras del informe deben coincidir con las salidas verificadas del notebook.

Guardar archivos localmente no los publica en GitHub: el equipo debe revisar y subir los cambios.

## Referencias

- Sakar, C. y Kastro, Y. (2018). *Online Shoppers Purchasing Intention Dataset*.
  UCI Machine Learning Repository. https://doi.org/10.24432/C5F88Q
- Instrucciones y rúbrica de Sumativa 1, Fase 2, MCDI501, disponibles en Canvas.
