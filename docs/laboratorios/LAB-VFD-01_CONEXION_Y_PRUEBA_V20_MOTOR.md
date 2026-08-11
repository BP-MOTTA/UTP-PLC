# LAB-VFD-01 — Conexión y prueba supervisada del SINAMICS V20 con motor trifásico

## Objetivo

Conectar, parametrizar y probar el SINAMICS V20 con el motor trifásico del banco, comenzando por una puesta en marcha de baja velocidad y avanzando luego al control desde PLC.

## Riesgo

**ALTO.** La red de 220 VAC, salida trifásica, bornes de potencia del variador y motor solo pueden ser manipulados por el docente o personal calificado.

## Componentes

- SINAMICS V20 `6SL3210-5BB13-7UV1`.
- Motor ABB M2QA, variante exacta pendiente de confirmar.
- Guardamotor `3RV2011-1CA10`.
- Parada de emergencia del banco.
- CPU 1215C para la fase de control por PLC.

## Compuertas obligatorias

Antes de energizar:

- [ ] referencia del V20 confirmada;
- [ ] placa del motor transcrita;
- [ ] conexión Y/Δ confirmada;
- [ ] PE confirmado;
- [ ] parada de emergencia probada;
- [ ] protección ajustada;
- [ ] parámetros originales registrados;
- [ ] motor sin carga peligrosa;
- [ ] zona despejada;
- [ ] supervisión docente presente.

Si falta cualquiera de las condiciones críticas, **NO ENERGIZAR**.

## Fase 1 — Conexión de potencia

La conexión física debe verificarse con el manual y el rótulo del banco.

| Desde | Hacia | Función |
|---|---|---|
| alimentación monofásica protegida | entrada AC del V20 | alimentación |
| PE | PE del V20 | protección |
| V20 U | motor U1 | fase de motor |
| V20 V | motor V1 | fase de motor |
| V20 W | motor W1 | fase de motor |
| PE del V20 | carcasa del motor | protección |

> La disposición de puentes del motor depende de la placa. No se prescribe hasta confirmarla.

## Fase 2 — Datos del motor

Registrar:

| Dato | Valor real |
|---|---|
| Potencia | Pendiente |
| Tensión | Pendiente |
| Corriente | Pendiente |
| Frecuencia | Pendiente |
| Velocidad nominal | Pendiente |
| cos φ | Pendiente |
| Conexión Y/Δ | Pendiente |

## Fase 3 — Primera puesta en marcha desde BOP

1. Registrar parámetros existentes.
2. Introducir datos de placa según procedimiento de puesta en marcha del manual.
3. Limitar inicialmente la frecuencia máxima a un valor reducido, por ejemplo 5–10 Hz como **EJEMPLO**, siempre que el motor y proceso lo permitan.
4. Usar rampas suaves.
5. Dar una orden breve de marcha.
6. Observar sentido, vibración, ruido y corriente.
7. Detener.
8. Repetir cinco veces antes de aumentar la frecuencia.

## Fase 4 — Control por terminales

Una vez validada la fase BOP:

| Señal | V20 | Función |
|---|---|---|
| salida digital PLC/interfaz | DI1 | marcha, según parametrización |
| común correspondiente | DI C | referencia digital |
| contacto DO2 del V20 | DI PLC | fallo/estado, si se configura |

Las direcciones PLC se registrarán después de validar la configuración real de TIA Portal.

## Fase 5 — Consigna analógica

El PLC incorpora salidas 0–20 mA, mientras que la referencia típica del V20 en AI1 puede configurarse como 0–10 V. El banco incluye un conversor 4–20 mA/0–10 V cuya función real debe validarse antes de usarlo.

Flujo conceptual:

```text
Consigna_Hz
   ↓
limitación
   ↓
escalamiento de AO
   ↓
AQ del PLC 0–20 mA
   ↓
conversor validado
   ↓
0–10 V
   ↓
AI1 del V20
```

No utilizar una resistencia de conversión sin comprobar la carga y el diseño del circuito.

## Variables sugeridas

| Variable | Tipo | Dirección |
|---|---|---|
| `V20_RunCmd` | Bool | Pendiente |
| `V20_Fault` | Bool | Pendiente |
| `V20_Setpoint_Hz` | Real | DB |
| `V20_AQ_Raw` | Int | Pendiente |
| `Emergency_OK` | Bool | Pendiente |
| `MotorProtection_OK` | Bool | Pendiente |

## Programa mínimo conceptual

```scl
Permiso_Marcha := Emergency_OK
                  AND MotorProtection_OK
                  AND NOT V20_Fault;

V20_RunCmd := Orden_Marcha AND Permiso_Marcha;
```

## Pruebas

| Prueba | Resultado esperado |
|---|---|
| Marcha corta a baja frecuencia | giro estable |
| Orden de parada | rampa de parada correcta |
| Variación de consigna | frecuencia sigue referencia |
| Emergencia | sistema entra en condición segura |
| Fallo del V20 | nueva marcha queda bloqueada |

## Diagnóstico

### V20 encendido, motor detenido

- comprobar orden de marcha;
- comprobar fuente de mando;
- comprobar frecuencia de referencia;
- comprobar fallos;
- comprobar datos de motor.

### Motor zumba o corriente aumenta rápidamente

Detener inmediatamente y revisar:

- conexión del motor;
- datos de placa;
- parámetros;
- carga mecánica.

### PLC ordena pero V20 no responde

- medir estado de DI1;
- revisar común digital;
- revisar fuente de mando configurada;
- revisar salida/interfaz del PLC.

## Evidencias

- foto de placa del motor;
- foto del cableado desenergizado;
- captura de parámetros principales;
- captura de Watch table;
- corriente y frecuencia de cada prueba;
- conclusión del grupo.

## Estado

**PENDIENTE DE VALIDACIÓN FÍSICA COMPLETA.**
