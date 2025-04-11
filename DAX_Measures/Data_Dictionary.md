# 📊 DAX Measures – Custo TI Report

> This file includes all the custom DAX measures used in the Power BI report “Custo TI”.

---

### 🔢 Base Measures
```DAX
Valores = SUM(Factos[Valor])
Montante = TOTALYTD(SUM(Factos[Valor]), 'Calendário'[Date]) * 0.3

```

### 💰 Scenario Amounts
```DAX
Montante Plan = CALCULATE([Montante], 'Cenários'[Cenário] = "Plan")
Montante LE3 = CALCULATE([Montante], 'Cenários'[Cenário] = "LE3")
Montante LE2 = CALCULATE([Montante], 'Cenários'[Cenário] = "LE2")
Montante LE1 = CALCULATE([Montante], 'Cenários'[Cenário] = "LE1")
Montante Actual = CALCULATE([Montante], 'Cenários'[Cenário] = "Actual")

```
### 📈 Variations

```DAX
Variação Plan = [Montante Actual] - [Montante Plan]
Variação LE3 = [Montante Actual] - [Montante LE3]
Variação LE2 = [Montante Actual] - [Montante LE2]
Variação LE1 = [Montante Actual] - [Montante LE1]

```
### 📊 Percent Variations

```DAX
% Variação Plan = DIVIDE([Variação Plan], [Montante Plan], 0)
% Variação LE3 = DIVIDE([Variação LE3], [Montante LE3], 0)
% Variação LE2 = DIVIDE([Variação LE2], [Montante LE2], 0)
% Variação LE1 = DIVIDE([Variação LE1], [Montante LE1], 0)

```
### 💼 Other

```DAX
Custos = CALCULATE([Valores], RELATEDTABLE(Custos))

```
### ✅ Notes

> The variation measures allow for comparing actual values with different planned scenarios (Plan, LE1, LE2, LE3).

> The use of DIVIDE prevents errors from division by zero.

> The [Montante] measure was adjusted with a multiplier of 0.3 to simulate a specific business logic.
