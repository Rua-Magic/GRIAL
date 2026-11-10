# Grial · Resumen del trabajo y rutas

Estado al **9 de noviembre de 2026**. Úsalo para retomar en otra computadora o para hacer la web de la agencia.

## Lo que hicimos
1. **Plan y negocio.**
   - Plan de 90 días, del 13 de noviembre de 2026 al 7 de febrero de 2027.
   - Paquetes y precios: Presencia, Crecimiento y Completo, más las mensualidades.
   - Documentos comerciales: propuesta, contrato, formulario de onboarding y guiones de venta.
   - CRM de prospectos, tablero de proyectos y molde de carpeta por cliente.
2. **Plantilla de webs para clientes (`web-base`).**
   - Hecha en Next.js 16 con Tailwind 4.
   - Cada web es un solo archivo de configuración y tiene 13 secciones intercambiables.
   - Incluye WhatsApp, SEO, política de privacidad y libro de reclamaciones.
   - Tiene dos demos: clínica dental y gimnasio.
3. **Bocetos por nicho.** Ocho propuestas de web inspiradas en la experiencia de usuario de Dribbble y Behance: dental, spa, gimnasio, pilates, restaurante, academia, veterinaria y barbería.
4. **Tipografías.**
   - Seis modelos de letra (A–F), uno por tipo de negocio, para que nada se vea "hecho con IA".
   - Ya están aplicados en los bocetos y en la plantilla.
5. **Nombre.** Elegiste **Grial**. Falta revisarlo en INDECOPI, dominios y redes antes del 18 de noviembre (ver `agencia/marca/nombres.md`).
6. **Logo.**
   - Primero hice una versión holográfica con flor.
   - Después probé cinco centros en celeste.
   - Elegiste el **cáliz de oro** sobre una estrella de luz celeste como logo y tipografía **provisionales**.

## Enlaces publicados
Se abren desde cualquier computadora con tu cuenta de Claude. Son privados hasta que los compartas.

| Qué | Enlace |
|---|---|
| Logo Grial (versiones, colores, tipografía, reglas) | https://claude.ai/artifact/RTBUXNt88rufD3juNujLU4 |
| Las cinco opciones de logo en celeste | https://claude.ai/artifact/75STH1VAaGG84sRy6BdyV3 |
| Bocetos web por nicho | https://claude.ai/artifact/Ukq9Rvmq7dBpLN6zd42D2B |
| Tipografías por nicho | https://claude.ai/artifact/1pBygjxggsikT4hbE1DHTF |

## Rutas dentro de la carpeta GRIAL
| Ruta | Qué hay |
|---|---|
| `CLAUDE.md` | Reglas del proyecto: idioma, stack, estándares de calidad. Claude lo lee solo al abrir la carpeta |
| `README.md` | Mapa de carpetas y cómo pedirle trabajo a Claude |
| `docs/Plan_de_Trabajo_Agencia.pdf` | Plan maestro de 90 días |
| `docs/bocetos-nichos/index.html` | Bocetos por nicho (se abre en el navegador) |
| `docs/muestrario-tipografias/index.html` | Los seis modelos de letra |
| `comercial/precios.md` | Paquetes, precios de lanzamiento y mensualidades (sin IGV) |
| `comercial/propuesta-plantilla.md`, `contrato-modelo.md`, `onboarding-formulario.md`, `guiones-venta.md` | Documentos de venta |
| `operaciones/crm-prospectos.csv`, `tablero-proyectos.md` | Prospectos y estado de proyectos |
| `clientes/_plantilla-cliente/` | Molde de carpeta para cada cliente nuevo |
| `plantillas/web-base/` | Plantilla de webs (su `README.md` explica cómo usarla) |
| `plantillas/kit-publicacion/checklist-publicacion.md` | Pasos para publicar apps en las tiendas |
| `agencia/README.md` | Cuentas de la agencia que tienes que crear |
| `agencia/marca/nombres.md` | Nombre elegido y revisión pendiente |
| **`agencia/marca/logo/`** | **Logo actual: SVG, PNG, ícono, foto de perfil y su `README.md`** |
| `agencia/marca/logo/v1-holografico/` | Primera versión del logo (guardada) |
| `agencia/marca/logo/fuente/` | Código que genera el logo (para ajustarlo) |
| `agencia/web/` | **Vacía: aquí va la web de la agencia** |

## Llevar el proyecto a tu casa
Todavía no hay commit ni copia en GitHub, así que la carpeta solo existe en esta computadora. Tienes dos formas:

- **Copia simple.** Copia la carpeta `GRIAL` a una USB o a Google Drive. Deja fuera `plantillas/web-base/node_modules` y `plantillas/web-base/.next`: pesan mucho y se vuelven a crear con `npm install`.
- **GitHub (recomendado).**
  1. Tú creas la cuenta y un repositorio **privado** vacío.
  2. Yo hago el commit y lo subo.
  3. En casa lo descargas con `git clone`.

  Así las dos computadoras quedan sincronizadas.

En la computadora de tu casa instala:
- Node.js 20 o más nuevo.
- Git.
- Google Chrome, solo si vas a volver a generar los PNG del logo.
- Claude Code, si quieres que Claude trabaje ahí.

## Hacer la web de la agencia
En el plan es la semana 1 (16–22 de noviembre). Se hace desde la plantilla, nunca desde cero.

### Opción rápida: pedírselo a Claude
Abre Claude Code en la carpeta `GRIAL` y escribe:

> Construye la web de la agencia Grial en `agencia/web` a partir de `plantillas/web-base`, siguiendo `RESUMEN.md`. Usa el logo de `agencia/marca/logo`, los colores y la tipografía de su README, y los paquetes de `comercial/precios.md`.

### A mano
1. Copia la plantilla a `agencia/web` sin `node_modules` ni `.next`. En Git Bash, desde la carpeta `GRIAL`:

   ```bash
   tar -C plantillas/web-base --exclude=node_modules --exclude=.next -cf - . | tar -C agencia/web -xf -
   ```

2. En `agencia/web/src/sitios/`, duplica `clinica-sonrisa.ts` como `grial.ts` y cambia:
   - `slug: "grial"`, `demo: false` y la `url` final.
   - En `negocio`: nombre Grial, razón social, RUC, correo, WhatsApp de la agencia y horario.
   - El `tema` con los colores del logo:

     ```ts
     tema: {
       esquema: "oscuro",
       fondo: "#060a16",
       superficie: "#0e1426",
       borde: "#1e2740",
       texto: "#eaf6ff",
       textoSuave: "#9aa8c0",
       primario: "#7fd4ff",
       sobrePrimario: "#060a16",
       acento: "#e8b44a",
       letra: "clinica", // Schibsted Grotesk + Atkinson Hyperlegible
       radio: "suave",
       contraste: { primario: "#2c66e0", sobrePrimario: "#ffffff" },
     },
     ```

   - Las `secciones`. Te sugiero este orden:
     1. Portada: "Tu negocio, en un solo flujo".
     2. Servicios: web, automatización y app.
     3. Planes: Presencia, Crecimiento y Completo, con "+ IGV".
     4. Proceso.
     5. Galería con los bocetos y las demos.
     6. Preguntas.
     7. Contacto.
3. En `src/sitios/index.ts`: registra `grial`, pon `SITIO_POR_DEFECTO = "grial"` y borra las dos demos.
4. Logo:
   - Copia `agencia/marca/logo/grial-horizontal-sobre-oscuro.svg` a `agencia/web/public/logo.svg`.
   - En `src/componentes/Logo.tsx`, cambia la inicial y el nombre por `<img src="/logo.svg" alt="Grial" className="h-8 w-auto" />`.
5. Ícono de la pestaña: copia `agencia/marca/logo/grial-icono.svg` como `agencia/web/src/app/icon.svg` y borra `src/app/icon.tsx`.
6. Pruébala:

   ```bash
   cd agencia/web && npm install && npm run dev
   ```

   Ábrela en http://localhost:3000, revísala en celular y computadora, y luego:

   ```bash
   npm run build
   ```

7. Publícala en Vercel con la cuenta de la agencia y conecta el dominio cuando lo compres.

## Pendientes
- [ ] Revisar "Grial" en INDECOPI (clases 35, 41 y 42), en los dominios .com y .pe, y en Instagram y TikTok, antes del **18 de noviembre**.
- [ ] Elegir los 2 nichos con los que empiezas, antes del **15 de noviembre**.
- [ ] Número de WhatsApp de la agencia: va en `plantillas/web-base/src/sitios/_agencia.ts` y en la web.
- [ ] Crear tus cuentas (lista en `agencia/README.md`): GitHub, Vercel, dominio y correo profesional.
- [ ] Flujo n8n del libro de reclamaciones, antes de la primera web de un cliente real.
- [ ] Semanas 2–3: plantilla de app (`plantillas/app-base`) y automatizaciones (`plantillas/automatizaciones`).
- [ ] Logo y tipografía son provisionales: cualquier ajuste se rehace con `node agencia/marca/logo/fuente/exportar.mjs`.
