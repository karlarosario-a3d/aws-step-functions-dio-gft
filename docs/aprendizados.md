# Aprendizados

Durante este laboratório, foi possível consolidar conceitos importantes sobre AWS Step Functions e documentação técnica.

## Principais aprendizados

- AWS Step Functions permite criar workflows automatizados e visuais.
- Uma máquina de estados representa o fluxo completo de execução.
- Cada etapa do fluxo é representada por um estado.
- O estado `Choice` permite criar decisões condicionais.
- O estado `Pass` pode ser usado para representar etapas intermediárias.
- Os estados `Succeed` e `Fail` encerram o workflow com sucesso ou falha.
- A documentação do processo ajuda a tornar o projeto mais compreensível e reutilizável.

## Dificuldades encontradas

- Entender como o JSON de entrada percorre a execução.
- Organizar a lógica condicional no estado `Choice`.
- Pensar em um cenário simples, mas útil para demonstrar o funcionamento do workflow.

## Insights

Este laboratório mostrou que o AWS Step Functions pode ser usado para representar processos de negócio de forma visual e organizada.

Mesmo em um exemplo simples, já é possível perceber como a ferramenta ajuda na rastreabilidade, validação e automação de etapas.
