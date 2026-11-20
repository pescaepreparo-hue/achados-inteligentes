# Achados Inteligentes — versão 10 (site estático)

## Hospedagem

- Site: https://achados-inteligentes.netlify.app/
- Código: `pescaepreparo-hue/achados-inteligentes` (branch `main`)
- Configuração: `netlify.toml`, publicação de `.` sem comando de build
- Netlify e GitHub conectados pelo proprietário. Em geral, commits na `main` geram novos deploys, salvo se a publicação estiver pausada ou o deploy falhar. Verifique **Deploys / Published** no painel.

## O que está implementado

- Interface V9 com categorias interativas, busca, responsividade e Disputa de Preço.
- Arquivo `ofertas.js` com produtos e links cadastrados, separado do HTML.
- Produto-piloto: Mini Power Bank 10.000 mAh com dois links fornecidos anteriormente, um Mercado Livre e um Shopee.
- Grade distingue **LINKS CADASTRADOS** (compra possível na loja) de **IDEIAS EM PESQUISA** (sem vendedor/preço).
- Painel de comparação lê o produto cadastrado e separa filtros ML, Shopee e disputas por loja.
- Páginas `sobre.html`, `privacidade.html`, `robots.txt`, `sitemap.xml`.

## Como inserir mais produtos

Edite `ofertas.js`: para cada produto, crie objeto com `id`, `title`, `category`, `emoji`, `description`, `keywords` e lista `offers` contendo `store` (`ml` ou `sp`), `label`, `title` e URL de afiliado real. Valide a elegibilidade do link e evite anúncios sem autorização.

**Nunca coloque chaves de API, senhas ou tokens no arquivo `ofertas.js`**: ele é público. Os links exibidos não são segredo.

## Pendências comerciais para lançamento

1. Conferir se os dois links cadastrados ainda funcionam e correspondem à conta de afiliado correta.
2. Acrescentar produtos com links reais (não inventar preço, vendedor ou estoque).
3. Validar regras de uso de imagens, marcas, conteúdo e parâmetros de afiliados dos marketplaces.
4. Se desejar comparação numérica automática, implementar dados de preços/frete por fonte autorizada. A V10 **não consulta preços em tempo real**, não identifica menor preço e não possui backend.
5. Definir e publicar canal de contato e revisar a política de privacidade com a operação real.
6. Validar no smartphone, links de saída, cadastro de compra no painel dos programas, e abrir em janela anônima para confirmar que o site não está restrito ao proprietário.
7. Se o Netlify estiver em **Private**, liberar visibilidade pública antes de compartilhar o endereço em campanha.

## Segurança e transparência

- Pesquisa e filtro locais, sem banco de clientes ou autenticação.
- Links de afiliados são marcados `rel="sponsored nofollow noopener noreferrer"` na interface de disputa.
- Preços e frete são consultados diretamente pelo visitante nas lojas; não há ganhos garantidos de comissão.
- Versão anterior preservada em `arquivo/index-v1-outubro-2026.html`.

## Critério de conclusão

A versão técnica está pronta para demonstração e inclusão de ofertas; só considere **concluído o lançamento comercial** quando houver links válidos, testes de rastreamento, publicação pública e conteúdo verificado.
