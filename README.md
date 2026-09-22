# Tech Challenge — Fase 2 | POSTECH Data Analytics

---

## 1. Identificação

| Campo | Valor |
|---|---|
| Turma | 2DTATBB |
| Grupo | 1 |
| Data de entrega | 10/10/2026 |

### Integrantes

| Nome completo | RM | E-mail |
|---|---|---|
| ELIZABETH APARECIDA DE CARVALHO E SILVA | RM377828 | elizabeth.carvalho@bb.com.br |
| GILBERTO DE SOUZA COSTA FILHO | RM377815 | gilberto.filho@bb.com.br |
| ISIDORO DUPP DA SILVA LEITE | RM377806 | dupp@bb.com.br |
| SILVIA JUNKO IWASHITA ALVARENGA| RM377768 | silvinhaji@yahoo.com.br |

---

## 2. Links da entrega


| Item | Link |
|---|---|
| Repositório | https://github.com/Ginkno/postech-tech-challenge-fase2-grupo1-12dtat |
| Vídeo executivo (≤ 5 min) | <!-- PREENCHER: YouTube não listado / Drive com acesso liberado --> |
| Apresentação | <!-- PREENCHER: link do arquivo em `docs/` ou Drive --> |


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

Existem 2 datasets usados nos notebooks:
1. Application record - contém as informações gerais do solicitante, tais como gênero, nível de escolaridade, renda, ocupação, etc)

| Campo | Valor |
|---|---|
| Fonte | [application_record.csv](https://www.kaggle.com/datasets/rikdifos/credit-card-approval-prediction/data?select=application_record.csv) |
| Linhas × colunas | 253877 x 18 |
| Período / versão | <!-- PREENCHER --> |
| Licença de uso | [CC0: Public Domain](https://creativecommons.org/publicdomain/zero/1.0/) |

Descrição das variáveis:

| Variável | Tipo | Descrição |
|---|---|---|
| ID | int64 | Número do cliente |
| CODE_GENDER | object  | Gênero |
| FLAG_OWN_CAR | object  | Tem algum carro? |
| FLAG_OWN_REALTY | object  | Existe alguma propriedade? |
| CNT_CHILDREN | int64 | Número de filhos |
| AMT_INCOME_TOTAL | float64 | Renda anual |
| NAME_INCOME_TYPE | object | Categoria de renda |
| NAME_EDUCATION_TYPE | object | Nível de escolaridade |
| NAME_FAMILY_STATUS | object | Estado civil |
| NAME_HOUSING_TYPE | object | Estilo de vida |
| DAYS_BIRTH | float64 | Aniversário - Conte regressivamente a partir do dia atual (0), -1 significa ontem. |
| DAYS_EMPLOYED | float64 |  Data de início do emprego - Conte regressivamente a partir do dia atual (0). Se positivo, significa que a pessoa está atualmente desempregada. |
| FLAG_MOBIL | float64 | Existe algum telefone celular? |
| FLAG_WORK_PHONE | float64 | Existe algum telefone de trabalho? |
| FLAG_PHONE | float64 | Tem algum telefone? |
| FLAG_EMAIL | float64 | Existe algum e-mail? |
| OCCUPATION_TYPE | object  | Ocupação |
| CNT_FAM_MEMBERS | float64 | Tamanho familiar |

2. Credit record - contém os registros de pagamentos dos empréstimos feitos pelos solicitantes.

| Campo | Valor |
|---|---|
| Fonte | [credit_record.csv](https://www.kaggle.com/datasets/rikdifos/credit-card-approval-prediction/data?select=credit_record.csv) |
| Linhas × colunas | 1048575 x 3 |
| Período / versão | <!-- PREENCHER --> |
| Licença de uso | [CC0: Public Domain](https://creativecommons.org/publicdomain/zero/1.0/) |

Descrição das variáveis:

| Variável | Tipo | Descrição |
|---|---|---|
| ID | int64 | Número do cliente |
| MONTHS_BALANCE | int64   | Mês recorde - O mês dos dados extraídos é o ponto de partida; retrocedendo, 0 representa o mês atual, -1 o mês anterior e assim por diante. |
| STATUS | object  | 0: 1 a 29 dias de atraso 1: 30 a 59 dias de atraso 2: 60 a 89 dias de atraso 3: 90 a 119 dias de atraso 4: 120 a 149 dias de atraso 5: Dívidas vencidas ou incobráveis, baixas contábeis por mais de 150 dias C: Quitado neste mês X: Sem empréstimo neste mês |
---

## 4. Como reproduzir

```bash
git clone https://github.com/Ginkno/postech-tech-challenge-fase2-grupo1-12dtat.git
cd postech-tech-challenge-fase2-grupo1-12dtat

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

| Tecnologia | Versão |
|---|---|
| pandas | 2.2.3 | 
| numpy | 2.1.3 |
| scikit-learn | 1.5.2 |
| matplotlib | 3.9.2 |
| seaborn | 0.13.2 |
| jupyter | 1.1.1 |
| joblib | 1.4.2 |
