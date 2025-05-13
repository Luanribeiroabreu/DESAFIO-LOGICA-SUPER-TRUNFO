# DESAFIO-LOGICA-SUPER-TRUNFO
class Carta:
    def _init_(self, nome, forca, inteligencia, velocidade):
        self.nome = nome
        self.atributos = {
            "forca": forca,
            "inteligencia": inteligencia,
            "velocidade": velocidade
        }

    def _str_(self):
        return f"{self.nome} - Força: {self.atributos['forca']}, Inteligência: {self.atributos['inteligencia']}, Velocidade: {self.atributos['velocidade']}"

def criar_cartas():
    return [
        Carta("Dragão", 9, 7, 6),
        Carta("Cavaleiro", 6, 5, 7),
        Carta("Mago", 4, 10, 5),
        Carta("Gigante", 10, 3, 4),
        Carta("Elfo", 5, 8, 9),
    ]

def jogar_rodada(carta_jogador, carta_maquina):
    print("\nSua carta:")
    print(carta_jogador)

    escolha = input("Escolha um atributo (forca, inteligencia, velocidade): ").lower()
    if escolha not in carta_jogador.atributos:
        print("Atributo inválido!")
        return

    print("\nCarta da máquina:")
    print(carta_maquina)

    valor_jogador = carta_jogador.atributos[escolha]
    valor_maquina = carta_maquina.atributos[escolha]

    print(f"\nVocê escolheu {escolha}!")
    print(f"{carta_jogador.nome}: {valor_jogador} x {valor_maquina} :{carta_maquina.nome}")

    if valor_jogador > valor_maquina:
        print("Você venceu a rodada!")
    elif valor_jogador < valor_maquina:
        print("A máquina venceu a rodada!")
    else:
        print("Empate!")

def main():
    cartas = criar_cartas()
    while True:
        input("\nPressione Enter para jogar uma rodada ou digite 'sair' para encerrar: ")
        if "sair" in input().lower():
            break

        carta_jogador = random.choice(cartas)
        carta_maquina = random.choice(cartas)

        jogar_rodada(carta_jogador, carta_maquina)

if _name_ == "_main_":
    main()
