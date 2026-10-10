# grafana-alloy-prometheus-loki-postgres-dockercompose_dadosgeograficos
Script do Docker Compose para criação de uma base PostgreSQL com dados geográficas (Estados e Regiões do Brasil), com a coleta de métricas (Prometheus) + logs (Loki) via Grafana Alloy e consulta destas informações através da funcionalidade Queries overview (Database Observability) a partir do Grafana Cloud.

## Testes

Queries executadas:

```sql
SELECT * FROM "Estados"
WHERE "IdRegiao" = 3;


SELECT * FROM "Regioes"
ORDER BY "NomeRegiao" DESC;


SELECT R."IdRegiao", R."CodRegiao", R."NomeRegiao", COUNT(E."SiglaEstado") AS "QuantidadeEstados"
FROM "Regioes" R
INNER JOIN "Estados" E ON R."IdRegiao" = E."IdRegiao"
GROUP BY R."IdRegiao", R."CodRegiao", R."NomeRegiao";
```

Resultado no VS Code:

![Queries executadas no Visual Studio Code](img/vscode-01.png)

A funcionalidade **Queries overview** no Grafana Cloud:

![Queries overview no Grafana Cloud 1](img/grafana-01.png)

![Queries overview no Grafana Cloud 2](img/grafana-02.png)

Detalhes de uma das queries:

![Detalhes de uma das queries](img/grafana-03.png)