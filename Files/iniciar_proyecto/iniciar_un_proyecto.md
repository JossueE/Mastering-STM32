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
4. Dirígete a la ventana `Board Selector` y en `Commercial Part Number` coloca el nombre de tu placa. 
5. Una ves encontrada seleccionala. 

> [!TIP]
> Te recomiendo darle a favoritos con el ícono de la ⭐ porque tendrás que usarla de manera recurrente.

6. Selecciona Next
7. Se abrirá una nueva pestaña en la que deberá definir el nombre de tu proyecto. 
8. Verifica que `Use default location` se encuentre activada, esto almacenará la información en tu workspace.
9. Selecciona el lenguaje en el que deseas programar, ya sea C++ o C.
10. Verifica que en las opciones se encuentre como archivo `Executable` 
11. Presiona `Finish`.
12. Selecciona `Disable All` o `Unselect All` y selecciona `Next`

> [!NOTE]
> Las definiciones necesarias para tu tarjeta de desarrollo específica se comenzarán a descargar. El tamaño de la descarga es de aproximadamente 1GB.
> Esta esla única vez que tendrás que realizar esta descarga.

13. Al terminar podrás ver una representación gráfica del microcontrolador integrado en tu tarjeta.
14. Al hacer `Zoom In` podrás ver que cada pin tiene un color diferente.
- El color gris representa que el pin no ha sido asignado. 
- El color crema (amarillo pálido) representa voltajes del microcontrolador (alimentación, tierra, referencia, ...).
- El color verde representa pines asignados. 
- El color rojo representa pines bloqueados o restringidos.

15. Si das `Click Izquierdo` sobre cualquier pin, verás las funciones que cada uno puede obtener.






