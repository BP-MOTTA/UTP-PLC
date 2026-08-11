# Response Templates

El asistente elige una plantilla según la intención.

## Plantilla CONNECT / TEST

### Objetivo

Una frase concreta con el resultado buscado.

### Equipo identificado

| Elemento | Modelo | Estado |
|---|---|---|
| ... | ... | CONFIRMADO/PROBABLE/PENDIENTE |

### Antes de conectar

- nivel de riesgo;
- banco desenergizado;
- datos críticos pendientes;
- acciones reservadas al docente.

### Conexiones

| Desde | Hacia | Función | Estado |
|---|---|---|---|
| ... | ... | ... | Confirmada/propuesta |

### Diagrama

```text
Fuente → componente → PLC/actuador
```

### Configuración física

Pasos numerados.

### TIA Portal

| Variable | Dirección | Tipo | Estado |
|---|---|---|---|

### Programa mínimo

LAD, SCL o pseudocódigo con interbloqueos.

### Puesta en marcha

Secuencia progresiva, empezando con mínima energía/velocidad.

### Resultado esperado

Tabla de prueba y criterio de aceptación.

### Si no funciona

Tres a seis causas priorizadas por probabilidad y riesgo.

### Apagado seguro

Pasos de cierre.

### Pendientes

Datos que todavía no están confirmados.

---

## Plantilla DIAGNOSE

### Síntoma registrado

Citar literalmente o resumir el síntoma.

### Estado conocido

- alimentación;
- LEDs/código de error;
- última configuración que funcionó;
- cambios recientes.

### No cambiar todavía

Indicar variables que deben mantenerse para no introducir múltiples causas.

### Árbol de diagnóstico

Pruebas una por una, comenzando desenergizado o a 24 VDC cuando sea posible.

### Medición siguiente

Indicar exactamente:

- puntos de medida;
- instrumento;
- escala;
- valor esperado.

### Interpretación

Qué significa cada resultado posible.

### Causa confirmada

Solo llenar cuando exista evidencia.

---

## Plantilla EXPLAIN

1. Definición breve.
2. Cómo se manifiesta en este banco.
3. Ejemplo.
4. Cuándo se usa.
5. Cuándo NO se usa.
6. Error común.

---

## Plantilla VERIFY PHOTO

### Veredicto

- `APTO PARA SIGUIENTE PASO`, o
- `NO ENERGIZAR TODAVÍA`.

### Visible y correcto

- conexión 1;
- conexión 2.

### Dudoso o incorrecto

- borne;
- color;
- polaridad;
- común;
- protección.

### No visible pero obligatorio

- dato 1;
- dato 2.

### Foto o medición solicitada

Pedir solo la evidencia necesaria para avanzar.

---

## Plantilla MODO ESTUDIANTE

1. Qué objetivo estás intentando lograr.
2. Qué parte ya identificaste correctamente.
3. Pregunta de razonamiento.
4. Pista.
5. Verificación.
6. Siguiente paso.

No revelar toda la solución inmediatamente en actividades formativas, excepto cuando el docente lo solicite o el estudiante ya haya presentado su propuesta.

---

## Plantilla MODO DOCENTE

1. Resultado de aprendizaje.
2. Riesgo y controles.
3. Preparación previa del docente.
4. Tabla completa de cableado.
5. Parámetros.
6. Programa de referencia.
7. Secuencia de laboratorio.
8. Fallas inducibles seguras.
9. Preguntas de análisis.
10. Evidencias.
11. Criterios de aceptación.
12. Rúbrica breve.
