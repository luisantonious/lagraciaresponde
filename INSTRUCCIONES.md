# La Gracia Responde — Guía de instalación (paso a paso)

No necesitas saber programar. Todo es "apuntar y hacer clic". Tiempo estimado: 1–2 horas.
Tienes 3 archivos listos en esta carpeta:

```
lagraciaresponde/
├── index.html        ← tu página web
├── package.json       ← configuración (no la toques)
└── api/
    └── chat.js        ← el "cerebro": aquí vive tu llave secreta
```

---

## FASE 1 — Tu llave de Anthropic (el motor de IA)

1. Entra a **https://console.anthropic.com** y crea una cuenta.
2. Ve a **Billing** (Facturación) y agrega un método de pago. Carga un saldo pequeño para empezar (p. ej. $10–$20). Solo pagas por uso.
3. Ve a **API Keys** → **Create Key**. Ponle nombre "lagraciaresponde".
4. **Copia la llave** (empieza con `sk-ant-...`) y guárdala en un lugar seguro.
   ⚠️ No la pegues en la página web ni se la des a nadie. Solo va en Vercel (Fase 3).

---

## FASE 2 — Sube el proyecto a GitHub (tu "casillero" de archivos)

1. Crea cuenta gratis en **https://github.com**.
2. Clic en **+** (arriba a la derecha) → **New repository**.
3. Nombre: `lagraciaresponde`. Déjalo **Public** o **Private**. Clic **Create repository**.
4. En la página del repo, clic en **uploading an existing file**.
5. Arrastra **index.html** y **package.json**.
6. Para el archivo de la carpeta api: arrastra **chat.js**, y en el nombre escribe al inicio `api/`
   (debe quedar `api/chat.js`). Eso crea la carpeta automáticamente.
7. Clic en **Commit changes**.

---

## FASE 3 — Publica con Vercel (pone tu web en internet)

1. Entra a **https://vercel.com** y haz **Sign up with GitHub** (conecta tu GitHub).
2. Clic en **Add New… → Project**.
3. Busca tu repo `lagraciaresponde` y clic **Import**.
4. Antes de desplegar, abre **Environment Variables** y agrega:
   - **Name:** `ANTHROPIC_API_KEY`
   - **Value:** pega tu llave `sk-ant-...`
   - Clic **Add**.
5. Clic **Deploy**. Espera ~1 minuto.
6. Te dará una dirección como `lagraciaresponde.vercel.app`. Ábrela y prueba el bot. 🎉

---

## FASE 4 — Conecta tu dominio lagraciaresponde.com

1. En tu proyecto de Vercel: **Settings → Domains**.
2. Escribe `lagraciaresponde.com` y clic **Add**.
3. Vercel te mostrará **los registros DNS exactos** que debes poner
   (normalmente un registro **A** para el dominio y un **CNAME** para `www`).
4. Entra al panel donde compraste el dominio (tu registrador) → sección **DNS**.
5. Copia EXACTAMENTE los registros que te dio Vercel. Guarda.
6. Espera de unos minutos a unas horas a que se propague. Listo: el bot vive en tu dominio.

---

## Para ajustar el bot después
- **Cambiar la voz o la doctrina:** edita el texto entre comillas de `SYSTEM` en `api/chat.js`
  (en GitHub puedes editar el archivo con el lápiz ✏️; Vercel re-publica solo).
- **Abaratar costos:** en `api/chat.js` cambia el modelo a `claude-haiku-4-5-20251001`.
- **Costo aproximado:** 1–3 centavos de dólar por respuesta. Pon un límite de gasto en
  la consola de Anthropic (Billing → límites) para tu tranquilidad.

¿Te atoras en algún paso? Dime en cuál y te guío con capturas/indicaciones exactas.
