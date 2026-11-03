# Voz & Código — sitio web (v4 + chatbot con IA)

## Antes de publicar
1. WhatsApp: en index.html cambia `573000000000` por tu número (código de país, sin +). Aparece en DOS lugares: el script principal y el script del chatbot (`var WHATSAPP=`).
2. Correo: cambia `hola@vozycodigo.com`.
3. Dominio: reemplaza `vozycodigo.com` en index.html, robots.txt, sitemap.xml y en `netlify/functions/chat.mjs` (ORIGENES_PERMITIDOS).
4. Google Analytics 4: cambia `G-XXXXXXXXXX`. El chat también mide: chat_abierto, chat_mensaje y chat_whatsapp.
5. Sube una imagen 1200x630 llamada og-image.jpg.

## Chatbot con IA
El asistente responde en nombre de Voz & Código con la información de la empresa (servicios, proceso, plazos, proyectos y contacto).
No da precios: invita al diagnóstico gratis y, cuando la persona quiere cotizar o hablar con alguien, muestra un botón para seguir por WhatsApp con un resumen de lo que preguntó.

Para cambiar lo que sabe o cómo responde, edita el texto INSTRUCCIONES en `netlify/functions/chat.mjs`.

### Activarlo en tu dominio (necesario para que use IA real)
1. Crea una cuenta en https://console.anthropic.com, agrega saldo y genera una API key.
2. Sube el proyecto a GitHub y conéctalo en Netlify ("Add new site" > "Import an existing project").
   OJO: arrastrar la carpeta a Netlify Drop NO publica la función del chat; usa GitHub o la CLI (`netlify deploy --prod`).
3. En Netlify: Site configuration > Environment variables > agrega `ANTHROPIC_API_KEY` con tu clave.
4. Vuelve a publicar. El chat usará la ruta /api/chat.

Si la función no está disponible, el chat no se rompe: responde con preguntas frecuentes y ofrece WhatsApp.
Documentación de la API: https://docs.claude.com/en/api/overview

## Publicar
Netlify con GitHub (recomendado, por la función del chat). Luego verifica el dominio en Google Search Console y envía sitemap.xml.

## Librerías (desde CDN)
Three.js r128, GSAP 3.12.5 + ScrollTrigger y Lenis.
