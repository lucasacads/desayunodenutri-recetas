# Estrutura da Pasta Public

## 📁 Visão Geral

A pasta `public/` contém todos os arquivos estáticos que são servidos diretamente sem passar pelo processo de build do Vite.

```
public/
├── assets/
│   ├── css/          # Estilos CSS públicos
│   ├── fonts/        # Fontes customizadas
│   ├── icons/        # Ícones do site (favicon, etc)
│   ├── images/       # Imagens públicas estáticas
│   ├── js/           # Scripts JavaScript públicos
│   └── README.md     # Documentação da estrutura de assets
├── .htaccess.example # Exemplo de config Apache
├── manifest.json     # PWA manifest
├── robots.txt        # Instruções para crawlers
└── sitemap.xml       # Mapa do site para SEO
```

## 📂 Detalhes das Pastas

### `/assets/css/`
Arquivos CSS que precisam ser carregados globalmente ou por terceiros.

**Quando usar:**
- Estilos para scripts de terceiros
- CSS que não deve ser processado pelo build
- Estilos de fallback

### `/assets/fonts/`
Fontes web customizadas hospedadas localmente.

**Quando usar:**
- Fontes que não estão disponíveis via CDN
- Quando precisar de controle total sobre o carregamento
- Fontes personalizadas da marca

### `/assets/icons/`
Ícones e imagens relacionadas ao site.

**Arquivos incluídos:**
- `favicon.png` - Ícone do site
- Apple touch icons
- Ícones para PWA
- Imagens de Open Graph

### `/assets/images/`
Imagens estáticas que não mudam frequentemente.

**Quando usar:**
- Logos permanentes
- Imagens de placeholder
- Gráficos de marca
- Imagens para compartilhamento social

### `/assets/js/`
Scripts JavaScript que devem ser carregados diretamente.

**Quando usar:**
- Scripts de analytics
- Widgets de terceiros
- Scripts que precisam estar disponíveis globalmente

## 🔧 Arquivos de Configuração

### `manifest.json`
Configuração para Progressive Web App (PWA).

**Inclui:**
- Nome e descrição do app
- Ícones para diferentes tamanhos
- Configurações de display
- Cores de tema

### `robots.txt`
Instruções para crawlers de busca.

**Configurações:**
- Permite indexação de todas as páginas
- Referencia o sitemap.xml

### `sitemap.xml`
Mapa do site para otimização SEO.

**Inclui:**
- URLs principais do site
- Prioridades de páginas
- Frequência de atualização

### `.htaccess.example`
Exemplo de configuração para servidor Apache.

**Recursos:**
- Roteamento SPA
- Compressão GZIP
- Cache de recursos estáticos

## 📝 Diferença: Public vs Attached Assets

### `public/` (esta pasta)
- ✅ Servidos diretamente sem processamento
- ✅ URLs fixas: `/assets/images/logo.png`
- ✅ Ideais para: SEO, analytics, terceiros
- ❌ Não são otimizados pelo build
- ❌ Não recebem hash de cache

### `attached_assets/` (para imports React)
- ✅ Processados pelo Vite
- ✅ Otimizados e com hash
- ✅ Importados no código: `import logo from '@assets/logo.png'`
- ✅ Ideais para: imagens de componentes, assets dinâmicos
- ❌ Não são acessíveis via URL direta

## 🚀 Como Usar

### Referenciar arquivos públicos no HTML:
```html
<link rel="icon" href="/assets/icons/favicon.png">
<img src="/assets/images/logo.png" alt="Logo">
<script src="/assets/js/analytics.js"></script>
```

### Referenciar no código React:
```tsx
// Para public (URL direta)
<img src="/assets/images/logo.png" alt="Logo" />

// Para attached_assets (importação)
import logo from '@assets/logo.png'
<img src={logo} alt="Logo" />
```

## 🎯 Boas Práticas

1. **Mantenha pequeno:** Apenas arquivos essenciais
2. **Use attached_assets para código:** Melhor otimização
3. **Organize por tipo:** Facilita manutenção
4. **Documente mudanças:** README em cada pasta
5. **Otimize imagens:** Antes de adicionar
6. **Versionamento:** Considere para assets críticos

## 📦 Deploy

Durante o build (`npm run build`):
- Toda a pasta `public/` é copiada para `dist/`
- Estrutura é mantida intacta
- Arquivos ficam disponíveis nas mesmas URLs
