# Tarea pendiente: limpiar solicitudes erróneas en el Airtable de Euro Desguace Málaga

Creada el 24/11/2026 al revisar las conversaciones del día del agente "WhatsApp EURO DESGUACE MALAGA" (agent_5501m37w867df7gsbgyscz4jyvbf).

## Requisito previo: acceso
La base de Euro Desguace **no es accesible** desde el conector de Airtable actual, que solo ve "Car Center Palafrugell" (appZQyh1eyjbVF5bO). Las consultas de Euro Desguace entran por un webhook de Make de otra cuenta (loopinnova), que no está en la organización de Make conectada.

Para hacerla: conectar la cuenta de Airtable de Euro Desguace, o compartir esa base con la cuenta que ya está conectada.

## Qué arreglar
1. **Solicitud 2208** (origen `euro-desguace-malaga-whatsapp`, conversación `conv_4201m86n22cafc59a57wvb5q0mqp`, cliente "mecánica jesus ruiz s.l", "caja de cambios semiautomática Renault Master").
   - No es un pedido nuevo: el cliente reclamaba una caja de cambios que ya le habían enviado y llegó con una pieza rota.
   - Pasarla a Cancelada, Anulada o Duplicada (según las opciones del campo Estado) con la nota: "Creada por error por el agente de WhatsApp: era una devolución, no un pedido nuevo".
   - No borrarla sin confirmarlo antes.
2. **La devolución real.** Comprobar que existe el aviso o la gestión de DEVOLUCIÓN de ese cliente del 24/11, con la referencia de envío **72946590-24** y la foto de la pieza rota.
3. **Revisión del día.** Buscar otras consultas de WhatsApp del 24/11 que sean reclamaciones o devoluciones guardadas como pedidos nuevos, y listarlas.

## A partir de ahora
Desde la versión `agtvrsn_1101m8737zg7fne82mj3nrn3ebxv` del agente de WhatsApp, cuando crea una solicitud por error deja un aviso "AVISO · ANULAR SOLICITUD · creada por error..." con `amplia_solicitud` = el número de esa solicitud.

Valorar una automatización en Airtable o en Make que marque la solicitud como anulada cuando llegue ese aviso.
