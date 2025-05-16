#Solicita nome do titular
nome_titular = input("Informe o nome da conta do titular: ")

#Abetura da conta(Deposito inicial)
while True:
    deposito_inicial = input("Digite o valor de deposito inicial: ")
    if deposito_inicial.replace(".","",1).isdigit():
        deposito_inicial = float(deposito_inicial)
        if deposito_inicial >= 0:
            conta = (nome_titular, [deposito_inicial],[])
            
            break
        else:
            print("Valor Inválido! Digite um número")
    else:
        print("Valor Inválido! Digite um número:")

#Opções (Depositar, Sacar, Consultar saldo, Consultar historico, sair)

while True:     
    print("----Escolha uma operação:---")
    print("\n1-Depositar \n2-Sacar \n3-Cosultar saldo \n4-Consultar histórico \n5-sair ")
    opcao = input("Escolha uma opção: ")

    if opcao == "1":
        while True:
            valor_deposito = input("Digite um valor de deposito: ")
            if valor_deposito.replace(".","",1).isdigit():
                valor_deposito = float(valor_deposito)
                if valor_deposito >= 0:
                    #valor_deposito += conta[1][0]
                    #Soma o valor do saldo
                    conta[1][0] += valor_deposito
                    #Adiciona ao historico
                    conta[2].append("Depósito de R$: {} ".format(valor_deposito))
                    print("Deposito realizado com sucesso")
                    break
                else:
                    print("Valor inválido.")
            else: 
                print("Entrada inválida. Digite um número.")
    elif opcao == "2":
        print("Sacar")
        while True:
            valor_deposito = input("Digite um valor: ")
            if valor_deposito.replace(".","",1).isdigit():
                valor_deposito = float(valor_deposito)
                if valor_deposito >= 0:
                    if valor_deposito <= conta[1][0]:
                        conta[1][0] -= valor_deposito
                        conta[2].append(f"Deposito de R$: {valor_deposito}")
                        print("Saque foi realizado de saque")
                        break
                    else:
                        print("Valor Inválido")
                else:
                    print("Entrada Inválida. Digite um número.")
    elif opcao == "3":
        print(f"Saldo Atual: {conta[1][0]}")
    elif opcao == "4":
        print("Histórico")
        if conta[2]:
            for item in conta[2]:
                print(f" - {item}")
    elif opcao == "5":
        print("Agradecemos por usar nosso Banco.")
        break
    else: 
        print("Opção Inválida. Por favor, escolha uma opção do menu.")

#if opcao == 2:
    #while True:
        #saque = float(input('Qual será o valor de saque?'))
        #if saque <= 0:
            #print("Valor inválido!")
        #elif saque > saldo:
            #print("Valor não disponível!")
        #elif saque == saldo:
         #print("Saque feito com sucesso.")
#else:
    #saldo = valor_deposito - saque
#print("Realizado com sucesso.")
#print("Saldo restante, {saldo}")

