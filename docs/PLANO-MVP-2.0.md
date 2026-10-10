# Achados Inteligentes 2.0 — Plano de execução
Atualizado em 10/10/2026. Documento de trabalho, sem publicação automática.

## Objetivo
Buscador e comparador de preços de produtos em oferta, com links de afiliado. Início: Mercado Livre e Shopee. Preparado para novos marketplaces. Prioridade: confiança do comprador, velocidade e experiência móvel.

## Regras obrigatórias
1. Não publicar uma oferta sem preço e disponibilidade verificados, link de afiliado válido e identificação clara da loja.
2. Comparar somente o mesmo produto e variação (marca, modelo, capacidade, cor/tamanho quando relevantes).
3. Ordenar pelo custo final conhecido (produto + frete - descontos aplicáveis), sinalizando quando frete ou cupom dependerem do CEP/usuário.
4. Não inventar desconto ou preço anterior. Mostrar data e hora da última checagem.
5. Não expor percentuais nem valores de comissão em HTML, JavaScript público, API pública ou metadados. Mostrar apenas aviso transparente sobre afiliação.
6. Não copiar vídeos, fotos ou avaliações sem autorização/licença. Respeitar regras de uso de marca e API dos marketplaces.
7. Se uma oferta expirar, ficar indisponível ou perder o link de afiliado, despublicar automaticamente.
8. Sem garantia de que a plataforma encontrou o menor preço de toda a internet: ranking restrito às ofertas monitoradas e verificadas.

## Fase A — Base visual
- Hero responsivo, busca central, banners adaptados ao celular e computador.
- Vitrine 'Achados do dia' com apenas ofertas verificadas.
- Card com foto, título, preço atual, desconto verificável, marketplace, horário de atualização e botão para o link de afiliado.
- Página de comparação para um mesmo produto com ofertas de diferentes lojas.
- Estados vazios, carregamento, acessibilidade e aviso de transparência.
- Dados demonstrativos apenas em ambiente de desenvolvimento, nunca apresentados como promoções reais.

## Fase B — Banco de dados e painel
Entidades sugeridas:
- products: id, title, brand, model, gtin, variant, category, canonical_image_url, status.
- marketplaces: id, name, slug, logo_url, status.
- offers: id, product_id, marketplace_id, external_product_id, seller_name, price_cents, shipping_cents_nullable, currency, original_price_cents_nullable, affiliate_url, source_url, image_url, verified_at, expires_at, is_available, is_published.
- price_history: id, offer_id, price_cents, observed_at, source.
- media_assets: id, product_id, url, type, rights_basis, attribution, status.
- click_events: id, offer_id, occurred_at, campaign, referrer, anonymous_session_id.
- admin_private_commissions: id, offer_id, rate_nullable, estimate_cents_nullable (acesso apenas administrativo).
- import_jobs: id, source, status, created_at, results_summary.

Banco: Supabase em projeto independente do RestaurantOS, com RLS e nenhuma credencial de serviço no navegador. A API pública deve expor só ofertas aprovadas e dados necessários ao consumidor. Painel protegido por autenticação.

## Fase C — Ingestão e integração
- Importação CSV para candidatos (meta até 1.120, não publicação automática).
- Adaptadores por marketplace: fetchCandidates, fetchOffer, normalizeOffer, validateAffiliateUrl.
- Agendamentos de revalidação e tratamento de limites de API.
- Checar acesso permitido a feeds/APIs e geração de links afiliados de cada plataforma antes de prometer automação.
- Fila de revisão para ofertas duvidosas, variantes diferentes e descontos não comprovados.

## Fase D — PWA e expansão
- Manifesto, ícones próprios, cache somente para interface e navegação offline segura.
- No PWA, preços precisam sempre exibir a última verificação; não apresentar cache antigo como oferta atual.
- Preparar adaptadores futuros (Amazon, Magalu etc.) sem exibir marcas não integradas como se fossem ofertas disponíveis.

## Fase E — Aquisição de tráfego
1. SEO de intenção de compra: páginas indexáveis de comparações úteis, dados estruturados apenas quando verdadeiros, conteúdo editorial original.
2. Compartilhamento por WhatsApp com título, imagem autorizada, preço verificado, data da checagem e link da página de comparação.
3. Conteúdo curto de demonstração usando mídia autorizada, sem promessa falsa de economia.
4. Medir: visitas orgânicas, pesquisas sem resultado, cliques externos, CTR, taxa de ofertas expiradas e comissões confirmadas nas plataformas.
5. Testar anúncios pagos só depois de validar rastreamento, custo de aquisição e margem.

## Ordem de execução sugerida
1. Revisar o HTML atual e remover referências públicas a percentuais de comissão.
2. Criar modelo de dados e catálogo real vazio.
3. Inserir manualmente 2 a 5 ofertas reais com links fornecidos pelo proprietário e preço conferido.
4. Construir comparador e medir cliques.
5. Integrar importação, validação e rechecagem.
6. Melhorar design e SEO com dados reais.
7. PWA e campanhas.

## Critérios para o primeiro lançamento
- Nenhum botão de compra fictício.
- Nenhuma comissão privada exposta.
- Nenhum desconto sem evidência.
- Produto + marketplace + link de afiliado coerentes.
- Testado em celular e desktop.
- Site atual preservado até a nova versão ser validada.

## Bloqueios externos
- Necessários: links de afiliado reais e confirmação das permissões de integração para cada marketplace.
- Ainda não confirmados: feeds, APIs de preços e acesso a mídia de terceiros.
