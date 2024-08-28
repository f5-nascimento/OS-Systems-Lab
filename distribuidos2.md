import time
import random

class Nodo:
    def __init__(self, nome):
        self.nome = nome

    def processar_subprograma(self, subprograma_id, tempo_processamento):
        print(f"{self.nome} está processando o subprograma {subprograma_id}...")
        time.sleep(tempo_processamento)  # Simula o tempo de processamento
        print(f"Subprograma {subprograma_id} concluído por {self.nome}.")

    def receber_subprograma(self, subprograma_id, tempo_processamento):
        print(f"{self.nome} recebeu o subprograma {subprograma_id}.")
        self.processar_subprograma(subprograma_id, tempo_processamento)

def balancear_carga(nodos, subprograma_id, tempo_processamento):
    nodo_disponivel = nodos[subprograma_id % len(nodos)] 
    print(f"Escolhendo {nodo_disponivel.nome} para processar o subprograma {subprograma_id}.")
    nodo_disponivel.receber_subprograma(subprograma_id, tempo_processamento)

def dividir_tarefa_em_subprogramas(tarefa_id, num_subprogramas):
    print(f"\nDividindo a tarefa {tarefa_id} em {num_subprogramas} subprogramas...")
    subprogramas = []
    for subprograma_id in range(1, num_subprogramas + 1):
        tempo_processamento = random.uniform(1, 5)  
        subprogramas.append((subprograma_id, tempo_processamento))
    return subprogramas


nodos = [Nodo("Nó 1"), Nodo("Nó 2"), Nodo("Nó 3")]


tarefas = [(1, 3), (2, 4), (3, 2), (4, 5), (5, 3)]


for tarefa_id, num_subprogramas in tarefas:
    subprogramas = dividir_tarefa_em_subprogramas(tarefa_id, num_subprogramas)
    print(f"\nIniciando a tarefa {tarefa_id} com {num_subprogramas} subprogramas...")
    for subprograma_id, tempo_processamento in subprogramas:
        balancear_carga(nodos, subprograma_id, tempo_processamento)
    print()
