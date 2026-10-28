# ONGConecta — Repositório de GCS

Repositório do projeto **ONGConecta**, utilizado na disciplina para aplicar práticas de **Gestão de Configuração de Software (GCS)**.

## Estrutura

```
.
├── .github/
│   └── pull_request_template.md   # modelo de Pull Request
├── docs/
│   ├── plano-gcs.md               # Plano de Gestão de Configuração
│   └── evidencias/                # prints de evidência (push recusado, PRs, etc.)
├── src/                           # código-fonte do projeto
├── CHANGELOG.md                   # histórico de versões
└── README.md
```

## Como contribuir

1. Crie uma branch a partir da `main`: `git checkout -b feature/minha-mudanca`
2. Faça commits seguindo o padrão do plano (`feat:`, `fix:`, `docs:`...)
3. Envie a branch e abra um Pull Request para a `main`
4. Aguarde a aprovação do revisor antes do merge

> Push direto na `main` é bloqueado. Toda mudança passa por Pull Request com revisão.

Consulte o [Plano de GCS](docs/plano-gcs.md) para os detalhes.
