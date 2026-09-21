# 🎬 CineControl — Banco de Dados

Projeto acadêmico de banco de dados para gerenciamento de um cinema, desenvolvido na **Etapa 1**.

## 📌 Sobre

O CineControl organiza informações de:

- Usuários, clientes e administradores;
- Filmes, gêneros e atores;
- Salas e assentos;
- Sessões e reservas;
- Histórico da situação dos filmes.

## 🛠️ Tecnologias

- **MySQL 8.0+**
- **SQL**
- **draw.io** para modelagem

## 📂 Arquivos principais

| Arquivo | Descrição |
|---|---|
| `01_ddl.sql` | Criação do banco, tabelas, restrições, índices e triggers |
| `02_carga.sql` | Inserção dos dados de teste |
| `03_consultas.sql` | Consultas SQL |
| `mer-conceitual.drawio` | Modelo Entidade-Relacionamento |
| `mer-conceitual.png` | Imagem do MER |
| `modelo-logico.pdf` | Modelo lógico |
| `dicionario-dados.pdf` | Dicionário de dados |
| `relatorio-etapa_1.pdf` | Relatório da etapa |

## 🗄️ Modelo de dados

Principais entidades:

`USUARIO`, `CLIENTE`, `ADMINISTRADOR`, `FILME`, `GENERO`, `ATOR`, `SALA`, `ASSENTO`, `SESSAO` e `RESERVA`.

Os relacionamentos N:N entre **filmes e gêneros** e **filmes e atores** são representados por tabelas associativas.

O banco também possui histórico da situação dos filmes e regras de integridade implementadas por restrições e triggers.

## 🚀 Como executar

Execute os scripts nesta ordem:

```text
01_ddl.sql
    ↓
02_carga.sql
    ↓
03_consultas.sql
```

O projeto é compatível com **MySQL 8.0+**.

> **Atenção:** o `01_ddl.sql` recria o banco `cinecontrol`, removendo uma versão anterior caso exista.

## 🎯 Objetivo

Aplicar conceitos de modelagem e implementação de bancos relacionais, incluindo entidades, relacionamentos, integridade referencial, consultas SQL, índices, triggers e dados de teste.

## 👥 Projeto

**CineControl — Etapa 1 | Laboratório de Banco de Dados**
