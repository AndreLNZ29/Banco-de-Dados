# CineControl — Etapa 1

Projeto Final — Laboratório de Banco de Dados — 2026/2
Base: Documento de Visão, História de Usuário HU01 e roteiro da disciplina.

**SGBD:** MySQL 8.0+

## Conteúdo

| Arquivo | Descrição |
|---|---|
| `relatorio-etapa1.pdf` | Relatório completo — seções A1 a A5 + implementação/carga/consultas |
| `mer-conceitual.png` | Diagrama entidade-relacionamento (conceitual) |
| `mer-conceitual.drawio` | Fonte editável do diagrama (draw.io / app.diagrams.net) |
| `modelo-logico.pdf` | Modelo relacional (relações, PKs e FKs) |
| `dicionario-dados.pdf` | Dicionário de dados completo |
| `01_ddl.sql` | DDL — MySQL 8.0+ |
| `02_carga.sql` | Carga sintética de dados |
| `03_consultas.sql` | 15 consultas (básicas, junções/agregação e avançadas) |

## Ordem de execução

```
01_ddl.sql  →  02_carga.sql  →  03_consultas.sql
```

## Checklist antes da entrega

- [ ] Executar o DDL e a carga em uma base MySQL limpa
- [ ] Conferir as 15 consultas em `03_consultas.sql`
- [ ] Revisar as cardinalidades do diagrama conceitual
- [ ] Confirmar que os triggers de `filme_genero` (gênero principal único por filme) estão ativos

## Notas desta revisão

- Os três scripts SQL foram convertidos de PostgreSQL 14+ para **MySQL 8.0+** (ver detalhes no relatório,
  seção *Implementação, carga e consultas*).
- Um bug pré-existente na carga (`id_filme % 40` com apenas 39 filmes cadastrados) foi corrigido para `% 39`.
- Toda a cadeia DDL → carga → consultas foi validada de ponta a ponta em uma instância MySQL/MariaDB limpa.
