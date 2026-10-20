# Resultados del parcial práctico 2

Registrar resultados reales después de implementar y probar los endpoints. Sustituir los IDs de ejemplo por los utilizados.

| Petición y datos utilizados | Código esperado | Código obtenido | Observación |
| --- | --- | --- | --- |
| Crear una reserva con datos válidos y sala existente. | 201 | 201 | `roomId: 1` (Room A). Se creó la reserva id 4 con estado `active`. |
| Crear con participants como texto. | 400 | 400 | `"participants": "3"` → `participants must be an integer number`. |
| Crear con una propiedad adicional, como status. | 400 | 400 | `"status": "cancelled"` → `property status should not exist`. |
| Crear con una sala inexistente. | 404 | 404 | `roomId: 999` → `Room was not found`. |
| Cancelar una reserva activa y consultar el cambio guardado. | 200 | 200 | `PATCH /api/reservations/1/cancel`; `GET /api/reservations/1` confirmó `cancelled`. |
| Cancelar de nuevo la misma reserva. | 409 | 409 | Reserva 1 → `Reservation is already cancelled`. |
| Intentar cancelar con ID abc. | 400 | 400 | `ParseIntPipe` → `Validation failed (numeric string is expected)`. |
| Intentar cancelar con un ID entero inexistente. | 404 | 404 | ID 999 → `Reservation with id 999 was not found`. |

## Pruebas unitarias

Registrar el resultado de `npm test`.

| Caso | Resultado obtenido |
| --- | --- |
| 1. La regla real rechaza una reserva cancelada. | Pasó |
| 2. El servicio cancela y guarda una reserva activa. | Pasó |
| 3. Si la regla simulada rechaza, conserva active y no guarda. | Pasó |

Resumen de ejecución: Test Suites: 2 passed, 2 total. Tests: 3 passed, 3 total.
