# Guía de UX Móvil - Especialidades

Este documento describe las mejoras de experiencia de usuario (UX) implementadas en la sección `./especialidades` para optimizar la lectura y aprendizaje desde dispositivos móviles.

## 🎯 Características Principales

### 📱 Diseño Responsive

El diseño se adapta automáticamente a diferentes tamaños de pantalla:

- **Móvil (< 768px):** Layout optimizado para smartphones con controles táctiles
- **Tablet (768px - 1023px):** Vista intermedia con mejor aprovechamiento del espacio
- **Desktop (≥ 1024px):** Experiencia completa con máximo ancho de 900px

### 🎨 Modo Oscuro Automático

El sitio detecta automáticamente las preferencias del sistema y aplica:
- **Modo claro:** Fondo blanco con texto oscuro para lectura diurna
- **Modo oscuro:** Fondo oscuro con texto claro para lectura nocturna o en ambientes con poca luz

### 🚀 Navegación Mejorada

#### Botones Flotantes
- **☰ Índice:** Abre un menú lateral con las secciones principales (solo en móvil cuando hay más de 3 secciones H2)
- **↑ Volver arriba:** Aparece al hacer scroll para regresar rápidamente al inicio

#### Barra de Progreso
Una barra de color en la parte superior muestra tu progreso de lectura en la página.

#### Secciones Colapsables
En la página de índice, las categorías son colapsables para facilitar la navegación.

### ♿ Accesibilidad

- **Tamaños táctiles adecuados:** Botones y enlaces de mínimo 44x44px
- **Alto contraste:** Ratios de contraste que cumplen WCAG 2.1 AA
- **Navegación por teclado:** Todos los elementos interactivos son accesibles por teclado
- **Respeta preferencias del usuario:** `prefers-reduced-motion` para animaciones

## 🔧 Características Técnicas

### Variables CSS Personalizables

El diseño utiliza variables CSS que pueden personalizarse fácilmente:

```css
:root {
  --primary-color: #3498db;      /* Color principal (azul) */
  --secondary-color: #2ecc71;    /* Color secundario (verde) */
  --text-color: #2c3e50;         /* Color del texto */
  --bg-color: #ffffff;           /* Color de fondo */
  /* ... más variables */
}
```

### JavaScript Progresivo

Las mejoras de JavaScript son progresivas y opcionales:
- El sitio funciona perfectamente sin JavaScript
- JavaScript agrega mejoras UX como:
  - Barra de progreso de lectura
  - Índice móvil dinámico
  - Scroll suave
  - Lazy loading de imágenes
  - Envolver tablas automáticamente

### Optimizaciones de Rendimiento

- **Lazy loading de imágenes:** Las imágenes se cargan solo cuando están cerca del viewport
- **Tablas responsive:** Envueltas automáticamente en contenedores con scroll horizontal
- **CSS optimizado:** Sin dependencias externas, todo en un solo archivo
- **Transiciones condicionales:** Se deshabilitan si el usuario prefiere movimiento reducido

## 📖 Uso

### Para Instructores

1. **Navegación móvil:** Use los botones flotantes para moverse rápidamente por el contenido
2. **Modo lectura:** Active el modo oscuro del sistema para lectura nocturna
3. **Impresión:** El diseño mantiene estilos de impresión optimizados para material didáctico

### Para Desarrolladores

1. **Layout principal:** `_layouts/guia_instruccion.html`
2. **Variables de diseño:** Modificar las variables CSS en `:root` y `@media (prefers-color-scheme: dark)`
3. **Breakpoints:** 768px (tablet) y 1024px (desktop)

## 🎨 Paleta de Colores

### Modo Claro
- **Primario:** #3498db (Azul cielo)
- **Secundario:** #2ecc71 (Verde esmeralda)
- **Texto:** #2c3e50 (Gris oscuro)
- **Fondo:** #ffffff (Blanco)

### Modo Oscuro
- **Primario:** #5dade2 (Azul claro)
- **Secundario:** #52c77e (Verde claro)
- **Texto:** #e8e8e8 (Gris claro)
- **Fondo:** #1a1a1a (Negro suave)

## 🔮 Mejoras Futuras Potenciales

- [ ] Búsqueda en el contenido
- [ ] Marcadores y favoritos
- [ ] Notas personales
- [ ] Compartir secciones específicas
- [ ] Modo de alto contraste adicional
- [ ] Soporte para múltiples idiomas

## 📝 Compatibilidad

- **Navegadores modernos:** Chrome, Firefox, Safari, Edge (últimas 2 versiones)
- **Móviles:** iOS 12+, Android 8+
- **Tablets:** iPad, Android tablets
- **Degradación elegante:** Funciona en navegadores antiguos con estilos básicos

---

*Última actualización: Noviembre 2024*
