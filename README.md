# 🌱 FarmTech Solutions — Fase 3: Banco de Dados Oracle

## 📋 Descrição do Projeto

Este repositório faz parte do PBL (Project-Based Learning) do curso de Inteligência Artificial, simulando o crescimento da startup fictícia **FarmTech Solutions**, uma consultoria de soluções para o agronegócio.

Nesta fase, os dados coletados pelos sensores agrícolas da Fase 2 foram carregados em um banco de dados relacional **Oracle**, utilizando o **Oracle SQL Developer** para criação da tabela, importação dos dados e execução de consultas SQL.

---

## 👥 Integrantes do Grupo

| Nome | RM |
|---|---|
| Antuny Marques | RM573852 |
| Tiago Gonçalves | RM570935 |
| Carlos Ribeiro | RM571449 |
| Lucas Ribeiro | RM572508 |
| Anderson Sapucaia | RM571668 |

---

## 🗂️ Estrutura do Repositório

```text
pbl/
└── fase3/
    ├── README.md
    ├── dados/
    │   └── sensores.csv
    ├── prints/
    │   └── *.png
    └── sql/
        └── consultas.sql
```

---

## 🛠️ Tecnologias Utilizadas

- **Oracle Database XE** — banco de dados relacional
- **Oracle SQL Developer** — interface gráfica para gerenciamento do banco
- **SQL** — linguagem de consulta utilizada

---

## 🗄️ Conexão e Estrutura da Tabela

A conexão com o banco de dados Oracle foi estabelecida com sucesso através do Oracle SQL Developer, permitindo o gerenciamento e a criação do nosso schema.

📸 **Conexão ao Banco de Dados**
![Conexão Banco de Dados](prints/conexao_banco_dados_sql_oracle_developer.png)

---

## 📥 Importação dos Dados

Os dados foram importados a partir do arquivo CSV gerado na Fase 2, contendo os registros de nossos sensores agrícolas simulados.

📸 **Importação de Dados Concluída com Sucesso**
![Importação dados com sucesso](prints/importacao_dados_com_sucesso.png)

📸 **Amostragem dos Dados Importados**
![Amostragem dados importados](prints/amostragem_dados_sensores_importados.png)

---

A tabela `sensores` foi criada inicialmente. Durante o processo, identificamos a necessidade de refinar o tipo de dado do pH.

### ⚙️ Ajustes na Tabela (Tratamento da coluna pH)

Para garantir maior precisão nos registros de acidez do solo, foi realizado um processo de migração da coluna de pH de inteiro para decimal (`NUMBER(4,2)`):

1. **Criação da nova coluna decimal:**
![Criação nova coluna pH decimal](prints/criacao_nova_coluna_ph_decimal.png)

2. **Conversão e cópia dos valores da coluna antiga para a nova:**
![Conversão valores nova coluna pH decimal](prints/conversao_valores_nova_coluna_ph_decimal.png)

3. **Conferência dos valores atualizados:**
![Conferência valores pH decimal](prints/confericao_valores_ph_decimal.png)

4. **Exclusão da coluna antiga (inteiro):**
![Exclusão coluna pH inteiro](prints/exclusao_coluna_ph_inteiro.png)

5. **Renomeação da nova coluna para o nome original (`ph`):**
![Renomeação pH decimal](prints/renomeacao_ph_decimal.png)

6. **Efetivação das alterações (Commit):**
![Commit pH decimal](prints/commit_ph_decimal.png)


## 🔍 Consultas SQL Realizadas (Insights)

Abaixo estão listadas as consultas realizadas no banco de dados para a obtenção de insights sobre as condições do solo e as regras de irrigação.

### 1. Consulta Básica Geral
Retorna todos os registros da tabela `sensores`, permitindo verificar a integridade geral dos dados.
![Consulta Básica Geral](prints/consulta_basica_geral.png)

### 2. Média das Variáveis
Analisa as médias gerais de umidade, pH e precipitação.
![Consulta Média Variáveis](prints/consulta_media_variaveis.png)

### 3. Média de Irrigação por Umidade
Avalia a relação entre o nível de umidade do solo e o acionamento médio do sistema de irrigação.
![Média Irrigação por Umidade](prints/media_irrigacao_por_umidade.png)

### 4. Relação Irrigação vs Precipitação
Compara os dados de chuva (precipitação) com a ativação da irrigação, mostrando se a precipitação natural foi suficiente ou se precisou de irrigação artificial.
![Irrigação x Precipitação](prints/consulta_irrigacao_x_precipitacao.png)

### 5. Casos Críticos (Baixa Umidade)
Identifica situações críticas onde a umidade está muito baixa, exigindo atuação severa do sistema de irrigação.
![Consulta Baixa Umidade](prints/consulta_baixa_umidade_casos_criticos.png)

### 6. Registros que Necessitam de Irrigação
Contabiliza e filtra quantos registros específicos demandaram a ativação do sistema de irrigação (`irrigacao = 1`).
![Registros necessitam irrigação](prints/consulta_quantos_registros_necessitam_irrigacao.png)

### 7. Solos com Nível de Acidez Elevado (Solo Ácido)
Filtra os sensores onde o pH apresentou características de alta acidez, o que pode requerer correção (calagem).
![Consulta Solo Ácido](prints/consulta_solo_acido.png)

### 8. Solos com Todos os Nutrientes (N, P, K)
Busca por amostras ideais de solo, onde a presença de Nitrogênio (N), Fósforo (P) e Potássio (K) é satisfatória.
![Solo com todos nutrientes](prints/consulta_solo_com_todos_nutrientes.png)

### 9. Top 5 Maiores Precipitações
Lista os 5 registros com o maior volume de chuva (precipitação) identificado pelos sensores.
![Top 5 Maiores Precipitações](prints/top_5_maiores_precipitacoes.png)

### 10. Consulta de Dados Equilibrados
Identifica amostras onde o solo se encontra em condições ideais e equilibradas, com boa umidade, pH neutro e nutrientes presentes, dispensando a necessidade de irrigação.
![Consulta Dados Equilibrados](prints/consulta_dados_equilibrados.png)

---

## 📊 Principais Achados

- O sistema demonstra eficácia lógica: a irrigação está sendo ativada majoritariamente em momentos de **baixa umidade** e **baixa precipitação**.
- Foram identificadas amostras em condições **críticas** de baixa umidade, atestando a importância do monitoramento contínuo.
- A presença simultânea de macronutrientes (N, P, K) não foi registrada em todas as amostras, indicando possíveis áreas que demandariam adubação na vida real.
- As consultas mostram variações reais nos níveis de pH, onde casos de solo ácido foram claramente detectados, evidenciando a utilidade da mudança do tipo de dado de inteiro para decimal.

---

## 🎥 Vídeo Demonstrativo

📺 [Link do vídeo no YouTube](https://youtube.com/seu-link-aqui)

> O vídeo demonstra o funcionamento do banco de dados, a execução das consultas no
> Oracle SQL Developer e a organização do repositório GitHub.

---

## 📚 Referências

- [Oracle SQL Developer Documentation](https://docs.oracle.com/en/database/oracle/sql-developer/)
- Global AI Jobs Barometer — PwC (2025)
- Material didático do curso de Inteligência Artificial — FIAP

---

*FarmTech Solutions — Fase 3 | Curso de Inteligência Artificial*
