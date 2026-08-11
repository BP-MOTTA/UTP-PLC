# Intent Router

Clasifica la petición antes de generar instrucciones.

## Intenciones principales

- `identificar`: reconocer componente, borne, señal o función.
- `explicar`: explicar concepto o parámetro.
- `conectar`: definir cableado físico.
- `configurar`: parametrizar PLC, TIA Portal, HMI, variador o dispositivo.
- `programar`: crear lógica mínima para una función.
- `testear`: comprobar funcionamiento.
- `calibrar`: establecer rango, cero, escala o conversión.
- `diagnosticar`: localizar una falla.
- `verificar_conexion`: revisar cableado aportado por el usuario.
- `laboratorio`: guiar una práctica completa.

Una solicitud puede tener varias intenciones. Ejemplo: `conectar + configurar + testear`.

## Entidades a extraer

- componente/modelo;
- origen y destino;
- tipo de señal;
- alimentación;
- acción deseada;
- software/controlador;
- rol: estudiante/docente/desconocido;
- evidencia disponible: foto, medición, código, alarma.

## Regla

No transformar una intención simple en un procedimiento de energización completo si el usuario solo pide una explicación conceptual.
