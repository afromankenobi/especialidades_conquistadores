# Guía de Desarrollo - Jekyll

## 🚀 Iniciar servidor de desarrollo

```bash
# Opción 1: Servidor Jekyll completo
bundle exec jekyll serve

# Opción 2: Con live reload
bundle exec jekyll serve --livereload

# Opción 3: Modo draft (incluye borradores)
bundle exec jekyll serve --drafts

# Opción 4: Puerto específico
bundle exec jekyll serve --port 4001
```

**Luego abre:** http://localhost:4000

## 📂 Estructura del Proyecto

```
.
├── _config.yml          # Configuración de Jekyll
├── _layouts/            # Layouts personalizados
│   └── default.html     # Layout con soporte Mermaid.js
├── Gemfile              # Dependencias Ruby
├── especialidades/      # Especialidades por área
├── jvargas/            # Versión líder (sin notas instructor)
├── assets/             # Recursos (logo, imágenes)
└── README.md           # Página de inicio
```

## 🎨 Características Configuradas

✅ **Soporte Mermaid.js** - Los diagramas se renderizan automáticamente
✅ **Rutas relativas** - Links internos funcionan correctamente
✅ **Markdown GFM** - Compatible con GitHub
✅ **Sin Front Matter requerido** - Los archivos .md funcionan directo
✅ **Assets servidos** - Logo e imágenes funcionan

## 🔧 Comandos Útiles

```bash
# Limpiar archivos generados
bundle exec jekyll clean

# Build para producción
bundle exec jekyll build

# Ver versión de Jekyll
bundle exec jekyll --version

# Actualizar dependencias
bundle update
```

## 🌐 Publicar en GitHub Pages

### Opción 1: Rama gh-pages

```bash
# Build
bundle exec jekyll build

# Copiar a rama gh-pages
git checkout -b gh-pages
cp -r _site/* .
git add .
git commit -m "Deploy to GitHub Pages"
git push -u origin gh-pages
```

### Opción 2: Configurar GitHub Actions

Crear `.github/workflows/jekyll.yml`:

```yaml
name: Deploy Jekyll site to Pages

on:
  push:
    branches: ["main"]
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: ruby/setup-ruby@v1
        with:
          ruby-version: '3.1'
          bundler-cache: true
      - name: Build with Jekyll
        run: bundle exec jekyll build
      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3

  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

Luego en GitHub:
1. Settings → Pages
2. Source: GitHub Actions
3. Listo!

## 🐛 Troubleshooting

**Problema:** Logo no se ve
- **Solución:** Asegúrate de servir desde la raíz: `bundle exec jekyll serve`

**Problema:** Mermaid no renderiza
- **Solución:** Verifica que usas bloques \`\`\`mermaid (no solo \`\`\`)

**Problema:** Cambios no se reflejan
- **Solución:** Usa `--livereload` o presiona Ctrl+C y reinicia

**Problema:** Error de dependencias
- **Solución:** `bundle install` nuevamente

## 📖 Recursos

- [Jekyll Docs](https://jekyllrb.com/docs/)
- [GitHub Pages Docs](https://docs.github.com/en/pages)
- [Mermaid.js Docs](https://mermaid.js.org/)
