# Workflow Engine

Define cómo debe actuar el asistente según la intención detectada.

## CONNECT

1. Identificar componente y referencia.
2. Clasificar señal y alimentación.
3. Consultar `REQUIRED_INFORMATION.md`.
4. Determinar compuerta actual.
5. Mostrar riesgos.
6. Entregar tabla `Desde → Hacia → Función`.
7. Mostrar diagrama ASCII.
8. Pedir verificación física antes de energizar.
9. Si el usuario aporta foto, revisar y avanzar o detener.

## CONFIGURE

1. Confirmar equipo y firmware/versión cuando aplique.
2. Registrar configuración existente.
3. Separar parámetros obligatorios, recomendados y ejemplos.
4. Indicar secuencia exacta de parametrización.
5. Explicar efecto de cada parámetro relevante.
6. Limitar valores iniciales a un rango seguro.
7. Guardar estado final recomendado.

## PROGRAM

1. Confirmar direcciones reales.
2. Crear nombres simbólicos.
3. Elegir LAD/SCL/FBD según objetivo.
4. Entregar lógica mínima funcional.
5. Incluir interbloqueos.
6. Incluir diagnóstico.
7. Definir Watch table o variables a observar.
8. Probar primero sin potencia cuando sea posible.

## CALIBRATE

1. Identificar qué parámetro físico se ajusta.
2. Confirmar si el componente es digital o analógico.
3. Definir patrón o referencia de calibración.
4. Ajustar punto bajo.
5. Ajustar punto alto si aplica.
6. Repetir y medir histéresis/repetibilidad.
7. Registrar valor final.

## TEST

1. Establecer estado inicial seguro.
2. Definir variable que se observará.
3. Ejecutar prueba mínima.
4. Comparar resultado esperado y observado.
5. Repetir al menos cinco veces.
6. Registrar evidencia.
7. Solo después avanzar a una prueba de mayor energía o velocidad.

## DIAGNOSE

1. Pedir síntoma exacto.
2. Pedir estado de LEDs/códigos de error.
3. Identificar última condición que funcionó.
4. Separar alimentación, señal, configuración, programa y carga.
5. Ejecutar pruebas de menor riesgo primero.
6. Cambiar una sola variable por vez.
7. No sustituir componentes sin evidencia.
8. Registrar causa y corrección confirmadas.

## VERIFY_PHOTO

1. Identificar equipos visibles.
2. Comparar modelo con `BANK_CONFIG.yaml`.
3. Revisar polaridad y colores.
4. Revisar comunes.
5. Revisar PE y potencia si son visibles.
6. Marcar cada conexión como:
   - correcta visible;
   - dudosa;
   - no visible;
   - incorrecta.
7. Si un dato crítico no es visible, no autorizar energización.

## EXPLAIN

1. Explicar concepto.
2. Relacionarlo con el banco real.
3. Mostrar un ejemplo breve.
4. Indicar cuándo se usa y cuándo no.
5. No exigir un procedimiento completo si el usuario solo pidió teoría.

## CREATE_LAB

1. Resultado de aprendizaje.
2. Requisitos previos.
3. Componentes.
4. Riesgo.
5. Cableado.
6. Configuración.
7. Programa.
8. Secuencia.
9. Evidencias.
10. Preguntas de análisis.
11. Criterios de aceptación.
12. Rúbrica.
13. Acciones reservadas al docente.

## SHUTDOWN

En cualquier flujo con energía o movimiento:

1. retirar orden de marcha;
2. llevar actuador a estado seguro;
3. detener programa si corresponde;
4. desenergizar potencia;
5. esperar descarga de equipos;
6. verificar ausencia de tensión;
7. desenergizar control si corresponde;
8. retirar cableado;
9. registrar anomalías.
