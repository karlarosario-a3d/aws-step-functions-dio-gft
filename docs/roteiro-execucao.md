# Roteiro de Execução

Este roteiro descreve como o laboratório pode ser executado no AWS Step Functions.

## Passo 1: Acessar o AWS Step Functions

Acesse o console da AWS e procure pelo serviço AWS Step Functions.

## Passo 2: Criar uma State Machine

Crie uma nova máquina de estados usando a opção de definição em código.

## Passo 3: Utilizar o arquivo ASL

Copie o conteúdo do arquivo:

```text
workflows/pedido-aprovacao.asl.json
```

Cole a definição no editor da máquina de estados.

## Passo 4: Iniciar uma execução

Execute a máquina de estados usando um dos arquivos da pasta `inputs`.

Exemplo:

```text
inputs/pedido-aprovado.json
```

## Passo 5: Validar o resultado

Observe no Workflow Studio o caminho percorrido pela execução.

Valide se o comportamento corresponde ao cenário esperado.

## Passo 6: Registrar evidências

Adicione prints da execução na pasta:

```text
images/
```

Sugestões de prints:

- Tela da máquina de estados.
- Execução aprovada automaticamente.
- Execução enviada para análise manual.
- Histórico da execução.
