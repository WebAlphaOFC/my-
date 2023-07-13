# my-

from datetime import datetime


#Aqui o from datetime e o  import datetime permitem acessar diretamente a classe datetime para manipulação de datas e horas


agenda = []


def adicionar_compromisso():
    data = input("Digite a data do compromisso (DD/MM/AAAA): ")
    hora = input("Digite a hora do compromisso (HH:MM): ")
    descricao = input("Digite a descrição do compromisso: ")
    compromisso = {
        "data": data,
        "hora": hora,
        "descricao": descricao
    }

 agenda.append(compromisso)
    print("Compromisso adicionado com sucesso!")
#Aqui captura informações sobre um compromisso fornecidas pelo usuário e adiciona o compromisso à lista agenda#

def visualizar_compromissos():
    print("---- Compromissos na Agenda ----")
    for i, compromisso in enumerate(agenda, start=1):
        print(f"{i}. Data: {compromisso['data']}, Hora: {compromisso['hora']}, Descrição: {compromisso['descricao']}")
    print("--------------------------------")
#Aqui exibe os compromissos presentes na lista agenda, mostrando a data, hora e descrição de cada compromisso#

def visualizar_compromissos_por_periodo():
    inicio = input("Digite a data de início do período (DD/MM/AAAA): ")
    fim = input("Digite a data de fim do período (DD/MM/AAAA): ")

    
try:
    inicio = datetime.strptime(inicio, "%d/%m/%Y")
        fim = datetime.strptime(fim, "%d/%m/%Y")
        print(f"\n---- Compromissos entre {inicio.strftime('%d/%m/%Y')} e {fim.strftime('%d/%m/%Y')} ----")
        for i, compromisso in enumerate(agenda, start=1):
            data_compromisso = datetime.strptime(compromisso['data'], "%d/%m/%Y")
            if inicio <= data_compromisso <= fim:
                print(f"{i}. Data: {compromisso['data']}, Hora: {compromisso['hora']}, Descrição: {compromisso['descricao']}")
        print("--------------------------------")
        
 except ValueError:
        print("Formato de data inválido. Certifique-se de digitar no formato DD/MM/AAAA.")
#Aqui exibe os compromissos da agenda dentro de um período definido pelo usuário, mostrando a data, hora e descrição de cada compromisso e lida com erros de formato de data#


def editar_compromisso():
    visualizar_compromissos()
    indice = int(input("Digite o número do compromisso que deseja editar: ")) - 1
    if indice >= 0 and indice < len(agenda):
        compromisso = agenda[indice]
        print("Selecione o campo que deseja editar:")
        print("1. Data")
        print("2. Hora")
        print("3. Descrição")
        opcao = input("Digite o número da opção desejada: ")


 if opcao == "1":
            nova_data = input("Digite a nova data do compromisso (DD/MM/AAAA): ")
            compromisso["data"] = nova_data
            print("Data do compromisso editada com sucesso!")
        elif opcao == "2":
            nova_hora = input("Digite a nova hora do compromisso (HH:MM): ")
            compromisso["hora"] = nova_hora
            print("Hora do compromisso editada com sucesso!")
        elif opcao == "3":
            nova_descricao = input("Digite a nova descrição do compromisso: ")
            compromisso["descricao"] = nova_descricao
            print("Descrição do compromisso editada com sucesso!")
        else:
            print("Opção inválida! Nenhum campo foi alterado.")
    else:
        print("Número de compromisso inválido!")
#Aqui permite editar um compromisso selecionado da agenda com base nas opções escolhidas pelo usuário#


def remover_compromisso():
    visualizar_compromissos()
    indice = int(input("Digite o número do compromisso que deseja remover: ")) - 1
    if indice >= 0 and indice < len(agenda):
        del agenda[indice]
        print("Compromisso removido com sucesso!")
    else:
        print("Número de compromisso inválido!")
 #Aqui permite remover um compromisso selecionado da agenda com base no número informado pelo usuário#


def menu():

    
while True:
        print("\n>>>>> MENU <<<<<<")
        print("1. Adicionar compromisso")
        print("2. Visualizar compromissos")
        print("3. Visualizar compromissos por período")
        print("4. Editar compromisso")
        print("5. Remover compromisso")
        print("6. Sair")
        opcao = input("Digite o número da opção desejada: ")
        if opcao == "1":
            adicionar_compromisso()
        elif opcao == "2":
            visualizar_compromissos()
        elif opcao == "3":
            visualizar_compromissos_por_periodo()
        elif opcao == "4":
            editar_compromisso()
        elif opcao == "5":
            remover_compromisso()
        elif opcao == "6":
            break
        else:
            print("Opção inválida! Digite novamente.")

            
#Aqui exibe um menu interativo onde o usuário pode escolher entre várias opções, como adicionar, visualizar, editar e remover compromissos, bem como sair do programa#


menu()
