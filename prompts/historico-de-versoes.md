# Histórico de versões do prompt

Cada versão foi uma resposta a problemas observados na anterior. Os testes foram feitos com uma execução por vaga; portanto, os efeitos descritos são observações, não medições.

Os textos completos das versões intermediárias (v2 a v2.3) não foram arquivados. Estão guardados apenas a v1 e a v2.4 (final), em [v1.md](v1.md) e [v2.4.md](v2.4.md). Para as intermediárias, o que está registrado abaixo é o que foi alterado e o que se observou.

| Versão | Modelo | O que mudou | O que se observou |
|---|---|---|---|
| v1 | GPT-4o mini | Prompt inicial, com perfil curto | Resposta veio em bloco de código; sem justificativa por status; riscos interpretativos; localização não avaliada; resposta variava entre execuções |
| v2 | GPT-4o mini, temperatura 0,2 | Campos novos `local_modelo` e `diferenciais`; justificativa por status; riscos com trecho da vaga; cidade no perfil | Sem bloco de código; localização passou a ser considerada. Problema: "não mencionado" virou "não possui" |
| v2.1 | GPT-4o mini, 0,2 | Habilidades do perfil uma por linha, com nível; regra do "indeterminado"; riscos = requisitos "nao_atende" + cidade | "indeterminado" passou a funcionar e os riscos vieram preenchidos. Persistiram: dashboards como "nao_atende", risco de cidade mesmo em home office, diferenciais vazios |
| v2.2 | GPT-4o mini, 0,2 | Regra "SEMPRE"; risco de cidade só para presencial/híbrido; "liste todos" os diferenciais | Persistiram os dashboards como "nao_atende" e a formação ignorada. Apareceu uma exigência inventada de morar em outra cidade |
| v2.3 | GPT-4o mini, 0,2 | Formação em andamento no perfil; resumo sobre o cargo; formação e idioma entre os requisitos; justificativa antes do status; um risco por "nao_atende" | Corrigiu formação, cidade e dashboards. Regressão: dois requisitos obrigatórios foram para `diferenciais` e os riscos passaram a trazer previsões. A causa foi a instrução de incluir "ferramentas citadas como opcionais" em diferenciais |
| v2.4 | GPT-4o mini e GPT-5 mini | Requisitos = TODOS; diferenciais só o que o anúncio marca como desejável; uma aderência por requisito; riscos só para "nao_atende", sem previsões | Com GPT-4o mini, o risco de cidade voltou. Com GPT-5 mini (adotado), não houve risco de cidade e o Excel saiu como "parcial" |

## Observações

- A migração para o GPT-5 mini foi motivada pela sensação de que cada correção gerava um problema novo. A comparação foi de uma execução por modelo, então não prova superioridade.
- O fluxo final não define temperatura (nó com opções vazias). O 0,2 vale só para os testes v2 a v2.4 com GPT-4o mini.
- Custo observado no teste com GPT-5 mini: cerca de US$ 0,01 por execução.
