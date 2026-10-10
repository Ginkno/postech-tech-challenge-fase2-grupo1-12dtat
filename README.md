# Tech Challenge — Fase 2 | POSTECH Data Analytics

---

## 1. Identificação

| Campo | Valor |
| --- | --- |
| Turma | 2DTATBB |
| Grupo | 1 |
| Data de entrega | 10/10/2026 |

### Integrantes

| Nome completo | RM | E-mail |
| --- | --- | --- |
| ELIZABETH APARECIDA DE CARVALHO E SILVA | RM377828 | <elizabeth.carvalho@bb.com.br> |
| GILBERTO DE SOUZA COSTA FILHO | RM377815 | <gilberto.filho@bb.com.br> |
| ISIDORO DUPP DA SILVA LEITE | RM377806 | <dupp@bb.com.br> |
| SILVIA JUNKO IWASHITA ALVARENGA | RM377768 | <silvinhaji@yahoo.com.br> |

---

## 2. Links da entrega

| Item | Link |
| --- | --- |
| Repositório | <https://github.com/Ginkno/postech-tech-challenge-fase2-grupo1-12dtat> |
| Vídeo executivo (≤ 5 min) | https://www.youtube.com/watch?v=Jn4iVuvQ6WU |
| Apresentação | https://github.com/Ginkno/postech-tech-challenge-fase2-grupo1-12dtat/blob/main/docs/apresentacao_executiva.pdf |

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

Definição da Variável Alvo: IS_BAD_PAYER

A variável alvo IS_BAD_PAYER foi definida para identificar clientes que apresentaram um atraso de 60 dias ou mais (ou seja, STATUS igual ou superior a 2) em seu histórico de crédito completo.

A utilização do histórico completo permite mapear de forma fidedigna o perfil comportamental de risco de crédito do cliente.

IS_BAD_PAYER = 1 (Mau Pagador): Se o cliente possui qualquer ocorrência de STATUS '2', '3', '4' ou '5' (atraso de 60 dias ou mais grave).

IS_BAD_PAYER = 0 (Bom Pagador): Caso contrário. Esta lógica foca na gravidade do atraso, estabelecendo uma clara diferenciação entre clientes com desvios pontuais e clientes com atrasos severos no histórico.

### Dataset

Existem 2 datasets usados nos notebooks:

1. Application record - contém as informações gerais do solicitante, tais como gênero, nível de escolaridade, renda, ocupação, etc

| Campo | Valor |
| --- | --- |
| Fonte | [application_record.csv](https://www.kaggle.com/datasets/rikdifos/credit-card-approval-prediction/data?select=application_record.csv) |
| Linhas × colunas | 253877 x 18 |
| Licença de uso | [CC0: Public Domain](https://creativecommons.org/publicdomain/zero/1.0/) |

Descrição das variáveis:

| Variável | Tipo | Descrição |
| --- | --- | --- |
| ID | int64 | Número do cliente |
| CODE_GENDER | object | Gênero |
| FLAG_OWN_CAR | object | Tem algum carro? |
| FLAG_OWN_REALTY | object | Existe alguma propriedade? |
| CNT_CHILDREN | int64 | Número de filhos |
| AMT_INCOME_TOTAL | float64 | Renda anual |
| NAME_INCOME_TYPE | object | Categoria de renda |
| NAME_EDUCATION_TYPE | object | Nível de escolaridade |
| NAME_FAMILY_STATUS | object | Estado civil |
| NAME_HOUSING_TYPE | object | Estilo de vida |
| DAYS_BIRTH | float64 | Aniversário - Conte regressivamente a partir do dia atual (0), -1 significa ontem. |
| DAYS_EMPLOYED | float64 | Data de início do emprego - Conte regressivamente a partir do dia atual (0). Se positivo, significa que a pessoa está atualmente desempregada. |
| FLAG_MOBIL | float64 | Existe algum telefone celular? |
| FLAG_WORK_PHONE | float64 | Existe algum telefone de trabalho? |
| FLAG_PHONE | float64 | Tem algum telefone? |
| FLAG_EMAIL | float64 | Existe algum e-mail? |
| OCCUPATION_TYPE | object | Ocupação |
| CNT_FAM_MEMBERS | float64 | Tamanho familiar |

2.Credit record - contém os registros de pagamentos dos empréstimos feitos pelos solicitantes.

| Campo | Valor |
| --- | --- |
| Fonte | [credit_record.csv](https://www.kaggle.com/datasets/rikdifos/credit-card-approval-prediction/data?select=credit_record.csv) |
| Linhas × colunas | 1048575 x 3 |
| Licença de uso | [CC0: Public Domain](https://creativecommons.org/publicdomain/zero/1.0/) |

Descrição das variáveis:

| Variável | Tipo | Descrição |
| --- | --- | --- |
| ID | int64 | Número do cliente |
| MONTHS_BALANCE | int64 | Mês recorde - O mês dos dados extraídos é o ponto de partida; retrocedendo, 0 representa o mês atual, -1 o mês anterior e assim por diante. |
| STATUS | object | 0: 1 a 29 dias de atraso 1: 30 a 59 dias de atraso 2: 60 a 89 dias de atraso 3: 90 a 119 dias de atraso 4: 120 a 149 dias de atraso 5: Dívidas vencidas ou incobráveis, baixas contábeis por mais de 150 dias C: Quitado neste mês X: Sem empréstimo neste mês |

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
| --- | --- | --- |
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
| --- | --- | --- | --- | --- | --- |
| XGBoost | 94,02% |  6,09% | 16,12% | 8,81% | 57,76% |
| Random Forest | 97,99% | 17,62% | 2,39% | 3,93% | 57,32% |
| Lightgbm | 88,33% |  3,43% | 21,35% | 5,90% | 56,57% |

**Modelo escolhido:** XGBoost — melhor performance de F1, sustentando por um bom Recall e a melhor relação de Precision

**Métricas priorizadas:** 
1. As métricas priorizadas para a tomada de decisão e avaliação dos modelos foram F1-Score, Precision (Precisão), Recall (Revocação) e ROC-AUC.

2. Justificativa pela Desconsideração da Acurácia (Desbalanceamento de Classes)
A métrica de Acurácia foi descartada como indicador principal devido ao severo desbalanceamento de classes na base de dados (onde a vasta maioria dos clientes é de bons pagadores e apenas uma pequena fração é de maus pagadores).

Em cenários assim, a acurácia gera uma falsa sensação de alto desempenho (um modelo ingênuo que aprovasse 100% dos clientes atingiria ~96% de acurácia, mas falharia completamente em identificar os maus pagadores).

Por isso, utilizar o F1-Score (média harmônica entre Precision e Recall) e o ROC-AUC garante uma medição equilibrada do real poder de discriminação do modelo sobre a classe minoritária.

3. Impacto Financeiro e Custo dos Erros no Negócio
Falso Negativo (O Erro Mais Caro):

O que é: O modelo classifica um mau pagador como bom pagador.

Impacto no Negócio: A instituição concede crédito a um cliente inadimplente, gerando perda financeira direta (prejuízo/calote) e aumento do risco da carteira. É o erro prioritário a ser minimizado na concessão de crédito.

Falso Positivo:

O que é: O modelo classifica um bom pagador como mau pagador.

Impacto no Negócio: Gera recusa indevida de crédito, resultando em custo de oportunidade de vendas, potencial insatisfação e atrito comercial com um cliente legítimo. Embora relevante para o crescimento comercial, seu custo imediato é menor do que absorver a inadimplência direta de um falso negativo.

---

## 6. Principais conclusões

1. As 3 variáveis cadastrais que mais direcionam a decisão do modelo
As variáveis de maior relevância no modelo foram:

Condição de Aposentado/Pensionista (NAME_INCOME_TYPE_Pensioner): É a variável com maior peso, indicando que o perfil de renda fixa garantida exige uma segmentação de risco diferenciada.

Morar com os Pais (NAME_HOUSING_TYPE_With parents): O segundo maior sinalizador, identificando perfil de dependência financeira ou público jovem em início de carreira.

Ocupação Desconhecida/Não Informada (OCCUPATION_TYPE_Unknown): A ausência de dados profissionais informados no cadastro correlaciona-se fortemente com maior nível de risco.

2. O modelo identifica a ponta de risco, mas não deve rodar em "piloto automático"
Na prática: Das métricas do teste, o modelo gerou 18 inadimplentes bloqueados, mas deixou passar 94 inadimplentes (83,9% de falsos negativos).

O que isso significa: O modelo atual atua como um filtro preliminar, mas não deve aprovar ou reprovar limites de forma 100% autônoma sem regras de negócio complementares ou análise humana.

3. Estratégia de "Limite Inicial Reduzido" para mitigar a inadimplência passante
Na prática: Para os clientes aprovados pelo modelo, a instituição financeira deve adotar a concessão de limites de crédito iniciais baixos e progressivos.

O que isso significa: Conforme o cliente demonstra um histórico real de pagamento em meses subsequentes, o limite é ampliado gradualmente. Essa estratégia mitiga o prejuízo financeiro causado pelos inadimplentes que o modelo não conseguiu barrar na entrada.

4. Redução da fricção comercial para resgatar bons clientes
Na prática: Ao aplicar o corte de risco, o modelo acabou bloqueando 388 bons pagadores para conseguir capturar os maus pagadores.

O que isso significa: Para não perder essas oportunidades de vendas e não frustrar clientes legítimos, a área comercial deve implementar alçadas de contestação rápida ou pedir comprovantes simplificados para reavaliar esses casos e liberar o crédito de forma segura.

5. Ações prioritárias: higienização cadastral e inteligência transacional
Na prática: Como a falta de preenchimento do campo de ocupação teve grande impacto nas previsões, a prioridade da equipe de negócio deve ser a higienização do cadastro no momento do onboarding.

O que isso significa: Além de exigir cadastros mais completos na entrada, o próximo passo para amadurecer o modelo é incorporar dados do comportamento transacional interno do cliente (como uso da conta corrente, histórico de pagamentos e saldo em conta) para além dos dados estáticos de cadastro.

### Limitações 

1. Elevada Taxa de Falsos Negativos (Vazamento de Risco): O modelo deixa de identificar 94 dos 112 inadimplentes no conjunto de teste (taxa de vazamento de 83,9%). Esses falsos negativos representam a principal limitação e a maior fonte de risco financeiro para a carteira.
2. Geração de Falsos Positivos (Fricção Comercial): Para conseguir bloquear 18 inadimplentes, o modelo reprova indevidamente 388 bons pagadores, o que gera atrito comercial e potencial perda de novos clientes legítimos.
3. Baixa Capacidade Discriminativa Geral: O poder de separação entre bons e maus pagadores ficou em ROC-AUC de 59,42%, o que indica um desempenho apenas ligeiramente superior ao de um classificador aleatório (50%).
4. Alta Dependência de Dados Omissos: O modelo atribuiu alto peso preditivo à ausência de informações cadastrais (como a variável OCCUPATION_TYPE_Unknown), evidenciando a fragilidade da base de dados estática atual.

### Próximos passos
  1.	Higienização e Enriquecimento Cadastral (Onboarding): Aprimorar os processos de coleta de dados no momento do cadastro para eliminar campos omissos (especialmente profissão/ocupação).
  2.	Inclusão de Dados Transacionais Internos: Evoluir a modelagem integrando variáveis de comportamento financeiro dinâmico (movimentação de conta corrente, histórico de pagamentos e uso de outros produtos do banco) em vez de depender exclusivamente de dados cadastrais estáticos.
  3.	Adopção de Estratégias de Concessão Progressiva de Crédito: Enquanto o modelo é aprimorado, implementar uma política de limites iniciais reduzidos e evolução progressiva conforme o histórico de pagamento do cliente.
  4.	Criação de Canais de Contestação Comercial: Estabelecer fluxos de reanálise rápida (com solicitação simplificada de comprovantes) para resgatar os bons clientes bloqueados indevidamente pelo modelo.

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
| --- | --- |
| pandas | 2.2.3 |
| numpy | 2.1.3 |
| scikit-learn | 1.5.2 |
| matplotlib | 3.9.2 |
| seaborn | 0.13.2 |
| jupyter | 1.1.1 |
| joblib | 1.4.2 |
| imbalanced-learn | 0.13.0 |
| lightgbm | 4.5.0 |
| xgboost | 2.1.3 |
