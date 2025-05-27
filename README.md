class Açaí:
    def __init__(self, nome, preço):
        self.nome = nome
        self.preço = preço

class Pedido:
    def __init__(self):
        self.itens = []

    def adicionar_item(self, açaí, quantidade):
        self.itens.append({"açaí": açaí, "quantidade": quantidade})

    def calcular_total(self):
        total = 0
        for item in self.itens:
            total += item["açaí"].preço * item["quantidade"]
        return total

    def visualizar_pedido(self):
        print("Pedido:")
        for item in self.itens:
            print(f"- {item['açaí'].nome} x{item['quantidade']} = R${item['açaí'].preço * item['quantidade']:.2f}")
        print(f"Total: R${self.calcular_total():.2f}")

class Loja:
    def __init__(self):
        self.açaís = []
        self.pedidos = []

    def adicionar_açaí(self, açaí):
        self.açaís.append(açaí)

    def fazer_pedido(self):
        pedido = Pedido()
        while True:
            print("Cardápio:")
            for i, açaí in enumerate(self.açaís):
                print(f"{i+1}. {açaí.nome} - R${açaí.preço:.2f}")
            escolha = input("Escolha um açaí (ou 'f' para finalizar): ")
            if escolha.lower() == 'f':
                break
            try:
                escolha = int(escolha) - 1
                if escolha < 0 or escolha >= len(self.açaís):
                    print("Escolha inválida!")
                    continue
                quantidade = int(input("Quantidade: "))
                pedido.adicionar_item(self.açaís[escolha], quantidade)
            except ValueError:
                print("Escolha inválida!")
        self.pedidos.append(pedido)
        pedido.visualizar_pedido()

loja = Loja()

açaí1 = Açaí("Açaí pequeno", 5.00)
açaí2 = Açaí("Açaí médio", 7.00)
açaí3 = Açaí("Açaí grande", 10.00)

loja.adicionar_açaí(açaí1)
loja.adicionar_açaí(açaí2)
loja.adicionar_açaí(açaí3)

while True:
    print("Loja de Açaí")
    print("1. Fazer pedido")
    print("2. Sair")
    escolha = input("Escolha uma opção: ")
    if escolha == "1":
        loja.fazer_pedido()
    elif escolha == "2":
        break
    else:
        print("Opção inválida!")
