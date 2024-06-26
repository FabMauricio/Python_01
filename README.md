# Python_01
Criando um Sistema Bancário com Python

![image](https://github.com/FabMauricio/Python_01/assets/153826437/67359d79-b483-4316-9a25-34b5199109c1)



# Código seguindo as orientações do instrutor....

menu = """  

[d] Depositar
[s] Sacar
[e] Extrato
[q] Sair

=> """

saldo = 0
limite = 500
extrato = ""
numero_saque = 0
LIMITE_SAQUES = 3


while True:
    opcao = input(menu)

    if opcao == "d":
        valor = float(input("Informe o valor do depósito: "))

        if valor > 0:
            saldo += valor
            extrato += f"Depósito: R$ {valor:.2f}\n"

        else:
            print("Operação falhou! o valor informado é inválido.")

    elif opcao == "s":
        valor = float(input("Informe o valor de saque:"))
        
        excedeu_saldo = valor > saldo
        
        excedeu_limite = valor > limite
        
        excedeu_saque = numero_saque >= LIMITE_SAQUES

        if excedeu_saldo:
            print("Operação falhou! Você não tem saldo suficiente.")

        elif excedeu_limite:
            print("Operação falhou! O valor do saque excede o limite.")

        elif excedeu_saque:
            print("Operação falhou! Número de saques diários excedidos.")

        elif valor > 0:
            saldo -= valor
            extrato += f"Saque: R$ {valor:.2f}\n"
            numero_saque += 1

        else:
            print("Operação falhou! O valor informado é inválido.")
        
    elif opcao =="e":
        print("\n ========Extrato=========")
        print("Não foram realizados movimentações." if not extrato else extrato)
        print(f"\n Saldo: R$ {saldo:.2f}")
        print("===========================")

    elif opcao == "q":
        break

    else:
        print("Operação inválida, por favor selecione novamente a operação desejada.")
