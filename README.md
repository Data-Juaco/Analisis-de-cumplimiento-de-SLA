#  Análisis de Cumplimiento de SLA – CLRM03

Analisis de Cumplimiento de SLA por Subproceso Logistico.

##  Objetivo

Medir el porcentaje de cumplimiento de SLA en cada subproceso, con foco en identificar desviaciones semanales que permitan tomar decisiones operativas informadas.

##  Herramientas utilizadas

- BigQuery (Google Cloud)
- SQL
- Google Sheets (para validaciones)
- Power BI (visualización opcional)

##  Estructura del análisis

1. **ETD Ajustado**: Se recalcula el `OUTBOUND_DEPARTURE_ESTIMATED_DATE` según una fecha de corte.
2. **Condiciones SLA**: Cada subproceso tiene su propia ventana de cumplimiento:
   - Waving: hasta 6 horas antes del ETD
   - Picking: hasta 4 horas antes del ETD
   - Packing: hasta 3 horas antes del ETD
   - Dispatch: hasta 1 hora antes del ETD
3. **Evaluación**: Se verifica si cada proceso cumple con su ventana.
4. **Resumen**: Se agrupan los datos por semana y subproceso, calculando el porcentaje de cumplimiento (`SLA_PCT`).

##  Métricas generadas

- Total de pedidos por subproceso y semana
- Pedidos que cumplieron SLA (`SLA_OK`)
- % de cumplimiento semanal (`SLA_PCT`)

##  Resultado esperado

Una tabla resumen con cumplimiento de SLA por semana y subproceso, ideal para construir visualizaciones o dashboards.

| Subproceso | Semana   | Total | Cumple | SLA_PCT |
|------------|----------|-------|--------|---------|
| picking    | 2025-20  | 980   | 867    | 88.47   |
| dispatch   | 2025-20  | 980   | 941    | 96.02   |

##  Archivo incluido

- `sla_clrm03_analysis.sql`: consulta principal de análisis SLA

##  Próximos pasos

- Integrar visualizaciones en Power BI / Looker
- Incluir análisis por turno y canal (FULL, FLEX)
- Documentar hallazgos y acciones sugeridas

