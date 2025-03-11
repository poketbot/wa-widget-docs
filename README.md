# Guía de Instalación y Configuración del Widget de WhatsApp de PoketBot

El **Widget de WhatsApp de PoketBot** te permite agregar un botón flotante a tu sitio web, facilitando el contacto directo con tus visitantes a través de WhatsApp. Es compatible con múltiples frameworks de frontend (React, Angular, Vue, etc.), así como con sitios estáticos o CMS.

---

## 1. Incluir el script en tu sitio

Debes cargar el script del widget desde la siguiente URL:

```html
<script src="https://poketbot.com/widgets/poketbot-wa-widget.js"></script>
```

Se recomienda incluirlo antes del cierre de la etiqueta `</body>` para mejorar el rendimiento, aunque también puede ir en `<head>`.

### Ejemplo mínimo en HTML estático:

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <title>Mi sitio con Widget de WhatsApp</title>
</head>
<body>

  <!-- Contenido de tu sitio -->

  <!-- Configuración global del widget -->
  <script>
    window.POKETBOT_WIDGET_CONFIG = {
      whatsappNumber: "521234567890",  // Reemplaza con tu número de WhatsApp
      welcomeText: "¡Hola! ¿En qué podemos ayudarte?",
      tooltipText: "¿Necesitas ayuda?",
      initialMessages: [
        "Me interesa más información",
        "Tengo una duda específica"
      ],
      showFooter: true,
      styles: {
        mainColor: "#25D366",
        hoverColor: "#1FB959"
      }
    };
  </script>

  <!-- Script del widget -->
  <script src="https://poketbot.com/widgets/poketbot-wa-widget.js"></script>
</body>
</html>
```

> **Importante**: Define la configuración en `window.POKETBOT_WIDGET_CONFIG` **antes** de cargar el script.

---

## 2. Configuración disponible

El objeto `window.POKETBOT_WIDGET_CONFIG` permite configurar las siguientes propiedades:

| Propiedad | Tipo | Descripción | Valor por defecto |
|-----------|------|-------------|------------------|
| `whatsappNumber` | `string` | Número de WhatsApp con código de país (ej. 521234567890). | "" |
| `welcomeText` | `string` | Mensaje de bienvenida en el menú del widget. | "Nuestro equipo está disponible para ayudarte." |
| `tooltipText` | `string` | Texto del tooltip en el botón flotante. | "¿Necesitas ayuda?" |
| `initialMessages` | `Array<string> \| Array<object>` | Botones de mensajes en el menú. | `["Quiero más información"]` |
| `showFooter` | `boolean` | Muestra "Powered by PoketBot" en el widget. | `true` |
| `styles` | `object` | Configuración de colores. | `{ mainColor: "#25D366", hoverColor: "#1FB959" }` |

### Uso de `initialMessages`

Puede recibir:
1. **Array de strings:** Botones con mensajes predefinidos.

```js
initialMessages: ["Hola", "Necesito información"];
```

2. **Array de objetos:** Cada objeto incluye `text` y un `link` opcional.

```js
initialMessages: [
  { text: "Hola", link: "" }, // Abre WhatsApp
  { text: "Visita nuestro sitio", link: "https://ejemplo.com" } // Redirige a otra URL
];
```

---

## 3. Ejemplo de configuración completa

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8" />
  <title>Ejemplo Completo - WhatsApp Widget</title>
</head>
<body>

  <script>
    window.POKETBOT_WIDGET_CONFIG = {
      whatsappNumber: "521234567890",
      welcomeText: "¡Hola! Estamos aquí para ayudarte con lo que necesites.",
      tooltipText: "Chatea con nosotros",
      initialMessages: [
        { text: "Solicitar información", link: "" },
        { text: "Agenda una reunión", link: "https://miagenda.com/hola" }
      ],
      showFooter: true,
      styles: {
        mainColor: "#25D366",
        hoverColor: "#1FB959"
      }
    };
  </script>

  <script src="https://poketbot.com/widgets/poketbot-wa-widget.js"></script>
</body>
</html>
```

---

## 4. Uso en frameworks modernos

### 4.1 React
1. Carga el script en `public/index.html`:

```html
<script src="https://poketbot.com/widgets/poketbot-wa-widget.js" defer></script>
```

2. Define la configuración en un archivo JS:

```js
window.POKETBOT_WIDGET_CONFIG = {
  whatsappNumber: "521234567890",
  ...
};
```

### 4.2 Angular
Agrega el script en `src/index.html`:

```html
<script>
  window.POKETBOT_WIDGET_CONFIG = {
    whatsappNumber: "521234567890",
    ...
  };
</script>
<script src="https://poketbot.com/widgets/poketbot-wa-widget.js"></script>
```

### 4.3 Vue
Usa el mismo método en `public/index.html` o en `index.html` de Vite.

---

## 5. Personalización avanzada

- **Ocultar el footer:**

```js
window.POKETBOT_WIDGET_CONFIG = { showFooter: false, ... };
```

- **Cambiar colores:**

```js
styles: {
  mainColor: "rgb(37, 211, 102)",
  hoverColor: "rgb(31, 185, 89)"
}
```

---

## 6. Resolución de problemas (FAQ)

### 1. El widget no aparece
- Verifica que el script esté correctamente incluido.
- Asegúrate de definir `window.POKETBOT_WIDGET_CONFIG` antes de cargar el script.

### 2. El widget no responde al hacer clic
- Asegúrate de usar un número de WhatsApp válido (sin `+` ni espacios).
- Revisa la consola del navegador en busca de errores de JavaScript.

### 3. No se muestran los mensajes iniciales
- Usa `initialMessages` en el formato correcto (array de strings o array de objetos).

### 4. Personalizar la posición del botón

```css
.poketbot-wa-widget-container {
  bottom: 50px !important;
  right: 50px !important;
}
```

---

## 7. Conclusión

El **Widget de WhatsApp de PoketBot** te permite integrar fácilmente WhatsApp en tu sitio web. Recuerda:
- Definir la configuración antes de cargar el script.
- Personalizar opciones como `whatsappNumber`, `welcomeText`, `tooltipText`, `styles`, etc.
- Utilizar frameworks modernos como React, Angular o Vue sin problemas.

Si tienes dudas, contacta al soporte de PoketBot o consulta nuestra documentación oficial.

