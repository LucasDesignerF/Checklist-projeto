### Checklist do Projeto "CodeAPI - Sales System’s"

#### 1. Estrutura Básica e Configuração
- [x] **Configuração do Ambiente**  
  - Status: Concluído  
  - Descrição: Ambiente Python configurado com `venv`, dependências instaladas via `requirements.txt` (FastAPI, MongoDB, Redis, SendGrid, etc.), e `.env` funcional.

- [x] **Estrutura do FastAPI**  
  - Status: Concluído  
  - Descrição: `main.py` inicializado com rotas básicas (`/`, `/user`, `/admin`, `/products`), templates Jinja2 e integrações (MongoDB, Redis).

- [x] **Conexão com MongoDB**  
  - Status: Concluído  
  - Descrição: Conexão estabelecida em `dependencies.py`, modelos (`users.py`, `products.py`, `orders.py`) criados e funcionando.

- [x] **Conexão com Redis**  
  - Status: Concluído  
  - Descrição: Sessões de usuário gerenciadas em `config.py` com `redis_client`, usadas no login OAuth2.

#### 2. Autenticação e Usuários
- [x] **Login OAuth2 com Discord**  
  - Status: Concluído  
  - Descrição: Implementado em `routes/auth.py` com redirecionamento para `/user` ou `/admin`, e suporte a `return_url` para compras sem login.

- [x] **Registro de Usuários no Banco**  
  - Status: Concluído  
  - Descrição: Usuários são criados em `users` após login OAuth2, corrigido em `routes/auth.py`.

- [x] **Sessões com Redis**  
  - Status: Concluído  
  - Descrição: Sessões armazenadas no Redis com TTL de 24 horas, funcionando em `get_current_user`.

#### 3. Produtos e Compras
- [x] **Página Pública de Produtos (`/products`)**  
  - Status: Concluído  
  - Descrição: Criada em `main.py` e `products.html`, acessível sem login, com botão "Comprar" redirecionando para login se necessário.

- [x] **Gestão Básica de Produtos (Admin)**  
  - Status: Concluído  
  - Descrição: Adição de produtos implementada em `routes/admin.py` com formulário em `admin.html`.

- [ ] **Gestão Avançada de Produtos (Admin)**  
  - Status: Pendente  
  - Descrição: Falta implementar edição e exclusão de produtos no dashboard admin.

- [x] **Fluxo de Compra**  
  - Status: Concluído  
  - Descrição: Compra em `/user/buy/{product_id}` funcionando, com redirecionamento para login OAuth2 se deslogado, QR Code e chave Pix validados.

- [x] **Gerador de Pix**  
  - Status: Concluído  
  - Descrição: Implementado em `pix_generator.py`, usando `order_id` como `txid`, validado no banco.

- [x] **Atualização de Estoque**  
  - Status: Concluído  
  - Descrição: Produtos "individual" têm estoque atualizado para "sold" ao confirmar pedido em `routes/admin.py`.

#### 4. Pedidos e Validação
- [x] **Registro de Pedidos**  
  - Status: Concluído  
  - Descrição: Pedidos criados em `orders` com `product_name`, funcionando em `routes/user.py`.

- [x] **Dashboard do Usuário**  
  - Status: Concluído  
  - Descrição: Exibe pedidos com `product_name` e status em `user.html`.

- [x] **Dashboard do Admin (Pedidos)**  
  - Status: Concluído  
  - Descrição: Lista pedidos pendentes e em verificação em `admin_orders.html`, com botões para confirmar/negar.

- [x] **Validação Manual de Pedidos**  
  - Status: Concluído  
  - Descrição: Implementada em `routes/admin.py` com `confirm-order` e `deny-order`, atualizando status e estoque.

#### 5. Interface e Experiência do Usuário
- [x] **Templates HTML com TailwindCSS**  
  - Status: Concluído  
  - Descrição: `index.html`, `user.html`, `admin.html`, `products.html`, `buy.html`, e `admin_orders.html` criados com TailwindCSS via CDN.

- [x] **Timer na Página de Compra**  
  - Status: Concluído  
  - Descrição: Timer de 10 minutos adicionado em `buy.html` com JavaScript.

- [x] **Favicon**  
  - Status: Concluído  
  - Descrição: Adicionado em todos os templates com a URL fornecida.

#### 6. Notificações e Suporte
- [ ] **Notificações por E-mail (SendGrid)**  
  - Status: Pendente (Prototipado)  
  - Descrição: Código prototipado em `routes/admin.py` para enviar e-mails ao confirmar/negar pedidos, mas ainda não testado ou integrado totalmente.

- [ ] **Sistema de Suporte (Tickets)**  
  - Status: Pendente  
  - Descrição: Botão "Abrir Ticket" existe em `user.html`, mas o sistema de tickets (criação, gestão) ainda não foi implementado.

#### 7. Monitoramento e Escalabilidade
- [ ] **Sentry para Monitoramento**  
  - Status: Pendente  
  - Descrição: Configurado no `.env`, mas não integrado ao código para capturar erros.

- [ ] **Cache Avançado com Redis**  
  - Status: Pendente  
  - Descrição: Redis usado apenas para sessões; cache de produtos ou pedidos ainda não implementado.

---

### Resumo
**Concluído (17/23):**
- Estrutura básica, autenticação OAuth2, registro de usuários, página pública de produtos, fluxo de compra com Pix, gestão básica de produtos, atualização de estoque, dashboards com pedidos, validação manual, templates com TailwindCSS, timer, favicon.

**Pendente (6/23):**
- Gestão avançada de produtos (editar/excluir), notificações por e-mail (finalizar/testar), sistema de tickets, integração com Sentry, cache avançado com Redis, validação automática do Pix (opcional).

