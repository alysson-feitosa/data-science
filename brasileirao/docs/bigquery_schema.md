# 🗃️ Dicionário de Dados — BigQuery

Projeto: `data-science-brasileirao` · Dataset: `brasileirao_dataset`

As tabelas ficam em um projeto **privado** do Google BigQuery e não são versionadas neste repositório. Este documento descreve a estrutura para que qualquer pessoa possa recriar as tabelas no próprio ambiente a partir das fontes públicas (Kaggle) citadas no [README](../README.md).

---

## `dados_brazilian_league`
Classificação final de cada time por temporada (a base analítica principal).

| Coluna | Tipo | Descrição |
|---|---|---|
| `season` | INTEGER | Ano/edição do campeonato. |
| `place` | INTEGER | Posição final na tabela (1 = campeão). |
| `team` | STRING | Nome do clube. |
| `points` | INTEGER | Pontos conquistados na temporada. |
| `goals` | INTEGER | Gols marcados. |
| `goals_taken` | INTEGER | Gols sofridos. |

> Colunas adicionais de classificação (vitórias, empates, derrotas etc.) podem existir na base conforme a fonte original.

---

## `dados_matches`
Resultado de cada partida individual do campeonato.

| Coluna | Tipo | Descrição |
|---|---|---|
| `date` | STRING | Data da partida (`dd/mm/aaaa`). |
| `hour` | STRING | Horário da partida. |
| `home_team` | STRING | Time mandante. |
| `score` | STRING | Placar no formato `"MxV"` (ex.: `"2x1"`). |
| `away_team` | STRING | Time visitante. |

**Colunas derivadas nos notebooks:** `home_team_score`, `away_team_score` (split de `score`), `total_gols`, `ano`.

---

## `dados_public_matches`
Média de público por time e temporada.

| Coluna | Tipo | Descrição |
|---|---|---|
| `year` | INTEGER | Ano da temporada. |
| `team` | STRING | Nome do clube. |
| `avg_attendance` | INTEGER | Média de público pagante/presente. |

> Observação: **2020 e 2021 não têm público** nos estádios (pandemia de COVID-19).

---

## `dados_teams`
Cadastro geográfico dos clubes (usado no raio-X regional).

| Coluna | Tipo | Descrição |
|---|---|---|
| `team` | STRING | Nome do clube (chave de junção). |
| `state` | STRING | Unidade federativa (UF) do clube. |
| `region` | STRING | Região do Brasil (Sudeste, Sul, Nordeste, etc.). |

---

## 🔗 Junções mais usadas

| Objetivo | Junção |
|---|---|
| Público × desempenho | `dados_brazilian_league` ⨝ `dados_public_matches` em `(season = year, team)` |
| Raio-X geográfico | `dados_brazilian_league` ⨝ `dados_teams` em `team` |
| Confronto regional | `dados_matches` ⨝ `dados_teams` (duas vezes: mandante e visitante) |
