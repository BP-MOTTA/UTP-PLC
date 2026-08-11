# Safety Gates

Las tareas físicas avanzan por estados. No se debe recomendar energizar si faltan verificaciones críticas.

## Estados

- `G0 IDENTIFICADO`: equipo/modelo suficientemente identificado.
- `G1 ALIMENTACION`: tensión, polaridad/fases y fuente confirmadas.
- `G2 SENAL`: tipo y niveles eléctricos de E/S confirmados.
- `G3 CABLEADO`: cableado propuesto con equipo desenergizado.
- `G4 PROTECCIONES`: protección, tierra y parada/emergencia aplicables verificadas.
- `G5 CONFIGURACION`: parámetros/software necesarios establecidos.
- `G6 PRUEBA_BAJA_ENERGIA`: primera prueba segura o sin carga cuando aplique.
- `G7 PRUEBA_FUNCIONAL`: operación controlada.
- `G8 VALIDADO`: resultado observado y documentado.

## Reglas

- No puentear protecciones ni parada de emergencia para acelerar una práctica.
- No asumir tensión, polaridad, PNP/NPN, tipo de entrada analógica o conexión Y/Δ.
- Para potencia, variadores y motores, separar claramente control y potencia.
- Ante una discrepancia entre foto, ficha y configuración documentada, detener el avance y pedir verificación.
- Indicar explícitamente `NO ENERGIZAR` cuando falte una condición crítica.
