# Finanzas PIBU — contexto para continuar

Pega este archivo al inicio de una conversación nueva junto con tu `index.html` actual.

## Dónde vive
- App: https://armando1991villaran-hub.github.io/finanzas-pibu/
- Repositorio: github.com/armando1991villaran-hub/finanzas-pibu (archivos: `index.html`, `firebase-config.js`, `firestore.rules`, `LEEME.md`, `manifest.webmanifest`, `sw.js`, `icon-192.png`, `icon-512.png`, `icon-maskable-512.png`, `apple-touch-icon.png`)
- Base de datos: Firebase, proyecto `finanzas-pibu` (Authentication con correo/contraseña + Firestore, plan gratuito Spark)
- Administrador principal: pibuskinbeauty@gmail.com
- Para actualizar: reemplazar `index.html` en GitHub (uno solo) y abrir con Ctrl+F5

## Cómo funciona
- **Administración** ve todo. **Vendedores** entran con usuario + PIN (`usuario@equipo.pibu.app`) y solo ven "Registrar venta" y "Gastos de tienda".
- Lo que captura el equipo se guarda en `capturas/{uid}/…` y la app de administración lo pasa a `ventas` / `gastos` como **Pendiente** para auditar.
- Colecciones: `ventas`, `gastos`, `nominas`, `config/general`, `catalogo/publico`, `usuarios`, `pines`, `capturas`, `recibos` (+ `recibos/{id}/partes`).
- Todo el código está en un solo `index.html` (HTML + CSS + JS, Firebase compat 10.12.2, jsPDF 2.5.1, JSZip 3.10.1 al descargar recibos).

## Pestañas (administración)
Registrar venta · Registrar gasto · Resumen · Dashboards · Auditoría · Recibos · Nómina · Ajustes

## Funciones ya hechas
- **Venta:** tienda, vendedor, turno, horas, **horas extra**, venta total, descuentos, cobro en MXN/USD/CAD/EUR (con tipo de cambio), BBVA, Mercado Pago, ventas en línea (Tomato, Página web, TikTok), gastos pagados de caja, diferencia/cuadre.
- **Gasto:** fecha, monto, concepto, tipo, clasificación, tienda, forma de pago, factura, **recibos adjuntos (foto o PDF, hasta 10, PDF máx. 8 MB)**.
- **Resumen y Dashboards:** estado de resultados, flujo de efectivo desde saldo inicial (BBVA, Mercado Pago, caja MXN/USD/EUR/CAD), gastos por concepto, ventas por plataforma en línea, gráficas de pay.
- **Auditoría:** estado Aprobado / Pendiente / Rechazado por registro; rechazados no cuentan en reportes. Detecta posibles duplicados y cruza gastos de caja con cortes.
- **Recibos:** por mes, filtro por tienda y búsqueda, ver/descargar, .zip del mes, lista de gastos sin recibo.
- **Nómina:** quincenal (horas × pago por hora + horas extra × tarifa extra) y comisiones semanales (comisión % tienda, % en línea, bono de puntualidad). Pago dividido entre cuentas. Recibos PDF individuales y generales. Se registran como gasto.
- **Marca y apariencia (Ajustes):** nombre, lema, logo, 9 paletas (incluye personalizada), modo claro/oscuro/automático; se aplica a la app, al equipo y a los PDF. Guardado en `config/general.marca` y `catalogo/publico.marca`.
- **App instalable (PWA):** manifest + service worker (archivos propios siempre en su versión nueva) + íconos; botón «Instalar app».
- **Proveedores:** campo en gasto, filtro y búsqueda en Auditoría, sección «Gasto por proveedor» en Resumen.
- **Compras personales del equipo:** en la venta (quién, monto, ticket), informativo; sección en Resumen con alerta de ticket repetido.
- **Ajustes:** saldo inicial, tiendas, vendedores (pago/hora, pago hora extra, comisión %, comisión en línea %, bono puntualidad), turnos y horas, tipos de cambio, multiplicador de hora extra (×2), accesos del equipo (crear, cambiar PIN, rol admin/vendedor, desactivar, eliminar), respaldo .json.

## Reglas importantes
- No subir el respaldo `.json` a GitHub.
- El equipo nunca debe ver nada fuera de su formulario.
- Si cambian las reglas de Firebase, se pegan completas en Firestore → Reglas → Publicar.
