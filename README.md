🎬 CineControl — Banco de Dados

Projeto de banco de dados do CineControl, desenvolvido para a Etapa 1 do projeto de Laboratório de Banco de Dados.

O sistema foi modelado para representar o funcionamento de um cinema, contemplando usuários, clientes, administradores, filmes, gêneros, atores, salas, assentos, sessões, reservas e histórico de situação dos filmes.

📌 Sobre o projeto

O CineControl utiliza um modelo relacional para organizar as informações necessárias ao gerenciamento de um cinema.

A Etapa 1 contempla:

Modelo Entidade-Relacionamento (MER);

Modelo lógico do banco;

DDL para criação do banco e das tabelas;

Carga de dados de teste;

Consultas SQL;

Restrições de integridade;

Índices;

Triggers;

Histórico temporal da situação dos filmes;

Documentação e dicionário de dados.

🛠️ Tecnologias

SGBD: MySQL 8.0+

Linguagem: SQL

Charset: utf8mb4

Engine: InnoDB

Modelagem: draw.io

Documentação: PDF e Markdown

🗂️ Estrutura do repositório

.
├── 01_ddl.sql
├── 02_carga.sql
├── 03_consultas.sql
├── mer-conceitual.drawio
├── mer-conceitual.png
├── modelo-logico.pdf
├── dicionario-dados.pdf
├── relatorio-etapa_1.pdf
└── README.md

Arquivos SQL

Arquivo

Descrição

01_ddl.sql

Criação do banco, tabelas, chaves, restrições, índices e triggers

02_carga.sql

Inserção dos dados de teste

03_consultas.sql

Consultas utilizadas para validar e explorar os dados

Documentação e modelagem

Arquivo

Descrição

mer-conceitual.drawio

Arquivo editável do Modelo Entidade-Relacionamento

mer-conceitual.png

Imagem do MER

modelo-logico.pdf

Modelo lógico do banco

dicionario-dados.pdf

Dicionário de dados

relatorio-etapa_1.pdf

Relatório da Etapa 1

🗄️ Modelo de dados

O banco cinecontrol é composto pelas seguintes tabelas principais:

usuario

cliente

administrador

genero

ator

filme

filme_genero

filme_ator

sala

assento

sessao

reserva

historico_situacao_filme

Principais relacionamentos

USUARIO
 ├── CLIENTE
 └── ADMINISTRADOR

FILME
 ├── FILME_GENERO ─── GENERO
 ├── FILME_ATOR ───── ATOR
 ├── SESSAO ───────── SALA
 │                     └── ASSENTO
 ├── RESERVA
 └── HISTORICO_SITUACAO_FILME

CLIENTE
 └── RESERVA

Relacionamentos N

O projeto possui relacionamentos muitos-para-muitos representados por tabelas associativas:

Filme ↔ Gênero: filme_genero

Filme ↔ Ator: filme_ator

A tabela filme_ator também registra o personagem interpretado e a ordem do crédito.

Entidade fraca

assento é modelada como uma entidade dependente de sala. Sua chave primária é composta por:

(id_sala, numero)

Dessa forma, o número do assento é identificado dentro de uma determinada sala.

Histórico temporal

A tabela historico_situacao_filme mantém o histórico de situações de cada filme, armazenando:

situação;

início do período;

fim do período;

sequência do registro.

🔐 Integridade e regras de negócio

O DDL implementa diversas regras para manter a consistência dos dados.

Chaves

São utilizadas:

chaves primárias (PRIMARY KEY);

chaves estrangeiras (FOREIGN KEY);

chaves únicas (UNIQUE);

chaves compostas.

Restrições CHECK

Entre as regras implementadas estão:

duração do filme maior que zero;

classificação do filme limitada aos valores definidos;

situação do filme limitada aos estados previstos;

capacidade da sala dentro do limite estabelecido;

preço da sessão não negativo;

quantidade de ingressos da reserva maior que zero;

situações válidas para reservas e sessões.

Triggers

Como o MySQL não possui índice único parcial da mesma forma que algumas implementações de PostgreSQL, foram utilizadas triggers para garantir que cada filme tenha no máximo um gênero principal.

São utilizadas:

trg_filme_genero_principal_ins

trg_filme_genero_principal_upd

📊 Dados de teste

O arquivo 02_carga.sql cria uma base de dados para testes, incluindo:

10 gêneros;

35 clientes;

5 administradores;

39 filmes;

40 atores;

10 salas;

20 assentos por sala;

120 sessões;

200 reservas;

registros de histórico de situação dos filmes.

Os dados são fictícios e foram criados para possibilitar a execução das consultas da Etapa 1.

🔎 Consultas SQL

O arquivo 03_consultas.sql contém consultas para diferentes situações do sistema.

Entre elas:

Filmes atualmente em cartaz;

Filmes com duração entre 100 e 120 minutos;

Filmes com determinadas palavras no título;

Sessões em salas específicas;

Filmes sem descrição;

Filmes e seus gêneros principais;

Clientes e quantidade de reservas;

Salas com mais de 10 sessões;

Próximas sessões;

Quantidade de ingressos reservados por sessão;

Clientes acima da média de reservas;

Filmes que possuem reservas confirmadas utilizando EXISTS;

Sessões com ocupação acima da média;

Clientes que reservaram mais de um filme;

Salas com menor disponibilidade média.

As consultas utilizam recursos como:

JOIN;

LEFT JOIN;

GROUP BY;

HAVING;

subconsultas;

EXISTS;

CASE;

funções de agregação;

ORDER BY;

LIMIT.

🚀 Como executar

1. Pré-requisitos

Tenha instalado:

MySQL 8.0 ou superior;

MySQL Workbench, DBeaver ou outro cliente SQL de sua preferência.

2. Criar o banco

Execute primeiro:

SOURCE 01_ddl.sql;

O script cria o banco:

cinecontrol

3. Inserir os dados

Depois execute:

SOURCE 02_carga.sql;

Esse script popula as tabelas com dados fictícios.

4. Executar as consultas

Por fim:

SOURCE 03_consultas.sql;

As consultas podem ser executadas individualmente para analisar os resultados.

Importante: o 01_ddl.sql contém DROP DATABASE IF EXISTS cinecontrol;. Portanto, a execução do script recria o banco e apaga uma versão anterior do banco cinecontrol.

⚙️ Compatibilidade

O projeto foi preparado para MySQL 8.0+.

Algumas construções foram adaptadas para o MySQL. Por exemplo:

geração de números feita por CTE recursiva;

uso de LIKE para buscas textuais;

triggers para controlar a existência de um único gênero principal por filme.

📁 Organização recomendada

Para utilizar o projeto em uma atividade acadêmica, recomenda-se executar os arquivos nesta ordem:

01_ddl.sql
      ↓
02_carga.sql
      ↓
03_consultas.sql

A documentação visual pode ser consultada antes ou durante a execução:

mer-conceitual.png
mer-conceitual.drawio
modelo-logico.pdf
dicionario-dados.pdf
relatorio-etapa_1.pdf

🎯 Objetivo da Etapa 1

A Etapa 1 tem como objetivo estruturar e implementar a base de dados do CineControl, partindo da modelagem conceitual e lógica até a criação das tabelas, inserção de dados e elaboração de consultas SQL.

O projeto busca demonstrar a aplicação de conceitos de banco de dados relacionais, incluindo:

modelagem de dados;

normalização e relacionamentos;

integridade referencial;

restrições de domínio;

consultas SQL;

índices;

triggers;

dados temporais;

carga e consulta de dados.

👥 Projeto acadêmico

Projeto: CineControl
Etapa: 1 — Banco de Dados
SGBD: MySQL 8.0+

📄 Licença

Este repositório faz parte de um projeto acadêmico. Caso seja necessário definir uma licença específica para distribuição do código, ela deve ser adicionada posteriormente ao projeto.
