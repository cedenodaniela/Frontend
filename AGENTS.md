# AGENTS.md — CanchApp · Frontend

App móvil en **Ionic + Angular + Capacitor** (Android e iOS) del proyecto **CanchApp**. Esta es la guía **breve** de este repositorio.

> **La guía completa vive fuera de este repositorio**, en la carpeta de trabajo, un nivel arriba:
> [`../AGENTS.md`](../AGENTS.md) · DERCAS: [`../DERCAS_CanchApp.pdf`](../DERCAS_CanchApp.pdf) · addendum v0.3: [`../docs/DERCAS_CanchApp_v0.3_addendum.md`](../docs/DERCAS_CanchApp_v0.3_addendum.md) · plan: [`../docs/PLANIFICACION.md`](../docs/PLANIFICACION.md).
>
> Si este archivo y la guía completa se contradicen, manda la guía completa y, sobre todo, el **DERCAS**.

## Qué se construye aquí

La app del **cliente** y la administración **desde el celular**. Cubre **RF-01 a RF-17**.

- `src/app/cliente/` — reservar, pago, mis-reservas, avisos.
- `src/app/admin/` — agenda, comprobantes, canchas, ajustes, reportes.
- `src/app/core/` — autenticación, interceptor JWT, guards por rol, servicios HTTP.
- `src/app/shared/` — componentes y pipes comunes.

El panel de administración web es otro repositorio (`../AdminWeb`). **No muevas funciones de un cliente al otro.**

## Reglas que no se rompen

- **La UI no calcula reglas de negocio.** Totales, plazos, límites y estados llegan resueltos desde la API. Si falta un dato derivado, se agrega al DTO del backend; **no se calcula en TypeScript**.
- Componentes **standalone**. El JWT va por interceptor HTTP y las rutas se protegen con guards por rol.
- **Fechas y horas** con `Intl.DateTimeFormat` y `timeZone: 'America/Guayaquil'`. Nunca la zona del navegador.
- **Estados con texto y color**, no solo color. Botones de al menos **44 px** de alto.
- **Paleta**: verde `#0F6B3E`, azul `#1D5FA8`, naranja `#B4541A`, rojo `#B42318`, fondo `#F4F6F1`.
- Comprobantes desde cámara o galería con Capacitor (JPG o PNG, máximo 5 MB).
- Mientras la app está abierta, los cambios llegan por **WebSocket (STOMP)**; con la app cerrada, por **notificación push** (FCM).
- El **pago en efectivo (P4) es solo de esta app**, no del panel web.

## Comandos

```bash
npm install
ionic serve
npm test
npm run lint
ionic cap sync android
```

## Pruebas y cierre

- Cada pantalla tiene su prueba de componente.
- Antes de commitear: `npm test` y `npm run lint` en verde.
- Un commit por cambio lógico, Conventional Commits en español, citando el RF.

## Contrato con el backend

Consume la API `/api/v1` de `../Backend`. El `openapi.json` de ese repositorio es el **contrato**: si un DTO cambia, se detecta en el Pull Request.

## Seguridad

**Nunca** subas secretos: credenciales de Firebase ni `google-services.json`.
