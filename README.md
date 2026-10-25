# D&D Glowy — Tienda de packs de belleza (Perú) 💗👑

Sitio web estático (HTML + CSS + JavaScript) para **D&D Glowy**, una tienda que vende
**packs de belleza, packs para uñas, packs para pestañas y packs para cejas**.
Todos los precios están expresados en **soles peruanos (S/)** y los pedidos se
envían directamente por **WhatsApp al 912 304 989**.

Diseño con identidad propia: tema *"Glow Pink"* (rosa neón sobre fondo oscuro),
logo con corona, brillos animados, tarjetas con efecto hover y totalmente responsive.

---

## 1. Estructura del proyecto

```
/
├── index.html              → Página principal (usa archivos separados)
├── dd-glowy-tienda.html    → ⭐ Versión TODO EN UN ARCHIVO (para Visual Studio)
├── css/
│   └── style.css           → Estilos del sitio (tema Glow Pink + responsive)
├── js/
│   ├── products.js         → Catálogo de packs y precios (editable)
│   └── main.js             → Carrito, filtros, WhatsApp, pedidos, cuenta regresiva
├── images/
│   ├── logo-dd-glowy.png           → Logo D&D Glowy
│   ├── pack-belleza-esencial.jpg
│   ├── pack-belleza-premium.jpg
│   ├── pack-unas-basico.jpg
│   ├── pack-unas-pro.jpg
│   ├── pack-pestanas-inicial.jpg
│   ├── pack-pestanas-pro.jpg
│   ├── pack-cejas-define.jpg
│   └── pack-cejas-pro.jpg
└── README.md
```

### 🖥️ Cómo visualizarlo en Visual Studio / VS Code

**Opción A — versión de un solo archivo (la más fácil):**
1. Crea una carpeta, por ejemplo `DYDGlowy`.
2. Copia dentro **`dd-glowy-tienda.html`** y la carpeta **`images/`**.
3. Abre `dd-glowy-tienda.html` en Visual Studio / VS Code y pulsa *Abrir en el navegador*
   (o clic derecho → *Open with Live Server*).

> ⚠️ Importante: la carpeta `images/` debe quedar **al lado** del archivo `.html`,
> porque las rutas son relativas (`images/...`). Si mueves el `.html` solo, el logo
> y las fotos no se verán.

**Opción B — estructura completa (recomendada para publicar):**
Copia toda la carpeta del proyecto (con `css/`, `js/` e `images/`) y abre `index.html`.

---

## 2. Funcionalidades completas

- ✅ **Catálogo dinámico** de 8 packs + 1 combo, generado por JavaScript.
- ✅ **Filtros por categoría**: Belleza, Uñas, Pestañas, Cejas (+ "Todos").
- ✅ **Buscador** de packs en tiempo real (nombre, descripción o contenido).
- ✅ **Carrito de compras lateral** con: agregar, sumar/quitar unidades, eliminar,
  vaciar, subtotal, envío y total. Se guarda en el navegador (`localStorage`).
- ✅ **Finalizar compra por WhatsApp** al **912 304 989**: el botón verde del carrito
  valida que escribas tu **nombre** y **distrito/ciudad** de entrega, y luego abre
  WhatsApp con el mensaje del pedido ya redactado (packs, cantidades, subtotal,
  envío, total, nombre y lugar de entrega).
- ✅ **Ventana de confirmación** después de finalizar: indica que el pedido está listo,
  permite **reabrir WhatsApp** con un clic y cerrar el aviso.
- ✅ **Botón "Finalizar compra" inteligente**: muestra el total (ej. *Finalizar compra (S/ 327.00)*)
  y se desactiva cuando el carrito está vacío.
- ✅ **Registro del pedido** en la API de tablas (`pedidos`) de forma silenciosa
  (si no está disponible, el pedido igual se envía por WhatsApp).
- ✅ **Cuenta regresiva** de la oferta "Combo Glowy Total -25%".
- ✅ **Precios en soles peruanos (S/)** con precio anterior tachado y precio actual.
- ✅ **Secciones**: Inicio (hero), Categorías, Packs, Promos, Beneficios,
  Opiniones, Contacto y Footer.
- ✅ **Botón flotante de WhatsApp**, botón "volver arriba", menú móvil hamburguesa.
- ✅ **Diseño responsive** (escritorio, tablet y celular) y animaciones al hacer scroll (AOS).
- ✅ **Accesibilidad**: textos alternativos, etiquetas ARIA y navegación semántica.
- ✅ **Panel de configuración, asistente de packs y 5 animaciones CSS** (ver sección 8).

---

## 3. Rutas / puntos de entrada del sitio

| Ruta | Descripción |
|------|-------------|
| `index.html` | Página principal (estructura completa) |
| `index.html#inicio` | Sección hero / portada |
| `index.html#packs` | Catálogo de packs con filtros y buscador |
| `index.html#promos` | Oferta "Combo Glowy Total" + cuenta regresiva |
| `index.html#beneficios` | Beneficios de compra |
| `index.html#opiniones` | Testimonios de clientas |
| `index.html#contacto` | Datos de contacto (WhatsApp, correo, ubicación) |
| `dd-glowy-tienda.html` | Versión autocontenida (un solo archivo) |

### Flujo de compra (carrito → WhatsApp)

1. La clienta agrega packs con el botón **+** de cada tarjeta (se abre el carrito).
2. Ajusta cantidades con **– / +** o elimina productos con la **✕**.
3. Completa **Tu nombre** y **Distrito / Ciudad de entrega** (obligatorios).
4. Pulsa **“Finalizar compra por WhatsApp”** (muestra el total en el botón).
5. Se abre WhatsApp con el pedido redactado y aparece la **ventana de confirmación**
   con la opción de *Abrir WhatsApp de nuevo*.

> El pedido queda registrado en la tabla `pedidos` y el mensaje de WhatsApp
> contiene: número de ítems, cantidades, subtotal, envío, **TOTAL**, nombre y lugar de entrega.

### API de tablas (uso interno)
| Método | Endpoint | Uso |
|--------|----------|-----|
| `POST` | `tables/pedidos` | Registra el pedido generado desde el carrito |
| `GET`  | `tables/pedidos` | Lista los pedidos registrados |

---

## 4. Contacto de la tienda

- 📱 **WhatsApp / Pedidos:** 912 304 989 → `https://wa.me/51912304989`
- ✉️ **Correo:** ventas@ddglowy.pe
- 📍 **Ubicación:** Av. Los Glow 123, Lima – Perú
- 🕘 **Horario:** lunes a sábado, 9:00 a.m. – 8:00 p.m.
- 💳 **Pagos:** Yape, Plin, transferencia BCP / Interbank y contra entrega (Lima).

---

## 5. Lista de precios actual (en soles)

| Pack | Categoría | Antes | Ahora |
|------|-----------|-------|-------|
| Pack Belleza Esencial | Belleza | S/ 119 | **S/ 89** |
| Pack Belleza Premium | Belleza | S/ 199 | **S/ 159** |
| Pack Uñas Básico | Uñas | S/ 89 | **S/ 69** |
| Pack Uñas Pro Nail Art | Uñas | S/ 159 | **S/ 129** |
| Pack Pestañas Inicial | Pestañas | S/ 129 | **S/ 99** |
| Pack Pestañas Pro Volumen | Pestañas | S/ 169 | **S/ 139** |
| Pack Cejas Define | Cejas | S/ 69 | **S/ 49** |
| Pack Cejas Pro Studio | Cejas | S/ 129 | **S/ 104** |
| Combo Glowy Total (3 packs) | Promo | S/ 372 | **S/ 279** |

> Envío: **gratis** en pedidos desde **S/ 150**; en Lima se considera **S/ 12** por debajo de ese monto.

---

## 6. Cómo personalizar

- **Cambiar precios o packs:** edita `js/products.js` (o el bloque `PACKS` dentro de
  `dd-glowy-tienda.html`). Cada pack tiene `price` (precio actual) y `priceOld` (precio anterior).
- **Cambiar el número de WhatsApp:** edita la constante `WHATSAPP_NUMBER` en `js/main.js`
  y en `dd-glowy-tienda.html`, y actualiza los enlaces `wa.me/...` del HTML.
- **Cambiar imágenes:** reemplaza los archivos dentro de `images/` manteniendo los mismos nombres.
- **Cambiar colores:** modifica las variables en `:root` dentro de `css/style.css`
  (por ejemplo `--pink-500` para el rosa principal).

---

## 7. Modelo de datos (tabla `pedidos`)

| Campo | Tipo | Descripción |
|-------|------|-------------|
| `id` | text | Identificador único del pedido |
| `customer_name` | text | Nombre de la clienta |
| `customer_place` | text | Distrito / ciudad de entrega |
| `phone` | text | WhatsApp de contacto de la tienda |
| `items` | text | Detalle de packs y cantidades |
| `units` | number | Total de unidades |
| `subtotal` | number | Subtotal en soles (sin envío) |
| `shipping` | number | Costo de envío en soles |
| `total` | number | Total del pedido en soles |
| `status` | text | nuevo / contactado / pagado / enviado / entregado / cancelado |

**Servicios usados:** tipografías de Google Fonts, iconos de Font Awesome y
animaciones de AOS (todo vía CDN). Los pedidos se almacenan con la API de tablas
del proyecto (almacenamiento gestionado).

---

## 8. Criterios de evaluación (diseño del sitio)

Ambas versiones (`index.html` con `css/` y `js/`, y `dd-glowy-tienda.html` de un solo archivo) incluyen estas mejoras.
En la versión separada, el código nuevo está al final de `css/style.css` (sección 22) y en `js/main.js` (sección 8, función `initExtras`).

**Criterio 1 — Experiencia de visualización, optimización e interactividad (12 pts)**
- **Panel de configuración** (botón ⚙ abajo a la izquierda): tema *Glow / Claro / Alto contraste*,
  tamaño de texto (A− a A++), tipografía *Fácil de leer* (Lexend), *Reducir animaciones* y
  *Restablecer*. Se guarda en `localStorage` y respeta `prefers-reduced-motion`.
- **Estructura creativa:** asistente *“Encuentra tu pack ideal”* (2 preguntas → recomendación con botón de agregar),
  cinta de ventajas, ordenar el catálogo (precio / valoración) y buscador + filtros.
- **Navegación simple:** 6 enlaces, barra de progreso de lectura, enlace activo con `aria-current`, menú móvil.
- **Accesibilidad y usabilidad:** enlace “Saltar al contenido”, foco visible, carrito y paneles con `inert`
  y cierre con `Esc`, tarjetas de categoría con teclado, botones táctiles ≥ 44 px, `aria-pressed`, `aria-live`.
- **Optimización:** carga diferida de imágenes y del script de animaciones, preferencias aplicadas antes de pintar.

**Criterio 2 — 5 animaciones CSS y fuentes personalizadas (8 pts)**
1. **Brillo barrido (shimmer)** en los botones principales (hover / foco).
2. **Destellos titilantes (twinkle)** alrededor del logo del hero.
3. **Degradado fluido** en los títulos resaltados (cambio suave de color).
4. **Icono gelatina (jelly)** en tarjetas de categoría, beneficios y contacto.
5. **Cinta en movimiento (ticker)**, con pausa al pasar el mouse o con el teclado.

Además hay transiciones suaves de color y posición entre estados (filtros, interruptores, panel, menú, carrito).
**Fuentes personalizadas:** Baloo 2 (títulos), Poppins (texto), Dancing Script (acentos) y Lexend (modo fácil de leer).

---

## 9. Pendientes / próximos pasos sugeridos

- [ ] Reemplazar las fotos de referencia (se ven marcas de otras tiendas en los empaques) por fotos reales de los packs de D&D Glowy.
- [ ] Añadir el número real de Instagram / TikTok en los enlaces sociales.
- [ ] Crear un **panel interno** para ver y gestionar los pedidos de la tabla `pedidos`
      (marcar estados: contactado, pagado, enviado…).
- [ ] Integrar **pago en línea** (Yape/Plin QR, Mercado Pago) si se desea cobrar automáticamente.
- [ ] Añadir sección de **preguntas frecuentes (FAQ)** y políticas de cambio/devolución.
- [ ] Conectar **Google Analytics** o píxel de Meta para medir visitas y campañas.
- [ ] Publicar el sitio (pestaña **Publish** o *Hosted Deploy*) para obtener la URL pública.

---

© D&D Glowy · Hecho en Perú 🇵🇪 — Precios en soles peruanos (S/) e incluyen IGV.
