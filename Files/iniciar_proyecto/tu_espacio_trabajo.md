# 🧰 Conoce tu Espacio de Trabajo

[(Volver al Indice)](https://github.com/JossueE/Mastering-STM32/tree/main?tab=readme-ov-file#%C3%ADndice)

---

Antes de comenzar a desarrollar, es importante conocer cómo se organiza tu **entorno de trabajo (Workspace)** dentro de **STM32CubeIDE**.  
Este espacio será donde se almacenen todos tus proyectos, configuraciones, archivos generados automáticamente y dependencias del compilador.  
Comprender su estructura te permitirá mantener tus proyectos ordenados y evitar errores al compilar o vincular archivos.

---

## 📖 Partes del Capítulo

- [📁 1. Estructura del Workspace](#1-estructura-del-workspace)
- [🧱 2. Carpetas principales del proyecto](#2-carpetas-principales-del-proyecto)
- [⚙️ 3. Archivos automáticos generados](#3-archivos-automáticos-generados)
- [💡 4. Recomendaciones de organización](#4-recomendaciones-de-organización)

---

## 📁 1. Estructura del Workspace

Tu **workspace** es una carpeta local que actúa como contenedor de todos tus proyectos STM32.  
Por defecto, CubeIDE crea una estructura como la siguiente:



NOTAAAAAA MENTALLLL Añadir Esta madre




---

## 🧱 2. Carpetas principales del proyecto

| Carpeta | Descripción |
|----------|-------------|
| **Core/** | Contiene el código fuente principal del usuario. Incluye `main.c`, `stm32h5xx_it.c` y archivos de inicialización. |
| **Drivers/** | Bibliotecas y controladores de bajo nivel del fabricante (HAL, CMSIS, BSP, etc.). |
| **Debug/** | Archivos de depuración generados por CubeIDE al compilar. |
| **Middlewares/** | Librerías opcionales como FreeRTOS, FatFS o LWIP (solo si se activan en el `.ioc`). |
| **.ioc** | Archivo de configuración central del proyecto (Pinout, Clock, Periféricos). |
| **.project / .cproject** | Archivos internos de Eclipse utilizados por el IDE. |

<p align="center">
  <img src="../../Images/workspace/estructura_workspace.png" alt="Estructura del Workspace en STM32CubeIDE" width="700">
  <br>
  <em>Estructura típica de un proyecto dentro del Workspace.</em>
</p>

---

## ⚙️ 3. Archivos automáticos generados

Cada vez que guardas cambios en el archivo `.ioc`, CubeIDE actualiza automáticamente los archivos base del proyecto.  
Estos archivos contienen la inicialización de periféricos, reloj del sistema y funciones HAL.

| Archivo | Función |
|----------|---------|
| **main.c** | Contiene la función principal `main()` y el bucle infinito del programa. |
| **stm32h5xx_hal_msp.c** | Configura los periféricos al nivel de pines y prioridades. |
| **system_stm32h5xx.c** | Inicializa los relojes del sistema (clocks). |
| **stm32h5xx_it.c** | Gestiona las interrupciones (NVIC). |

> [!WARNING]  
> No elimines ni renombres estos archivos; forman parte de la estructura base del proyecto.  
> Puedes agregar tu propio código dentro de las secciones marcadas con:  
> ```c
> /* USER CODE BEGIN */  
> /* USER CODE END */
> ```

---

## 💡 4. Recomendaciones de organización

- Crea una carpeta dedicada para **documentación** (por ejemplo, `Docs/`) donde guardes notas, esquemas y diagramas.  
- Si tu proyecto incluye varios módulos (por ejemplo, `Sensors/`, `Motors/`, `Comm/`), agrúpalos dentro de **Core/Src** y **Core/Inc**.  
- Usa nombres descriptivos para tus proyectos:  
NUCLEO_LED_Blink
NUCLEO_UART_Com


- Haz copias de seguridad periódicas de tu workspace o sincronízalo con GitHub.

<p align="center">
<img src="../../Images/workspace/workspace_view.png" alt="Vista del Workspace en STM32CubeIDE" width="700">
<br>
<em>Vista general del Workspace en STM32CubeIDE.</em>
</p>

---

Con esto ya comprendes la estructura básica del **Workspace** y cómo STM32CubeIDE organiza tus proyectos.  
En el siguiente capítulo aprenderás a **crear tu primer proyecto desde cero** y configurar los pines, periféricos y relojes de tu microcontrolador STM32. ⚡  

[(Ir al siguiente capítulo: Inicia tu Primer Proyecto)](../../Files/iniciar_proyecto/Iniciar_Proyecto.md)
