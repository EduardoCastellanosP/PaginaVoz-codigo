# Voz & Código — sitio web (v6)

## Cambios de la v6
- **Arreglado el error que dejaba muertos los botones.** "Hablemos", "Quiero este plan", "Empezar", "Diagnóstico gratis", el equipo y los modales vuelven a funcionar.
- **Un solo lugar para los datos de contacto.** En `index.html`, busca `window.VYC=`: ahí están el WhatsApp, el correo y el webhook de leads. El chat, el formulario y el footer los toman de ahí.
- **Equipo.** Cada persona tiene `publicar:true/false`. La segunda integrante está oculta hasta que llenes sus datos. Las fotos ahora son WebP (pasaron de 4,2 MB a 172 KB).
- **Proyectos honestos.** LUXUME aparece como cliente y el resto como productos propios. Al tocar LUXUME se abre su ficha con el botón "Ver sitio en vivo".
- **Cifras.** Se cambiaron por promesas que el equipo sí cumple: landing en 2 semanas, 24/7, todo a nombre del cliente y diagnóstico gratis.
- **Planes.** La etiqueta "Más elegido" ahora dice "Recomendado".
- **Intro.** Se muestra solo en la primera visita de la sesión.
- **SEO.** El H1 ahora es "Agencia de marketing digital, páginas web y chatbots con IA en Bucaramanga". El eslogan grande se ve igual.
- **Rendimiento.** Hay menos partículas en celulares y equipos modestos, y la animación se pausa donde no se ve (cifras y footer).
- **Chatbot.**
  - Sus instrucciones viven solo en `chat.mjs`, así que ya no se ven en el código de la página.
  - Las respuestas automáticas se mejoraron: "farmacia" ya no se confunde con "IA", y ahora entiende plazos, saludos y "hablar con una persona".
  - La función solo acepta peticiones de tu dominio y permite 20 mensajes cada 10 minutos por persona.
- **Leads (opcional).** Si pegas la URL de un webhook (n8n, Make o Formspree) en `leadsWebhook`, cada contacto del formulario se guarda aunque la persona no termine de enviar el WhatsApp. El texto de privacidad se ajusta solo.
- `.htaccess`: caché para WebP, PNG y fuentes; HSTS y Permissions-Policy.

## Publicar en Spaceship (hosting Apache/LiteSpeed)
Sube al `public_html` del dominio solo esto: `index.html`, `favicon.svg`, `og-image.jpg`, `robots.txt`, `sitemap.xml`, `.htaccess` y la carpeta `img/`.
**No subas** la carpeta `.git` ni `netlify/`.
**Borra del servidor** las fotos viejas `img/equipo/shadi.jpg`, `danna.png` y `eduardo.jpeg`. Ya no se usan.
En Spaceship el chat responde con preguntas frecuentes. Para que use IA real, el sitio tiene que estar en Netlify (ver abajo).

## Pendientes (solo tú tienes estos datos)
1. **Google Analytics 4:** crea la propiedad y cambia `G-XXXXXXXXXX` en `index.html`.
2. **Segunda integrante del equipo:** en `var equipo=` llena nombre, rol, bio, especialidades y trabajos, y cambia `publicar:false` por `publicar:true`. Su foto ya está lista (`img/equipo/danna.webp`).
3. **Correo y dominio:** confirma que `hola@vozycodigo.com` y `vozycodigo.com` existen. Si cambian, edita `window.VYC`, `robots.txt`, `sitemap.xml` y `ORIGENES_PERMITIDOS` en `chat.mjs`.
4. **Redes sociales:** cuando existan, vuelve a poner el bloque "Síguenos" del footer (hay un comentario donde va).
5. **Testimonio de LUXUME:** cuando lo tengas, conviene agregarlo debajo de Proyectos.

## Chatbot con IA (Netlify)
1. Crea una API key en https://console.anthropic.com y agrega saldo.
2. Sube el proyecto a GitHub y conéctalo en Netlify ("Add new site" > "Import an existing project"). Arrastrar la carpeta a Netlify Drop NO publica la función.
3. En Netlify, ve a Site configuration > Environment variables y agrega `ANTHROPIC_API_KEY`. Si quieres otro modelo, agrega también `ANTHROPIC_MODEL` (es opcional).
4. Vuelve a publicar. El chat usará la ruta `/api/chat`. Para cambiar lo que sabe, edita `INSTRUCCIONES` en `netlify/functions/chat.mjs`.

Si la función no está disponible, el chat no se rompe: responde con preguntas frecuentes y ofrece WhatsApp.

## Después de publicar
Verifica el dominio en Google Search Console, envía `sitemap.xml` y crea el perfil de Google Business de la agencia en Bucaramanga.

## Librerías (desde CDN)
Three.js r128, GSAP 3.12.5 + ScrollTrigger y Lenis.
