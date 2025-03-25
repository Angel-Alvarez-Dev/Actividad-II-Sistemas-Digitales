# Actividad II - Sistemas Digitales

## Objetivo
Desarrollar la habilidad para utilizar las técnicas de reducción de funciones lógicas en el proceso de diseño de sistemas digitales.

## Descripción
Este proyecto implementa un **sistema digital** que:
1. **Compara** dos datos de 2 bits (A y B) para determinar si A > B, A < B o A = B.  
2. **Suma** esos datos de 2 bits (A + B).  
3. **Muestra** en un único display de 7 segmentos, según un selector de 2 bits (S1, S0), uno de los siguientes valores:
   - Valor de A  
   - Valor de B  
   - Suma (A + B)  
   - Letra que indica el resultado de la comparación: **G** (Greater), **L** (Less), o **E** (Equal).  
4. Incluye **4 LEDs** para indicar qué operación se está mostrando en el display (A, B, Suma o Comparador).

---

![Img](https://github.com/user-attachments/assets/7c4d3c63-5aaf-4343-b8ba-aeccd0b98a07)


- **`sumador_2bits.circ`**  
  Implementa la lógica para sumar dos números de 2 bits, generando un resultado de 3 bits (extendido a 4 para el multiplexor).

- **`comparador_2bits.circ`**  
  Determina la relación entre A y B (mayor, menor, igual), y codifica el resultado (G, L, E) en 4 bits.

- **`multiplexor_4x1.circ`**  
  Selecciona, de entre cuatro entradas de 4 bits, cuál se envía a la salida según las líneas de selección (S1, S0).

- **`decodificador_4bits_7seg.circ`**  
  Convierte 4 bits en las 7 señales que activan un display de 7 segmentos, incluyendo la posibilidad de mostrar letras (G, L, E).

- **`leds_indicadores.circ`**  
  Enciende el LED correspondiente a la operación seleccionada, usando las líneas de selección (S1, S0).

- **`main.circ`**  
  Integra todos los módulos anteriores en un solo circuito. Aquí se conectan las entradas A, B, el selector y se observan las salidas en el display y los LEDs.

---

## Instrucciones de Uso

1. **Clona o descarga** este repositorio en tu computadora.
2. **Abre** el archivo `main.circ` con [Logisim Evolution](https://github.com/reds-heig/logisim-evolution).
3. **Configura** las entradas:
   - `A[1:0]` y `B[1:0]` para los datos de 2 bits.
   - `S1, S0` para elegir qué mostrar:
     - `00`: Muestra A  
     - `01`: Muestra B  
     - `10`: Muestra A + B  
     - `11`: Muestra el resultado del comparador (G, L, E)
4. **Observa** en el **display de 7 segmentos** el valor o la letra seleccionada.
5. **Verifica** que el LED correspondiente (A, B, Suma o Comparador) se encienda.

---

## Paso a Paso de Conexión (Resumen)

1. **Entradas A y B** → se conectan tanto al `sumador_2bits` como al `comparador_2bits`.  
2. **Salida del sumador** (3 bits) → se extiende a 4 bits y va a la entrada #2 del `multiplexor_4x1`.  
3. **Salida del comparador** (4 bits) → va a la entrada #3 del `multiplexor_4x1`.  
4. **A y B (2 bits)** → también se extienden a 4 bits y van a las entradas #0 y #1 del `multiplexor_4x1`.  
5. **Selector (S1, S0)** → controla tanto el `multiplexor_4x1` como el módulo `leds_indicadores`.  
6. **Salida del multiplexor** (4 bits) → `decodificador_4bits_7seg` → **display de 7 segmentos**.  
7. **Salida de `leds_indicadores`** → se conecta a 4 LEDs, uno por cada operación (A, B, Suma, Comparador).

---

## Referencias

- [Logisim Evolution](https://github.com/reds-heig/logisim-evolution): Herramienta para diseñar y simular circuitos digitales.
- Material de clase sobre **Sistemas Digitales**, tablas de verdad, mapas de Karnaugh y codificación en 7 segmentos.

---
