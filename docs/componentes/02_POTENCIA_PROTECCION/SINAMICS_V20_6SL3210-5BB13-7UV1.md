# SINAMICS V20 — 6SL3210-5BB13-7UV1

## Estado

**CONFIRMADO** por placa fotografiada.

## Función

Variador de frecuencia para controlar un motor trifásico mediante frecuencia y tensión variables.

## Datos principales

| Parámetro | Valor |
|---|---|
| Fabricante | Siemens |
| Familia | SINAMICS V20 |
| Referencia | 6SL3210-5BB13-7UV1 |
| Entrada | 1~ AC 200–240 V |
| Potencia de motor | 0,37 kW / 0,5 HP |
| Corriente de salida indicada | 2,3 A |
| Frecuencia de salida | 0–550 Hz |
| Comunicación | RS485, USS/Modbus RTU |

## Bornes de control visibles en el panel didáctico

| Borne | Función indicada |
|---:|---|
| 1 | 10 V |
| 2 | AI1 |
| 3 | AI2 |
| 4 | AO1 |
| 5 | 0 V analógico |
| 6 | RS485 P+ |
| 7 | RS485 N− |
| 8–11 | DI1–DI4 |
| 12 | DI C |
| 13 | 24 V |
| 14 | 0 V |
| 15–16 | DO1 transistor |
| 17–19 | DO2 relé NC/NO/C |

## Alimentación y motor

> **RIESGO ALTO**
> La conexión de entrada AC, PE y salida U/V/W es exclusiva del docente o personal calificado.

La conexión exacta del motor depende de los datos de placa y de la configuración estrella/triángulo permitida. No se debe inferir.

## Modos de control didáctico recomendados

### Nivel 1 — BOP

Primera puesta en marcha desde el panel del propio V20, con frecuencia limitada y motor validado.

### Nivel 2 — Terminales digitales

- DI1: orden de marcha, según parametrización.
- fuente de consigna definida aparte.

### Nivel 3 — Referencia analógica

- AI1 puede recibir una consigna 0–10 V si el V20 está configurado para ello.
- La CPU 1215C del banco entrega AO 0–20 mA, por lo que debe utilizarse el conversor del banco o una interfaz validada para obtener 0–10 V.

### Nivel 4 — RS485

Control mediante USS o Modbus RTU después de validar el control básico por terminales.

## Parámetros de puesta en marcha

Antes de cambiar parámetros:

1. registrar configuración existente;
2. leer placa del motor;
3. confirmar frecuencia nominal;
4. confirmar corriente nominal;
5. confirmar tensión y conexión Y/Δ;
6. confirmar velocidad nominal;
7. definir rampas iniciales suaves;
8. limitar frecuencia de la primera prueba.

Valores como P0700, P1000, P1080, P1082, P1120 y P1121 deben verificarse contra el manual y la configuración real antes de aplicarse.

## Integración con PLC

Variables sugeridas, no direcciones confirmadas:

| Variable | Tipo | Función |
|---|---|---|
| `V20_RunCmd` | Bool | Orden de marcha |
| `V20_Fault` | Bool | Estado de fallo |
| `V20_Setpoint_Hz` | Real | Consigna de frecuencia |
| `V20_AQ_Raw` | Int | Valor de salida analógica |

## Lógica mínima conceptual

```scl
Permiso_Marcha := Emergencia_OK
                  AND Guardamotor_OK
                  AND NOT V20_Fault;

V20_RunCmd := Orden_Marcha AND Permiso_Marcha;
```

## Primera prueba recomendada

Después de validar placa, conexión, PE y emergencia:

1. motor sin carga peligrosa;
2. frecuencia máxima temporal reducida;
3. orden de marcha corta;
4. verificar sentido, ruido y corriente;
5. detener;
6. repetir antes de aumentar frecuencia.

## Diagnóstico inicial

- V20 no arranca → revisar fuente de mando.
- frecuencia en 0 Hz → revisar fuente de consigna.
- motor zumba → detener y revisar placa/cableado.
- sobrecorriente → detener y revisar carga, motor y parametrización.
- sentido incorrecto → no cambiar cables energizado; corregir con banco aislado o por parámetro cuando corresponda.

## Pendientes de validación del banco

- parámetros actualmente cargados;
- conexión exacta entre AQ del PLC y AI1 del V20;
- funcionamiento real del conversor 0–20 mA / 0–10 V;
- contacto de fallo usado hacia el PLC;
- direcciones de E/S reales del proyecto TIA.

## Referencia

Consultar `docs/referencias/DATASHEETS_OFICIALES.md`.
