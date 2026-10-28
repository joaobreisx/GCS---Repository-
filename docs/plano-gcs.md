# Plano de Gestão de Configuração de Software (GCS)

**Projeto:** ONGConecta
**Responsável:** João (@joaobreisx)
**Modalidade:** individual
**Revisor (par de revisão):** a definir — colaborador com acesso de escrita (Write)
**Versão do documento:** 1.0

---

## 1. Objetivo

Definir como os itens do projeto ONGConecta são identificados, versionados, alterados, revisados e liberados, garantindo rastreabilidade, integridade e controle sobre todas as mudanças.

## 2. Escopo

Este plano se aplica a todo o conteúdo versionado neste repositório: código-fonte, documentação, configurações e automações.

## 3. Papéis e responsabilidades

| Papel | Pessoa | Responsabilidades |
|---|---|---|
| Gerente de Configuração / Dono | @joaobreisx | Mantém o plano, configura proteções de branch e ambientes, aprova deploy em produção |
| Revisor (par de revisão) | Colaborador com permissão Write | Revisa e aprova Pull Requests (acesso de escrita) |
| Desenvolvedores | Equipe | Criam branches, fazem commits e abrem Pull Requests |

## 4. Itens de configuração (ICs)

| IC | Local | Descrição |
|---|---|---|
| Código-fonte | `src/` | Implementação do sistema |
| Plano de GCS | `docs/plano-gcs.md` | Este documento |
| Evidências | `docs/evidencias/` | Prints que comprovam o cumprimento das regras |
| Documentação geral | `README.md` | Visão geral e instruções |
| Histórico de versões | `CHANGELOG.md` | Registro das alterações por versão |
| Modelo de PR | `.github/pull_request_template.md` | Padroniza as solicitações de mudança |
| Configurações do repositório | GitHub (Settings) | Proteção de branch, colaboradores e environments |

## 5. Estratégia de branches

- **`main`**: linha de base estável. **Protegida**: não aceita push direto.
- **`feature/<nome>`**: novas funcionalidades.
- **`fix/<nome>`**: correções de erro.
- **`docs/<nome>`**: alterações de documentação.

Toda branch nasce da `main` e volta para ela somente via Pull Request.

## 6. Padrão de commits

Baseado em *Conventional Commits*:

- `feat:` nova funcionalidade
- `fix:` correção de erro
- `docs:` documentação
- `refactor:` refatoração sem mudança de comportamento
- `chore:` tarefas de manutenção

Exemplo: `docs: adiciona evidência do push recusado`

## 7. Versionamento e baselines

Utiliza-se **Versionamento Semântico** (`MAJOR.MINOR.PATCH`):

- **MAJOR**: mudanças incompatíveis
- **MINOR**: novas funcionalidades compatíveis
- **PATCH**: correções

Cada versão liberada gera uma **tag** no Git (ex.: `v1.0.0`) e é registrada no `CHANGELOG.md`. A tag representa a baseline daquela versão.

## 8. Controle de mudanças

1. O desenvolvedor cria uma branch a partir da `main`.
2. Realiza as alterações e os commits.
3. Abre um Pull Request para a `main` usando o modelo padrão.
4. O revisor analisa e **aprova** (mínimo de 1 aprovação obrigatória).
5. Após a aprovação, é feito o merge.

### Proteção da branch `main`

Configurada em *Settings → Branches*:

- Pull Request obrigatório antes do merge
- Mínimo de 1 aprovação
- Regras aplicadas também a administradores (sem bypass)

**Evidência:** a tentativa de `git push` direto na `main` é recusada pelo GitHub. Ver `docs/evidencias/push-recusado.png`.

## 9. Ambientes

| Ambiente | Finalidade | Proteção |
|---|---|---|
| `staging` | Homologação e testes antes da liberação | Sem aprovação obrigatória |
| `production` | Versão em uso pelos usuários finais | **Revisor obrigatório: @joaobreisx** |

Configurados em *Settings → Environments*. Nenhum deploy chega em `production` sem a aprovação do responsável.

## 10. Auditoria e rastreabilidade

- Todo o histórico de mudanças fica registrado nos commits e Pull Requests.
- Cada PR registra quem alterou, quem revisou e quando houve o merge.
- As versões ficam identificadas por tags e pelo `CHANGELOG.md`.
