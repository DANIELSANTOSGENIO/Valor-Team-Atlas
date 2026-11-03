# Product Requirements Document (PRD)
## Sistema Valor Team Atlas — CRM & Gestão Documental Inteligente

---

### Metadados do Documento
* **Produto:** Valor Team Atlas
* **Organização / Cliente Alvo:** Valor Soluções
* **Autor / Product Owner:** Daniel Alves dos Santos
* **Versão:** 1.0 (Versão de Entrega / MVP Consolidado)
* **Data:** Novembro de 2026
* **Status:** Em Produção / V1 Operacional ([valor-team-atlas.lovable.app](https://valor-team-atlas.lovable.app))

---

## 1. Visão Geral do Produto e Contexto de Negócio

### 1.1 Contexto
A **Valor Soluções** atua prestando consultoria e assessoria especializada na regularização documental, obtenção e renovação de licenças, alvarás, certidões e conformidades legais para pessoas jurídicas. A operação lida diariamente com uma multiplicidade de órgãos emissores (Prefeituras, Governos Estaduais, Receita Federal, Bombeiros, Vigilância Sanitária e Conselhos de Classe), cada qual com prazos de validade distintos, portais descentralizados e penalidades severas para empresas em caso de expiração (multas, paralisação de atividades, impedimento de emitir notas ou participar de licitações).

### 1.2 O Problema
Antes do **Valor Team Atlas**, a operação enfrentava os seguintes gargalos críticos:
1. **Descontrole de Prazos de Validade:** Gestão manual por planilhas dispersas, aumentando o risco de documentos vencerem sem aviso prévio ao cliente.
2. **Custo Operacional de Digitação:** A entrada de novos documentos exigia que o analista abrisse cada arquivo (PDF ou foto) e digitasse manualmente número, órgão, datas de emissão e vencimento.
3. **Falta de Rastreabilidade Comercial:** Ausência de histórico estruturado de conversas e contatos realizados via WhatsApp para cobrar a documentação dos clientes.
4. **Desconexão Financeira:** Dificuldade em conciliar os honorários de assessoria e taxas de renovação diretamente com os documentos e processos em andamento.

### 1.3 A Proposta de Valor
O **Valor Team Atlas** é um CRM vertical e especializado que centraliza o ciclo de vida dos clientes, automatiza a extração de dados de documentos com Inteligência Artificial por visão computacional, prevê alertas de vencimento com régua de prazos customizada, gerencia o funil de renovações operacionais e integra o controle financeiro de cobranças em uma única plataforma web moderna.

---

## 2. Personas e Stakeholders

### Persona 1: O Analista de Regularidade (Usuário Operacional)
* **Perfil:** Profissional responsável por emitir certidões, cadastrar novos alvarás, monitorar validades e contatar os clientes para solicitar documentos para renovação.
* **Necessidades:**
  * Rapidez para cadastrar dezenas de documentos sem digitação repetitiva.
  * Visão clara de quais documentos estão para vencer hoje ou nos próximos dias.
  * Acesso rápido aos portais dos órgãos públicos para emissão.
  * Modelo pronto de mensagem para enviar ao cliente pelo WhatsApp com 1 clique.

### Persona 2: O Gestor Operacional / Administrador (Admin)
* **Perfil:** Sócio ou gerente da Valor Soluções.
* **Necessidades:**
  * Painel com visão panorâmica: quantos clientes estão ativos, volume financeiro a receber, renovações abertas e documentos críticos em alerta.
  * Parametrização da empresa: configuração dos dias de antecedência para alerta (ex.: 60, 30, 15 dias).
  * Controle de acesso por usuário e auditoria de atividades.

### Stakeholder Externo: O Cliente / Empresa Contratante
* **Perfil:** Empresário ou responsável financeiro/administrativo da empresa cliente.
* **Expectativa:** Ser lembrado com antecedência suficiente para não ter sua operação paralisada por falta de alvarás ou certidões vencidas.

---

## 3. Jornadas Principais do Usuário

### Jornada A: Extração Inteligente de Documento (IA)
1. O analista recebe uma foto ou PDF de um alvará sanitário do cliente.
2. Acessa o menu **"Ler documento com IA"** (`/extrair`).
3. Faz o upload da imagem ou arquivo.
4. O motor de IA analisa o documento, identifica o CNPJ, localiza o cliente cadastrado, infere o tipo do documento, número, órgão emissor, UF e calcula as datas de emissão e vencimento.
5. O analista valida os campos pré-preenchidos na tela e confirma o salvamento.
6. O documento entra automaticamente na esteira de monitoramento do sistema com o anexo armazenado em nuvem.

### Jornada B: Gestão Ativa de Vencimento e Contato
1. O analista abre o **Painel** (`/painel`) no início do dia e visualiza o contador de "Documentos em alerta" e "Meus acompanhamentos".
2. Clica na lista de documentos e filtra por status "Em alerta".
3. Clica na ação de contato rápido: o sistema monta a mensagem personalizada pronta com os dados da empresa, nome do contato, documento e dias restantes para expirar.
4. Abre o WhatsApp com a mensagem formatada e registra uma nota de acompanhamento no histórico do cliente.
5. Inicia o processo de renovação em 1 clique, movendo o documento para o pipeline de renovação.

### Jornada C: Cobrança e Baixa Financeira
1. No fechamento da renovação ou serviço de consultoria, o analista/financeiro gera uma cobrança vinculada ao cliente e documento.
2. Na tela de **Financeiro** (`/financeiro`), o sistema lista as cobranças em aberto, valores recebidos e saldos devedores.
3. Conforme o cliente efetua o pagamento, o analista lança a baixa do pagamento (parcial ou total) atualizando o saldo em tempo real.

---

## 4. Requisitos Funcionais (RF)

| ID | Módulo | Requisito Funcional | Descrição Detalhada | Prioridade |
| :--- | :--- | :--- | :--- | :--- |
| **RF01** | Autenticação | Controle de Acesso e Perfis | Autenticação segura por e-mail/senha com separação de perfis (`admin` e `member`). Acesso a configurações restrito a administradores. | Alta |
| **RF02** | Clientes | Cadastro e Ficha 360º | Cadastro de clientes PJ com Razão Social, Nome Fantasia, CNPJ, Contatos, E-mail, WhatsApp e Endereço. Visão unificada com documentos, cobranças e histórico de notas. | Alta |
| **RF03** | Clientes | Ativação / Inativação | Opção de inativar ou reativar clientes para preservação do histórico comercial e documental sem perda de integridade relacional. | Média |
| **RF04** | IA & OCR | Leitura e Extração de Documentos | Módulo com visão computacional para ler fotos/PDFs, extrair metadados estruturados (tipo, número, órgão, validade, CNPJ) e sugerir o vínculo automático. | Alta |
| **RF05** | Documentos | Gestão de Validades e Alertas | Cálculo dinâmico do status do documento (`Válido`, `Em Alerta`, `Vencido`) com base na data atual e nas regras de antecedência configuradas. | Alta |
| **RF06** | Documentos | Anexos e Armazenamento | Upload e download de cópias digitais dos documentos com armazenamento seguro em nuvem (Storage bucket). | Alta |
| **RF07** | Renovações | Pipeline / Workflow de Renovações | Funil operacional de acompanhamento das renovações com atribuição de responsável interno, data de próximo follow-up e status da solicitação. | Alta |
| **RF08** | Lembretes | Agenda Diária de Follow-up | Listagem automática no painel principal dos acompanhamentos atribuídos ao analista logado agendados para o dia ou em atraso. | Alta |
| **RF09** | Financeiro | Gestão de Cobranças e Saldos | Emissão de contas a receber por cliente com valor total, controle de saldo remanescente, data de vencimento e status (`Pendente`, `Parcial`, `Pago`). | Alta |
| **RF10** | Financeiro | Registro de Pagamentos | Lançamento de baixas parciais ou integrais com registro de método de pagamento, data e abatimento automático do saldo. | Alta |
| **RF11** | Atendimento | Notas com IA e Resumo de Reunião | Registro de atas/conversas com cliente com geração automatizada de resumo e próximos passos por inteligência artificial. | Média |
| **RF12** | Tipos & Portais| Parametrização e Links Úteis | Cadastro de tipos de documentos (com flag de validade obrigatória e se gera alerta) e catálogo de links rápidos para portais de emissão por UF/órgão. | Alta |
| **RF13** | Configuração | Parâmetros Globais da Empresa | Edição dos dados da Valor Soluções (razão, contato, WhatsApp oficial) e parametrização dos prazos de alerta antes do vencimento (ex.: 60, 30, 15 dias). | Alta |
| **RF14** | Relatórios | Exportação em CSV | Exportação sob demanda de listas completas em formato `.csv` para Clientes, Documentos, Renovações e Cobranças Financeiras. | Média |

---

## 5. Requisitos Não-Funcionais (RNF)

* **RNF01 — Segurança e Privacidade de Dados:**
  * Implementação de Row Level Security (RLS) no PostgreSQL via Supabase para isolamento de dados.
  * Sanitização de entradas e proteção contra injeções SQL e XSS.
  * Armazenamento seguro de anexos com políticas de controle de acesso.
* **RNF02 — Performance e Tempo de Resposta:**
  * Processamento de extração documental por IA com tempo médio de resposta inferior a 8 segundos.
  * Renderização otimizada com TanStack Router e chamadas assíncronas com invalidação inteligente de cache.
* **RNF03 — Usabilidade e Interface:**
  * Interface limpa, responsiva (desktop e tablet/mobile) baseada em Tailwind CSS e biblioteca de componentes consistentes.
  * Indicadores visuais claros por cores para validades (verde = válido, âmbar = alerta, vermelho = vencido).
* **RNF04 — Disponibilidade e Escalabilidade:**
  * Arquitetura em nuvem distribuída com deploy contínuo e banco de dados relacional gerenciado.

---

## 6. Arquitetura Técnica e Modelo de Dados

### 6.1 Stack Tecnológica
* **Frontend / Fullstack:** TanStack Start (React 19, Vite, TypeScript, Tailwind CSS, TanStack Router).
* **Backend & Banco de Dados:** PostgreSQL hospedado via Supabase / Lovable Cloud.
* **Inteligência Artificial:** Lovable AI Vision & Text Gateway (modelos multimodais para extração documental e sumarização de texto).
* **Armazenamento:** Supabase Storage para guarda de PDFs e fotos de licenças.
* **Design & UI:** Tailwind CSS, Shadcn UI / Lucide Icons, Sonner (notificações toast).

### 6.2 Modelo Entidade-Relacionamento (13 Entidades do Sistema)

```
[clients] 1 ──── ∞ [documents] 1 ──── ∞ [renewals]
   │                      │                    │
   │ 1                    │ 1                  │ 1
   │                      │                    │
   ├─── ∞ [charges] 1 ────┴────────────────────┘
   │           │
   │           └── ∞ [payments]
   │
   ├─── ∞ [client_notes]
   │
   └─── ∞ [contact_logs] (via documents)

[document_types] 1 ──── ∞ [documents]
[document_types] 1 ──── ∞ [portal_links]
[profiles] 1 ──── ∞ [user_roles]
[app_settings] (Singleton de configuração global)
[audit_log] (Rastreamento de ações e auditoria)
```

#### Resumo das Tabelas do Banco:
1. `clients`: Cadastro de clientes (Razão Social, Nome Fantasia, CNPJ, contatos, status ativo/inativo).
2. `documents`: Acervo de documentos com validade, tipo, anexo em storage e flags de alerta.
3. `document_types`: Catálogo de tipos de licenças/certidões (ex.: AVCB, Alvará, CND Federal) com flags de exigência de validade.
4. `renewals`: Processos ativos de renovação documental, responsável interno e prazo de follow-up.
5. `charges`: Títulos a receber por cliente com valor, vencimento e saldo.
6. `payments`: Baixas e comprovantes de pagamentos vinculados às cobranças.
7. `client_notes`: Anotações comerciais e resumos de conversas gerados por IA.
8. `contact_logs`: Registros de tentativas de contato e conversas com clientes.
9. `portal_links`: Catálogo de URLs externas para emissão rápida de certidões por estado/órgão.
10. `app_settings`: Dados da empresa e lista de dias de antecedência para cálculo dos alertas.
11. `profiles`: Perfis complementares dos colaboradores do sistema.
12. `user_roles`: Mapeamento de papéis (`admin` vs `member`).
13. `audit_log`: Registro de histórico de alterações críticas no banco.

---

## 7. Métricas de Sucesso do Produto (KPIs)

1. **Taxa de Renovação Preventiva:** Percentual de documentos renovados antes da expiração da validade (Meta: > 98%).
2. **Redução do Tempo de Cadastro:** Tempo médio para dar entrada em um novo documento (Meta: redução de ~5 minutos para menos de 45 segundos com a IA).
3. **Redução de Inadimplência:** Saldo médio em aberto e tempo médio de recebimento de honorários vinculados às renovações.
4. **Engajamento Operacional:** Cumprimento da lista diária de acompanhamentos do responsável direto pelo painel.

---

## 8. Roadmap e Próximos Passos (Versão 2.0)

* [ ] **Disparo Automatizado via WhatsApp:** Integração com API de mensageria (ex.: Evolution/Z-API) para disparo direto sem depender de clique manual.
* [ ] **Notificações por E-mail:** Envio automatizado de avisos de vencimento para o e-mail financeiro do cliente.
* [ ] **Interface Completa de Edição/Exclusão:** Inclusão de botões e modais de edição e exclusão direta para clientes e documentos na interface do usuário.
* [ ] **Portal do Cliente (Área Restrita):** Permitir que o próprio cliente faça login para visualizar suas certidões vigentes e emitir segundas vias.

---
# Valor-Team-Atlas
## Imagens
<img width="1897" height="965" alt="image" src="https://github.com/user-attachments/assets/ef0b69c9-6869-4909-b04d-5990935fbc01" />
## Um resumo do conceito do seu app
1. Organização e gestão de alguns serviços feitos pelo meu parceiro aonde erao tratados em planilhas de excel
2. Repositorio


