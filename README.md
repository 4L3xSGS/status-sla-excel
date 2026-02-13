STATUS_SLA — Fórmula de Controle de Prazo (Excel)
📌 Visão Geral
STATUS_SLA é uma lógica de controle de prazo mensal desenvolvida em Excel para monitorar atividades, demandas ou registros operacionais com base em status e data de referência.
A fórmula atua como um classificador automático de SLA (Service Level Agreement), indicando quando um item está dentro do prazo, em atenção ou em atraso crítico.
O objetivo é eliminar verificações manuais e padronizar o acompanhamento de backlog e processos em planilhas operacionais.
________________________________________
🎯 Finalidade
A fórmula avalia:
•	A data base da atividade
•	O status atual do item
•	O ciclo mensal de fechamento
•	A diferença entre o período esperado e o período atual
Com base nisso, ela retorna automaticamente um indicador de situação.
________________________________________
📥 Entradas (Inputs)
Célula	Descrição
M6	Data base do item (data de medição ou referência)
R6	Status atual do processo
Status considerados válidos
•	Backlog
•	em Andamento
•	em Avaliação
•	Cancelado
________________________________________
📤 Saídas (Resultados)
Resultado	    Significado
(vazio)	      Item dentro do prazo
mmm/aa	      Atenção — atraso de 1 ciclo mensal
Alerta HOLD	  Atraso igual ou superior a 2 meses
HOLD	        Item cancelado
________________________________________
⚙️ Como a lógica funciona
1.	Define o dia de corte conforme o status:
o	Backlog / em Andamento → dia 20
o	em Avaliação → dia 25
2.	Ajusta o mês de referência caso a data ultrapasse o dia de corte.
3.	Calcula o último dia útil do mês usando:
4.	DIATRABALHO.INTL()
5.	Calcula o fechamento equivalente no mês atual.
6.	Converte as datas em períodos mensais comparáveis.
7.	Mede a diferença entre períodos e classifica automaticamente o status do SLA.
________________________________________
▶️ Como utilizar
1.	Insira a data base na coluna correspondente (ex.: M6).
2.	Informe o status do item (ex.: R6).
3.	Cole a fórmula na coluna de controle.
4.	Arraste para as demais linhas da planilha.
A classificação será atualizada automaticamente conforme a data atual do sistema.
________________________________________
✅ Requisitos
•	Excel 365 ou Excel 2021+
•	Suporte às funções:
o	LET
o	DIATRABALHO.INTL
o	SE, OU, E, DATA, HOJE
________________________________________
💡 Casos de uso
•	Controle de backlog
•	Monitoramento de SLA operacional
•	Gestão de demandas
•	Acompanhamento de processos mensais
•	PMO e governança operacional
________________________________________
🔧 Personalização
É possível adaptar facilmente:
•	Dias de corte (20 / 25)
•	Status aceitos
•	Mensagens de alerta
•	Calendário de dias úteis
________________________________________
📄 Licença
Uso livre para fins educacionais e operacionais. Recomenda-se documentar alterações ao adaptar a regra de negócio.
________________________________________
Autor: Alexander dos Santos Gomes Souto
