# Relatório Metodológico: Projeto 4 - Análise Micro (Perfil Sociodemográfico)

Este relatório descreve detalhadamente a metodologia aplicada no **Projeto 4**, conduzido no contexto do TCC de Mara Oliveira. O objetivo principal do estudo foi analisar a probabilidade de sucesso (Taxa de Conclusão) dos alunos da Rede Federal de Ensino, estruturada a partir de seus perfis sociodemográficos (Cor/Raça, Renda, Faixa Etária e Sexo).

---

## 1. Origem e Preparação dos Dados

A análise foi fundamentada exclusivamente no conjunto de dados consolidado: Dados Acadêmicos - Classificação Racial, Renda, Sexo e Faixa Etária da plataforma Nilo Peçanha, aqui denominado de `Candidatos.csv`.

Antes de iniciar as análises estatísticas, os dados passaram por um rigoroso processo de preparação e limpeza:

- **Padronização:** Foram removidos espaços em branco desnecessários (trailing/leading spaces) dos nomes das colunas e dos valores textuais, garantindo consistência na manipulação das strings.
- **Filtro de Instituição:** O estudo focou especificamente na Rede Federal. Para isso, os dados foram filtrados para incluir apenas as instituições cujos nomes iniciavam com "IF" (Institutos Federais).
- **Tratamento de Dados Faltantes e Ruídos:** Para evitar que a ausência de declaração distorcesse as análises de perfis demográficos específicos, foram excluídos todos os registros em que as variáveis de interesse (`CorRaca`, `RendaFamiliar`, `FaixaEtaria` e `Sexo`) constavam como `'S/I'` (Sem Informação) ou `'Não Declarada'`.

---

## 2. Construção da Variável de Desfecho e Unidade de Análise

A principal métrica de sucesso definida para o projeto foi a **Taxa de Conclusão**.

### 2.1 Agrupamento por Perfis
Em vez de analisar os alunos puramente como indivíduos desagregados numa primeira etapa, a metodologia agrupou a base para criar uma "Unidade de Análise" baseada no **Perfil Completo** (interseção exata entre `Cor/Raça`, `Renda Familiar`, `Faixa Etária` e `Sexo`).

Para garantir robustez e evitar vieses provocados por amostras ínfimas (outliers estatísticos), foi estabelecido um **corte amostral**: apenas perfis que historicamente possuíam mais de 100 alunos ingressantes na Rede Federal foram mantidos para as etapas de ranqueamento.

### 2.2 Cálculo da Taxa de Conclusão
A taxa foi calculada dividindo o total de concluintes pelo total de ingressantes de cada perfil e multiplicando por 100, gerando um indicador percentual comparável de eficácia/sucesso.

---

## 3. Etapas e Escolhas de Análises Analíticas

A metodologia seguiu uma trilha lógica de aprofundamento: partiu da visualização descritiva isolada, avançou para a interseccionalidade e concluiu com validação estatística e modelagem multidimensional.

### 3.1 Análises Descritivas e Comparações de Extremos
- **Ranking de Perfis (Top 10 vs Bottom 10):** A primeira análise ordenou os perfis completos para identificar visualmente quais contextos sociodemográficos apresentam as maiores taxas de sucesso e quais figuram na base da pirâmide (maior risco de retenção/evasão). O uso da média geral da rede serviu como linha de base (baseline) para comparação.
- **Análises Isoladas:** Para compreender o peso individual de cada fator, foram gerados gráficos de barras que isolavam o impacto exclusivo da **Renda**, da **Cor/Raça** e da **Idade** sobre a Taxa de Conclusão.

### 3.2 Interseccionalidade Visual
- **Mapa de Calor (Heatmap) Cor vs. Renda:** Foi aplicado para avaliar estruturalmente como a Renda Familiar e a Cor/Raça se afetam mutuamente. Esta técnica permite observar se o aumento da renda atenua discrepâncias raciais ou se a barreira racial prevalece independente da classe social.

### 3.3 Validação de Hipóteses (Teste de Significância)
Para garantir que as discrepâncias observadas nos gráficos não eram meras flutuações aleatórias da amostra, introduziu-se o rigor estatístico.
- **Teste Qui-Quadrado de Independência:** Foi aplicado individualmente às variáveis sociodemográficas contra a situação do aluno (Concluinte vs Não Concluinte). A utilização deste teste não-paramétrico foi a escolha ideal, uma vez que o objetivo era avaliar a associação entre variáveis categóricas, baseando-se nas frequências observadas e esperadas de evasão/conclusão.

### 3.4 Análise Multidimensional (Análise de Correspondência Múltipla - ACM)
O ápice metodológico do projeto foi a aplicação da ACM, técnica essencial para explorar padrões simultâneos em múltiplas variáveis categóricas.

- **Preparação dos Dados:** A base agrupada foi "desdobrada" novamente em registros individuais simulados para permitir que o algoritmo da ACM calculasse corretamente as distâncias geométricas entre as categorias (quem conclui e quem não conclui).
- **Correção de Benzécri:** Uma escolha metodológica avançada e crucial. Na ACM clássica, a inércia (variância) explicada pelas primeiras dimensões costuma ser matematicamente subestimada devido à expansão da matriz em variáveis indicadoras (dummies). A Correção de Benzécri ajustou os autovalores, entregando ao estudo um percentual realista e cientificamente mais rigoroso da variância explicada no relatório de TCC.
- **Interpretação via Biplot:** O gráfico gerado pela ACM permitiu identificar, em um plano cartesiano 2D, quais categorias demográficas "orbitam" (estão fortemente associadas) ao desfecho de "Concluinte" e quais gravitam em torno do desfecho "Não Concluinte", fornecendo um retrato consolidado da desigualdade estrutural.

---

## 4. Conclusão da Metodologia
A esteira analítica do Projeto 4 apresentou uma progressão robusta: utilizou estatística descritiva para exploração inicial, validação por testes de hipótese (Qui-Quadrado) para blindagem científica e técnicas não-supervisionadas (ACM com correção de Benzécri) para mapeamento interseccional de alta complexidade. Essa abordagem garante ao TCC de Mara Oliveira um grau analítico profundo, embasado e à prova de viés interpretativo casual.
