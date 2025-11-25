# Solución: Renderizado de Diagramas Mermaid.js

## Problema
Los diagramas Mermaid.js en los archivos markdown no se estaban renderizando correctamente en el sitio Jekyll.

## Cambios Realizados

### 1. Actualización de `_layouts/default.html`

Se realizaron los siguientes cambios para asegurar que los diagramas Mermaid.js se rendericen correctamente:

#### Cambio de CDN
- **Antes:** `https://cdn.jsdelivr.net/npm/mermaid@10/dist/mermaid.esm.min.mjs` (ES Module)
- **Después:** `https://unpkg.com/mermaid@10/dist/mermaid.min.js` (Script estándar)
- **Razón:** Mayor compatibilidad con navegadores y GitHub Pages

#### Cambio de Inicialización
- **Antes:** Importación ES Module con `startOnLoad: true`
- **Después:** Script tag estándar con procesamiento manual
- **Razón:** Necesitamos convertir los bloques de código generados por Jekyll antes de renderizar

#### Nuevo Procesamiento
Se agregó código JavaScript que:
1. Espera a que el DOM esté completamente cargado (`DOMContentLoaded`)
2. Convierte bloques `<pre><code class="language-mermaid">` (generados por Jekyll/Kramdown) en `<div class="mermaid">`
3. También maneja bloques `<pre class="mermaid">` directos
4. Finalmente llama a `mermaid.run()` para renderizar todos los diagramas

## Cómo Funciona

### En el Markdown
Los usuarios escriben diagramas usando la sintaxis estándar de markdown:

\`\`\`mermaid
graph TB
    A[Inicio] --> B[Fin]
\`\`\`

### Procesamiento por Jekyll
Jekyll/Kramdown convierte esto en:

```html
<pre><code class="language-mermaid">
graph TB
    A[Inicio] --> B[Fin]
</code></pre>
```

### Procesamiento por JavaScript
Nuestro script convierte esto en:

```html
<div class="mermaid">
graph TB
    A[Inicio] --> B[Fin]
</div>
```

### Renderizado por Mermaid.js
Finalmente, Mermaid.js convierte el contenido del `<div class="mermaid">` en un diagrama SVG renderizado.

## Archivos con Diagramas Mermaid

Los siguientes archivos contienen diagramas Mermaid.js que ahora se renderizarán correctamente:

- `especialidades/EN/arboles.md` - Contiene 2 diagramas:
  - Diagrama de partes de una hoja (graph TB)
  - Diagrama de clases del herbario (classDiagram)
- `jvargas/EN/arboles.md` - Mismos diagramas que la versión anterior

## Verificación

Para verificar que los diagramas se renderizan correctamente:

1. **En desarrollo local:**
   ```bash
   bundle exec jekyll serve
   ```
   Luego visita: http://localhost:4000/especialidades/EN/arboles

2. **En GitHub Pages:**
   Después de hacer push, visita la URL del sitio en GitHub Pages
   Ejemplo: https://afromankenobi.github.io/especialidades_conquistadores/especialidades/EN/arboles

3. **Qué buscar:**
   - Los diagramas deben aparecer como gráficos SVG renderizados (no como código)
   - El diagrama de partes de una hoja debe mostrar cajas conectadas con colores
   - El diagrama de clases debe mostrar las relaciones entre HERBARIO, IDENTIFICACIÓN, etc.

## Solución de Problemas

### Los diagramas aparecen como código
- Verifica que el archivo `_layouts/default.html` tiene la última versión
- Asegúrate de que el CDN de Mermaid.js no esté bloqueado por tu navegador
- Revisa la consola del navegador (F12) para ver errores

### Los diagramas no tienen colores
- Verifica que la sintaxis de `style` en el diagrama sea correcta
- Mermaid.js requiere formato específico: `style NodeId fill:#COLOR`

### Error de sintaxis en Mermaid
- Revisa la documentación de Mermaid.js: https://mermaid.js.org/
- Usa el editor en vivo: https://mermaid.live/

## Recursos Adicionales

- [Documentación de Mermaid.js](https://mermaid.js.org/)
- [Editor en vivo de Mermaid](https://mermaid.live/)
- [Sintaxis de diagramas](https://mermaid.js.org/intro/syntax-reference.html)
