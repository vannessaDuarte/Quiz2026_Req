# Taller mecánico (Django)

## Cómo ejecutarla

### Con Docker (PostgreSQL, usando tu `.env`)
```bash
docker compose up --build
```
Al iniciar, el contenedor genera las migraciones, migra la BD, carga datos de ejemplo
(`cargar_demo`, solo si la BD está vacía) y levanta el servidor en http://localhost:8000



## Flujo de una orden
1. **Recepcionista**: registra cliente → vehículos → crea la orden (estado *Recibido*, con fecha).
2. **Administrador**: asigna un mecánico libre (*En diagnóstico*) → el mecánico recibe notificación.
3. **Mecánico**: registra diagnóstico, repuestos (descuentan stock) y mano de obra → "Enviar al cliente"
   (*Esperando aprobación*; se crea notificación y se imprime un correo en consola).
4. **Cliente**: aprueba o rechaza → se notifica a recepción y administrador.
5. **Recepcionista**: genera la orden de reparación → se avisa al administrador y al mecánico.
   El administrador puede **reasignar** si el mecánico ya no está libre.
6. **Mecánico**: *En reparación* → *Listo para retiro* (botón grande inferior) → se genera la boleta/factura.
7. **Administrador**: ve facturas, aplica descuentos y revisa reportes.

## Cobertura de requerimientos
Todos los requerimientos están cargados como historias de usuario en el proyecto Quiz2026

## Notas

