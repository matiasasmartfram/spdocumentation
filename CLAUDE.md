# SmartPedidos - Portal de Mockups

## Comportamiento automático del agente

Cuando el usuario mencione que agregó un archivo nuevo (o cuando detectes un archivo HTML en la
raíz del proyecto que no está en `index.html`), **sin esperar que lo pidan explícitamente**:

1. Ejecutá un `Glob("*.html")` en la raíz para listar todos los archivos HTML presentes.
2. Compará contra los links en `index.html` para identificar cuál o cuáles faltan.
3. Aplicá las reglas de clasificación (sección, nombre legible, orden) definidas más abajo.
4. Actualizá `index.html` con el nuevo link en la sección y posición alfabética correcta.
5. Actualizá también la sección "Estado actual de archivos por sección" al final de este CLAUDE.md.

No hagas preguntas antes de ejecutar. Solo confirmá al usuario qué cambios hiciste.

### Actualizar el repositorio remoto

Cuando el usuario pida **"actualizar el repo"** (o equivalentes: "subir", "pushear", "publicar"),
ejecutar siempre estos pasos en orden:

1. `git add -A` — stagear todos los cambios pendientes.
2. `git commit -m "[descripción breve de los cambios]"` — con un mensaje claro.
3. `git push` — publicar en GitHub Pages para que los links del index queden activos.

Confirmá al usuario el hash del commit y que el push fue exitoso.

---

## Descripción del proyecto

Repositorio de mockups visuales HTML estáticos del sistema SmartPedidos / SmartCloud.
Son consumidos por desarrolladores y analistas internos para entender el diseño y flujo de
funcionalidades antes de su implementación.

El archivo `index.html` es el portal de entrada. Los links apuntan a la versión publicada en
GitHub Pages (`https://matiasasmartfram.github.io/spMockup/`).

---

## Convención de nombres de archivos

Patrón: `[tipo]_[módulo]_[funcionalidad]_[variante].html`

| Tipo | Descripción |
|------|-------------|
| `mockup_` | Prototipo visual de una funcionalidad |
| `documentacion_` | Documento técnico o funcional |

---

## Módulos y su sección en el index

Cada módulo (segundo segmento del nombre de archivo) se mapea a una sección del accordion en
`index.html`. Las secciones se ordenan **alfabéticamente**.

| Prefijo de archivo | Nombre de sección en index |
|--------------------|---------------------------|
| `mockup_backoffice_` | MockUps Backoffice |
| `mockup_canal_` | MockUps Canal |
| `mockup_catalog_` | MockUps Catálogo |
| `mockup_comanda_` | MockUps Comanda |
| `mockup_extras_` | MockUps Extras |
| `mockup_items_` | MockUps Items |
| `mockup_kamban_` | MockUps Kanban |
| `mockup_kds` | MockUps KDS |
| `mockup_mercadoPago_` | MockUps Mercado Pago |
| `mockup_pos_` | MockUps POS |
| `mockup_promociones_` | MockUps Promociones |
| `mockup_sobreventa_` | MockUps Sobreventa |
| `documentacion_` | Documentación |

Si se agrega un módulo nuevo no listado acá, crear una sección nueva siguiendo el patrón
`Mockups [Nombre del Módulo Capitalizado]` e insertarla en orden alfabético.

---

## Reglas para actualizar index.html

Cada vez que se agregue o elimine un archivo HTML, actualizar `index.html` siguiendo estos pasos:

### 1. Identificar la sección
Leer el prefijo del archivo y mapear a la sección usando la tabla de arriba.
Ejemplo: `mockup_promociones_nuevo_flujo.html` → sección **MockUps Promociones**.

### 2. Generar el nombre legible del link
- Quitar el prefijo `mockup_` o `documentacion_`
- Quitar el nombre del módulo si ya aparece en el título de la sección
- Reemplazar `_` por espacios
- Capitalizar cada palabra

Ejemplos:
| Archivo | Sección | Nombre del link |
|---------|---------|-----------------|
| `mockup_promociones_grupo_admin.html` | MockUps Promociones | Grupo Admin |
| `mockup_backoffice_ordertimes.html` | MockUps Backoffice | Order Times |
| `mockup_catalog_listadeprecios_POS.html` | MockUps Catálogo | Lista de Precios POS |
| `documentacion_catalog_v2.html` | Documentación | Catálogo v2 |

### 3. Ordenar los links dentro de cada sección
Los links de cada sección se ordenan **alfabéticamente por nombre legible** (A → Z).

### 4. Ordenar las secciones del accordion
Las secciones (`<details>`) se ordenan **alfabéticamente** de arriba a abajo.

### 5. Estructura HTML del link
```html
<a href="https://matiasasmartfram.github.io/spMockup/nombre-del-archivo.html" class="doc-link">
  <strong>Nombre Legible</strong>
</a>
```

---

## Estado actual de archivos por sección

### Documentación
- `documentacion_catalog_v1.html` → Catálogo v1
- `documentacion_catalog_v2.html` → Catálogo v2
- `documentacion_comanda_weiss.html` → Comanda Weiss
- `documentacion_formato_pedidos.html` → Formato de Pedidos

### MockUps Backoffice
- `mockup_backoffice_checkin-schedule.html` → Check-in Schedule
- `mockup_backoffice_order.detaisl.html` → Order Details *(typo en el nombre del archivo)*
- `mockup_backoffice_ordertimes.html` → Order Times
- `mockup_backoffice_popup_exportacionplataformas.html` → Popup Exportación Plataformas

### MockUps Canal
- `mockup_canal_punto_de_venta.html` → Punto de Venta

### MockUps Catálogo
- `mockup_catalog_item_multimedia.html` → Item Multimedia
- `mockup_catalog_listadeprecios_manager.html` → Lista de Precios Manager
- `mockup_catalog_listadeprecios_POS.html` → Lista de Precios POS
- `mockup_catalog_promocion_multimedia.html` → Promoción Multimedia

### MockUps Comanda
- `mockup_comanda_cocina.html` → Cocina
- `mockup_comanda_pedidos.html` → Pedidos
- `mockup_comanda_seleccion_beeper.html` → Selección Beeper

### MockUps Extras
- `mockup_extras_admin.html` → Admin
- `mockup_extras_pos.html` → POS

### MockUps Items
- `mockup_items_orden_de_venta.html` → Orden de Venta (Original)
- `mockup_items_orden_de_venta_new.html` → Orden de Venta (Nueva)
- `mockup_items_para_cocina.html` → Para Cocina

### MockUps Kanban
- `mockup_kamban_pedidos.html` → Pedidos

### MockUps KDS
- `mockup_kds.html` → Kitchen Display System

### MockUps Mercado Pago
- `mockup_mercadoPagoDeliveryCloudv1.html` → Delivery Cloud v1

### MockUps POS
- `mockup_pos_rejectedMessages.html` → Rejected Messages por Estado

### MockUps Promociones
- `mockup_promociones_adaptado.html` → Adaptado
- `mockup_promociones_admin.html` → Admin
- `mockup_promociones_admin_sku.html` → Admin SKU
- `mockup_promociones_grupo_admin.html` → Grupo Admin
- `mockup_promociones_pos.html` → POS

### MockUps Sobreventa
- `mockup_sobreventa_admin.html` → Admin
