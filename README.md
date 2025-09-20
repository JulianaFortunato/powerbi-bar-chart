# Power BI - Gráfico de Barras Arredondadas

Este repositório contém um exemplo de **gráfico de barras arredondadas** criado no **Power BI** usando o **visual Deneb**.

---

## 📊 Visualização
Exemplo do gráfico criado no Power BI:

![Exemplo do Gráfico](https://github.com/JulianaFortunato/powerbi-bar-chart/blob/main/bar_chart.png)

---

## ✅ Campos obrigatórios
Para que o código JSON funcione corretamente, o dataset precisa ter **exatamente estes nomes de campo**:

- **`categorias`** → texto (nominal)  
- **`valores`** → número (quantitativo)  

⚠️ Se no seu modelo as colunas tiverem nomes diferentes (ex.: `Categoria`, `Valor`), você deve:  
1. Renomear no Power Query/Model para `categorias` e `valores`, **ou**  
2. Editar o JSON substituindo os nomes dos campos.

> Observação: o Deneb cria automaticamente um campo de destaque com o sufixo `__highlight`.  
> No nosso caso, isso gera `valores__highlight`.

## 📄 Código JSON usado no Deneb
```json
{
  "$schema": "https://vega.github.io/schema/vega-lite/v5.json",
  "data": { "name": "dataset" },
  "height": { "step": 20 },

  "encoding": {
    "y": {
      "field": "categorias",
      "type": "nominal",
      "sort": {
        "field": "valores",
        "op": "sum",
        "order": "descending"
      },
      "axis": {
        "grid": false,
        "domain": false,
        "tickSize": 0,
        "title": null,
        "labelPadding": 10,
        "labelFontSize": 12
      }
    }
  },

  "layer": [
    {
      "description": "Barras opacas (base)",
      "mark": {
        "type": "bar",
        "cornerRadius": 6,
        "color": "#1565C0",
        "opacity": 0.3
      },
      "encoding": {
        "x": {
          "field": "valores",
          "type": "quantitative",
          "axis": {
            "values": [],
            "ticks": false,
            "labels": false,
            "title": null
          }
        }
      }
    },
    {
      "description": "Barras com highlight",
      "mark": {
        "type": "bar",
        "cornerRadius": 6,
        "color": "#1565C0"
      },
      "encoding": {
        "x": {
          "field": "valores__highlight",
          "type": "quantitative",
          "axis": {
            "values": [],
            "ticks": false,
            "labels": false,
            "title": null
          }
        },
        "opacity": {
          "condition": {
            "test": { "field": "__selected__", "equal": "off" },
            "value": 0
          },
          "value": 1
        }
      }
    },
    {
      "description": "Texto do valor nas barras com highlight",
      "mark": {
        "type": "text",
        "align": "left",
        "baseline": "middle",
        "dx": 6,
        "font": "Segoe UI"
      },
      "encoding": {
        "x": {
          "field": "valores__highlight",
          "type": "quantitative",
          "axis": {
            "values": [],
            "ticks": false,
            "labels": false,
            "title": null
          }
        },
        "text": { "field": "valores__highlight", "type": "quantitative", "format": ",.0f" },
        "opacity": {
          "condition": {
            "test": { "field": "__selected__", "equal": "off" },
            "value": 0
          },
          "value": 1
        }
      }
    }
  ],

  "config": {
    "view": { "stroke": null },
    "axis": {
      "grid": false,
      "domain": false,
      "tickSize": 0,
      "labelFont": "Segoe UI",
      "titleFont": "Segoe UI"
    },
    "legend": {
      "labelFont": "Segoe UI",
      "titleFont": "Segoe UI"
    },
    "header": {
      "labelFont": "Segoe UI",
      "titleFont": "Segoe UI"
    }
  }
}
```
---

## 📝 Como usar
1. Abra o Power BI Desktop.  
2. Importe o visual **Deneb** do marketplace.  
3. Copie e cole o código JSON acima no editor do Deneb.
4. Certifique-se de que as seguintes opções estejam **marcadas** na aba de settings:
   - `Expose cross-highlight values for measures`
   - `Expose cross-filtering values for dataset rows`
5. Substitua o dataset de exemplo pelo seu conjunto de dados.  

---

## 📂 Arquivos disponíveis
- `bar_chart.png` → Print do gráfico  
- `grafico_arredondado.pbix` → Relatório Power BI com o visual pronto  

---

## 🔗 Redes
👉 Me acompanhe também no [LinkedIn](https://www.linkedin.com/in/juliana-fortunato-006b56190/)  

---

#PowerBI #DataVisualization #DataViz #DashboardDesign #DesignDeDashboard #BusinessIntelligence #AnaliseDeDados #DataAnalytics 
