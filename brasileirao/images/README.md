# 📸 Imagens do README

Esta pasta guarda os gráficos que aparecem no `README.md` principal. Como os dados
ficam no BigQuery privado, os gráficos precisam ser **exportados por você** a partir
dos notebooks (rode no Colab e salve as figuras).

## Como exportar cada gráfico

No Colab, em cada célula de gráfico, adicione a linha abaixo **antes** do `plt.show()`:

```python
plt.savefig('nome_do_arquivo.png', dpi=150, bbox_inches='tight')
```

Depois baixe o `.png` (menu de arquivos do Colab → *Download*) e coloque nesta pasta.
Alternativa rápida: clique com o botão direito no gráfico já renderizado no Colab →
*Salvar imagem como…*

## Arquivos referenciados no README

| Arquivo | Notebook de origem | Gráfico |
|---|---|---|
| `02_boxplot_gols_por_ano.png` | `02_evolucao_ofensiva_e_consistencia` | Box-plot da evolução dos gols por temporada |
| `02_consistentes_x_ioios.png` | `02_evolucao_ofensiva_e_consistencia` | Top 5 consistentes × Top 5 "ioiô" |
| `03_correlacao_publico_pontos.png` | `03_fator_casa_e_publico` | Regressão público × pontos (Pearson) |
| `04_dominio_g4_regiao.png` | `04_raio_x_geografico` | Aparições no G4 por região |

> Sugestão: exporte também o gráfico do **Teste T** (`05`) e o do **Fator Casa ao longo dos anos**
> (`03`) — são ótimos para ilustrar posts de LinkedIn.
