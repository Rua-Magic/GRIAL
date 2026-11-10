# Agencia digital Grial — Lima, Perú

Nombre elegido por el dueño el 9 de noviembre de 2026 (falta la revisión en INDECOPI, dominios y redes: ver `agencia/marca/nombres.md`). Logo y tipografía provisionales (cáliz de oro sobre estrella celeste) y reglas de uso en `agencia/marca/logo/`. Estado general, rutas y pasos para la web de la agencia en `RESUMEN.md`.

Agencia de páginas web, automatización de negocios y apps personalizadas.
El dueño se encarga de ventas, clientes, cuentas y pagos. Claude es el equipo de producción.
Plan maestro: `docs/Plan_de_Trabajo_Agencia.pdf` (90 días, del 13 de noviembre de 2026 al 7 de febrero de 2027).

## Idioma y tono
- Todo en **español neutro con trato de "tú"**, pensado para negocios de Lima.
- Textos para clientes finales: claros, cálidos y sin tecnicismos.
- Moneda: soles (S/). Los precios a clientes se expresan **sin IGV** y se indica "+ IGV".

## Estructura del repositorio
| Carpeta | Contenido |
|---|---|
| `plantillas/web-base/` | Plantilla Next.js reutilizable para webs de clientes |
| `plantillas/app-base/` | App Expo (React Native) modular y configurable por cliente |
| `plantillas/automatizaciones/` | Flujos n8n (.json) reutilizables y su catálogo |
| `plantillas/kit-publicacion/` | Política de privacidad, fichas de tienda, checklists de publicación |
| `comercial/` | Precios, propuesta, contrato modelo, formulario de onboarding, guiones de venta |
| `clientes/<slug>/` | Un cliente por carpeta. Copiar desde `clientes/_plantilla-cliente/` |
| `agencia/` | Marca, web y app demo de la propia agencia |
| `operaciones/` | CRM de prospectos y tablero de proyectos |
| `docs/` | Plan de trabajo y documentos de referencia |

## Stack estándar (no cambiar sin motivo)
- **Webs:** Next.js (App Router) + TypeScript + Tailwind CSS. Hosting en Vercel.
- **Apps:** Expo (React Native) + TypeScript + Expo Router. Builds con EAS Build, envío con EAS Submit, correcciones con EAS Update.
- **Backend:** Supabase (Postgres, Auth, Storage). Row Level Security activado siempre.
- **Automatizaciones:** n8n autoalojado. WhatsApp mediante la API oficial de Meta (WhatsApp Business Platform).
- **Pagos en Perú:** Culqi, Mercado Pago o Izipay.

## Plantillas
- **Web base:** `plantillas/web-base/`. Cada web es un archivo de configuración en `src/sitios/<slug>.ts`; las secciones y opciones están tipadas en `src/sitio/tipos.ts`. Pasos para un cliente en `plantillas/web-base/README.md`. Next.js 16: antes de escribir código nuevo, revisa la guía en `node_modules/next/dist/docs/` (ver su AGENTS.md).

## Flujo para un cliente nuevo
1. Copiar `clientes/_plantilla-cliente/` a `clientes/<slug-del-cliente>/` (slug en minúsculas con guiones).
2. Completar `brief.md` con los datos del formulario de onboarding. Si falta información, listarla en "Pendientes" y no inventarla.
3. Producir desde las plantillas: nunca empezar un proyecto desde cero si existe una plantilla.
4. Registrar cada entrega, cambio o decisión en `bitacora.md` del cliente (fecha, qué se hizo, qué falta).
5. Actualizar `operaciones/tablero-proyectos.md`.

## Estándares de calidad (obligatorios antes de entregar)
- Web: adaptada a celular, botón de WhatsApp funcionando, SEO básico (title, description, Open Graph), https, política de privacidad y libro de reclamaciones.
- Accesibilidad básica: contraste suficiente, textos alternativos en imágenes, botones con etiqueta.
- App: funciona sin errores en iOS y Android, cuenta demo para revisores, política de privacidad publicada, textos e íconos del cliente (nunca una app genérica con solo el logo cambiado).
- Probar el resultado (build, lint, abrir en el navegador) antes de decir que algo está listo.

## Reglas importantes
- **Cuentas a nombre del cliente.** Dominio, Apple Developer, Google Play, Meta y Supabase pertenecen al cliente; la agencia entra como miembro invitado. Las apps hechas desde plantilla deben publicarse desde la cuenta del cliente (regla 4.2.6 de Apple).
- **Nada de secretos en el repositorio.** Claves y tokens van en `.env.local` (ignorado por Git) o en el gestor de secretos del servicio.
- Claude no crea cuentas, no escribe contraseñas, no paga ni acepta términos: se le pide al dueño.
- Mensajes, propuestas y correos a clientes: Claude los redacta y el dueño los envía o aprueba.
- Datos personales de clientes finales: tratar según la Ley 29733 de Protección de Datos Personales.

## Paquetes vigentes (detalle en `comercial/precios.md`)
- Presencia S/ 1,890 · Crecimiento S/ 5,490 · Completo S/ 14,900 (precios de lanzamiento solo para los 3 primeros pilotos).
- Mensualidades: Básico S/ 129 · Pro S/ 390 · App Care S/ 790.
