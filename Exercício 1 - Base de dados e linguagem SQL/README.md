<img src="https://raw.githubusercontent.com/rhatiro/Curso_EBAC-Profissao_Cientista_de_Dados/main/ebac-course-utils/media/logo/newebac_logo_black_half.png" alt="ebac-logo">

---

# **Exercício 1** | Base de dados & Linguagem SQL

Aluno [Iago Barbosa Correa](https://www.linkedin.com/in/iago-barbosa-dados/)<br>

---

## Atividades

### **1 Criação da tabela de clientes**

```sql
CREATE EXTERNAL TABLE clientes(
	id BIGINT,
	idade BIGINT,
	sexo STRING,
	dependentes BIGINT,
	escolaridade STRING,
	tipo_cartao STRING,
	limite_credito DOUBLE,
	valor_transacoes_12m DOUBLE,
	qtd_transacoes_12m BIGINT
)
ROW FORMAT SERDE 'org.apache.hadoop.hive.serde2.OpenCSVSerde'
WITH SERDEPROPERTIES (
	'separatorChar' = ',',
	'quoteChar' = '"',
	'escapeChar' = '\\'
)
STORED AS TEXTFILE
```

### **2. Explorando os dados da tabela de clientes**

#### [**2.1. Query 1**](https://raw.githubusercontent.com/IagoBCorrea/SQL_EBAC/refs/heads/main/query_1.csv)
```sql
SELECT *
FROM clientes;
```

#### [**2.2. Query 2**](https://raw.githubusercontent.com/IagoBCorrea/SQL_EBAC/refs/heads/main/query_2.csv)
```sql
SELECT id,
	idade,
	limite_credito
FROM clientes
WHERE sexo = 'M'
ORDER BY idade DESC;
```

#### [**2.3. Query 3**](https://raw.githubusercontent.com/IagoBCorrea/SQL_EBAC/refs/heads/main/query_3.csv)
```sql
SELECT sexo,
	AVG(idade) AS "media_idade_por_sexo"
FROM clientes
GROUP BY sexo;
```
