# Criando um Sistema Bancário com Python

Desafio Python: Criação de um sistema bancário simples utilizando os fundamentos básicos da linguagem.

## Menu

O sistema possui um menu simples com as opções: **Depósito, Sacar, Extrato e Sair**. Cada opção chama uma função no nosso sistema e o a opção Sair dá um break no nosso código.

```python
menu = """
--------------------------------
======== Menu Principal ========
|| Opções:                    ||
||  (D) Depositar             ||
||  (S) Sacar                 ||
||  (E) Extrato               ||
||  (X) Sair                  ||
================================
>> """
```

## Código

O código é **procedural** e não utiliza funções nem POO, tendo comandos bem simples, mas que cumprem o solicitado pelo desafio.

Abaixo podemos conferir o código completo, onde chamo a atenção para a variável **EXTRATO**, que não é uma lista, e sim uma String.

```python
menu = """
--------------------------------
======== Menu Principal ========
|| Opções:                    ||
||  (D) Depositar             ||
||  (S) Sacar                 ||
||  (E) Extrato               ||
||  (X) Sair                  ||
================================
>> """

saldo = 0
limite = 500
extrato = ""
numero_saques = 0
LIMITE_SAQUES = 3

while True:

    opcao = input(menu)

    if opcao.lower() == "d":
        valor = float(input("Informe o valor do depósito: "))

        if valor > 0:
            saldo += valor
            extrato += f"Depósito: R$ {valor:.2f}\n"

        else:
            print("Erro de operação! Valor inválido.")

    elif opcao.lower() == "s":
        valor = float(input("Informe o valor do saque: "))

        excedeu_saldo = valor > saldo

        excedeu_limite = valor > limite

        excedeu_saques = numero_saques >= LIMITE_SAQUES

        if excedeu_saldo:
            print("Erro de operação! Saldo insuficiente.")

        elif excedeu_limite:
            print("Erro de operação! O valor do saque excede o limite.")

        elif excedeu_saques:
            print("Erro de operação! Número máximo de saques diário excedido.")

        elif valor > 0:
            saldo -= valor
            extrato += f"Saque: R$ {valor:.2f}\n"
            numero_saques += 1

        else:
            print("Operação falhou! O valor informado é inválido.")

    elif opcao.lower() == "e":
        print("\n================ EXTRATO ================")
        print("Não foram realizadas movimentações." if not extrato else extrato)
        print(f"\nSaldo: R$ {saldo:.2f}")
        print("==========================================")

    elif opcao.lower() == "x":
        break

    else:
        print("Operação inválida, por favor selecione novamente a operação desejada.")

print("Volte sempre!")
```

Perceba que a variável **extrato** é uma string e a cada operação ela recebe um novo texto com o comando **Enter** no final (**\n**), dispensando a utilização de listas para a impressão do extrato.

Abaixo temos um exemplo de saída da varíavel:

```python
================ EXTRATO ================
Depósito: R$ 1550.00
Depósito: R$ 125.00
Saque: R$ 450.00
Depósito: R$ 260.00
Saque: R$ 410.00
Depósito: R$ 80.00


Saldo: R$ 1155.00
==========================================
```

---
