# AWS Step Functions - Workflow Automatizado

## Descrição

Este projeto foi desenvolvido como parte do desafio do bootcamp da DIO em parceria com a GFT e AWS. O objetivo foi consolidar os conhecimentos adquiridos sobre AWS Step Functions, documentando conceitos, aprendizados e a estrutura de um workflow automatizado.

O projeto apresenta um exemplo de fluxo de aprovação de pedido utilizando uma máquina de estados, com etapas de validação, decisão e finalização do processo.

## Objetivos do Projeto

* Compreender o funcionamento do AWS Step Functions.
* Entender o conceito de máquinas de estado.
* Documentar a criação de um workflow automatizado.
* Praticar a organização de documentação técnica em um repositório GitHub.
* Registrar aprendizados e possíveis melhorias futuras.

## O que é AWS Step Functions?

O AWS Step Functions é um serviço de orquestração serverless que permite criar fluxos de trabalho automatizados. Ele ajuda a coordenar diferentes etapas de um processo, permitindo representar visualmente a execução de tarefas, decisões, tratamentos de erro e finalizações.

Os workflows são definidos como máquinas de estado, onde cada etapa representa uma ação ou decisão dentro do processo.

## Conceitos Aprendidos

Durante o laboratório, foram revisados os seguintes conceitos:

* State Machine
* Amazon States Language
* Estados do tipo Pass
* Estados do tipo Choice
* Estados de sucesso e falha
* Execução visual de workflows
* Organização de documentação técnica
* Uso do GitHub para entrega de projetos

## Arquitetura do Workflow

O exemplo escolhido foi um fluxo de aprovação de pedido.

Fluxo proposto:

1. O workflow recebe os dados de um pedido.
2. O valor do pedido é validado.
3. Se o valor for menor ou igual a 500, o pedido é aprovado automaticamente.
4. Se o valor for maior que 500, o pedido segue para análise manual.
5. O processo é finalizado com sucesso.

Representação simplificada:

```text
Receber pedido
     ↓
Validar valor
     ↓
Pedido <= 500?
   /        \
Sim        Não
 |          |
Aprovar    Análise manual
 |          |
Finalizar processo
```

## Exemplo de entrada

```json
{
  "pedidoId": "PED-001",
  "cliente": "Cliente Exemplo",
  "valor": 350
}
```

## Exemplo de definição da máquina de estados

```json
{
  "Comment": "Workflow simples de aprovação de pedido",
  "StartAt": "ReceberPedido",
  "States": {
    "ReceberPedido": {
      "Type": "Pass",
      "Next": "ValidarValor"
    },
    "ValidarValor": {
      "Type": "Choice",
      "Choices": [
        {
          "Variable": "$.valor",
          "NumericLessThanEquals": 500,
          "Next": "AprovarPedido"
        },
        {
          "Variable": "$.valor",
          "NumericGreaterThan": 500,
          "Next": "EnviarParaAnalise"
        }
      ],
      "Default": "FalhaValidacao"
    },
    "AprovarPedido": {
      "Type": "Succeed"
    },
    "EnviarParaAnalise": {
      "Type": "Pass",
      "Next": "FinalizarAnalise"
    },
    "FinalizarAnalise": {
      "Type": "Succeed"
    },
    "FalhaValidacao": {
      "Type": "Fail",
      "Error": "ValorInvalido",
      "Cause": "O valor do pedido não pôde ser validado."
    }
  }
}
```

## Prints da Execução

As capturas de tela da execução do workflow podem ser encontradas na pasta `/images`.

Sugestão de imagens:

* Criação da máquina de estados no Workflow Studio.
* Execução com valor aprovado automaticamente.
* Execução com valor enviado para análise.
* Histórico da execução.

## Aprendizados

Durante a prática, foi possível entender como o AWS Step Functions facilita a orquestração de processos automatizados. A visualização do fluxo ajuda a compreender cada etapa da execução, tornando o processo mais rastreável e organizado.

Também foi possível perceber a importância de documentar tecnicamente cada decisão tomada durante o laboratório, pois isso facilita futuras consultas, revisões e implementações em cenários reais.

## Possíveis Melhorias Futuras

* Integrar o workflow com uma função AWS Lambda.
* Adicionar envio de notificações com Amazon SNS.
* Registrar os pedidos em uma tabela Amazon DynamoDB.
* Criar tratamento de erros mais detalhado.
* Automatizar o deploy com AWS SAM ou Terraform.

## Conclusão

Este desafio ajudou a consolidar os conceitos fundamentais de AWS Step Functions e mostrou como workflows automatizados podem ser utilizados para organizar processos de negócio de forma visual, escalável e documentada.

A prática também reforçou a importância do GitHub como ferramenta de documentação e compartilhamento de conhecimento técnico.
