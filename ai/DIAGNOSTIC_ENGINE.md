# Diagnostic Engine

Árboles de diagnóstico iniciales para el banco UTP-PLC.

## Principios

- Diagnosticar de menor riesgo a mayor riesgo.
- Separar alimentación, señal, configuración, programa y carga.
- Cambiar una sola variable por vez.
- No atribuir una causa sin una prueba que la apoye.
- Después de resolver, registrar causa confirmada, corrección y evidencia.

## PLC no visible desde TIA Portal

1. ¿CPU energizada?
   - No → revisar 24 VDC.
   - Sí → continuar.
2. ¿LINK activo en CPU/CSM?
   - No → cable/puerto.
   - Sí → continuar.
3. ¿PC y CPU en misma subred?
   - No → corregir IP/máscara.
4. ¿Accessible devices encuentra la CPU?
   - No → revisar adaptador de red/firewall.
5. ¿Nombre PROFINET/IP duplicada?
   - Sí → corregir.

## Entrada digital no cambia

1. Confirmar tipo PNP/NPN/contacto seco.
2. Medir alimentación del sensor.
3. Medir la salida directamente.
4. Verificar común del grupo de entrada.
5. Verificar borne físico y dirección de TIA.
6. Revisar filtro de entrada si hay pulsos rápidos.

## Sensor PNP siempre activo

1. Medir BK respecto a 0 V sin objeto.
2. Revisar sensibilidad/calibración.
3. Revisar fondo o material circundante.
4. Comprobar que el común esté a 0 V.
5. Confirmar lógica NO/NC real.

## Ultrasónico UB1000 E01 no responde

1. Confirmar modelo `UB1000-18GM75-E01-V15`.
2. Medir BN–BU ≈ 24 VDC.
3. Confirmar que BK/WH son salidas digitales NPN.
4. Verificar adaptación NPN hacia PLC.
5. Observar LEDs al mover una placa plana.
6. Si no conmuta, repetir Teach-In dentro de la ventana permitida.
7. Si el usuario intenta usar AI/NORM_X/SCALE_X, corregir el enfoque.

## Contactor recibe orden pero no atrae

1. Medir A1–A2 durante la orden.
2. Si no hay 24 VDC → revisar salida/interfaz/común.
3. Si hay 24 VDC → medir resistencia de bobina con banco apagado.
4. Revisar supresor o conexión de polaridad si aplica.
5. Si atrae pero no hay feedback → revisar 13–14 y DI.

## Motor paso a paso vibra pero no gira

1. Detener movimiento.
2. Confirmar pares de bobinas A y B.
3. Verificar PUL y frecuencia.
4. Verificar DIR y ENA.
5. Confirmar corriente configurada.
6. Reducir frecuencia y aceleración.
7. Confirmar microstep y pasos/mm.
8. Si sigue vibrando, intercambiar solo una fase tras identificarla correctamente.

## Motor DC no gira

1. Confirmar 12 V en potencia.
2. Confirmar 5 V o nivel lógico requerido.
3. Verificar ENA/PWM.
4. Verificar IN1/IN2.
5. Medir tensión A+–A−.
6. Medir corriente.
7. Si módulo se calienta, detener: posible sobrecorriente.

## Encoder cuenta mal

1. Confirmar VCC y GND del encoder.
2. Observar canal A y B.
3. Confirmar CPR declarado.
4. Definir si CPR es antes o después de reductora.
5. Definir conteo x1/x2/x4.
6. Verificar HSC y filtro de entrada.
7. Comparar una vuelta física con conteo real.

## SINAMICS V20 enciende pero motor no gira

1. ¿Existe código de fallo?
   - Sí → leer código exacto y consultar manual.
2. ¿Orden de marcha activa?
   - No → revisar fuente de mando y DI.
3. ¿Frecuencia de referencia > 0 Hz?
   - No → revisar fuente de consigna y AI.
4. ¿Datos de placa cargados?
   - No → detener y configurar.
5. ¿Motor conectado según placa?
   - No confirmado → no continuar.
6. ¿Corriente sube anormalmente?
   - Sí → detener y revisar motor/cableado/carga.

## Entrada analógica da valor incorrecto

1. Confirmar que la señal sea realmente analógica.
2. Medir tensión/corriente físicamente.
3. Confirmar capacidad de la AI.
4. Verificar masa 3M.
5. Comparar valor bruto con rango esperado.
6. Revisar `NORM_X`.
7. Revisar `SCALE_X` y unidades.
8. Si se usa resistencia de carga, verificar su valor y compatibilidad con el transmisor.
