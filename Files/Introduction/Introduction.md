# 🧠 Mastering STM32 *(versión en Español)*
> Una guía práctica para entender, configurar y dominar los microcontroladores STM32 desde cero.
[(Volver al Indice)](https://github.com/JossueE/Mastering-STM32/tree/main?tab=readme-ov-file#%C3%ADndice)

## 👋 Hola! Soy Jossue Espinoza.

Estoy creando esta guía porque, al igual que tú, alguna vez tuve curiosidad por la familia de microcontroladores **STM32**. Sin embargo, muchas guías disponibles en internet suelen ser confusas, incompletas o excesivamente técnicas. Mi propósito es ofrecerte una ruta clara y práctica **para aprender los componentes esenciales y desarrollar tu primer proyecto funcional con STM32, paso a paso**. Quiero ayudarte a romper la barrera de entrada a esta poderosa familia de microcontroladores y que descubras por qué es una de las más utilizadas en el mundo **industrial y embebido**.

Si ya tienes experiencia en **sistemas embebidos** y has trabajado con **Arduino o ESP32**, notarás que trabajar con **STM32** es una experiencia distinta.
Esto se debe a que los STM32 utilizan núcleos **ARM Cortex-M**, diseñados para ofrecer un **procesamiento determinístico, alto rendimiento, bajo consumo energético y una fidelidad temporal excepcional**.

Además, cuentan con **más periféricos** y capacidades avanzadas que los hacen ideales para tareas críticas, como la implementación de **sistemas Hard-RTOS** (tiempo real estricto), manteniendo un **costo comparable o incluso menor** que otras plataformas populares.
Por ello, esta familia de microcontroladores no solo destaca en proyectos académicos o de prototipado, sino que también se utiliza ampliamente en **aplicaciones industriales y profesionales**.

Ahora, quiero ser honesto contigo. Al principio, sentirás que todo requiere **más esfuerzo** que en Arduino o ESP32.
Puede que te frustres cuando veas que una ESP32 parece hacer “lo mismo” de forma más sencilla.
Pero debes recordar que el STM32 **no es solo una tarjeta de desarrollo**, sino un **microcontrolador industrial** diseñado para ofrecer control total sobre el hardware.

Esa complejidad adicional es justamente lo que lo hace tan poderoso.
Al comienzo, las diferencias pueden parecer pequeñas, pero a medida que tus proyectos crezcan en **exigencia, precisión y complejidad**, apreciarás que esa base sólida marca una gran diferencia. 

---

## 📘 Introducción 

Los **STM32** son una familia de microcontroladores desarrollados por STMicroelectronics, basados en la arquitectura ARM Cortex-M.
Su potencia, flexibilidad y bajo consumo los han convertido en un estándar industrial dentro del mundo de los sistemas embebidos, la robótica, el IoT y el control en tiempo real.

A diferencia de plataformas como **Arduino o ESP32**, los STM32 ofrecen un control de bajo nivel sobre el hardware, acceso directo a los periféricos y una integración completa con sistemas **RTOS (como FreeRTOS)** y **buses de comunicación industriales** (CAN, I²C, SPI, UART, PWM, DMA, ADC, DAC).
Esto los hace ideales para proyectos donde la precisión temporal y la confiabilidad son esenciales.

Gran parte del contenido de este repositorio está inspirado en el libro **Mastering STM32 de Carmine Noviello**, una de las referencias más completas para entender esta familia de microcontroladores.

En este curso utilizaremos la placa **NUCLEO-H563ZI** como base de desarrollo.

> [!IMPORTANT]
> Si tienes otra placa, no te preocupes. Aunque no podrás seguir los ejemplos de forma idéntica, incluiré notas y recomendaciones para adaptar cada sección a diferentes modelos.

---

<figure style="margin:0; text-align:center; border:1px solid #eaecef; padding:6px; border-radius:6px;">
  <img src="Images/Introduction/NUCLEO-H563ZI.jpg"
       alt="Placa NUCLEO-H563ZI"
       style="max-width:50%; height:auto;" />
  <figcaption style="font-size:0.9em; color:#6a737d; margin-top:4px;">
    NUCLEO-H563ZI (STM32) — vista general de la placa.
  </figcaption>
</figure>

---
### ⚙️ ¿Qué es ARM y por qué es tan importante?

**ARM (Advanced RISC Machine)** es una arquitectura de procesadores **RISC (Reduced Instruction Set Computing)** optimizada para eficiencia energética y rendimiento determinista. 

Los núcleos **Cortex-M** (como M0, M3, M4, M7) están diseñados específicamente para **microcontroladores**, ofreciendo:

- Ejecución en tiempo real con latencias muy bajas.

- Consumo mínimo (ideal para baterías).

- Instrucciones simples y rápidas.

- Ecosistema estandarizado (CMSIS, HAL, CubeMX).

Por eso casi todos los fabricantes (ST, NXP, TI, Nordic, etc.) usan núcleos ARM en sus productos.


---
### 🔍 Comparativa: STM32 vs ESP32 vs Arduino

| Característica | STM32 | ESP32 | Arduino |
|-----------------|--------|--------|----------|
| **Arquitectura** | ARM Cortex-M (M0–M7) | Tensilica Xtensa LX6/LX7 | AVR de 8-bit (ATmega328, etc.) |
| **Frecuencia típica** | 32 MHz – 480 MHz | 160 MHz – 240 MHz | 16 MHz |
| **Memoria Flash / RAM** | 64 KB – 2 MB / 8 KB – 512 KB | 4 MB – 16 MB / 512 KB – 520 KB | 32 KB / 2 KB |
| **Periféricos** | ✅ ADC, DAC, PWM, I²C, SPI, UART, CAN, USB, Ethernet, DMA | ⚠️ ADC, PWM, I²C, SPI, UART, Wi-Fi, Bluetooth pero sin CAN nativo | ⚠️ ADC, PWM, I²C, SPI, UART, usos simples|
| **Conectividad inalámbrica** | ❌ Requiere módulo externo (Wi-Fi, BT) | ✅ Wi-Fi y Bluetooth integrados | ❌ Requiere módulo externo (Wi-Fi, BT)  |
| **Soporte RTOS** | Total (FreeRTOS, Zephyr, CMSIS-RTOS) | FreeRTOS nativo | Limitado o inexistente |
| **Consumo energético** | ✅ Muy bajo (modo Sleep/Stop) | ✅ Medio-alto | ⚠️ Bajo |
| **Voltaje de operación** | 1.8 V – 3.3 V (tolerante a 5 V en algunos pines) | 3.3 V | 5 V (algunos modelos 3.3 V) |
| **Nivel de complejidad** | Medio-alto (programación a bajo nivel) | Medio (SDK ESP-IDF o Arduino Core) | Bajo (Arduino IDE) |
| **Entorno de desarrollo** | STM32CubeIDE, Keil, PlatformIO, Arduino Core STM32 | Arduino IDE, ESP-IDF, PlatformIO | Arduino IDE |
| **Precio aproximado** | 10 – 30 USD (según serie y placa) | 6 – 12 USD | 5 – 10 USD |
| **Aplicaciones típicas** | Robótica, industrial, automotriz, control en tiempo real | IoT, domótica, conectividad Wi-Fi/BT | Educación, prototipado, makers |
| **Ventaja principal** | Precisión y fiabilidad industrial | Conectividad integrada y versatilidad | Simplicidad y facilidad de uso |
| **Desventaja principal** | Curva de aprendizaje más alta | Menor precisión en tiempo real | Limitado en potencia y periféricos |

---
### 🏭 ¿Por qué STM32 se usa en entornos industriales?

Los STM32 son el puente entre el mundo académico y la industria.
Su éxito en aplicaciones industriales se debe a:

- **Alta confiabilidad:** Tiempos de respuesta deterministas y baja latencia.

- **Amplia gama:** Desde microcontroladores pequeños (M0) hasta potentes M7.

- **Periféricos dedicados:** CAN-Bus, PWM de alta resolución, ADC de 16 bits, control de motores, muchísimos timers.

- **Compatibilidad con FreeRTOS y CMSIS-RTOS2**.

- **Certificaciones:** Muchos modelos cumplen normas IEC/ISO para automoción o control médico.

- **Ecosistema sólido:** CubeMX genera código base y configuraciones automáticas.

Por eso los encontrarás en **robots, drones, PLCs, equipos médicos y automotrices**. 

En resumen, los STM32 representan la frontera entre el **aprendizaje y la ingeniería profesional**, permitiéndote construir proyectos que trascienden el laboratorio y llegan al mundo real.

---

## ✨ Autor

**Jossue Espinoza**

Ingeniero en sistemas embebidos y robótica.

Apasionado por el desarrollo con **STM32, ROS2 y RTOS**.

📫 **Contacto:** [LinkedIn](https://www.linkedin.com/in/jossuee/) · [GitHub](https://github.com/JossueE)
