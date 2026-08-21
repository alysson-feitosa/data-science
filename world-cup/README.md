# 🌍⚽ O futebol sul-americano ficou para trás? — Copa do Mundo 2022

> Uma análise descritiva de dados para testar, com números, a famosa frase de **Kylian Mbappé** sobre o futebol da América do Sul.

<p align="left">
  <img src="https://img.shields.io/badge/Python-3.12-blue?logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Pandas-Data_Analysis-150458?logo=pandas&logoColor=white" alt="Pandas">
  <img src="https://img.shields.io/badge/Fonte-Kaggle-20BEFF?logo=kaggle&logoColor=white" alt="Kaggle">
</p>

---

## 📌 Contexto

O ponto de partida foi esta declaração de Mbappé:

> *"Na América do Sul o futebol não é tão avançado quanto na Europa. E é por isso que, quando você olha para as últimas Copas, sempre são os europeus que ganham."*

**Objetivo:** usar os dados das partidas da **Copa do Mundo de 2022** para *provar* ou *desmentir* essa tese — comparando o desempenho técnico de cada continente e o resultado dos confrontos diretos.

---

## 📊 Os dados

- **Fonte:** [Kaggle — FIFA World Cup 2022 Match Data](https://www.kaggle.com/datasets/swaptr/fifa-world-cup-2022-match-data)
- **Formato:** planilha Excel (`partidas.xlsx`) com estatísticas detalhadas de cada partida (placar, *expected goals*, posse, chutes no alvo, desarmes, passes, disputas aéreas, etc.).
- O **dicionário de dados** completo, descrevendo cada variável, está documentado no próprio notebook.

> ⚠️ Os dados brutos não são versionados neste repositório. Baixe o dataset na fonte acima para reproduzir a análise.

---

## 🛠️ Metodologia

Análise 100% em **Python + Pandas**, cobrindo várias etapas de tratamento e modelagem de dados:

1. **Enriquecimento** — criação da coluna de **continente** de cada seleção a partir de um dicionário (CONMEBOL, UEFA, etc.).
2. **Manipulação de strings (regex)** — extração dos gols a partir do placar em texto (ex.: `"2–0"`, `"(4) 3–3 (2)"`).
   > 🐛 *Caso real de depuração documentado no notebook:* o separador do placar era um **en-dash** (`–`), diferente do hífen comum (`-`), o que quebrava a expressão regular e retornava gols como `NaN`.
3. **Reestruturação (reshape)** — "empilhamento" dos dados para ter **uma linha por time** (e não por partida), facilitando o cálculo de médias por continente.
4. **Agregação** — `groupby('continent')` com médias das principais métricas.
5. **Confronto direto** — filtro (máscara booleana) isolando apenas os jogos **Europa × América do Sul** e apuração do placar geral.

**Conceitos aplicados:** dicionários, expressões regulares, `apply`, reshape de DataFrames, `groupby`, filtros com máscaras booleanas.

---

## 💡 Principais achados

**Médias por continente na Copa 2022:**

| Continente | Gols | xG (Expected Goals) | Chutes no alvo | Posse (%) |
|---|:---:|:---:|:---:|:---:|
| 🌎 **América do Sul** | 1,61 | **19,22** | **5,61** | 54,9 |
| 🌍 **Europa** | 1,61 | 14,57 | 3,86 | 55,2 |

> A América do Sul teve **xG e chutes no alvo bem superiores** — ou seja, gerou mais e melhores chances de gol.

**Confrontos diretos Europa × América do Sul (9 jogos):**

| Resultado | Vitórias |
|---|:---:|
| 🌎 América do Sul | **4** |
| 🤝 Empates (inclui decisões por pênaltis) | 4 |
| 🌍 Europa | 1 |

### 🎯 Conclusão

Olhando para os dados da Copa de 2022, a tese de Mbappé **não se sustenta**: no confronto direto, a América do Sul venceu mais (4 × 1) e, nas estatísticas de criação de jogo (xG e finalizações no alvo), esteve à frente da Europa. Os números contam uma história bem diferente da frase. ⚽📉

---

## ▶️ Como reproduzir

```bash
git clone https://github.com/alysson-feitosa/data-science.git
cd data-science/world-cup
pip install pandas openpyxl jupyter
jupyter notebook notebooks/mbappe_vs_realidade_dos_dados.ipynb
```
Baixe o `partidas.xlsx` a partir do [dataset do Kaggle](https://www.kaggle.com/datasets/swaptr/fifa-world-cup-2022-match-data) e coloque-o na mesma pasta do notebook.

---

## 👤 Autor

**Alysson Leonardo**
🔗 [LinkedIn](https://www.linkedin.com/in/alyssonleonardo/) • 💻 [GitHub](https://github.com/alysson-feitosa)
