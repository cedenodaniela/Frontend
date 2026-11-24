# CanchApp · Frontend

App móvil de reservas del **Complejo Deportivo Calceta** (Calceta, Manabí, Ecuador), para Android e iOS.

Ionic + Angular + Capacitor · TypeScript.

Este repositorio contiene **solo la app móvil** (cliente y administración desde el celular). La API vive en `../Backend` y el panel web en `../AdminWeb`.

## Documentación

La documentación general del proyecto **no vive aquí**: está en la carpeta de trabajo, un nivel arriba.

| Documento | Ruta |
|---|---|
| Guía para agentes y convenciones | `../AGENTS.md` |
| DERCAS (fuente de verdad) | `../DERCAS_CanchApp.pdf` |
| Addendum v0.3 (panel web) | `../docs/DERCAS_CanchApp_v0.3_addendum.md` |
| Planificación de las 5 iteraciones | `../docs/PLANIFICACION.md` |

## Puesta en marcha

```bash
npm install
ionic serve
```

## Pruebas

```bash
npm test
npm run lint
```

## Compilar para Android

```bash
ionic cap sync android
```

## Flujo de trabajo

Ramas `main` y `develop`; una rama por tarea y un Pull Request por RF. Los issues y milestones se gestionan en el repositorio `Backend`. Ver `../AGENTS.md` §12.

## Estado

En construcción. La primera iteración del plan crea el esqueleto de la app y la pantalla de inicio de sesión.
