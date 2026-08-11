# UTP-PLC

Asistente técnico-pedagógico para laboratorios con PLC Siemens S7-1200, TIA Portal, sensores, actuadores y SINAMICS V20.

## Objetivo

Permitir que un usuario formule una petición natural como:

> “Ayúdame a conectar y testear el variador de frecuencia al motor”.

El sistema debe identificar el equipo, comprobar información crítica, aplicar compuertas de seguridad, recuperar la ficha y el laboratorio correctos, y entregar pasos específicos de conexión, configuración, prueba y diagnóstico.

## Arquitectura

- `ai/PLC_ASSISTANT_CORE.md`: reglas centrales del asistente.
- `ai/INTENT_ROUTER.md`: clasificación de intenciones.
- `ai/REQUIRED_INFORMATION.md`: datos mínimos antes de responder.
- `ai/SAFETY_GATES.md`: compuertas de seguridad y progreso.
- `ai/WORKFLOW_ENGINE.md`: flujo por tipo de solicitud.
- `ai/DIAGNOSTIC_ENGINE.md`: árboles de diagnóstico.
- `ai/RESPONSE_TEMPLATES.md`: formato estándar de respuestas.
- `ai/TEST_SCENARIOS.md`: pruebas del comportamiento del asistente.
- `config/BANK_CONFIG.yaml`: configuración maestra del banco.

## Principios

1. No inventar direcciones de TIA Portal.
2. Distinguir datos confirmados, probables, pendientes y ejemplos.
3. No mezclar señales PNP/NPN o analógicas sin comprobar compatibilidad.
4. No permitir saltar compuertas de seguridad.
5. Mantener modo estudiante y modo docente diferenciados.
6. Usar documentación oficial como referencia.
7. La IA no sustituye la verificación física del banco.

## Estado

Repositorio en construcción. Primero se implementa el motor conversacional y luego se incorporan fichas, laboratorios, esquemas y validaciones físicas del banco.
