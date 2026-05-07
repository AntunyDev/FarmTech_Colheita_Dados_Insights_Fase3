# 🌱 FarmTech Solutions — Fase 3: Banco de Dados Oracle

## 📋 Descrição do Projeto

Este repositório faz parte do PBL (Project-Based Learning) do curso de Inteligência Artificial,
simulando o crescimento da startup fictícia **FarmTech Solutions**, uma consultoria de soluções
para o agronegócio.

Nesta fase, os dados coletados pelos sensores agrícolas da Fase 2 foram carregados em um
banco de dados relacional **Oracle**, utilizando o **Oracle SQL Developer** para criação
da tabela, importação dos dados e execução de consultas SQL.

---

## 👥 Integrantes do Grupo

| Nome | RM |
|---|---|
| Nome do integrante 1 | RM00000 |
| Nome do integrante 2 | RM00000 |

---

## 🗂️ Estrutura do Repositório

pbl/
└── fase3/
├── README.md
├── dados/
│   └── sensores.csv
└── sql/
└── consultas.sql

---

## 🛠️ Tecnologias Utilizadas

- **Oracle Database XE** — banco de dados relacional
- **Oracle SQL Developer** — interface gráfica para gerenciamento do banco
- **SQL** — linguagem de consulta utilizada

---

## 🗄️ Estrutura da Tabela

A tabela `sensores` foi criada com o seguinte comando:

```sql
CREATE TABLE sensores (
    id        NUMBER GENERATED ALWAYS AS IDENTITY PRIMARY KEY,
    umidade   NUMBER(5,2),
    ph        NUMBER(4,2),
    n         NUMBER(1),
    p         NUMBER(1),
    k         NUMBER(1),
    precipitacao NUMBER(5,2),
    irrigacao NUMBER(1)
);
```

### Descrição das Colunas

| Coluna | Tipo | Descrição |
|---|---|---|
| `id` | NUMBER | Identificador único (gerado automaticamente) |
| `umidade` | NUMBER(5,2) | Umidade do solo (%) |
| `ph` | NUMBER(4,2) | Nível de pH do solo |
| `n` | NUMBER(1) | Presença de Nitrogênio (0 ou 1) |
| `p` | NUMBER(1) | Presença de Fósforo (0 ou 1) |
| `k` | NUMBER(1) | Presença de Potássio (0 ou 1) |
| `precipitacao` | NUMBER(5,2) | Precipitação em mm |
| `irrigacao` | NUMBER(1) | Status da irrigação: 1 = ativada, 0 = desativada |

---

## 📥 Importação dos Dados

Os dados foram importados a partir do arquivo `sensores.csv` gerado na Fase 2,
utilizando o assistente de importação do **Oracle SQL Developer**:

1. Clique com o botão direito na tabela `sensores`
2. Selecione **Import Data**
3. Selecione o arquivo `sensores.csv`
4. Mapeie as colunas corretamente
5. Confirme a importação

Ao final, **40 registros** foram importados com sucesso.

---

## 🔍 Consultas SQL Realizadas

### Consulta 1 — Todos os registros
```sql
SELECT * FROM sensores;
```
> Retorna todos os 40 registros importados, permitindo verificar a integridade dos dados.

📸 *[inserir print aqui]*

---

### Consulta 2 — Total de registros importados
```sql
SELECT COUNT(*) AS total_registros FROM sensores;
```
> Confirma que todos os 40 registros foram carregados corretamente.

📸 *[inserir print aqui]*

---

### Consulta 3 — Média das variáveis por status de irrigação
```sql
SELECT 
  irrigacao,
  ROUND(AVG(umidade), 2)      AS media_umidade,
  ROUND(AVG(ph), 2)           AS media_ph,
  ROUND(AVG(precipitacao), 2) AS media_precipitacao
FROM sensores
GROUP BY irrigacao;
```
> Compara as condições médias de solo quando a irrigação está ativa (1) ou inativa (0).

📸 *[inserir print aqui]*

---

### Consulta 4 — Registros com irrigação ativada, ordenados por umidade
```sql
SELECT * FROM sensores
WHERE irrigacao = 1
ORDER BY umidade ASC;
```
> Exibe apenas os registros em que a irrigação foi acionada, do menor para o maior nível de umidade.

📸 *[inserir print aqui]*

---

### Consulta 5 — Condições críticas (baixa umidade com irrigação ativa)
```sql
SELECT * FROM sensores
WHERE umidade < 40 AND irrigacao = 1;
```
> Identifica situações críticas onde a umidade está muito baixa e o sistema de irrigação foi acionado.

📸 *[inserir print aqui]*

---

## 📊 Principais Achados

- Registros com **irrigação ativada** apresentam, em média, **menor umidade e menor precipitação**,
  o que confirma que o sistema responde corretamente às condições do solo.
- Todos os registros com **umidade abaixo de 40%** tiveram a irrigação acionada automaticamente.
- O pH médio do solo se mantém entre **5,0 e 7,8**, dentro da faixa adequada para culturas agrícolas.

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

