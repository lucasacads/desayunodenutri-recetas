# Assets Directory Structure

Esta pasta contém todos os recursos estáticos públicos da aplicação.

## Estrutura de Pastas

### `/css`
Arquivos CSS globais e estilos públicos que não estão no sistema de build do Vite.

### `/js`
Scripts JavaScript públicos que precisam ser carregados diretamente (analytics, terceiros, etc).

### `/images`
Imagens estáticas que são referenciadas diretamente via URL pública.
- Ícones de redes sociais
- Imagens de Open Graph
- Logos e marcas
- Imagens de fallback

### `/fonts`
Fontes customizadas locais (se não usar Google Fonts ou CDN).

### `/icons`
Ícones do site (favicon, apple-touch-icon, etc).

## Uso

Arquivos nesta pasta são servidos estaticamente e podem ser acessados via:
- `/assets/images/exemplo.png`
- `/assets/css/custom.css`
- etc.

**Nota:** Para imagens importadas no código React, use a pasta `attached_assets` com o alias `@assets`.
