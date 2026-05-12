# Configuración de Google Tag Manager para WhatsApp

## ✅ Lo que ya está hecho en el código:

1. **HTML**: Todos los enlaces a WhatsApp ahora tienen:
   - `data-gtm-event="whatsapp_click"`
   - `data-gtm-location="header|hero_section|cta_intermedio_1|cta_intermedio_2"` (ubicación específica)

2. **JavaScript** (main.js): El código ahora escucha clics en estos enlaces y envía eventos a `dataLayer` de GTM con:
   - `event: 'whatsapp_click'`
   - `whatsapp_location: [ubicación]`
   - `timestamp: [hora del clic]`

---

## 🔧 Pasos para configurar en Google Tag Manager

### Paso 1: Crear un Trigger en GTM

1. Accede a tu contenedor en [Google Tag Manager](https://tagmanager.google.com/)
2. Ve a **Desencadenadores** (Triggers) en el menú izquierdo
3. Haz clic en **Nuevo**
4. Dale un nombre: "WhatsApp Click Trigger"
5. En "Configuración del desencadenador", selecciona **Evento personalizado**
6. En el campo "Nombre del evento", escribe: `whatsapp_click`
7. Guarda el trigger

### Paso 2: Crear una Acción de Google Analytics

1. Ve a **Etiquetas** (Tags) en el menú izquierdo
2. Haz clic en **Nuevo**
3. Dale un nombre: "GA - WhatsApp Click"
4. Selecciona **Google Analytics: GA4 Configuration** (o el que uses)

**Opción A - Si usas Google Analytics 4 (GA4):**
- Configuración de etiqueta: Selecciona tu configuración de GA4
- Haz clic en **Configuración más adelantada** → **Parámetros de evento**
- Agrega estos parámetros:
  - Nombre: `location`  |  Valor: `{{whatsapp_location}}`
  - Nombre: `event_category` | Valor: `engagement`

5. **Desencadenador**: Selecciona "WhatsApp Click Trigger"
6. Guarda la etiqueta

### Paso 3: Crear una Variable para capturar la ubicación

1. Ve a **Variables** en el menú izquierdo
2. Haz clic en **Nuevo** (en la sección de Variables definidas por el usuario)
3. Dale un nombre: `whatsapp_location`
4. Selecciona el tipo: **Data Layer Variable**
5. En "Nombre de la variable de Data Layer", escribe: `whatsapp_location`
6. Guarda la variable

### Paso 4: Publicar cambios en GTM

1. Haz clic en **Enviar** (arriba a la derecha)
2. Agrega descripción: "Agregar rastreo de clics en WhatsApp"
3. Selecciona **Crear versión** y **Publicar**

---

## 📊 Verificar que funcione

1. Busca en Chrome: **Tag Assistant** (extensión de Google)
2. Ve a tu página en Landpage
3. Haz clic en un botón de WhatsApp
4. En Tag Assistant deberías ver el evento `whatsapp_click` dispararse
5. Revisa en Google Analytics → Eventos → `whatsapp_click` para ver las ubicaciones

---

## 📌 Ubicaciones rastreadas:

- **header**: Botón en el encabezado
- **hero_section**: Botón en la sección hero
- **cta_intermedio_1**: Primer CTA intermedio
- **cta_intermedio_2**: Segundo CTA intermedio

Así puedes saber desde dónde se generan más clics a WhatsApp en tu página.
