# Forno — Gestão da pizzaria

Código-fonte do projeto publicado, exportado em 08/10/2026.

## Estrutura
- app/: painel, estilos, autenticação e API de clientes, sabores e pedidos.
- db/: conexão e esquema do banco de dados.
- drizzle/: migração SQL e metadados do banco.
- components/ e hooks/: componentes e utilitários de interface.
- lib/: funções compartilhadas e suporte a integrações.
- public/: arquivos públicos.
- build/ e scripts/: infraestrutura de desenvolvimento e compilação.
- .openai/hosting.json: identificação do Site e declaração do banco DB.
- package.json e pnpm-lock.yaml: dependências e comandos.
- docs/README-original.md: documentação técnica completa do projeto original.

## Executar no computador
Instale Node.js 22.13 ou superior e pnpm 11.25.0 (versão indicada em package.json). Abra a pasta no VS Code e execute no terminal:

```sh
pnpm install --frozen-lockfile
pnpm build
node --import ./scripts/sites-env.mjs ./node_modules/wrangler/bin/wrangler.js d1 execute DB --local --config dist/server/wrangler.json --persist-to .wrangler/state --file drizzle/0000_skinny_wraith.sql
pnpm dev
```
Aplique a migração apenas na primeira inicialização do banco local. Abra o endereço informado no terminal (normalmente http://localhost:5173). O perfil padrão de uma cópia limpa é portable; o login simulado funciona apenas no desenvolvimento local. Se necessário, acesse /signin-with-chatgpt?return_to=/ no mesmo endereço.

## Outros comandos
```sh
pnpm build
pnpm start
pnpm lint
pnpm db:generate
```
`start` executa a compilação local e não simula o login. Use `dev` para desenvolvimento com a autenticação simulada.

## Banco e autenticação
A aplicação usa React/TypeScript, Vinext/Vite, Cloudflare Workers, D1 e Drizzle. O login de produção é fornecido pela hospedagem Sites. Para publicar em outro provedor, será necessário configurar o banco D1 e uma autenticação equivalente; não basta abrir os arquivos diretamente no navegador. Não aceite cabeçalhos de identidade enviados livremente por visitantes em uma implantação própria.

Este pacote contém o código-fonte e a estrutura do banco. Não contém dados de clientes, pedidos, credenciais, dependências instaladas ou arquivos compilados. O banco local começa vazio e não acessa automaticamente os dados de produção.

## Referência da exportação
Site: https://forno-pizzaria-robson.nosbor-gomes.chatgpt.site
Commit: b04489adfaae69e5dceceb6441f2e991801ed348
O código original foi preservado; apenas este guia e o índice de arquivos foram acrescentados ao pacote.
