# Cenários de Teste — App Mobile Front

## 1. Login
- **CT-F01 — Login válido:** informar e-mail e senha válidos; resultado esperado: acesso ao Dashboard e token armazenado.
- **CT-F02 — Senha inválida:** informar senha incorreta; resultado esperado: mensagem de credenciais inválidas e permanência na tela de login.
- **CT-F03 — Campos obrigatórios:** deixar e-mail ou senha vazio; resultado esperado: validação do formulário.
- **CT-F04 — Sessão expirada:** acessar rota protegida sem token válido; resultado esperado: redirecionamento para /login.
- **CT-F05 — Logout:** clicar em Sair; resultado esperado: token removido e retorno para /login.

## 2. Dashboard
- **CT-F06 — Carregamento:** após login, consultar o Dashboard; resultado esperado: tenant, receitas, despesas, saldo e contas exibidos.
- **CT-F07 — Saldo:** conferir se o saldo apresentado corresponde a receitas menos despesas retornadas pela API.
- **CT-F08 — Erro da API:** indisponibilizar a API; resultado esperado: tratamento de erro sem quebrar a aplicação.

## 3. Contas
- **CT-F09 — Listagem:** abrir Contas; resultado esperado: registros paginados.
- **CT-F10 — Paginação:** testar primeira, anterior, próxima e última página; resultado esperado: página e total de páginas coerentes.
- **CT-F11 — Inclusão:** cadastrar conta válida; resultado esperado: registro criado e exibido na lista.
- **CT-F12 — Alteração:** editar conta; resultado esperado: dados atualizados.
- **CT-F13 — Exclusão:** excluir conta; resultado esperado: registro removido.
- **CT-F14 — Isolamento por tenant:** autenticar usuários de tenants diferentes; resultado esperado: cada usuário visualizar somente seus próprios registros.

## 4. Categorias
- **CT-F15 — CRUD completo:** incluir, consultar, alterar e excluir categoria.
- **CT-F16 — Tipo:** validar categorias de receita e despesa.
- **CT-F17 — Paginação e isolamento:** validar os mesmos comportamentos de Contas.

## 5. Transações
- **CT-F18 — Inclusão de receita:** cadastrar receita válida; resultado esperado: transação exibida.
- **CT-F19 — Inclusão de despesa:** cadastrar despesa válida; resultado esperado: transação exibida.
- **CT-F20 — Alteração:** editar valor, descrição, categoria ou data; resultado esperado: dados atualizados.
- **CT-F21 — Exclusão:** excluir transação; resultado esperado: registro removido.
- **CT-F22 — Ordenação:** validar que as transações são apresentadas por data decrescente.
- **CT-F23 — Paginação:** validar navegação entre páginas.

## 6. Segurança e integração
- **CT-F24 — Header Authorization:** requisições protegidas devem enviar Bearer token.
- **CT-F25 — API indisponível:** validar mensagem amigável para falha de comunicação.
- **CT-F26 — URL de produção:** validar que o frontend utiliza a URL configurada no environment de produção.
- **CT-F27 — Navegação direta:** acessar diretamente /contas, /categorias e /transacoes; resultado esperado: rota carregada corretamente após configuração do rewrite da Vercel.

## Critérios de aceite
Todos os cenários críticos (CT-F01, CT-F04, CT-F05, CT-F09, CT-F11, CT-F12, CT-F13, CT-F15, CT-F18, CT-F20, CT-F21 e CT-F24) devem passar antes da publicação.
