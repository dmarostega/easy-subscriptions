# Prompt Codex — Easy Subscriptions

Este arquivo contém o prompt principal usado para orientar a implementação do projeto no Codex.

## Produto

Easy Subscriptions é um SaaS para profissionais que recebem mensalidades recorrentes de alunos, clientes ou assinantes simples, como professores particulares, personal trainers, instrutores, clubes pequenos, escolinhas, consultores e prestadores recorrentes.

## Stack obrigatória

- Laravel 13
- Vue.js 3
- TypeScript
- MySQL
- Tailwind CSS
- Vite
- Inertia.js

## Regras principais

- Seguir SOLID e Clean Code.
- Usar Controllers finos.
- Usar Services para regras de negócio.
- Usar Form Requests para validação.
- Usar Policies para autorização.
- Usar Enums para status de cobranças, períodos, pagamentos e roles.
- Criar Commands para geração de cobranças recorrentes quando necessário.
- Criar painel admin.
- Criar CRUD de planos do SaaS.
- Criar pelo menos um Plano Gratuito.
- Criar SEO básico.
- Criar `public/robots.txt`.
- Criar `public/sitemap.xml`.
- Criar manual em Markdown.
- Preparar deploy para VPS Hostinger KVM 1 com CloudPanel, Nginx, PHP-FPM, MySQL e Cloudflare.

## Observação importante

Não implementar gateway de pagamento no MVP. O controle de pagamento deve ser manual, com estrutura preparada para futura integração com Pix ou checkout externo.

## Prompt completo

Você é um arquiteto de software especialista em Laravel 13, Vue.js 3, TypeScript, MySQL, SaaS para autônomos, SOLID e Clean Code.

Crie um SaaS chamado "Mensalidade Fácil", focado em profissionais que recebem mensalidades recorrentes de alunos, clientes ou assinantes simples, como professores particulares, personal trainers, instrutores, clubes pequenos, escolinhas, consultores e prestadores recorrentes.

Stack:
- Laravel 13
- Vue.js 3
- TypeScript
- MySQL
- Tailwind CSS
- Vite
- Inertia.js com Vue 3
- Autenticação compatível com Laravel 13

Objetivo:
Controlar clientes, planos de mensalidade, vencimentos, pagamentos manuais e inadimplência.

Personas:
1. Professor particular.
2. Personal trainer.
3. Instrutor de música.
4. Escolinha pequena.
5. Consultor com clientes recorrentes.

Funcionalidades do usuário:
- Cadastro/login.
- Dashboard:
  - mensalidades a vencer;
  - mensalidades vencidas;
  - mensalidades pagas no mês;
  - receita prevista;
  - limite do plano.
- CRUD de clientes.
- CRUD de planos de mensalidade do próprio usuário:
  - nome;
  - valor;
  - periodicidade;
  - dia de vencimento;
  - ativo/inativo.
- Vincular cliente a um plano de mensalidade.
- Gerar cobranças mensais.
- Controle de pagamentos:
  - pendente;
  - pago;
  - atrasado;
  - cancelado.
- Baixa manual de pagamento.
- Mensagem copiável para WhatsApp:
  - cobrança;
  - lembrete de vencimento;
  - confirmação de pagamento.
- Relatórios:
  - inadimplentes;
  - recebido no mês;
  - previsto no mês.
- Cores configuráveis por variáveis.

Painel admin:
- Role admin.
- CRUD de planos do SaaS.
- CRUD de usuários.
- Admin altera plano manualmente.
- Configurações globais:
  - nome;
  - domínio;
  - e-mail;
  - cores;
  - SEO;
  - limites.
- Relatórios:
  - usuários por plano;
  - cobranças geradas;
  - usuários ativos.

Planos do SaaS:
- Gratuito:
  - até 10 clientes;
  - até 20 cobranças/mês.
- Pro:
  - até 200 clientes;
  - cobranças recorrentes;
  - mensagens WhatsApp.
- Plus:
  - clientes ilimitados;
  - relatórios avançados;
  - personalização visual.

SEO:
- Home.
- Recursos.
- Preços.
- Termos.
- Privacidade.
- Metatags, canonical, Open Graph, Twitter Card.
- Schema.org SoftwareApplication.
- Criar public/robots.txt.
- Criar public/sitemap.xml.
- Não indexar dados financeiros, clientes, cobranças ou admin.

Arquitetura:
- Services:
  - MembershipPlanService;
  - ChargeGenerationService;
  - PaymentService;
  - PlanLimitService.
- Commands:
  - gerar cobranças recorrentes mensalmente.
- Form Requests.
- Policies.
- Enums:
  - ChargeStatus;
  - BillingPeriod;
  - UserRole.
- Seeders:
  - admin;
  - planos SaaS;
  - configs.
- Factories.
- Testes:
  - gerar cobrança mensal;
  - marcar cobrança como paga;
  - limite do plano gratuito;
  - isolamento de dados por usuário;
  - admin altera plano.

Entidades:
- User
- Plan
- UserPlan
- Customer
- MembershipPlan
- CustomerMembership
- Charge
- Payment
- AppSetting

Manual:
- Criar docs/MANUAL.md.
- Criar README.md.
- Criar docs/DEPLOY.md para VPS Hostinger KVM 1.

Não implementar gateway de pagamento no MVP. Tudo será controlado manualmente, com estrutura preparada para futura integração.

### Regras globais do projeto:

1. Stack obrigatória:
   - Laravel 13
   - Vue.js 3
   - TypeScript
   - MySQL
   - Tailwind CSS
   - Vite

2. Arquitetura:
   - Seguir SOLID, Clean Code e separação de responsabilidades.
   - Controllers devem ser finos.
   - Usar Form Requests para validação.
   - Usar Policies para autorização.
   - Usar Services/Actions para regras de negócio.
   - Usar Enums para status, roles e tipos fixos.
   - Usar migrations com foreign keys, índices e constraints.
   - Usar seeders para dados iniciais.
   - Usar factories e testes mínimos.

3. SaaS:
   - Todo projeto deve ter planos.
   - Deve existir no mínimo Plano Gratuito.
   - Planos devem ser configuráveis pelo painel admin.
   - Admin deve poder alterar plano do usuário manualmente.
   - Não implementar pagamento online no MVP.
   - Preparar estrutura para futura integração com cobrança.

4. Admin:
   - Criar role admin.
   - Criar painel admin protegido.
   - Admin deve gerenciar usuários, planos e configurações globais.
   - Admin deve visualizar relatórios básicos.

5. SEO:
   - Criar páginas públicas:
     - Home
     - Recursos
     - Preços
     - Termos de Uso
     - Política de Privacidade
   - Implementar title, meta description, canonical, Open Graph e Twitter Card.
   - Criar Schema.org SoftwareApplication quando aplicável.
   - Criar public/robots.txt.
   - Criar public/sitemap.xml.
   - Não indexar rotas autenticadas, admin, dashboard ou dados privados.

6. Front-end:
   - Usar Vue 3 com TypeScript.
   - Componentizar telas e elementos reutilizáveis.
   - Usar Tailwind CSS.
   - Cores principais devem ser configuráveis via variáveis CSS.
   - Evitar cores hardcoded espalhadas no projeto.
   - Criar layout público, layout autenticado e layout admin.

7. Deploy:
   - Preparar para VPS KVM 1 da Hostinger com Nginx, PHP-FPM, MySQL e Node.
   - Criar docs/DEPLOY.md.
   - Documentar:
     - composer install
     - npm install
     - npm run build
     - php artisan migrate --seed
     - php artisan storage:link
     - permissões
     - configuração .env
     - cache de config, routes e views

8. Documentação:
   - Criar / Atualizart README.md técnico.
   - Criar / Atualizart docs/MANUAL.md para uso do sistema.
   - Criar / Atualizart docs/ROADMAP.md com melhorias futuras.
   - Criar / Atualizart docs/DEPLOY.md.

9. Segurança:
   - Isolar dados por usuário.
   - Nunca permitir que um usuário acesse dados de outro.
   - Validar permissões via Policies.
   - Proteger rotas admin.
   - Não expor dados privados no sitemap.
   - Não indexar páginas privadas.

10. Qualidade:
   - Criar testes mínimos para regras principais.
   - Evitar overengineering.
   - Priorizar MVP funcional, limpo, simples e evolutivo.