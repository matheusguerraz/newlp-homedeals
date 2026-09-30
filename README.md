# Home Deals — Landing Page

Landing page performática para aquisição de participantes dos grupos Home Deals no WhatsApp.

## Requisitos

- Node.js 20 ou superior
- npm 10 ou superior

## Ambiente de desenvolvimento

Instale as dependências:

```bash
npm install
```

Inicie o servidor local:

```bash
npm run dev
```

O terminal mostrará o endereço local, normalmente `http://localhost:5173`.

## Build de produção

```bash
npm run build
```

O resultado otimizado será gerado em `dist/`. Para conferir o build:

```bash
npm run preview
```

## Estrutura

```text
home-deals-site/
├── .openai/hosting.json     # configuração de hospedagem
├── public/assets/           # imagens otimizadas e logos oficiais
├── index.html               # página, estilos e rastreamento
├── package.json             # scripts e dependências
├── vite.config.js           # configuração do build
└── dist/                    # saída gerada; não versionada
```

## Conversão e mensuração

- O CTA direciona para o grupo oficial do WhatsApp.
- Parâmetros `utm_source`, `utm_medium`, `utm_campaign`, `utm_content`, `utm_term` e `utm_id` são preservados durante a sessão.
- Cliques nos CTAs enviam o evento interno `click_join_whatsapp` para `window.dataLayer`.
- Após consentimento, o Meta Pixel `3685724848391162` registra `PageView` e o evento personalizado `ClickWhatsAppInvite`.
- A landing page não dispara `Lead`: clique no convite não comprova entrada no grupo.
- A entrada confirmada deve ser conciliada separadamente por grupo/coorte e período.

## Publicação

O diretório público é `dist/`. Ele pode ser publicado no GitHub Pages, Netlify, Vercel ou qualquer hospedagem estática. A opção `base: "./"` mantém os ativos funcionais também em subdiretórios do GitHub Pages.

Antes de publicar:

1. Execute `npm run check`.
2. Confira os links do WhatsApp em desktop e celular.
3. Valide os parâmetros UTM da campanha.
4. Publique o conteúdo gerado em `dist/`.

## Versão

Versão inicial: `v1.0.0`.
