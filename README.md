# Tech Challenge — Fase 2 | POSTECH Data Analytics

---

## 1. Identificação

| Campo | Valor |
|---|---|
| Turma | 2DTATBB |
| Grupo | <!-- PREENCHER: ex. Grupo 07 --> |
| Data de entrega | <!-- PREENCHER: DD/MM/AAAA --> |

### Integrantes

| Nome completo | RM | E-mail |
|---|---|---|
| ELIZABETH APARECIDA DE CARVALHO E SILVA | RM377828 | elizabeth.carvalho@bb.com.br |
| GILBERTO DE SOUZA COSTA FILHO | | gilberto.filho@bb.com.br |
| ISIDORO DUPP DA SILVA LEITE | | dupp@bb.com.br |
| SILVIA JUNKO IWASHITA ALVARENGA| | silvinhaji@yahoo.com.br |

---

## 2. Links da entrega


| Item | Link |
|---|---|
| Repositório | https://github.com/Ginkno/postech-tech-challenge-fase2-grupo1-12dtat |
| Vídeo executivo (≤ 5 min) | <!-- PREENCHER: YouTube não listado / Drive com acesso liberado --> |
| Apresentação | <!-- PREENCHER: link do arquivo em `docs/` ou Drive --> |

> ⚠️ Repositório privado ou inacessível **zera** toda a Dimensão 1 da rúbrica.
> Confira o acesso em uma janela anônima antes de enviar.

---

## 3. O problema

A concessão de cartão de crédito é uma das principais operações de instituições financeiras, permitindo a expansão da base de clientes e a geração de receita. No entanto, a concessão inadvertida de crédito a perfis com alto risco de inadimplência gera prejuízos diretos para a instituição, ao mesmo tempo em que a recusa indevida a bons pagadores reduz o potencial de faturamento e prejudica a experiência do cliente.

O desafio da instituição é avaliar com precisão o perfil financeiro e comportamental dos solicitantes (considerando atributos como renda, ocupação, estado civil e histórico profissional) para decidir de forma assertiva quem deve ter o pedido aprovado.

A análise tradicional de crédito baseada em regras manuais ou modelos estáticos costuma ser rígida, lenta e propensa a erros de viés ou desatualização diante de novas dinâmicas de mercado.

O uso de Machine Learning se justifica por:

Automação e Escala: Processar grandes volumes de solicitações em tempo real, reduzindo o tempo de resposta ao cliente.

Identificação de Padrões Complexos: Algoritmos de aprendizado supervisionado conseguem mapear relações não lineares e cruzamentos entre variáveis pessoais e financeiras que não seriam evidentes em análises convencionais.

Redução da Inadimplência: Aumentar a precisão na discriminação entre bons e maus pagadores, diminuindo o risco de default e os custos de cobrança.

Otimização da Decisão: Permitir o ajuste fino das métricas de aprovação para equilibrar o nível de risco aceitável com a taxa de conversão de novos clientes.

### Variável alvo

<!-- PREENCHER: qual é a variável alvo, como foi definida e — se houve binarização —
     qual limiar foi adotado e por quê. Justifique com base na distribuição das classes. -->

### Dataset

| Campo | Valor |
|---|---|
| Fonte | <!-- PREENCHER: URL --> |
| Linhas × colunas | <!-- PREENCHER --> |
| Período / versão | <!-- PREENCHER --> |
| Licença de uso | <!-- PREENCHER --> |

Descrição das variáveis:

| Variável | Tipo | Descrição |
|---|---|---|
| | | |

---

## 4. Como reproduzir

```bash
git clone <URL_DO_REPOSITORIO>
cd <NOME_DO_REPOSITORIO>

python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate

pip install -r requirements.txt
jupyter notebook
```

Baixe o dataset e coloque o arquivo bruto em `data/raw/` (os dados **não** são versionados —
veja `data/README.md`).

Depois execute os notebooks nesta ordem:

| # | Notebook | O que faz |
|---|---|---|
| 1 | `notebooks/01_eda.ipynb` | Análise exploratória |
| 2 | `notebooks/02_preprocessamento.ipynb` | Limpeza, escala e feature engineering |
| 3 | `notebooks/03_modelagem.ipynb` | Treino e comparação dos modelos |
| 4 | `notebooks/04_avaliacao.ipynb` | Métricas, importância de variáveis e conclusões |

**Semente fixa:** `RANDOM_STATE = 42`, declarada na primeira célula de cada notebook.
Rodar os notebooks na ordem acima, a partir de um ambiente limpo, deve reproduzir
exatamente os números da seção 5.

---

## 5. Resultados

| Modelo | Acurácia | Precisão | Recall | F1 | AUC-ROC |
|---|---|---|---|---|---|
| <!-- PREENCHER --> | | | | | |
| | | | | | |

**Modelo escolhido:** <!-- PREENCHER --> — <!-- PREENCHER: por quê. -->

**Métricas priorizadas:** <!-- PREENCHER: justifique a escolha considerando o
     desbalanceamento de classes e o custo de cada tipo de erro no contexto do negócio. -->

---

## 6. Principais conclusões

<!-- PREENCHER: 3 a 5 conclusões em linguagem de negócio.
     Inclua quais variáveis mais influenciam o resultado e o que isso significa
     na prática para quem vai usar o modelo. -->

1.
2.
3.

### Limitações e próximos passos

<!-- PREENCHER -->

---

## 7. Estrutura do repositório

```
.
├── data/          dados brutos (raw) e tratados (processed) — não versionados
├── notebooks/     análise em ordem numerada
└── docs/          apresentação executiva
```

Detalhes e convenções em [`ESTRUTURA.md`](ESTRUTURA.md).
Antes de enviar, percorra o [`CHECKLIST.md`](CHECKLIST.md).

---

## 8. Tecnologias

<!-- PREENCHER: Python 3.11, pandas, scikit-learn, ... -->
