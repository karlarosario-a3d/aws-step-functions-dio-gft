# Cenários de Teste

Este documento apresenta os cenários simulados para validação da máquina de estados criada com AWS Step Functions.

## Cenário 1: Pedido aprovado automaticamente

Arquivo de entrada:

```text
inputs/pedido-aprovado.json
```

Entrada:

```json
{
  "pedidoId": "PED-001",
  "cliente": "Cliente Exemplo",
  "valor": 350
}
```

Resultado esperado:

O workflow deve seguir para o estado `AprovarPedido`, pois o valor do pedido é menor ou igual a 500.

---

## Cenário 2: Pedido enviado para análise manual

Arquivo de entrada:

```text
inputs/pedido-analise-manual.json
```

Entrada:

```json
{
  "pedidoId": "PED-002",
  "cliente": "Cliente Corporativo",
  "valor": 1200
}
```

Resultado esperado:

O workflow deve seguir para o estado `EnviarParaAnalise`, pois o valor do pedido é maior que 500.

---

## Cenário 3: Pedido inválido

Arquivo de entrada:

```text
inputs/pedido-invalido.json
```

Entrada:

```json
{
  "pedidoId": "PED-003",
  "cliente": "Cliente Teste"
}
```

Resultado esperado:

O workflow deve cair em uma condição de falha ou validação padrão, pois o campo `valor` não foi informado.
