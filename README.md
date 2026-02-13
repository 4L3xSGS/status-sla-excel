# STATUS\_SLA — Fórmula de Controle de Prazo (Excel)

Uma lógica de classificação automática de SLA (Service Level Agreement) para monitoramento mensal de atividades em planilhas operacionais.  
O objetivo é eliminar verificações manuais e padronizar o acompanhamento de backlog, demandas e processos cíclicos.

***

## 📌 Visão Geral

**STATUS\_SLA** é uma fórmula desenvolvida em **Excel** para analisar prazos com base em:

*   Data de referência do item
*   Status atual
*   Ciclo mensal de fechamento
*   Diferença entre período esperado × período atual

A saída é um indicador automático que aponta:

*   Itens dentro do prazo
*   Itens em atenção (1 mês de atraso)
*   Itens críticos (2+ meses de atraso)
*   Itens cancelados (HOLD)

***

## 🎯 Finalidade

A lógica calcula automaticamente a situação do item com base em:

*   `M6` → **Data base**
*   `R6` → **Status atual**
*   Regras de corte mensal
*   Conversão para períodos mensais comparáveis

Sem intervenção manual e sem necessidade de macros.

***

## 📥 Entradas (Inputs)

| Célula | Descrição                                         |
| ------ | ------------------------------------------------- |
| **M6** | Data base do item (data de medição ou referência) |
| **R6** | Status atual do processo                          |

**Status válidos**:

*   `Backlog`
*   `em Andamento`
*   `em Avaliação`
*   `Cancelado`

***

## 📤 Saídas (Resultados)

| Resultado     | Significado                 |
| ------------- | --------------------------- |
| *(vazio)*     | Item dentro do prazo        |
| `mmm/aa`      | Atenção — atraso de 1 ciclo |
| `Alerta HOLD` | Atraso ≥ 2 ciclos           |
| `HOLD`        | Item cancelado              |

***

## ⚙️ Como a lógica funciona

1.  **Define o dia de corte conforme o status**
    *   Backlog / em Andamento → **20**
    *   em Avaliação → **25**

2.  **Ajusta o mês de referência**  
    Se a data ultrapassa o dia de corte, a contagem passa para o próximo mês.

3.  **Calcula o último dia útil do mês**  
    Usando `DIATRABALHO.INTL()`.

4.  **Determina o fechamento equivalente do mês atual**

5.  **Converte tudo em períodos mensais comparáveis**

6.  **Mede a diferença de ciclos**

7.  **Classifica automaticamente o SLA**
    *   0 ciclos → OK
    *   1 ciclo → Atenção
    *   ≥2 ciclos → Alerta HOLD
    *   Cancelado → HOLD

***

## ▶️ Como utilizar

1.  Inserir data base na coluna (ex.: **M6**)
2.  Informar o status (ex.: **R6**)
3.  Colar a fórmula na coluna de controle
4.  Arrastar para as demais linhas

A fórmula atualiza automaticamente com a data do sistema.

***

## ✅ Requisitos

*   **Excel 365 ou Excel 2021+**
*   Funções necessárias:
    *   `LET`
    *   `DIATRABALHO.INTL`
    *   `SE`, `OU`, `E`
    *   `DATA`, `HOJE`

***

## 💡 Casos de uso

*   Controle de backlog
*   Monitoramento de SLA operacional
*   Gestão de demandas internas
*   Acompanhamento de processos mensais
*   PMO, governança e qualidade operacional

***

## 🔧 Personalização

Você pode adaptar:

*   Dias de corte (20 / 25)
*   Lista de status aceitos
*   Mensagens exibidas
*   Calendário de dias úteis

***

## 📄 Licença

Uso livre para fins educacionais e operacionais.  
Recomenda-se documentar alterações ao adaptar a lógica para regras de negócio específicas.

***

## ✍️ Autor

*Alexander S. G. Souto*

***

Se quiser, posso **incluir a fórmula completa**, gerar um **exemplo de planilha**, ou criar uma **versão em inglês para repositório internacional**. Quer adicionar algo?
