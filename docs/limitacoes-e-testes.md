# Testes e limitações

## Como foi testado

- Prompt v2.4 com GPT-5 mini.
- 10 anúncios públicos de vagas de dados e BI, mais 1 anúncio usado nas iterações do prompt (11 no total).
- Uma execução por vaga. Cada resultado foi conferido manualmente contra o texto do anúncio.
- Perfil fictício no prompt: cursando Sistemas de Informação; SQL básico a intermediário; Power BI básico; Excel intermediário; Python básico; automação no-code; documentação e processos; inglês básico; mora em São Paulo e aceita remoto/híbrido na própria cidade.

Não houve medição de tempo, de acurácia ou de repetibilidade. É uma avaliação qualitativa.

## Anúncios usados (anonimizados)

| # | Tipo de vaga | Local / modelo |
|---|---|---|
| 1 | Analista de Dados Jr (distribuidora) | São Paulo, modelo não informado |
| 2 | Analista de Dados e CRM Jr | Belo Horizonte, híbrido |
| 3 | Analista de Dados Jr (e-commerce) | São Paulo, híbrido |
| 4 | Analista de Dados (automotiva) | São Bernardo do Campo, híbrido |
| 5 | Analista de Banco de Dados Jr | não informado |
| 6 | Analista Power BI Pleno | Rio de Janeiro, híbrido |
| 7 | Analista de BI Jr | Remoto |
| 8 | Analista de Dados Jr | Belo Horizonte, presencial |
| 9 | Analista de Dados I | São Paulo, presencial, PJ |
| 10 | Analista de Dados/Relatórios Jr (área de saúde) | Campinas |
| 11 | Desenvolvedor de Dashboards e Copilot (anúncio usado para iterar o prompt) | Rio de Janeiro, home office |

## Exemplo de melhoria (vaga 3, v1 → v2.4)

Na v1, a resposta para esse anúncio listava como riscos o modelo híbrido e o "ambiente ágil", sem relação com o perfil informado, e deixava de fora do campo `requisitos` as ferramentas citadas como desejáveis. Na v2.4, os riscos passaram a existir só quando um requisito saiu como "nao_atende", citando o trecho do anúncio, e os requisitos e diferenciais vieram em campos separados.

## Limitações observadas

1. **Nível de comparação inconsistente.** O mesmo tipo de lacuna aparece como "parcial" em uma vaga e "nao_atende" em outra.
2. **Requisitos com várias partes.** Um item que juntava, por exemplo, duas ferramentas era marcado como "atende" mesmo cobrindo só uma delas.
3. **Anúncio mal estruturado.** Em uma vaga PJ presencial, o modelo dividiu requisitos e diferenciais de forma ruim e contou "presencial" duas vezes.
4. **Localização vaga.** Para uma vaga em São Bernardo do Campo (perfil em São Paulo), o ponto foi tratado de forma imprecisa.
5. **Observações repetitivas.** O campo `observacoes` às vezes só repetia informações do perfil.
6. **Sem avaliação de senioridade.** Uma vaga Pleno pode receber vários "atende" sem sinalização de que o nível exigido é maior que o do perfil.
7. **Empresa vazia.** Quando o anúncio não cita a empresa, o campo pode ficar vazio em vez de "indeterminado".

Além disso:

- Cada versão foi testada com uma única execução por vaga; a variação entre execuções não foi medida.
- A temperatura não está definida no fluxo final.
- O resultado depende do perfil fictício escrito no prompt e deve ser tratado como apoio à leitura, não como decisão.
