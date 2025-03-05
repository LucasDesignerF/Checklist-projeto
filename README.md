### Checklist Atualizado do Projeto "CodeAPI - Sales System’s" (04/03/2025)

#### 1. Estrutura Básica e Configuração
- [x] **Configuração do Ambiente**  
  - Status: Concluído  
  - Descrição: Ambiente Python com `venv`, dependências em `requirements.txt` (FastAPI, MongoDB, Redis, SendGrid, etc.), `.env` configurado.

- [x] **Estrutura do FastAPI**  
  - Status: Concluído  
  - Descrição: `main.py` com rotas básicas (`/`, `/user`, `/admin`, `/products`), templates Jinja2, integrações MongoDB e Redis.

- [x] **Conexão com MongoDB**  
  - Status: Concluído  
  - Descrição: Conexão em `dependencies.py`, modelos (`users.py`, `products.py`, `orders.py`, `tickets.py`) criados e funcionais.

- [x] **Conexão com Redis**  
  - Status: Concluído  
  - Descrição: Sessões gerenciadas em `config.py` com `redis_client`, TTL de 24 horas.

#### 2. Autenticação e Usuários
- [x] **Login OAuth2 com Discord**  
  - Status: Concluído  
  - Descrição: Implementado em `routes/auth.py`, redireciona para `/user`, `/admin` ou `return_url` (ex.: `/user/buy/{product_id}`).

- [x] **Registro de Usuários no Banco**  
  - Status: Concluído  
  - Descrição: Usuários criados em `users` após login OAuth2 em `routes/auth.py`.

- [x] **Sessões com Redis**  
  - Status: Concluído  
  - Descrição: Sessões armazenadas no Redis, validadas por `get_current_user`.

#### 3. Produtos e Compras
- [x] **Página Pública de Produtos (`/products`)**  
  - Status: Concluído  
  - Descrição: Rota em `main.py`, template `products.html`, acessível sem login, botão "Comprar" redireciona para login se necessário.

- [x] **Gestão Básica de Produtos (Admin)**  
  - Status: Concluído  
  - Descrição: Adição de produtos em `routes/admin.py` com formulário em `admin.html`.

- [ ] **Gestão Avançada de Produtos (Admin)**  
  - Status: Pendente  
  - Descrição: Edição e exclusão de produtos ainda não implementadas.

- [x] **Fluxo de Compra**  
  - Status: Concluído  
  - Descrição: Compra em `/user/buy/{product_id}`, redirecionamento para login se deslogado, QR Code e chave Pix gerados.

- [x] **Gerador de Pix**  
  - Status: Concluído  
  - Descrição: `pix_generator.py` gera payloads válidos com `order_id` como `txid`.

- [x] **Atualização de Estoque**  
  - Status: Concluído  
  - Descrição: Produtos "individual" têm estoque atualizado para "sold" em `routes/admin.py`.

#### 4. Pedidos e Validação
- [x] **Registro de Pedidos**  
  - Status: Concluído  
  - Descrição: Pedidos salvos em `orders` com `product_name` em `routes/user.py`.

- [x] **Dashboard do Usuário**  
  - Status: Concluído  
  - Descrição: Exibe pedidos com `product_name` e status em `user.html`.

- [x] **Dashboard do Admin (Pedidos)**  
  - Status: Concluído  
  - Descrição: Lista pedidos pendentes e em verificação em `admin_orders.html`, com ações de confirmar/negar.

- [x] **Validação Manual de Pedidos**  
  - Status: Concluído  
  - Descrição: Confirmação e negação em `routes/admin.py`, atualiza status e estoque.

#### 5. Interface e Experiência do Usuário
- [x] **Templates HTML com TailwindCSS**  
  - Status: Concluído  
  - Descrição: Todos os templates (`index.html`, `user.html`, `admin.html`, `products.html`, `buy.html`, `admin_orders.html`, `admin_tickets.html`) usam TailwindCSS via CDN.

- [x] **Timer na Página de Compra**  
  - Status: Concluído  
  - Descrição: Timer de 10 minutos em `buy.html` com JavaScript.

- [x] **Favicon**  
  - Status: Concluído  
  - Descrição: Adicionado em todos os templates.

#### 6. Notificações e Suporte
- [x] **Notificações por E-mail (SendGrid) - Usuário**  
  - Status: Concluído  
  - Descrição: E-mails de confirmação e negação enviados ao usuário em `utils/email.py`, chamados em `routes/admin.py`.

- [x] **Notificações por E-mail (SendGrid) - Admin (Pedidos)**  
  - Status: Concluído  
  - Descrição: E-mail ao admin quando pedido muda para "em_verificacao" em `utils/email.py`, chamado em `routes/user.py`.

- [ ] **Notificações por E-mail (SendGrid) - Tickets**  
  - Status: Pendente  
  - Descrição: Faltam e-mails específicos para novos tickets e respostas (ex.: `send_new_ticket_email`, `send_ticket_response_email`).

- [x] **Sistema de Suporte (Tickets) - Básico**  
  - Status: Concluído  
  - Descrição: Criação de tickets em `routes/user.py`, listagem e resposta em `routes/admin.py`, com modelo `tickets.py` e templates `user.html` e `admin_tickets.html`.

- [ ] **Sistema de Suporte (Tickets) - Completo**  
  - Status: Pendente  
  - Descrição: Faltam notificações por e-mail para tickets e exibição de respostas no dashboard do usuário.

#### 7. Monitoramento e Escalabilidade
- [ ] **Sentry para Monitoramento**  
  - Status: Pendente  
  - Descrição: Configurado no `.env`, mas não integrado ao código.

- [ ] **Cache Avançado com Redis**  
  - Status: Pendente  
  - Descrição: Redis usado apenas para sessões; cache de produtos ou pedidos ainda não implementado.

- [ ] **Validação Automática do Pix**  
  - Status: Pendente (Opcional)  
  - Descrição: Não implementada, validação permanece manual.

---

### Resumo
**Concluído (20/26):**
- Estrutura básica, autenticação OAuth2, registro de usuários, página pública de produtos, gestão básica de produtos, fluxo de compra com Pix, atualização de estoque, registro de pedidos, dashboards (usuário e admin), validação manual, templates com TailwindCSS, timer, favicon, notificações por e-mail para pedidos (usuário e admin), sistema básico de tickets.

**Pendente (6/26):**
- Gestão avançada de produtos (editar/excluir), notificações completas para tickets, exibição de respostas de tickets no dashboard do usuário, integração com Sentry, cache avançado com Redis, validação automática do Pix (opcional).

---

### Comparação com o Último Checklist
Desde o último checklist (17/23 concluídos):
- **Novos Itens Concluídos:**
  - Notificações por e-mail para admin (pedidos em verificação).
  - Sistema básico de suporte (tickets) com criação, listagem e resposta.
- **Ajustes:**
  - Dividi o item "Sistema de Suporte (Tickets)" em "Básico" (concluído) e "Completo" (pendente) para refletir o progresso parcial.
