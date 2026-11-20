# Achados Inteligentes — Vitrine inicial de 10 produtos (20/11/2026)

## Hospedagem

- Site: https://achados-inteligentes.netlify.app/
- Código: `pescaepreparo-hue/achados-inteligentes` (branch `main`)
- Configuração: `netlify.toml`, publicação de `.` sem comando de build
- Netlify e GitHub conectados pelo proprietário. Em geral, commits na `main` geram novos deploys, salvo se a publicação estiver pausada ou o deploy falhar. Verifique **Deploys / Published** no painel.

## O que está implementado

- Interface V9 com categorias interativas, busca, responsividade e Disputa de Preço.
- Arquivo `ofertas.js` com produtos e links cadastrados, separado do HTML.
- 10 produtos selecionados na vitrine. GTA VI (lançado em 19/11/2026) aparece em destaque na categoria Games e Consoles.\n- Produto-piloto: Mini Power Bank 10.000 mAh, com dois links informados anteriormente, um Mercado Livre e um Shopee.
- Grade distingue **LINKS CADASTRADOS** (compra possível na loja) de **AGUARDANDO LINK DE AFILIADO** (sem vendedor/preço confirmado).
- Painel de comparação lê o produto cadastrado e separa filtros ML, Shopee e disputas por loja.
- Páginas `sobre.html`, `privacidade.html`, `robots.txt`, `sitemap.xml`.

## Como inserir mais produtos

Edite `ofertas.js`: para cada produto, crie objeto com `id`, `title`, `category`, `emoji`, `description`, `keywords` e lista `offers` contendo `store` (`ml` ou `sp`), `label`, `title` e URL de afiliado real. Valide a elegibilidade do link e evite anúncios sem autorização.

**Nunca coloque chaves de API, senhas ou tokens no arquivo `ofertas.js`**: ele é público. Os links exibidos não são segredo.

## Pendências comerciais para lançamento

1. Conferir se os dois links cadastrados ainda funcionam e correspondem à conta de afiliado correta.
2. Inserir links reais dos programas de afiliados nos 8 produtos que ainda não os possuem e verificar o link recém-informado para GTA 6 (não inventar preço, vendedor ou estoque).
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

## Banner principal — destaques editoriais

O banner inicial agora traz **GTA VI** com arte oficial da Rockstar Games e faz a rotação dos produtos escolhidos no catálogo:
1. GTA VI (lançamento em 19/11/2026) — destaque prioritário, botão abre a comparação/cadastro do produto;
2. Mini Power Bank 10.000 mAh — produto com dois links enviados anteriormente;
3. Controle DualSense PS5 — produto relevante para a categoria Games, ainda sem link de afiliado.

As duas chamadas laterais levam diretamente aos detalhes de Power Bank e DualSense. A seleção é controlada pelo atributo `featured` de cada item no `ofertas.js` (ordem `featured.priority`; textos, botão, imagem oficial opcional, crédito). Novos lançamentos entram no banner ajustando esses dados, sem alterar o HTML. A rotação respeita a preferência por movimento reduzido. Não anunciar como oferta verificada antes de validar o link e o preço.

O uso de imagens oficiais da Rockstar deve observar os termos do titular e as regras dos programas de afiliados. A imagem do banner é carregada do CDN da Rockstar e pode deixar de funcionar se a origem mudar.

## Produtos da primeira seleção

1. Grand Theft Auto VI (GTA 6) — PlayStation 5 (Games; link Mercado Livre https://meli.la/11xMJVi informado pelo responsável, sem confirmação do anúncio nem atribuição de comissão)
2. Mini Power Bank 10.000 mAh (Eletrônicos; dois links já cadastrados e pendentes de validação)
3. Controle sem fio DualSense — PS5 (Games)
4. Headset gamer HyperX Cloud Stinger 2 (Games)
5. Fone Bluetooth QCY T13 ANC (Eletrônicos)
6. Caixa de som portátil JBL Go 4 (Eletrônicos)
7. Redmi Watch 5 Active (Eletrônicos)
8. Air Fryer Mondial — 4 litros (Casa)
9. Aspirador vertical WAP Silent Speed Max (Casa)
10. Kit de potes herméticos (Casa)

**Cadastro não equivale a oferta comercial comissionada.** Para emitir links do Mercado Livre, use o gerador de links dentro da conta de afiliados, a partir da página específica do produto. Para Shopee, utilize a área de afiliados aprovada. Não atribuir comissão a links de busca genéricos.

## Atualização de 20/11/2026 — GTA VI

- Link Mercado Livre recebido para GTA VI: `https://meli.la/11xMJVi`.
- O destino final do link abreviado não pôde ser validado automaticamente. A interface avisa **link em verificação** e mantém a referência de checagem de plataforma, mídia e vendedor.
- Não considerar comissão garantida antes de confirmar o link no painel do afiliado e testar a atribuição.
- Agora dois produtos possuem links informados (GTA VI e Power Bank); oito ainda aguardam links de afiliados.
