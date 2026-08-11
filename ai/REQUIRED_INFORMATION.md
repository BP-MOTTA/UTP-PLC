# Required Information

Este archivo define la información mínima que el asistente necesita antes de entregar instrucciones operativas.

## Regla general

No preguntar por datos que ya estén confirmados en `BANK_CONFIG.yaml`, en la ficha del componente o en evidencia enviada por el usuario.

Si falta un dato crítico para evitar daño, detener el procedimiento antes de energizar.

## PLC S7-1200

### Conectar entradas digitales

Obligatorio:

- modelo de CPU;
- tipo de sensor: PNP, NPN o contacto seco;
- tensión de alimentación;
- grupo de entrada y común asociado;
- dirección real o estado de dirección propuesta.

### Conectar entradas analógicas

Obligatorio:

- tipo de señal: 0–10 V, 4–20 mA u otra;
- rango del transmisor;
- capacidad real de la entrada PLC;
- masa/común analógico;
- rango bruto usado por la CPU.

## SINAMICS V20

### Conectar y testear motor

Obligatorio antes de energizar potencia:

- referencia exacta del V20;
- tensión de alimentación;
- datos de placa del motor;
- conexión estrella/triángulo o esquema equivalente;
- continuidad de PE;
- parada de emergencia operativa;
- guardamotor/protección disponible;
- modo de control deseado: BOP, terminales, analógico o comunicación;
- confirmación de supervisión docente/técnica.

Recomendado:

- carga mecánica;
- frecuencia máxima inicial;
- rampas;
- parámetros actuales guardados.

## Sensores PNP/NPN

Obligatorio:

- modelo exacto;
- alimentación;
- tipo de salida;
- color/pin de salida;
- común del grupo de entradas;
- si existe interfaz de adaptación.

## Sensor ultrasónico UB1000 E01

Obligatorio:

- confirmar terminación `E01`;
- confirmar que se usarán salidas digitales BK/WH;
- esquema NPN compatible o interfaz;
- distancias de Teach-In deseadas.

No solicitar ni usar:

- NORM_X;
- SCALE_X;
- resistencia de 500 ohmios;

salvo que el usuario esté trabajando con otro sensor analógico distinto.

## TB6600 / motor paso a paso

Obligatorio:

- nivel eléctrico de PUL/DIR/ENA;
- topología de entrada del módulo;
- tensión de alimentación;
- corriente del motor;
- configuración de microstep;
- pasos por vuelta;
- avance del husillo;
- finales de carrera;
- salida PTO disponible.

## L298N / motor DC

Obligatorio:

- tensión de motor;
- corriente real de operación;
- niveles lógicos del módulo;
- confirmación de adaptación 24 V → 5 V, si existe;
- frecuencia PWM;
- conexión del encoder;
- CPR y método de conteo.

## Contactores

Obligatorio:

- tensión y corriente de bobina;
- capacidad de la salida PLC o interfaz;
- supresión de sobretensión;
- contacto auxiliar de realimentación;
- estado de potencia desacoplada para la primera prueba.

## Regla para fotografías

Si el usuario pregunta “¿puedo energizar?” a partir de una foto, comprobar al menos:

- polaridad;
- PE;
- comunes;
- bornes de potencia;
- ausencia de puentes no documentados;
- estado de protecciones;
- emergencia;
- datos no visibles que sigan siendo críticos.

Si algo crítico no puede verse, responder `NO ENERGIZAR TODAVÍA` y pedir una foto o medición concreta.
