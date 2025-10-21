# 🔨 Inicia tu Primer Proyecto

[(Volver al Índice)](../README.md)

---

Una vez que hayas definido tu **workspace**, podemos comenzar a construir tu **primer proyecto con STM32CubeIDE**.  
En esta sección aprenderás a crear un nuevo proyecto desde cero, seleccionar el microcontrolador o placa de desarrollo, configurar los periféricos básicos y compilar tu primer programa.

---

## 🧱 1. Crear un nuevo proyecto

1. Con **STM32CubeIDE** abierto y el workspace seleccionado.  
2. En la barra superior izquierda, selecciona:  
   **File → New → STM32 Project**
3. Se abrirá una ventana llamada **Target Selection**. Aquí podrás elegir:
   - Tu **placa NUCLEO** (por ejemplo: `NUCLEO-H563ZI`)  
   - O directamente el **microcontrolador** (por ejemplo: `STM32H563ZITx`)

![Ventana Target Selection](Images/iniciar_proyecto/TargetSelection.png)

*Ventana Target Selection*


4. Dirígete a la ventana `Board Selector` y en `Commercial Part Number` coloca el nombre de tu placa. 

<figure style="margin:0; text-align:center; border:1px solid #eaecef; padding:6px; border-radius:6px;">
  <img src="Images/iniciar_proyecto/BoardSelector.png"
       alt="Ventana Target Selection"
       style="max-width:50%; height:auto;" />
  <figcaption style="font-size:0.9em; color:#6a737d; margin-top:4px;">
    Ventana Target Selection
  </figcaption>
</figure>   

5. Una ves encontrada seleccionala. 

> [!TIP]
> Te recomiendo darle a favoritos con el ícono de la ⭐ porque tendrás que usarla de manera recurrente.

6. Selecciona Next
7. Se abrirá una nueva pestaña en la que deberá definir el nombre de tu proyecto. 
8. Verifica que `Use default location` se encuentre activada, esto almacenará la información en tu workspace.
9. Selecciona el lenguaje en el que deseas programar, ya sea C++ o C.
10. Verifica que en las opciones se encuentre como archivo `Executable` 
11. Presiona `Finish`.

<figure style="margin:0; text-align:center; border:1px solid #eaecef; padding:6px; border-radius:6px;">
  <img src="Images/iniciar_proyecto/ConfigurationFile.png"
       alt="Ventana de Configuración"
       style="max-width:50%; height:auto;" />
  <figcaption style="font-size:0.9em; color:#6a737d; margin-top:4px;">
    Ventana de Configuración
  </figcaption>
</figure>   

12. Selecciona `Disable All` o `Unselect All` y selecciona `Next`

<figure style="margin:0; text-align:center; border:1px solid #eaecef; padding:6px; border-radius:6px;">
  <img src="Images/iniciar_proyecto/BoardOptions.png"
       alt="Ventana de Opciones"
       style="max-width:50%; height:auto;" />
  <figcaption style="font-size:0.9em; color:#6a737d; margin-top:4px;">
    Ventana de Opciones
  </figcaption>
</figure>   

> [!NOTE]
> Las definiciones necesarias para tu tarjeta de desarrollo específica se comenzarán a descargar. El tamaño de la descarga es de aproximadamente 1GB.
> Esta esla única vez que tendrás que realizar esta descarga.

13. Al terminar podrás ver una representación gráfica del microcontrolador integrado en tu tarjeta.
<figure style="margin:0; text-align:center; border:1px solid #eaecef; padding:6px; border-radius:6px;">
  <img src="Images/iniciar_proyecto/ReMicro.png"
       alt="Representación Gráfica del Micro"
       style="max-width:50%; height:auto;" />
  <figcaption style="font-size:0.9em; color:#6a737d; margin-top:4px;">
    Representación Gráfica del Micro
  </figcaption>
</figure>   

14. Al hacer `Zoom In` podrás ver que cada pin tiene un color diferente.

| Color       | Significado                                                     | Ejemplo                         |
| ----------- | --------------------------------------------------------------- | ------------------------------- |
| ⚪ Gris    | Pin **no asignado** (disponible).                               | Sin función seleccionada.       |
| 🟡 Amarillo | Pin **configurado por el usuario** (GPIO, o periférico simple). | PB0 → GPIO_Output (LED).        |
| 🟢 Verde    | Pin **asignado automáticamente a un periférico**.               | USART2_TX, I2C1_SCL, SPI1_MISO. |
| 🔵 Azul     | Pin **usado por una función fija del sistema**.                 | Reset, Vref, NRST, OSC_IN.      |
| 🔴 Rojo     | **Conflicto o error** (dos funciones usan el mismo pin).        | SPI1 y USART2 en el mismo pin.  |
| 🟣 Morado   | **Función alternativa activa (Alternate Function)**.            | PWM, I²C, SPI, UART, TIM.       |


15. Si das `Click Izquierdo` sobre cualquier pin, verás las funciones que cada uno puede obtener.
<figure style="margin:0; text-align:center; border:1px solid #eaecef; padding:6px; border-radius:6px;">
  <img src="Images/iniciar_proyecto/FuncionesPin.png"
       alt="Funciones de cada Pin"
       style="max-width:50%; height:auto;" />
  <figcaption style="font-size:0.9em; color:#6a737d; margin-top:4px;">
    Funciones de cada Pin
  </figcaption>
</figure>   






