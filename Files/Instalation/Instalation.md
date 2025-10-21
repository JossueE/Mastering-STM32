# 🧩 Instalación del entorno de desarrollo para STM32

[(Volver al Indice)](README.md)

En este capítulo aprenderás a preparar tu entorno de desarrollo para trabajar con **microcontroladores STM32**.  
Instalaremos las herramientas oficiales de STMicroelectronics y otras utilidades necesarias para compilar, cargar y depurar tus proyectos. Cabe mencionar que la familia STM32 es muy extensa, es por ello que algunas placas orientadas a diferentes entornos como la **STM32H747I-DISCO**  que incluye pantalla, tienen interfases propias para su desarrollo. 

> [!NOTE]
> En este curso utilizaremos la placa **NUCLEO-H563ZI** como base de desarrollo.

---
## 📖 Partes del Capítulo

- [🧠 1. ¿Qué softwares existen?](#-1-qué-softwares-existen)
- [⚙️ 2. Instalación paso a paso](#%EF%B8%8F-2-instalaci%C3%B3n-paso-a-paso) 
  - [🪟 Windows](#-windows)
  - [🐧 Linux (Ubuntu / Debian)](#-linux-ubuntu--debian)
  - [🍎 macOS](#-macos)
- [🗂️ 3. Configura tu Workspace](#%EF%B8%8F-3-configura-tu-workspace)
---

## 🧠 1. ¿Qué softwares existen?

| Herramienta | Descripción | Enlace |
|--------------|-------------|---------|
| **STM32CubeIDE** | Entorno de desarrollo oficial de ST (basado en Eclipse). Incluye compilador GCC, depurador, editor y programador. | [Descargar STM32CubeIDE](https://www.st.com/en/development-tools/stm32cubeide.html) |
| **STM32CubeMX** | (Opcional) Asistente visual para configurar periféricos, pines y generar código automáticamente. | [Descargar STM32CubeMX](https://www.st.com/en/development-tools/stm32cubemx.html) |
| **ST-LINK Utility / STM32CubeProgrammer** | (Opcional) Herramientas para flashear y verificar firmware en placas STM32. | [Descargar CubeProgrammer](https://www.st.com/en/development-tools/stm32cubeprog.html) |
| **Drivers USB ST-Link/V2** | (Opcional) Controladores necesarios para que tu PC reconozca el programador ST-Link integrado en las placas Nucleo o Discovery. | [Descargar Drivers](https://www.st.com/en/development-tools/stsw-link009.html) |

> [!IMPORTANT]
> Estos son algunos de los softwares más importantes, pero te recomiendo validar el software a utilizar, basandote en tu modelo de placa.

---
## ⚙️ 2. Instalación paso a paso

### 1. Crear una cuenta

Entra a la págnia oficial [st.com](https://www.st.com/content/st_com/en.html) y crea una cuenta. Si eres estudiante puedes hacerlo con tu correo institucional, pero recuerda que tu cuenta estará ligada a tu correo. Es necesario que inicies sesión para poder descargar el software de manera **gratuita**.

### 2. Descargar el Software

Con tu cuenta Iniciada:

- Dirígete a [STM32CubeIDE](https://www.st.com/content/st_com/en/products/development-tools/software-development-tools/stm32-software-development-tools/stm32-ides/stm32cubeide.html) da un scroll hacia abajo y ahí selecciona la opción que más se ajuste a tu sistema operativo y comienza la descarga. (

> [!NOTE]
> El archivo debe pesar aproximadamente 1Gb

#### 🪟 Windows
1. Descomprime el software al finalizar la descarga. 
2. Comienza la instalación usando la configuración por default. Dicha configuración incluye el software necesario para la comunicación USB con tu tarjeta.
3. Al terminar la instalación conecta tu NUCLEO a la computadora. Los drivers deben reconocer el dispositivo.
4. (Opcional) Si tu placa no es reconocida, primero valida estar conectado por el puerto **ST-LINK** no el de alimentación o instala los **drivers ST-Link** manualmente.

---

### 🐧 Linux (Ubuntu / Debian)
1. Descomprime el software al finalizar la descarga. Yo te recomiendo hacerlo en `~/Downloads`
2. Aparecerá un archivo `.sh` de STM32CubeIDE.
3. Abre una nueva terminal con `Ctrl + Alt + T`
    ```bash
    # Dirígete en donde hayas descomprimido el archivo
    cd Downloads
    ```
4. Ahora haremos ejecutable al archivo:
    ```bash
    chmod +x st-stm32cubeide*.sh
    ./st-stm32cubeide*.sh
    # Deberás aceptar los términos y condiciones, para proceder con la descarga. 
    ```
> [!NOTE]
> Te recomiendo ser cuidadoso al aceptar los términos, ya que de no responder de manera adecuada a alguna de las indicaciones. La descarga se interrumpirá, quedándose a medias. Y no podrás continuarla después, deberás volver a empezar.

5. (Opcional) Crear un acceso directo:
    Debido a la manera como se descarga, tu sistema no la reconocerá y deberás abrir la carpeta y ejecutar el .exec cada vez que desees usar el ID.

    Esta solución lo arregla para siempre
    ```bash
    # En una nueva terminal
    nano ~/.local/share/applications/stm32cubeide.desktop
    ```
    y pega:

   ```bash
   [Desktop Entry]
    Name=STM32CubeIDE
    Exec={TU_RUTA}/stm32cubeide
    Icon={TU_RUTA}/icon.xpm
    Type=Application
    Categories=Development;IDE;
    Terminal=false
   ```
   > [!IMPORTANT]
    > No olvides modificar el valor `TU_RUTA` con la dirección que se haya creado

    Guarda (`Ctrl+O`, `Enter`, `Ctrl+X`)
    y luego:

    ```bash
        chmod +x ~/.local/share/applications/stm32cubeide.desktop
        update-desktop-database ~/.local/share/applications
    ```
    👉 Ahora te aparecerá en el menú de aplicaciones y podrás anclarlo al dock como cualquier otro programa.

6. Al terminar la instalación conecta tu NUCLEO a la computadora. Los drivers deben reconocer el dispositivo.
7. (Opcional) Si tu placa no es reconocida, primero valida estar conectado por el puerto **ST-LINK** no el de alimentación o instala los **drivers ST-Link** manualmente.

---

### 🍎 macOS
1. Una vez finalizada la descarga, arrastra la app a tu carpeta de `Aplicaciones`
2. Comienza la instalación usando la configuración por default. Dicha configuración incluye el software necesario para la comunicación USB con tu tarjeta.
3. Conecta la placa, macOS instalará los drivers automáticamente.
4. (Opcional) Si tu placa no es reconocida, primero valida estar conectado por el puerto **ST-LINK** no el de alimentación o instala los **drivers ST-Link** manualmente.

---
## 🗂️ 3. Configura tu Workspace
Cuando abras **STM32CubeIDE** por primera vez, el programa te pedirá elegir la ubicación de tu **espacio de trabajo (workspace)**, que es donde se guardarán todos tus proyectos, configuraciones y archivos generados.
- ⚠️ Evita rutas con espacios o caracteres especiales, ya que algunas bibliotecas y compiladores pueden fallar al procesarlas.
- También puedes ubicar tu workspace dentro de carpetas sincronizadas con la nube (como Google Drive, Dropbox o OneDrive) sin problemas; el entorno funciona correctamente con esas ubicaciones.
- Si no tienes una razón específica para cambiarlo, usa la carpeta por defecto sugerida por STM32CubeIDE. Es la opción más estable y fácil de respaldar.

---
[(Manejo de GPIO)](README.md)