# Sistema-Bancario
Sistema Bancário com Python
#Sistema Bancário com Python.

#Menu de opções do sistema:
menu = """

[d] Depositar

[s] Sacar

[e] Extrato

[q] Sair


=> """

saldo = 0
limite = 500
extrato = ""
numero_saques = 0
LIMITE_SAQUES = 3


while True:
    
    opcao = input(menu)
    
    #1 - Operações de depósito:
    #Deve ser possível depositar valores positivos
    #Todos os depósitos devem ser armazenados em uma variável e exibidos na operação de extrato

    if opcao == "d":
        print("Depósito")
        
        valor = float(input("Informe o valor do depósito: "))
        
        if valor > 0:
            saldo += valor
            extrato += f"Depósito: R${valor:.2f}\n"
        else:
            print("Operação falhou! O valor informado é inválido.")
        
    #2 - Operações de saque:
    #O sistema deve permitir realizar 3 saques diários com limite máximo de R$ 500,00 por saque. 
    #Caso o usuário não tenha saldo em conta, o sistema deve exibir uma mensagem informando que não será possível sacar o dinheiro por falta de saldo
    #Todos os saques devem ser armazenados em uma variável e exibidos na operação de extrato
    
    elif opcao == "s":
        print("Saque")

        valor = float(input("Informe o valor do saque: "))

        if valor > saldo:
            print("Operação inválida! Você excedeu o saldo atual, tente novamente.")

        elif valor > limite:
            print("Operação inválida! Você excedeu o limite do valor do saque de R$500.00, tente novamente.")

        elif valor > numero_saques >= LIMITE_SAQUES:
            print("Operação inválida! Você excedeu o limite de quantidade diária de saques, tente novamente outro dia.")

        elif valor > 0:
            saldo -= valor
            extrato += f"Saque: R$ {valor:.2f}\n"
            numero_saques += 1
       
        else:
            print("Operação falhou! O valor informado é inválido.")
           
    #3 - Operações de extrato:
    #Listar todos os depósitos e saques realizados na conta. 
    #No fim da listagem deve ser exibido o saldo atual da conta
    #Os valores devem ser exibidos utilizado o formato R$ xxx.xx: R$ 1500.45

    elif opcao == "e":
        print(">>>>Extrato<<<<")
        print("\nNão foram realizadas movimentações." if not extrato else extrato)
        print(f"\nSaldo: R${saldo:.2f}")        

    elif opcao == "q":
        
        break
    else:
        print("Operação inválida, por favor selecione novamente a operação desejada:")
